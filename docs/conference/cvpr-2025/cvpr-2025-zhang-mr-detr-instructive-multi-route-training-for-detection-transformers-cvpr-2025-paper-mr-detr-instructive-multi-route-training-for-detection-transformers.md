---
title: "Mr. DETR: Instructive Multi-Route Training for Detection Transformers"
title_zh: Mr. DETR：检测变压器的指导性多路径训练
authors: "Zhang, Chang-Bin, Zhong, Yujie, Han, Kai"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Zhang_Mr._DETR_Instructive_Multi-Route_Training_for_Detection_Transformers_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 10.0
evidence: 针对检测变压器的多路径训练机制，将解码器组件视为多任务学习器
tldr: 现有方法通过辅助一对多分配增强检测变压器训练，但未充分利用解码器组件潜力。本文提出Mr. DETR多路径训练机制，将模型视为同时进行一对一和一对多预测的多任务框架，并发现解码器中任何独立组件都能有效学习双重目标。基于此，设计了主路径和辅助训练路径。实验表明该方法在不改变架构的情况下提升了检测性能，为Transformer检测器训练优化提供了新视角。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-mr-detr-instructive-multi-route-training-for-detection-transformers-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 875, \"height\": 672, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-mr-detr-instructive-multi-route-training-for-detection-transformers-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 868, \"height\": 313, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-mr-detr-instructive-multi-route-training-for-detection-transformers-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1810, \"height\": 395, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-mr-detr-instructive-multi-route-training-for-detection-transformers-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1818, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-mr-detr-instructive-multi-route-training-for-detection-transformers-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 867, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-mr-detr-instructive-multi-route-training-for-detection-transformers-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1823, \"height\": 418, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-mr-detr-instructive-multi-route-training-for-detection-transformers-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 818, \"height\": 597, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-mr-detr-instructive-multi-route-training-for-detection-transformers-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1801, \"height\": 1555, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-mr-detr-instructive-multi-route-training-for-detection-transformers-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 866, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-mr-detr-instructive-multi-route-training-for-detection-transformers-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1811, \"height\": 532, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-mr-detr-instructive-multi-route-training-for-detection-transformers-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 863, \"height\": 275, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-mr-detr-instructive-multi-route-training-for-detection-transformers-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 874, \"height\": 313, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-mr-detr-instructive-multi-route-training-for-detection-transformers-cvpr-2025-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 804, \"height\": 324, \"label\": \"Table\"}]"
motivation: 现有检测变压器训练未充分探索解码器组件在多种分配下的学习能力。
method: 提出多路径训练机制，主路径一对一预测，辅助路径一对多预测，共享组件。
result: 解码器组件可同时学习两种目标，多路径训练提升了检测性能。
conclusion: 多路径训练有效挖掘了检测变压器的潜力，为高效训练提供了新方法。
---

## Abstract
Existing methods enhance the training of detection transformers by incorporating an auxiliary one-to-many assignment. In this work, we treat the model as a multi-task framework, simultaneously performing one-to-one and one-to-many predictions. We investigate the roles of each component in the transformer decoder across these two training targets, including self-attention, cross-attention, and feed-forward network. Our empirical results demonstrate that any independent component in the decoder can effectively learn both targets simultaneously, even when other components are shared. This finding leads us to propose a multi-route training mechanism, featuring a primary route for one-to-one prediction and two auxiliary training routes for one-to-many prediction. We enhance the training mechanism with a novel instructive self-attention that dynamically and flexibly guides object queries for one-to-many prediction. The auxiliary routes are removed during inference, ensuring no impact on model architecture or inference cost. We conduct extensive experiments on various baselines, achieving consistent improvements as shown in Fig. 1. Project page: https://visual-ai.github.io/mrdetr

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：检测Transformer（DETR）因其一对一匹配策略收敛缓慢，现有方法通过引入辅助的一对多匹配来加速训练，但对于解码器中各组件（自注意力、交叉注意力、前馈网络）在同时处理两种匹配目标时的作用缺乏系统研究。
- **背景与动机**：DETR系列检测器采用一对一分配，避免了NMS，但稀疏监督导致训练效率低。许多辅助训练方法（如H-DETR, DN-DETR, Group-DETR, DAC-DETR, MS-DETR）尝试加入一对多监督以改善定位质量，但它们往往只考察单任务设定，或者粗暴地共享/分割解码器组件。本文希望将模型视为多任务框架，严谨探究组件共享与独立对双重目标学习的影响，从而设计更有效的辅助训练机制。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：将模型构建为多任务框架，同时进行一对一和一对多预测。通过实验发现解码器中任何独立组件都能有效学习两种目标，且共享其他组件时仍能显著提升一对一预测性能。基于此提出“多路径训练机制”（Multi-route Training），包含一条主路径（一对一）和两条辅助路径（一对多），辅助路径在推理时丢弃。
- **方法细节**：
  - **辅助路径设计**：
    - Route-2（主路径）：`Q2 = (FFN_o2o ◦ CA ◦ SA)(Q)`，用标准一对一损失。
    - Route-1（独立FFN路径）：`Q1 = (FFN_o2m ◦ CA ◦ SA)(Q)`，共享自注意和交叉注意，但使用独立的FFN进行一对多预测。
    - Route-3（指导性自注意力路径）：`Q3 = (FFN_o2o ◦ CA ◦ InstructSA ◦ E)(Concat(Q, Q_ins))`，其中 `InstructSA` 与主路径共享参数，但通过引入可学习的 **指令令牌（Instruction Tokens）** 与对象查询拼接，经自注意力后丢弃指令令牌的输出，仅利用其传递信息，实现一对多预测的动态引导。
  - **指令令牌设计**：将 `m` 个可学习令牌 `Q_ins` 与对象查询 `Q` 拼接，经自注意力后，保留对象查询对应输出传给后续网络。相较于加法方式或独立查询方式，拼接更为灵活，可自适应引导对象查询进行一对多预测。
  - **一对多匹配策略**：使用匹配得分 `M_ij = α·s_i + (1−α)·IoU(b_i, b̄_j)`，选取前K个最高分正样本，并过滤IoU低于阈值的预测。
