---
title: "ANNet: A first-principles neural network for forward and inverse dynamics"
title_zh: ANNet：用于正向和逆向动力学的第一性原理神经网络
authors: "Bahdasariants, S., Parola, L., Kacker, K., Feldman, A. K., Zdobinski, Z., Kang, I., Weber, D. J."
date: 2026-06-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.03.729998v1.full.pdf"
tags: ["query:msk-rl"]
score: 7.0
evidence: 物理信息神经网络用于正/逆向动力学，可应用于生物力学模拟
tldr: 生物和机器人系统必须求解逆动力学和正动力学，但现有方法常将两者分离，忽略了共享物理结构。本文提出一种基于第一性原理的神经网络ANNet，通过学习单一标量函数——Appell加速度能量，将逆动力学转化为能量对加速度的梯度，正动力学则通过优化同一能量函数实现。在双摆范例上，网络在未见过的测试中实现了实时准确的逆动力学和正向仿真。该工作为利用单一学习表示同时支持运动预测和控制提供了一条原理性路径。
source: biorxiv
selection_source: fresh_fetch
motivation: 现有方法将逆动力学和正动力学分离建模，忽略了共享的物理结构，导致效率低下且泛化受限。
method: 提出ANNet，学习Appell加速度能量，通过梯度计算逆动力学，通过优化最小化同一能量实现正动力学。
result: 在双摆系统上，ANNet在未见过的测试中实时准确，逆动力学和基于优化的正向仿真均达到实时精度。
conclusion: 首次证明单一学习表示可同时支持预测和控制的双重计算，为运动控制提供第一性原理方法。
---

## 摘要
生物和机器人系统必须解决两个相关的计算问题来运动：逆向动力学，即确定产生期望运动所需的力或力矩，以及正向动力学，即将施加的力映射为运动。尽管这两个计算由相同的运动方程耦合，但在基于模型和数据驱动的公式中，它们通常被估计或实现为不同的逆向和正向映射。这种分离可能掩盖了约束这两个问题的共享结构。在这里，我们提出了ANNet，一种物理信息神经网络，通过从经典力学中学习一个标量量——阿佩尔加速度能量，将两个计算置于一个共同的习得表示上。该网络将运动学状态和候选加速度映射到这个标量函数，通过将习得能量函数对加速度求导以恢复关节力矩，从而获得逆向动力学。然后，通过将相同的习得能量景观嵌入到一个优化目标中（其无约束最小值满足吉布斯-阿佩尔方程），无需重新训练即可计算正向动力学。得到的加速度随时间向前积分。我们在双摆范例上评估了ANNet。在训练期间网络未见过的试验中，基于逆向和优化的正向仿真是实时的且准确。我们的结果为使用单一习得表示来支持预测和控制提供了一条第一性原理的途径。

## Abstract
Biological and robotic systems must solve two related computations to move: inverse dynamics, which determines the forces or torques needed to produce a desired movement, and forward dynamics, which maps applied forces to motion. Although these computations are coupled by the same equations of motion, they are usually estimated or implemented as distinct inverse and forward mappings, in both model-based and data-driven formulations. This separation can obscure the shared structure that constrains both problems. Here, we present ANNet, a physics-informed neural network that places both computations on a common learned representation by learning a single scalar quantity from classical mechanics--Appell acceleration energy. The network maps kinematic state and candidate accelerations to this scalar function, and inverse dynamics is obtained by differentiating the learned energy function with respect to acceleration to recover joint torques. Forward dynamics is then calculated without retraining by embedding the same learned energy landscape in an optimization objective whose unconstrained minimum satisfies the Gibbs-Appell equation. The resulting accelerations are integrated forward in time. We evaluate ANNet on a double pendulum paradigm. In trials unseen by the network during training, inverse and optimization-based forward simulations are real-time accurate. Our results provide a first-principles route for using a single learned representation to support both prediction and control.