---
title: "SP3D: Boosting Sparsely-Supervised 3D Object Detection via Accurate Cross-Modal Semantic Prompts"
title_zh: SP3D：通过精确跨模态语义提示提升稀疏监督三维目标检测
authors: "Zhao, Shijia, Xia, Qiming, Guo, Xusheng, Zou, Pufan, Zheng, Maoji, Wu, Hai, Wen, Chenglu, Wang, Cheng"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Zhao_SP3D_Boosting_Sparsely-Supervised_3D_Object_Detection_via_Accurate_Cross-Modal_Semantic_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 9.0
evidence: 通过跨模态语义提示提升稀疏监督的三维目标检测
tldr: 在标注极度稀疏的条件下，现有稀疏监督3D目标检测方法仍面临挑战。本文提出SP3D策略，利用大型多模态模型生成跨模态语义提示，通过自信点语义转移模块精确传递语义信息，增强3D检测器特征判别力，大幅提升少样本下的检测性能。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-sp3d-boosting-sparsely-supervised-3d-object-detection-via-accurate-cross-modal-semantic-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 872, \"height\": 282, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-sp3d-boosting-sparsely-supervised-3d-object-detection-via-accurate-cross-modal-semantic-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 780, \"height\": 343, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-sp3d-boosting-sparsely-supervised-3d-object-detection-via-accurate-cross-modal-semantic-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1790, \"height\": 903, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-sp3d-boosting-sparsely-supervised-3d-object-detection-via-accurate-cross-modal-semantic-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 780, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-sp3d-boosting-sparsely-supervised-3d-object-detection-via-accurate-cross-modal-semantic-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1760, \"height\": 427, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-sp3d-boosting-sparsely-supervised-3d-object-detection-via-accurate-cross-modal-semantic-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1843, \"height\": 652, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-sp3d-boosting-sparsely-supervised-3d-object-detection-via-accurate-cross-modal-semantic-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 909, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-sp3d-boosting-sparsely-supervised-3d-object-detection-via-accurate-cross-modal-semantic-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1834, \"height\": 564, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-sp3d-boosting-sparsely-supervised-3d-object-detection-via-accurate-cross-modal-semantic-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 827, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-sp3d-boosting-sparsely-supervised-3d-object-detection-via-accurate-cross-modal-semantic-cvpr-2025-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 711, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-sp3d-boosting-sparsely-supervised-3d-object-detection-via-accurate-cross-modal-semantic-cvpr-2025-paper/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 847, \"height\": 348, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-sp3d-boosting-sparsely-supervised-3d-object-detection-via-accurate-cross-modal-semantic-cvpr-2025-paper/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 687, \"height\": 224, \"label\": \"Table\"}]"
motivation: 稀疏标注下3D检测器性能受限，需要外部语义知识。
method: 利用多模态大模型生成语义提示，通过CPST模块转移。
result: 在稀疏标注场景下3D检测性能接近全监督方法。
conclusion: 跨模态语义提示是提升稀疏监督3D检测的有效途径。
---

## Abstract
Recently, sparsely-supervised 3D object detection has gained great attention, achieving performance close to fully-supervised 3D detectors while requiring only a few annotated instances. Nevertheless, these methods suffer challenges when accurate labels are extremely absent. In this paper, we propose a boosting strategy, termed SP3D, explicitly utilizing the cross-modal semantic prompts generated from Large Multimodal Models (LMMs) to boost the 3D detector with robust feature discrimination capability under sparse annotation settings. Specifically, we first develop a Confident Points Semantic Transfer (CPST) module that generates accurate cross-modal semantic prompts through boundary-constrained center cluster selection. Based on these accurate semantic prompts, which we treat as seed points, we introduce a Dynamic Cluster Pseudo-label Generation (DCPG) module to yield pseudo-supervision signals from the geometry shape of multi-scale neighbor points. Additionally, we design a Distribution Shape score (DS score) that chooses high-quality supervision signals for the initial training of the 3D detector. Experiments on the KITTI dataset and Waymo Open Dataset (WOD) have validated that SP3D can enhance the performance of sparsely supervised detectors by a large margin under meager labeling conditions. Moreover, we verified SP3D in the zero-shot setting, where its performance exceeded that of the state-of-the-art methods. The code is available at https://github.com/xmuqimingxia/SP3D.

---

## 论文详细总结（自动生成）

