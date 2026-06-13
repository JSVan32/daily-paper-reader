---
title: "Reliability-weighted target-position estimation in a musculoskeletal arm model: adaptive priors and learned source weighting under violations of fixed-precision assumptions"
title_zh: 肌肉骨骼手臂模型中可靠性加权的目标位置估计：固定精度假设违反下的自适应先验与学习源加权
authors: "Kobayashi, J."
date: 2026-06-11
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.08.730995v1.full.pdf"
tags: ["query:msk-rl"]
score: 6.0
evidence: 肌肉骨骼手臂模型中的可靠性加权整合
tldr: 在肌肉骨骼手臂模型中，可靠性加权整合是线索组合的规范方法，但面对违反固定精度假设时其局限性尚不明确。本研究通过场域架构中的视觉、前向预测和任务先验进行精度加权，并引入自适应先验和学习的softmax积分器。实验表明，精度加权在校准条件下充分，而自适应统计或学习源加权在假设变化或失败时能改善目标位置估计。这些结果界定了计算边界，为复杂环境下的感知整合提供了新见解。
source: biorxiv
selection_source: fresh_fetch
motivation: 探究肌肉骨骼模型中可靠性加权整合在违反固定精度假设时的表现，明确自适应与学习扩展的适用条件。
method: 采用场域架构，通过精度加权整合视觉、前向预测和任务先验，并引入自适应先验及学习softmax积分器处理误差。
result: 精度加权在校准条件下有效；自适应和扩展在未校准、异常值下改善估计，但优势源于源加权而非逐帧检测。
conclusion: 界定计算边界：固定精度假设成立时精度加权足够，否则自适应或学习扩展不可或缺。
---

## 摘要
可靠性加权整合是线索组合的规范解释，但在肌肉骨骼模型以及需要自适应或学习扩展的条件下，其适用范围仍不清楚。我们在MyoSuite手臂中研究了场级架构下的目标位置估计，该架构代表视觉、本体感觉、前向预测和任务先验。在目标位置实验中，通过精度加权组合了视觉、前向预测以及（如果适用）任务先验；本体感觉为其他状态场提供信息。在开环状态估计层面，当视觉可靠性降低时，一个可信但错误的先验会导致目标估计偏差增大；在低噪声下会跟随错误的视觉线索，在高噪声下则忽略它；两种效应都遵循偏差≈ w × 偏移模式。在多次试验中，自适应先验跟踪了目标均值的偏移，而方差跟踪则随着目标分布的增加降低了先验权重。对于校准的高斯合成观测通道，学习到的softmax积分器相对于精度加权达到了预设的奇偶性标准，并且在报告方差未校准、通道误差有偏、重尾或相关时改善了估计。对于来自两个保留的MyoSuite rollout种子的目标位置观测，在校准预测错误和注入视觉异常情况下，离线重放期间种子间的方向性改进一致。在异常状态下的MSE收益反映了状态级别的源加权，而非一致的单次试验异常检测。这些结果定义了一个计算边界：在此处测试的校准条件下，精度加权是足够的，而当假设发生变化或失败时，自适应统计或学习源加权变得有用。来自手臂模型的证据仅限于目标位置估计；终点传播仍未解决。

## Abstract
Reliability-weighted integration is a normative account of cue combination, but its scope in musculoskeletal models and conditions requiring adaptive or learned extensions remains unclear. We studied target-position estimation in a MyoSuite arm within a field-wise architecture representing vision, proprioception, forward prediction, and a task prior. Target-position experiments combined vision, forward prediction, and, where applicable, the task prior by precision weighting; proprioception informed other state fields. At the open-loop state-estimate level, a trusted but wrong prior biased the target estimate more as visual reliability decreased, and a false visual cue was followed under low noise and discounted under high noise; both effects followed the bias {approx} w x offset pattern. Across trials, an adaptive prior tracked shifts in the target mean, while variance tracking reduced the prior weight as the target spread increased. A learned softmax integrator met the prespecified parity criterion relative to precision weighting for calibrated Gaussian synthetic observation channels and improved estimation when reported variance was miscalibrated, or channel errors were biased, heavy-tailed, or correlated. On target-position observations from two held-out MyoSuite rollout seeds, improvements under prediction miscalibration and injected visual outliers were directionally consistent across seeds during offline replay. The MSE benefit in the outlier regime reflected regime-level source weighting rather than consistent per-trial outlier detection. These results define a computational boundary: precision weighting was sufficient in the calibrated conditions tested here, whereas adaptive statistics or learned source weighting became useful when assumptions changed or failed. Evidence from the arm model is limited to target-position estimates; endpoint propagation remains unresolved.