---
title: "CorrBEV: Multi-View 3D Object Detection by Correlation Learning with Multi-modal Prototypes"
title_zh: CorrBEV：基于多模态原型关联学习的多视图3D目标检测
authors: "Xue, Ziteng, Guo, Mingzhe, Fan, Heng, Zhang, Shihui, Zhang, Zhipeng"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Xue_CorrBEV_Multi-View_3D_Object_Detection_by_Correlation_Learning_with_Multi-modal_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 9.0
evidence: 基于关联学习的多视图3D目标检测
tldr: 针对自动驾驶多视图3D目标检测中的遮挡问题，本文受人类非模态感知启发，提出通过多模态原型进行关联学习，以重建被遮挡对象的完整语义。该方法在BEV架构基础上引入新的关联模块，实验表明在遮挡场景下检测精度显著提升，增强了安全关键场景的可靠性。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-xue-corrbev-multi-view-3d-object-detection-by-correlation-learning-with-multi-modal-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 848, \"height\": 686, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-xue-corrbev-multi-view-3d-object-detection-by-correlation-learning-with-multi-modal-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1795, \"height\": 751, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-xue-corrbev-multi-view-3d-object-detection-by-correlation-learning-with-multi-modal-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 685, \"height\": 538, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-xue-corrbev-multi-view-3d-object-detection-by-correlation-learning-with-multi-modal-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 859, \"height\": 437, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-xue-corrbev-multi-view-3d-object-detection-by-correlation-learning-with-multi-modal-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 751, \"height\": 564, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-xue-corrbev-multi-view-3d-object-detection-by-correlation-learning-with-multi-modal-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1681, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-xue-corrbev-multi-view-3d-object-detection-by-correlation-learning-with-multi-modal-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 806, \"height\": 418, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-xue-corrbev-multi-view-3d-object-detection-by-correlation-learning-with-multi-modal-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1531, \"height\": 596, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-xue-corrbev-multi-view-3d-object-detection-by-correlation-learning-with-multi-modal-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1798, \"height\": 875, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-xue-corrbev-multi-view-3d-object-detection-by-correlation-learning-with-multi-modal-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 864, \"height\": 188, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-xue-corrbev-multi-view-3d-object-detection-by-correlation-learning-with-multi-modal-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 862, \"height\": 180, \"label\": \"Table\"}]"
motivation: 现有多视图3D目标检测方法在遮挡等复杂场景下性能不足，未充分关注非模态感知能力。
method: 提出CorrBEV，利用多模态原型进行关联学习，模拟人类非模态感知，增强遮挡对象的重建。
result: 在NuScenes等数据集上，遮挡场景下的检测性能明显提升，证明了方法的有效性。
conclusion: 关联学习与多模态原型能有效缓解遮挡影响，提升自动驾驶3D目标检测的安全性。
---

## Abstract
Camera-only multi-view 3D object detection in autonomous driving has witnessed encouraging developments in recent years, largely attributed to the revolution of fundamental architectures in modeling bird's eye view (BEV). Despite the growing overall average performance, we contend that the exploration of more specific and challenging corner cases hasn't received adequate attention. In this work, we delve into a specific yet critical issue for safe autonomous driving: occlusion. To alleviate this challenge, we draw inspiration from the human amodal perception system, which is proven to have the capacity for mentally reconstructing the complete semantic concept of occluded objects with prior knowledge. More specifically, we introduce auxiliary visual and language prototypes, akin to human prior knowledge, to enhance the diminished object features caused by occlusion. Inspired by Siamese object tracking, we fuse the information from these prototypes with the baseline model through an efficient depth-wise correlation, thereby enhancing the quality of object-related features and guiding the learning of 3D object queries, especially for partially occluded ones. Furthermore, we propose the random pixel drop to mimic occlusion and the multi-modal contrastive loss to align visual features of different occlusion levels to a unified space during training. Our inspiration originates from addressing occlusion, however, we are surprised to find that the proposed framework also enhances robustness in various challenging scenarios that diminish object representation, such as inclement weather conditions. By applying our model to different baselines, i.e., BEVFormer and SparseBEV, we demonstrate consistent improvements.