# SP3D: Boosting Sparsely-Supervised 3D Object Detection via Accurate Cross-Modal Semantic Prompts 论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：现有稀疏监督三维目标检测方法（如 SS3D、CoIn）在标注实例极度稀少（例如标注率降至 2% 或更低）时，性能大幅下降，难以保持鲁棒的特征判别能力。主要原因是初始检测器无法从少量标注中学习到充分的类别区分特征。
- **研究动机**：如何在不增加人工标注的前提下，利用外部先验知识增强稀疏监督检测器的初始化能力。最近大型多模态模型（LMMs）在二维视觉任务中表现出色，已有工作尝试将二维 LMM 的图文知识迁移至三维点云，但通常仅针对实例级分类，直接应用于室外三维目标检测存在语义歧义和伪标签质量低的问题。
- **整体含义**：本文提出 SP3D 策略，显式地利用 LMM 生成的跨模态语义提示（准确的前景语义点）作为“种子点”，动态生成高质量的伪标签，为检测器提供强先验初始化，再配合少量真实标签微调，从而大幅提升稀疏监督下的三维目标检测性能，实现“近全监督”甚至“零样本”检测能力。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
SP3D 包含三个核心模块：**Confident Points Semantic Transfer (CPST)**、**Dynamic Cluster Pseudo-label Generation (DCPG)** 和 **Distribution Shape Score (DS score)**。

### 2.1 核心思想
先通过 LMM 提取准确的二维前景语义掩码，经边界收缩和坐标变换得到无噪声的三维语义种子点；再以种子点为中心，根据多尺度邻域几何形状动态聚类并拟合出具有完整性的伪标签候选框；最后利用无监督先验（分布形状和元形状约束）评估候选框质量，通过 NMS 保留高质量伪标签训练初始检测器。

### 2.2 CPST：自信点语义转移模块
- **LMMs 引导的语义提取**：使用 FastSAM 对输入图像 I 生成类别无关掩码 MI，再将其作为提示输入 SemanticSAM 获得掩码描述 TD。计算描述与类别文本提示 TC 的余弦相似度，过滤出前景掩码 M′I。
- **自信点过滤（边界约束中心聚类选择）**：对 M′I 沿像素坐标系 (u,v) 进行收缩，只保留中心区域：
  - u ∈ [umin + 1/2(1-γ)(umax-umin), umin + 1/2(1+γ)(umax-umin)]
  - v ∈ [vmin + 1/2(1-γ)(vmax-vmin), vmin + 1/2(1+γ)(vmax-vmin)]
  其中 γ 为收缩因子（默认 0.3）。将收缩后的掩码通过相机内参与外参矩阵投射到三维点云上，得到准确的前景种子点 PT。

### 2.3 DCPG：动态聚类伪标签生成模块
- 以种子点 pt 为聚类中心，使用 DBSCAN 进行聚类，**聚类半径 r 动态更新**：
  - r = rinit · t/N(k) + δ, t = 1,2,…,N(k)
  - rinit 为基础半径（默认 1.0），δ 为调节项（0.1），N(k) 为当前实例种子点数。
- 对每个种子点动态聚类后，采用 L-shape 拟合等边界框拟合方法生成伪标签提案 ˆB(k)。
- 算法流程（见论文 Algorithm 1）确保为每个种子点生成多尺度感受野的候选框，捕获完整前景。

### 2.4 DS 分数：分布形状质量评估分数
- **分布约束分数（sdc）**：假设高质量伪标签内部点到边界距离 D 服从 N(0.8,0.2) 的正态分布，计算对数似然作为分数。
- **元形状约束分数（smsc）**：衡量候选框归一化尺寸 (l,w,h) 与类级元实例 Bc 之间的 KL 散度，作为类感知形状约束。
- DS(ˆb) = λ1·sdc + λ2·smsc（λ1, λ2 均为 0.5）。
- 将 DS 分数替代传统 NMS 中的置信度分数，抑制低质量伪标签。

训练流程：首先使用高质量伪标签+CoIn 对比实例特征挖掘训练初始检测器；第二阶段使用少量精确标签（例如 2% 实例）进行微调。

## 3. 实验设计：数据集、benchmark 和对比方法
- **数据集**：
  - KITTI：7481 帧训练/验证划分（3712/3769），随机选取 10% 场景并仅保留每帧最多一个标注，得到约 2% 标注代价的 limited split；还测试了 1%、0.5% 等标注率。
  - Waymo Open Dataset (WOD)：798 训练序列、202 验证序列，采用 1% 标注成本，IoU 阈值 0.7。
- **评测指标**：
  - KITTI：3D AP (R40)，分 Easy/Moderate/Hard，类别为 Car、Pedestrian、Cyclist。
  - WOD：3D mAP 和 mAPH，Level 1、Level 2。
