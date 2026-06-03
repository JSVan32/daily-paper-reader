---
title: Neural networks learn forward dynamics when freed from numerical integration
title_zh: 免于数值积分时神经网络学习正向动力学
authors: "Bahdasariants, S., Yakovenko, S."
date: 2026-06-01
pdf: "https://www.biorxiv.org/content/10.64898/2026.05.27.728310v1.full.pdf"
tags: ["query:msk-rl"]
score: 8.0
evidence: 用神经网络学习肌肉骨骼系统前向动力学以用于控制
tldr: 人机接口中预测肢体动力学的神经网络常因数值积分导致不稳定。本文提出人工物理引擎（APE），将运动方程近似与时间积分分离，避免了直接映射循环神经网络（RNN）的数值误差。在外部扰动下，APE预测误差低且稳定，而直接映射RNN产生不一致结果。这表明通过物理因果结构约束网络，可提升对变异的鲁棒性，为鲁棒人机接口设计提供新思路。
source: biorxiv
selection_source: fresh_fetch
motivation: 直接映射神经网络在预测向前动力学时存在数值不稳定性，需解决运动方程近似与时间积分的计算对称性。
method: 提出人工物理引擎（APE），将运动方程近似与数值积分分离为两阶段模型，替代直接映射RNN。
result: 在外部扰动和新型初始条件下，APE预测误差低且稳定，而直接映射RNN产生与交互力矩不符的大误差。
conclusion: 以运动方程形式映射系统动力学，通过因果物理结构提高了对内外变异源的鲁棒性。
---

## 摘要
人类与机器之间的无缝交互需要接口对生物信号和物理环境中固有的变异性保持鲁棒性。先进的人机接口越来越多地依赖机器学习来预测或控制肢体动力学。这些系统必须学习控制变量与肢体状态之间的输入-输出映射，例如从作用于分段手臂关节的肌肉力或关节力矩到随时间变化的肢体姿态的映射。这种统计的输入-输出变换可能导致预测的肌肉骨骼运动学和动力学的数值不稳定性。实现生物运动控制的鲁棒性需要同时解决正向和逆向动力学问题；然而，这些问题在计算上是不对称的，因为它们涉及相反的操作——积分和微分。由于我们之前已经证明，当训练神经网络在达到过程中将运动学信号映射到动力学信号时，它们能解决逆向动力学问题，因此我们假设，分别表示运动方程(EOM)的近似及其时间数值积分可能捕捉到正向动力学问题的相关计算结构。我们通过比较传统的直接映射递归神经网络(RNN)与两阶段模型——人工物理引擎(APE)来检验这一假设。在预测训练中未遇到的外部扰动下的两段系统状态时，直接映射的单一模型产生了与预期交互力矩不一致的大预测误差，而APE在新型初始条件和扰动下保持低误差并保持稳定。以运动方程的形式映射系统动力学，通过在人机接口设计中施加因果的、基于物理的结构，提高了对内在和外在变异性源的鲁棒性。

## Abstract
Seamless interaction between humans and machines requires interfaces that remain robust to the variability inherent in biological signals and physical environments. Advanced human-machine interfaces (HMIs) increasingly rely on machine learning to predict or control limb dynamics. These systems must learn input-to-output mappings between control variables and limb state, such as the mapping from muscle forces or joint torques acting about segmented arm joints to limb posture over time. Such statistical input-to-output transformations can result in numerical instability of predicted musculoskeletal kinematics and dynamics. Achieving the robustness of biological motor control requires solving both forward and inverse dynamics problems; however, these problems are computationally asymmetric because they entail opposing operations-integration and differentiation. Since we have previously shown that neural networks solve the inverse dynamics problem when trained to map kinematic to dynamic signals during reaching, we hypothesized that representing separately the approximation of equations of motion (EOM) and their temporal numerical integration may capture the relevant computational structure of the forward dynamics problem. We tested this hypothesis by comparing a conventional direct-mapping recurrent neural network (RNN) with a two-stage model, the artificial physics engine (APE). When predicting the state of a two-segment system under external perturbations not encountered during training, the direct-mapping, monolithic model produced large prediction errors inconsistent with the expected interaction torque, whereas the APE maintained low error and remained stable under novel initial conditions and perturbations. Mapping system dynamics in the terms of the EOM improves robustness against intrinsic and extrinsic sources of variability by imposing a causal, physics-based structure on HMI design.

---

## 论文详细总结（自动生成）

好的，以下是根据您提供的论文内容生成的详细中文总结，采用 Markdown 格式并按指定要点展开。