- **训练与推理**：辅助路径仅用于训练，推理时仅保留主路径，不增加推理耗时或改变模型结构。

### 3. 实验设计：使用了哪些数据集/场景，它的benchmark是什么，对比了哪些方法
- **主要数据集**：COCO 2017 目标检测和实例分割数据集。
- **评估指标**：标准COCO指标（mAP, AP_50, AP_75, AP_s, AP_m, AP_l）。
- **基准方法**：
  - 变形DETR++（Deformable-DETR++）、H-DETR、DINO、Align-DETR、DAC-DETR、MS-DETR等。
  - 在主实验中对比了不同查询数（300/900）、训练周期（12/24 epochs）下的多种基线模型。
- **消融与扩展实验**：
  - 探究不同组件独立/共享对性能的影响。
  - 多路径组合消融（Route-1, Route-2, Route-3）。
  - 指令机制设计对比（独立自注意力、移除自注意力、独立查询、加法方式、拼接方式）。
  - 指令令牌数量、应用层数的影响。
  - 扩展至实例分割任务（Mask AP）。
  - 基于Swin-L骨干网络的大模型实验。

### 4. 资源与算力：文中有无提到算力使用情况
- 文中 **未明确提及** 使用的GPU型号、数量、训练时长等详细算力信息。实验设置中仅提到批量大小为16，AdamW优化器，初始学习率2e-4，权重衰减1e-4等超参数，但未报告所需计算资源。

### 5. 实验数量与充分性：大概做了多少组实验，是否充分、客观、公平
- **实验数量丰富**：涵盖多个基线模型（Deformable-DETR++、H-DETR、DINO、Align-DETR）、多种训练配置（12/24 epochs, 300/900 queries）、大量对比方法（DAC-DETR, MS-DETR, Rank-DETR, Stable-DINO等），以及消融实验（多路径、指令设计、令牌数量、应用层数、实例分割扩展、Swin-L骨干验证）。总计约20余项实验表格和图示结果。
- **充分性与公平性**：
  - 对比基线时保持相同骨干网络、数据增强、训练超参数，公平性较高。
  - 消融实验系统验证了各组件贡献与设计选择，内部有效性较强。
  - 提供了注意力图可视化（图6），增强了可解释性。
  - 实验覆盖了不同规模模型和训练时长，具有一定普适性。
  - 然而未报告标准差或多次运行误差，统计显著性未提供。

### 6. 论文的主要结论与发现
- **关键发现**：解码器中的任何独立组件（自注意力、交叉注意力、FFN）都能在共享其他组件时有效学习一对多和一对一目标，且独立组件能缓解任务间冲突，显著提升一对一预测性能。
- **方法有效性**：提出的多路径训练机制（结合独立FFN路径和指导性自注意力路径）在多个基线模型上取得一致提升，如Deformable-DETR++（+2.5/+3.1 mAP）、DINO（+1.9 mAP）等。
- **指令令牌优势**：拼接方式的指导性自注意力优于独立自注意力、独立查询或加法方式，能以极少参数量动态引导对象查询。
- **推理无额外开销**：辅助路径可在推理时安全移除，保持模型原有推理速度和架构。
- **广泛适用性**：方法可扩展至实例分割，获得3.6% mask mAP提升。

### 7. 优点：方法或实验设计上的亮点
- **系统性的经验研究**：首次在多任务框架下对解码器各组件的角色进行细致分析，得出直观且有价值的结论。
- **创新的指令机制**：通过拼接少量可学习令牌实现参数高效、灵活的任务引导，避免了独立路径的大量额外参数。
- **极低的推理成本**：辅助训练路径不影响推理模型，易于集成到现有检测器中。
- **广泛的实验验证**：覆盖多个主流DETR变体、两种任务（检测与分割）、多种训练计划，证明了方法的普适性和鲁棒性。
- **可解释性**：通过注意力图展示指令令牌的作用，增强了对方法有效性的理解。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等
- **理论解释有限**：虽给出经验观察，但对“为何独立组件能缓解任务冲突”缺乏更深入的理论分析或机制解释。
- **超参数依赖性**：指令令牌数量、辅助路径数量等均需手动选择，可能在不同数据集或模型尺度下需重新调整。
- **仅限DETR系列**：方法针对Transformer解码器设计，推广到其他检测范式（如单阶段检测器）的可行性未知。
- **未报告稳定性指标**：实验结果多为单次运行，缺少方差信息，结果的统计显著性未验证。
- **计算资源未披露**：未给出训练成本，无法评估实际部署的性价比。
- **仅COCO基准**：仅在COCO数据集上评测，在其他领域数据集的迁移能力未知。

（完）