- **对比方法**：
  - **稀疏监督**：CoIn、CoIn++、SS3D 等。
  - **全监督基线**：VoxelRCNN、CenterPoint、CasA。
  - **半监督**：HSSDA。
  - **弱监督/零样本**：VS3D、WS3D、SAM3D、CM3D。
  - **无监督**：CPD。
  - 我们将 SP3D 与 CoIn/CoIn++、HINTED 等结合，验证通用性。

## 4. 资源与算力
- **训练配置**：所有实验在 4 张 RTX 3090 GPU 上进行，batch size 为 8，学习率 0.003。生成伪标签阶段直接使用 FastSAM 和 SemanticSAM 预训练模型，无需额外微调，未报告伪标签生成时间。训练时间未明确给出。
- **算力要求**：未提及具体训练时长，但使用 4×3090，batch 8，推测在 KITTI 上单阶段微调训练较快，WOD 较大规模训练可能需较长时间。

## 5. 实验数量与充分性
- **实验组数**：
  - 在 KITTI 上与 SoTA 稀疏方法对比（VoxelRCNN 基线，2% 标注）；在 WOD 上同样对比（CenterPoint 基线，1% 标注）。
  - 不同全监督检测架构（单阶段 CenterPoint、两阶段 VoxelRCNN、多阶段 CasA）适配验证。
  - 不同标注率鲁棒性实验（2%、1%、0.5%）对半监督、稀疏方法进行增强测试。
  - 零样本设置对比（KITTI、WOD）。
  - 无监督方法结合实验（CPD+SP3D）。
  - 消融实验验证 CPST（Mask shrink）、DCPG、DS 分数以及 DS 的两组分。
- **充分性与公平性**：实验覆盖了主流数据集和多种基线，消融实验逻辑清晰，证明了各模块贡献；对比时均使用相同基座和训练设置，较为公平；并验证了 SP3D 对多种检测范式的通用性。实验规模充分。
- **偏差风险**：在极低标注率（<0.1%）下性能下降明显，但文中未展示相关定量结果；部分 Easy 类别精度轻微下降，解释为伪标签尺寸与人工标注惯例差异，这可能是初始化偏差。

## 6. 论文的主要结论与发现
- SP3D 通过 LMM 语义提示生成的准确种子点，结合动态聚类和 DS 分数，能够为稀疏监督检测器提供高质量伪标签初始化，大幅提升检测性能。
- 在 KITTI 2% 标注下，SP3D 初始化 CoIn++ 在多个类别和难度级别上实现大幅超越（如 Pedestrian 从 36.1 提升至 58.7）。
- 在 WOD 1% 标注下，CoIn+SP3D 的 Vehicle Level 1 mAP 提升 +7.1。
- 在零样本场景下，SP3D 超越现有零样本方法，显示其强大的先验学习能力。
- 结合不同监督范式（稀疏、半监督、无监督）均能取得稳定增益，具有通用性。
- 随着标注率降低，SP3D 的优势更加明显，有效缓解性能锐减问题。

## 7. 优点
- **方法简洁高效**：无需微调 LMM，只利用推理结果生成种子点，易于部署。
- **准确的语义传递**：通过掩码收缩有效消除由于深度歧义和校准误差引起的边缘噪声，保证语义点可靠性。
- **动态伪标签生成**：自适应半径聚类和多尺度融合，避免固定半径导致的前景缺失或背景噪声。
- **无监督质量评估**：基于统计先验的 DS 分数替代 GT-IoU，使 NMS 在无真值场景下可用。
- **兼容性强**：可即插即用地与主流稀疏监督、半监督、无监督方法结合，提升各类检测架构（单阶段、两阶段、多阶段）的性能。
- **实验充分**：在两个大规模数据集、多种标注率、多种基线设置下验证，消融实验严谨。

## 8. 不足与局限
- **极低标注率下的性能衰减**：当标注率低于 0.1% 时，微调过程可能引入过多噪声，SP3D 效果退化明显，需研究更鲁棒的微调策略。
- **检测器初始化偏差**：伪标签依赖几何形状估计，尺寸可能不符合人工标注习惯，导致部分 Easy 实例指标轻微下降（如 Car Easy），可能影响下游任务中尺寸的严格一致性。
- **对图像质量的依赖性**：LMM 提取的语义掩码质量直接影响种子点精度，在昏暗、遮挡或复杂环境中可能出现漏检或误分割。
- **未考虑动态物体或行人的特殊形变**：DS 分数中的元形状约束是基于固定类别先验，对形变大的类别（如行人姿态）可能不够鲁棒。
- **算力开销未明确**：虽然不需要微调 LMM，但伪标签生成需要运行两个分割模型，实际推理时间及对大规模数据集的处理效率缺乏详细分析。

（完）