---

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：在人机接口（HMI）中，使用神经网络直接学习从控制变量（如肌肉力、关节力矩）到肢体状态（如关节角度、速度）的前向动力学映射时，会因数值积分误差累积而出现预测不稳定、误差大的问题。这种“直接映射”的统计学习方法忽略了运动方程与时间积分在计算结构上的根本不对称性。
- **研究动机**：生物运动控制能同时解决正向（微分→积分）和逆向（积分→微分）动力学问题，但当前机器学习方法往往将正向动力学作为一个“黑箱”映射，导致鲁棒性不足。作者先前已证明神经网络可有效解决逆向动力学（从运动学到动力学），因此假设将正向动力学分解为运动方程近似与数值积分两个阶段，能更好地捕捉其计算结构，从而提高鲁棒性。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出“人工物理引擎”（Artificial Physics Engine, APE），将正向动力学的学习分为两个独立的阶段：
  1. **运动方程（EOM）近似阶段**：用一个神经网络（例如前馈或RNN）学习从当前状态（位置、速度）和输入力矩到加速度的映射，即 $a = f(x, u)$。
  2. **数值时间积分阶段**：将预测的加速度通过一个固定、可微分的数值积分器（如欧拉法或龙格-库塔法）更新状态，得到下一时刻的速度和位置。积分器本身不含可学习参数，仅执行确定性计算。
- **对比方法**：传统的**直接映射递归神经网络（RNN）**，该网络端到端地直接学习从当前状态和输入力矩到下一时刻状态的映射，即 $x_{t+1} = g(x_t, u_t)$，将动力学与积分合并为一个统计模型。

### 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

- **数据集/场景**：两段式（两关节）手臂系统，模拟前向动力学。训练数据由标准运动（如未受扰动的到达运动）生成。测试时引入**外部扰动**（如外力矩）和**新型初始条件**，这些在训练中从未出现。
- **Benchmark**：以真实物理模型的仿真数据作为地面真值（Ground Truth），比较预测的状态误差（位置、速度）以及交互力矩的一致性。
- **对比方法**：
  - 直接映射 RNN（单阶段、端到端）
  - 人工物理引擎 APE（两阶段，EOM近似 + 数值积分）

### 4. 资源与算力

- 论文摘要及元数据中**未明确说明**使用的 GPU 型号、数量、训练时长或任何计算资源。仅从论文语境推测为中等规模的仿真训练（模拟二维两关节系统），可能不需要昂贵的硬件。关于算力信息缺失这一点，需在总结中明确指出。

### 5. 实验数量与充分性

- **实验数量**：仅报告了针对“两段系统在外部扰动下”的预测对比结果，并提及“新型初始条件”下的表现。未提及多组不同数据集、不同系统复杂度（如更高自由度、真实肌肉骨骼模型）的消融实验或参数敏感性分析。
- **充分性与客观性**：实验设计对比了直接映射与 APE，但覆盖范围较窄（单一系统、单一扰动模式）。结论有一定说服力，但缺乏统计检验（如多次随机初始化、不同扰动强度等）和更全面的基准比较。因此**充分性不足**，公平性方面，由于直接映射 RNN 的结构本身已被作者论证存在数值不稳定，对比可能有偏向性。

### 6. 论文的主要结论与发现

- 在外部扰动和新初始条件下，直接映射 RNN 产生与预期交互力矩不一致的大预测误差，而 APE 保持低误差且稳定。
- APE 通过将运动方程近似与积分分离，引入因果的、基于物理的结构，提高了对内在（如初始条件变化）和外在（如外部扰动）变异源的鲁棒性。
- 结论：正向动力学问题的有效学习不应依赖于纯统计映射，而应利用物理方程的结构信息。

### 7. 优点：方法或实验设计上的亮点

- **方法创新**：将正向动力学分解为物理模型（EOM）与确定性积分器，合理反映了正向问题的计算不对称性，简单且可解释。
- **实验设计亮点**：特意选择在训练未见的扰动下测试，直接突显了 APE 的鲁棒性优势。
- **理论意义**：为设计更鲁棒的人机接口提供了新思路——通过因果物理约束替代纯数据驱动的端到端学习。

### 8. 不足与局限

- **实验覆盖不足**：仅测试了一个两段手臂模型，未扩展到更多自由度、真实肌肉骨骼系统、或有噪声的传感器数据。结论的泛化性存疑。
- **偏差风险**：直接映射 RNN 可能在优化过程中陷入局部最优，对比可能未充分调优；同时未报告 APE 的网络结构复杂度、超参数选择等细节。
- **应用限制**：该方法假设我们可以获得加速度标签或训练数据中加速度可精确计算，但实际上很多现实场景可能仅有位置观测。此外，数值积分器步长的选择、模型离散化误差等也可能影响 APE 性能。
- **算力与复现**：未说明使用的GPU/训练时长，且元数据提到论文来自 bioRxiv 且需要安全验证，可能尚未公开发布代码或完整实验细节，不利于复现验证。

---

（完）