---

## 论文详细总结（自动生成）

好的，请查收以下基于论文《CorrBEV: Multi-View 3D Object Detection by Correlation Learning with Multi-modal Prototypes》的详细中文总结。

### 论文核心问题与整体含义
*   **核心问题**：论文聚焦于自动驾驶纯视觉多视角3D目标检测中的一个关键但尚未被充分探索的挑战——**目标遮挡**。作者指出，当前研究主要追求整体平均性能（如mAP，NDS）的提升，而忽视了遮挡等对安全驾驶至关重要的极端场景，导致模型在部分遮挡情况下性能下降，可能漏检关键目标。
*   **整体含义**：受人类“**非模态感知**”能力的启发，即人类能借助先验知识在脑中补全被遮挡物体的完整概念，论文提出通过引入**多模态先验知识**来增强由遮挡导致的退化物体特征，从而提升对遮挡目标的检测鲁棒性，并意外地发现该方法对其他恶劣天气等挑战性场景同样有效。

### 论文提出的方法论
论文提出了名为 **CorrBEV** 的即插即用框架，其核心思想、技术细节和流程如下：

*   **核心思想**：引入辅助的**视觉原型**和**语言原型**作为先验知识，通过高效的深度可分离相关操作与基线模型融合，以补偿被遮挡目标缺失的特征信息，并引导3D目标查询的生成与学习。
*   **关键技术细节与流程**：
    1.  **多模态原型生成器**：
        *   **视觉原型**：离线裁剪训练集中的2D目标模板，用冻结的图像编码器（DeViT）提取特征，然后根据目标可见度级别和类别进行聚类和平均，形成遮挡感知的视觉原型 \(P_{vo}\)。
        *   **语言原型**：使用预训练的BERT将类别名称（如“car”、“pedestrian”）转化为语言嵌入 \(P_l\)，并在训练中进行微调。
        *   将两种原型进行广播和拼接，得到最终的多模态原型 **P**。
    2.  **关联引导的查询学习器**：
        *   **深度相关融合**：受孪生目标跟踪启发，将多模态原型 **P** 作为1x1卷积核，与主干网络提取的图像特征 \(F_b\) 进行深度可分离相关操作，得到相关特征图 \(F_{corr}\)。此操作旨在增强目标相关特征的响应，抑制无关背景。公式表达为：\(F_{corr} = \text{Conv}_{1\times1}(P, F_b)\)。
        *   **目标查询初始化**：基于 \(F_{corr}\) 预测每个可见度和类别的置信度图，从中选取Top-k位置的嵌入作为目标感知查询 \(Q_t\)，并与基线模型的可学习查询 \(Q_{learn}\) 通过交叉注意力融合。
        *   **双路径混合采样**：3D目标查询在采样特征时，不仅从原始主干特征 \(F_b\) 中采样，还同时从相关特征 \(F_{corr}\) 中采样，并将二者聚合，用于更新3D目标查询，从而缓解遮挡目标的特征模糊性。
    3.  **遮挡感知训练器**：
        *   **伪遮挡处理器**：在训练时，随机丢弃低遮挡（高可见度）目标2D边界框内的部分像素，以模拟更高程度的遮挡，平衡不同遮挡级别样本的分布。
        *   **多模态对比损失**：对模型预测的3D查询特征与语言原型进行对比学习，将同类别、不同遮挡级别的目标视觉特征拉向统一的空间（即语言中心），并推开不同类别的特征，以提升分类准确性。

### 实验设计
*   **数据集与基准**：主要在 **nuScenes** 数据集上进行实验，使用其提供的700/150/150的标准训练/验证/测试集划分。重点评估指标为 **mAP** 和 **NDS**，以及五个真阳性误差指标（mATE, mASE, mAOE, mAVE, mAAE）。为评估遮挡性能，额外使用了nuScenes提供的四个可见度级别（0-40%, 40-60%, 60-80%, 80-100%）上的召回率作为指标。
*   **对比方法**：为了验证方法的通用性，作者将CorrBEV应用于两种代表性的基线模型上：**密集查询式**的 `BEVFormer-small` 和 **稀疏查询式**的 `SparseBEV`，并与众多最新方法（SOTA）进行了比较，如 BEVDet系列、PETR系列、SOLOFusion、StreamPETR、RayDN等。

