---
title: "How a Predictive State Observer Can Self-Adapt Its Sensory Prediction-Error Correction Gain: Closed-Loop Evidence from a Muscle-Driven Reaching Task"
title_zh: 预测状态观测器如何自适应调整感官预测误差校正增益：来自肌肉驱动到达任务的闭环证据
authors: "Kobayashi, J."
date: 2026-06-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.03.729790v1.full.pdf"
tags: ["query:msk-rl"]
score: 6.0
evidence: 肌肉驱动到达任务中的预测状态观测器
tldr: 基于前向模型的预测状态观察器如何自主调整感官预测误差校正增益是关键问题。在34肌肉MyoSuite臂的到达任务中，使用残差MLP前向模型和闭环控制器训练自适应增益。无感官延迟时中间增益最优，18步延迟时高增益更优；可靠性自适应观测器在延迟场景改进1.9-2.5 cm，但仍差于固定增益最优值。研究揭示了延迟依赖的校正结构及仅前向模型的失效模式，并指出当前自适应校正的局限性。
source: biorxiv
selection_source: fresh_fetch
motivation: 探究前向模型预测状态观察器能否仅从智能体可用信号（创新历史与每次到达结果）自适应设置校正增益，而非依赖全局最优标签。
method: 在34肌肉MyoSuite臂的以下肩部到达任务中，部署残差MLP前向模型与闭环端点探针控制器，训练可靠性自适应观测器和特征条件β适配器。
result: 无延迟时中间校正增益(K=0.25-0.50)最优；18步延迟时高增益(K=1.0)最优。自适应方法在延迟场景提升1.9-2.5 cm，但比固定增益最优值差1.4-1.8 cm。
conclusion: 证实了延迟依赖的校正结构和仅前向模型(K=0)的失败模式，但基于智能体可用信号的自适应校正仍存在性能上限。
---

## 摘要
我们探讨了基于前向模型的预测状态观测器在肌肉驱动到达任务中应如何设置其感官预测误差校正增益，以及该增益是否可以从智能体可获得的信号（创新历史与每次尝试的到达结果）中自适应调整，而非通过扫描的或标签。我们在具有34块肌肉的MyoSuite手臂上，在一个IK可达的肩下任务中，评估了一个残差MLP前向模型，该模型与一个稳定的端点探针控制器闭环部署，该控制器使用非负最小二乘肌肉路由和虚拟目标斜坡；该控制器是用于评估状态估计效果的稳定探针，而非生物运动规划器。扫描固定增益的闭环标签揭示了延迟相关的校正结构：无感官延迟时，中等校正增益最佳（K=0.25-0.50），而18步延迟时，观察重校正占优（K=1.0）。仅前向模型的K=0消融并非标签：它比最佳固定K系统性差1.9-6.1厘米，并且由于长时域自回归漂移导致NNLS控制器残差很大；因此我们将K=0作为诊断。基于结果训练的可信度自适应观测器在延迟状态下比默认可信度提高了1.9-2.5厘米，而在无延迟状态下保持中性，此时标签已是中等。一个特征条件化的β适配器将细胞级创新统计量映射到场级增益参数，在5/6个细胞中几乎匹配细胞级训练的诊断，但在18步延迟时两者仍比扫描固定K标签差1.4-1.8厘米。这些结果分离了延迟依赖的校正结构、仅前向模型的K=0失效模式，以及智能体可用的自适应校正的剩余限制。

## Abstract
We ask how a forward-model-based predictive state observer should set its sensory prediction-error correction gain during muscle-driven reaching, and whether that gain can be adapted from agent-available signals -- innovation history and per-episode reaching outcome -- rather than from swept oracle labels. We evaluate a residual-MLP forward model in a 34-muscle MyoSuite arm on an IK-reachable below-shoulder task, deployed in closed loop with a stabilized endpoint probe controller that uses non-negative least-squares muscle routing and a virtual target ramp; the controller is a stabilized probe for evaluating state-estimation effects, not a biological motor planner. A swept fixed-gain closed-loop oracle reveals a delay-dependent correction structure: with no sensory delay, intermediate correction gains are best (K = 0.25-0.50), whereas with 18-step delay observation-heavy correction wins (K = 1.0). The forward-model-only K = 0 ablation is not the oracle: it is systematically worse than the best fixed K by 1.9-6.1 cm and shows large NNLS controller residuals caused by long-horizon autoregressive drift; we therefore report K = 0 as a diagnostic. Outcome-trained reliability-adaptive observers improve the delayed regime by 1.9-2.5 cm over default reliability while remaining neutral in no-delay cells, where the oracle is already intermediate. A feature-conditioned {beta} adapter that maps cell-level innovation statistics to per-field gain parameters nearly matches a per-cell trained diagnostic in 5/6 cells, but both remain 1.4-1.8 cm worse than the swept fixed-K oracle at 18-step delay. These results separate the delay-dependent correction structure, the forward-model-only failure mode of K = 0, and the remaining limits of agent-available adaptive correction.