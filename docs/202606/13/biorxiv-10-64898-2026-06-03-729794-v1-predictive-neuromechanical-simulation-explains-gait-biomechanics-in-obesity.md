---
title: Predictive Neuromechanical Simulation Explains Gait Biomechanics in Obesity
title_zh: 预测性神经力学模拟解释肥胖中的步态生物力学
authors: "Choi, C. W., Ton, V., Gill, S. V., Song, S."
date: 2026-06-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.03.729794v1.full.pdf"
tags: ["query:msk-rl"]
score: 7.0
evidence: 预测性神经力学模拟步态生物力学
tldr: 肥胖导致步态异常，但机制不明。本研究采用预测性神经力学模拟，结合肌肉骨骼变化和运动目标优化，发现仅生理变化无法复现步态，而加入膝关节负荷惩罚目标后有效重现了膝关节屈曲减少、肌肉协调改变、步速减慢和步长缩短等特征。模拟揭示了肥胖步态可能源于调节膝关节负荷的协调策略。
source: biorxiv
selection_source: fresh_fetch
motivation: 探索肥胖相关步态适应机制及其对膝关节骨关节炎负荷的影响。
method: 使用反射式神经步行模型，对非肥胖和肥胖体态进行预测模拟，优化肌肉努力和膝关节负荷权重。
result: 肥胖模型需组合目标惩罚膝关节负荷才能重现步态特征；质量分布影响温和，体质量增加主导步态变化。
conclusion: 肥胖步态是协调策略降低膝关节负荷的结果，预测模拟有助于揭示肥胖与步态生物力学的因果机制。
---

## 摘要
肥胖个体表现出步态适应性，包括早期支撑期膝关节屈曲减少、肌肉协调改变、偏好行走速度减慢和步长缩短。尽管这些特征已被充分记录，但肥胖相关的生理变化如何产生这些模式并影响与骨关节炎（OA）相关的膝关节负荷的机制仍不清楚。本研究采用预测性神经力学模拟，探讨肌肉骨骼变化与运动目标如何相互作用，从而产生肥胖相关的步态模式和胫股关节负荷。使用基于反射的神经力学行走模型进行预测性模拟。将基线非肥胖模型（1.8米，80公斤）修改为代表肥胖相关的节段质量分布和肌肉力量变化（1.8米，140公斤），包括更苹果型和更梨型的体质量分布。优化控制参数以产生稳定行走，同时最小化肌肉做功和胫股关节负荷。通过将模拟的膝关节运动学与典型行走速度下的实验观察相匹配，确定目标权重。使用选定的权重，我们比较了关节运动学、动力学和肌肉激活，并在不同行走速度下进行模拟，以评估最优行走速度、步长、肌肉做功和膝关节负荷。基线模型仅使用肌肉做功目标就最佳匹配了参考膝关节运动学，而肥胖模型则需要一个同时惩罚肌肉做功和膝关节负荷的联合目标。这种公式重现了关键的步态特征，包括早期支撑期膝关节屈曲减少、股内侧肌群激活减少而跖屈肌激活增加、最优行走速度减慢以及步长缩短。与体质量增加带来的较大影响相比，体质量分布的变化对步态力学产生了中等但一致的影响。仅凭肥胖相关的体质量和肌肉力量变化并不能重现观察到的步态模式，但加入惩罚膝关节负荷的目标则产生了多个特征性变化。预测性神经力学模拟提供了一个框架，用于识别连接肥胖、步态生物力学和膝关节负荷的候选机制。

作者总结：理解肥胖如何以及为何改变步态是一个复杂的生物力学问题，涉及多个相互作用因素，包括节段质量增加、惯性特性改变和相对肌肉力量下降。这些因素的相互作用方式难以通过实验观察单独分离。在这里，我们使用计算机模拟来研究肌肉骨骼变化和运动目标如何相互作用，从而产生肥胖相关的步态模式和膝关节负荷。我们发现，仅生理变化并不能重现观察到的步态特征，而加入惩罚膝关节负荷的目标则同时产生了多个特征性变化，包括早期支撑期膝关节屈曲减少、肌肉协调改变、最优行走速度减慢和步长缩短。这些发现表明，肥胖相关的步态反映了在体质量增加下调节膝关节负荷的协调策略。

## Abstract
Individuals with obesity exhibit gait adaptations including reduced early-stance knee flexion, altered muscle coordination, slower preferred walking speeds, and shorter step lengths. Although these features are well documented, the mechanisms by which obesity-related physiological changes produce these patterns and influence knee joint loading relevant to osteoarthritis (OA) remain unclear. This study used predictive neuromechanical simulation to examine how musculoskeletal changes and movement objectives interact to generate obesity-associated gait patterns and tibiofemoral loading. Predictive simulations were performed using a reflex-based neuromechanical walking model. A baseline non-obese model (1.8 m, 80 kg) was modified to represent obesity-related changes in segment mass distribution and muscle strength (1.8 m, 140 kg), including more apple-like and more pear-like body mass distributions. Control parameters were optimized to generate stable walking while minimizing muscle effort and tibiofemoral joint loading. Objective weightings were identified by matching simulated knee kinematics to experimental observations at a typical walking speed. Using the selected weightings, we compared joint kinematics, kinetics, and muscle activations, and simulations were performed across walking speeds to evaluate optimal walking speed, step length, muscle effort, and knee loading. The baseline model best matched reference knee kinematics using a muscle-effort objective alone, whereas the obese model required a combined objective penalizing both muscle effort and knee loading. This formulation reproduced key gait features, including reduced early-stance knee flexion, reduced vastii activation with increased plantarflexor activation, slower optimal walking speeds, and shorter step lengths. Variations in body mass distribution produced moderate but consistent effects on gait mechanics relative to larger effects of increased body mass. Obesity-related changes in body mass and muscle strength alone did not reproduce observed gait patterns, but incorporating an objective that penalizes knee loading generated multiple characteristic features. Predictive neuromechanical simulation provides a framework for identifying candidate mechanisms linking obesity, gait biomechanics, and knee joint loading.

Author SummaryUnderstanding how and why obesity alters gait is a complex biomechanical problem involving multiple interacting factors including increased segmental mass, altered inertial properties, and reduced relative muscle strength. These factors interact in ways that are difficult to isolate through experimental observation alone. Here, we used computer simulations to examine how musculoskeletal changes and movement objectives interact to generate obesity-associated gait patterns and knee loading. We found that physiological changes alone did not reproduce observed gait features, whereas incorporating an objective that penalizes knee loading generated multiple characteristic features simultaneously, including reduced early-stance knee flexion, altered muscle coordination, slower optimal walking speeds, and shorter step lengths. These findings suggest that obesity-associated gait reflects coordination strategies that regulate knee loading under increased body mass.