### 资源与算力
*   **硬件与时长**：所有实验均在 **8块 NVIDIA GeForce RTX 3090 GPU** 上完成。
*   **计算开销**：以SparseBEV为基线，CorrBEV引入了 **7.48%** 的额外训练成本（单卡3090训练时长从19.92 GPU天增加到21.41 GPU天）。推理速度方面，FPS从基线的21.7略微下降到18.4，影响较小。

### 实验数量与充分性
*   **实验数量**：论文进行了多组充分的实验，具体包括：
    *   **整体性能对比**：在nuScenes验证集和测试集上，与十余种SOTA方法进行全面比较（表1，表2）。
    *   **遮挡性能专项评估**：对比了不同方法在四个可见度级别上的召回率，并可视化了相对提升（图4）。
    *   **鲁棒性测试**：在 **RoboBEV** 基准的多种挑战性场景（如雨雪、模糊、低光）下评估性能（图5）。
    *   **组件化消融实验**：针对SparseBEV基线，系统验证了语言原型、视觉原型、对比损失、伪遮挡处理器等每个组件的作用（表3）。
    *   **原型微调策略消融**：分析了冻结或训练语言/视觉原型对性能的影响（表4）。
    *   **定性分析**：展示了遮挡场景下的检测结果可视化对比（图6）。
    *   **特征分布可视化**：使用t-SNE可视化了对比学习前后易混淆类别特征的可分性（图7）。
*   **充分性与公平性**：实验设计**非常充分且客观公平**。不仅涵盖了主流数据集和全面的评价指标，还通过将方法应用于两种不同架构的基线、与多种SOTA方法对比、详细的消融和鲁棒性测试，有力地证明了方法的有效性、通用性和各组件的贡献。

### 论文的主要结论与发现
*   **遮挡检测性能显著提升**：CorrBEV能显著提升基线模型对部分遮挡目标的检测能力。例如，在SparseBEV上，最严重遮挡级别（Vis 1）的召回率从60.4%大幅提升至**69.1%**，mAP和NDS也分别提升了**2.7%** 和**1.6%**。
*   **方法具有强通用性**：该框架能够即插即用地应用于不同的基线模型（如BEVFormer和SparseBEV），并均带来一致性的性能增益。
*   **鲁棒性延伸至更多场景**：最初针对遮挡问题的设计，意外地增强了模型在恶劣天气、运动模糊等会导致物体表征退化的多种挑战场景下的鲁棒性。
*   **多模态先验与相关操作的有效性**：引入视觉和语言多模态原型并通过相关学习进行融合，是补偿退化特征、引导检测的有效途径。

### 优点
*   **问题导向明确**：聚焦于实际应用中的安全关键问题（遮挡），而非仅追求榜单平均性能。
*   **方法论新颖且高效**：将人类非模态感知机制与孪生网络中的相关操作相结合，优雅地将多模态先验知识注入3D检测模型，计算开销较小。
*   **即插即用，通用性强**：可无缝集成到主流的、不同范式（密集/稀疏查询）的3D检测模型上。
*   **实验全面扎实**：不仅在标准指标上验证，还专门构建了遮挡感知的评估，并在多种挑战性基准上进行鲁棒性测试，消融实验详尽。

### 不足与局限
*   **依赖于2D标注**：视觉原型的生成依赖于训练集中的2D边界框标注，这限制了其在无精密2D标注数据集上的直接应用。
*   **完全遮挡目标未解决**：方法主要针对**部分遮挡**的目标，对于完全不可见的目标，单帧方法依然无能为力。
*   **离线原型生成的局限性**：视觉原型是通过离线聚类平均得到的，可能丢失目标的多样性，且其质量依赖于预训练的图像编码器。
*   **复杂度略有增加**：尽管高效，但推理速度（FPS）和训练时间仍有少量增加，对超低延迟要求的系统可能存在影响。

（完）
