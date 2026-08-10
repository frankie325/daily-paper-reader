---
title: Learning Class Prototypes for Unified Sparse-Supervised 3D Object Detection
title_zh: 学习类原型实现统一稀疏监督3D目标检测
authors: "Zhu, Yun, Hui, Le, Yang, Hang, Qian, Jianjun, Xie, Jin, Yang, Jian"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Zhu_Learning_Class_Prototypes_for_Unified_Sparse-Supervised_3D_Object_Detection_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 9.0
evidence: 基于类原型的统一稀疏监督3D目标检测
tldr: 针对稀疏监督3D目标检测现有方法仅关注室外场景的问题，本文提出基于类原型的统一方法，适用于室内外场景。通过原型匹配挖掘未标注对象，利用最优传输分配标签，并结合室内外场景协同学习，在极少量标注下实现了高精度检测，为通用3D感知提供了高效方案。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhu-learning-class-prototypes-for-unified-sparse-supervised-3d-object-detection-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 857, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhu-learning-class-prototypes-for-unified-sparse-supervised-3d-object-detection-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 865, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhu-learning-class-prototypes-for-unified-sparse-supervised-3d-object-detection-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1816, \"height\": 875, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhu-learning-class-prototypes-for-unified-sparse-supervised-3d-object-detection-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 871, \"height\": 452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhu-learning-class-prototypes-for-unified-sparse-supervised-3d-object-detection-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 863, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhu-learning-class-prototypes-for-unified-sparse-supervised-3d-object-detection-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1733, \"height\": 409, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhu-learning-class-prototypes-for-unified-sparse-supervised-3d-object-detection-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 864, \"height\": 802, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhu-learning-class-prototypes-for-unified-sparse-supervised-3d-object-detection-cvpr-2025-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 789, \"height\": 373, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhu-learning-class-prototypes-for-unified-sparse-supervised-3d-object-detection-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 830, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhu-learning-class-prototypes-for-unified-sparse-supervised-3d-object-detection-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1484, \"height\": 445, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhu-learning-class-prototypes-for-unified-sparse-supervised-3d-object-detection-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1537, \"height\": 457, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhu-learning-class-prototypes-for-unified-sparse-supervised-3d-object-detection-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 751, \"height\": 313, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhu-learning-class-prototypes-for-unified-sparse-supervised-3d-object-detection-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 875, \"height\": 340, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhu-learning-class-prototypes-for-unified-sparse-supervised-3d-object-detection-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 865, \"height\": 175, \"label\": \"Table\"}]"
motivation: 现有稀疏监督3D目标检测局限于室外场景，未考虑室内设置，限制了通用性。
method: 提出类原型驱动的统一检测框架，将未标注对象挖掘转化为原型与特征的最优传输匹配问题。
result: 在室内外多个数据集上，使用少量标注即可达到接近全监督的性能。
conclusion: 类原型方法实现了高效统一的稀疏监督3D目标检测，扩展了场景适用性。
---

## Abstract
Both indoor and outdoor scene perceptions are essential for embodied intelligence. However, current sparse supervised 3D object detection methods focus solely on outdoor scenes without considering indoor settings. To this end, we propose a unified sparse supervised 3D object detection method for both indoor and outdoor scenes through learning class prototypes to effectively utilize unlabeled objects. Specifically, we first propose a prototype-based object mining module that converts the unlabeled object mining into a matching problem between class prototypes and unlabeled features. By using optimal transport matching results, we assign prototype labels to high-confidence features, thereby achieving the mining of unlabeled objects. We then present a multi-label cooperative refinement module to effectively recover missed detections in sparse supervised 3D object detection through pseudo label quality control and prototype label cooperation. Experiments show that our method achieves state-of-the-art performance under the one object per scene sparse supervised setting across indoor and outdoor datasets. With only one labeled object per scene, our method achieves about 78%, 90%, and 96% performance compared to the fully supervised detector on ScanNet V2, SUN RGB-D, and KITTI, respectively, highlighting the scalability of our method.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：现有稀疏监督 3D 目标检测方法仅针对室外场景（如自动驾驶），依赖“每个场景包含所有类别”的前提，通过 GT 采样策略挖掘未标注目标。但这种策略在室内场景中不适用，因为室内类别具有场景特异性（例如“马桶”不能出现在客厅）。
- **研究动机**：稀疏监督（每个场景仅标注极少数目标）能大幅降低标注成本，但需要一种统一的方法同时适用于室内和室外环境，以支持具身智能的通用感知。
- **整体含义**：提出一种基于类原型（class prototypes）的统一稀疏监督 3D 目标检测框架，通过跨场景的类别原型学习和最优传输匹配，有效利用未标注目标，摆脱对场景全覆盖类别的依赖，在室内外数据集上均显著提升性能。

## 2. 论文提出的方法论：核心思想、关键技术细节
整体方法包含两个核心模块，采用两阶段训练范式。

### 2.1 原型驱动目标挖掘（Prototype-based Object Mining）
- **核心思想**：将未标注目标挖掘转化为类原型与未标注特征之间的匹配问题，利用跨场景的类别原型为未标注区域分配伪标签。
- **类感知原型聚类（Class-aware Prototype Clustering）**：
  - 输入点云经检测器得到提议特征 \(X\)，通过 MLP 投影得到特征 \(F\)。
  - 对每个类别 \(k\)，用稀疏标注筛选出的该类特征 \(F_k\)，与 \(O\) 个可学习的类别原型 \(P_k\in\mathbb{R}^{O\times C}\)（\(O>1\) 保证类内多样性）进行最优传输匹配。
  - 使用 Sinkhorn-Knopp 迭代求解匹配矩阵 \(L_k\)，并基于动量更新原型：
    \[
    p'_{k,i} \leftarrow \mu p_{k,i} + (1-\mu) \frac{1}{N_k} \sum_{i=1}^{N_k} F_{k,i}
    \]
  - 引入原型-特征对比损失（InfoNCE）优化原型分布。
- **原型标签匹配（Prototype Label Matching）**：
  - 获取可区分类别原型后，计算场景内投影特征与所有原型的亲和度矩阵 \(A\)，并与检测器分类分数 \(S\) 逐元素相乘得到 \(W\)，取每行最大类别作为特征标签。
  - 通过前景阈值、舍弃已标注区域、范围过滤等筛选出高质量原型标签 \(C'_p\)，用于监督未标注目标。
- **标签性质**：原型标签仅提供类别信号，不包含精确位置，训练时不引入测试开销。

### 2.2 多标签协同精炼（Multi-label Cooperative Refinement）
- **迭代伪标签生成**：用训练好的检测器生成伪标签，依次经分类分数阈值、IoU 过滤、碰撞过滤（避免与稀疏标注重叠）得到高质量伪标签。
- **原型标签协作**：在伪标签基础上，利用原型标签恢复被遗漏的检测（例如前景区域未被伪标签覆盖的），通过分离前景/背景、识别已标注区域、对剩余前景赋予原型标签，实现多标签协同。
- **训练策略**：
  - 第一阶段：仅用稀疏标注加原型挖掘模块，损失 \(L_{\text{stage1}} = L_{\text{det}} + L_{\text{pcon}} + L_{\text{pcls}}\)。
  - 第二阶段：加入伪标签和原型标签协作，损失 \(L_{\text{stage2}} = L_{\text{stage1}} + L_{\text{ref}}\)。

### 2.3 关键参数与流程
- 原型数 \(O=10\)，动量系数 \(\mu=0.9\)，Sinkhorn 迭代步数 3，温度 \(\kappa=0.05\)，原型的预热迭代 1000 次。
- 各阈值：αpro=0.2，αcls=0.2，αiou=0.5，αcol=0.2。

## 3. 实验设计
### 3.1 数据集与评估指标
- **室内**：ScanNet V2（1201 训练，312 验证，18 类，mAP@0.25 和 mAP@0.5）；SUN RGB-D（约 5000 训练/验证）。采用每场景仅 1 个标注目标（one object per scene）的稀疏设置。
- **室外**：KITTI（3712 训练，3769 验证，仅汽车类），采用约 2% 标注成本的稀疏设置，评价 Car 3D AP 和 BEV AP (R40)。
- 评价与全监督和最新稀疏/半监督方法比较。

### 3.2 基准方法
- 室内检测器：TR3D（作为基座），对比 FCAF3D（全监督）、SparseDet、Co-mining、CoIn 等。
- 室外检测器：Voxel-RCNN + CenterHead，对比 CenterPoint、Voxel-RCNN（全监督）、SS3D、CoIn/CoIn++。
- 还对比了半监督方法（SESS、3DIoUMatch、DQS3D 等）在相同标注对象数下的 ScanNet 结果。

## 4. 资源与算力
论文未明确提及所使用的 GPU 型号、数量及具体训练时长。实验均基于 mmdetection3d 和 OpenPCDet 框架实现，通常这类检测任务需消耗一定 GPU 资源，但文中无直接说明，因此无法提供具体算力信息。

## 5. 实验数量与充分性
- 主要结果表：室内 ScanNet、SUN RGB-D 对比表（表1）；室外 KITTI（表2）；与半监督方法对比（表3）。
- 消融实验：关键模块（原型标签匹配、类原型聚类、多标签精炼）的逐步增益（表5）；原型数量、预热迭代、动量系数的影响（图6）；阈值 αpro、αcls、αiou、αcol 的敏感性（表6、图8）。
- 标签质量统计：对原型标签和伪标签的精度与召回进行了定量分析（表4）。
- 可视化：挖掘的原型标签示例（图5）、检测结果可视化（图7）。
总体实验设计较为充分，覆盖室内外多个数据集，对比方法全面，消融覆盖核心组件与超参数，且公平性较好（统一基座检测器、相同稀疏设置）。

## 6. 论文的主要结论与发现
- 提出统一的稀疏监督 3D 目标检测方法，通过类原型有效利用未标注数据，摆脱了对“每场景全类别覆盖”的依赖，适用于室内和室外场景。
- 在每场景仅标注 1 个目标时，室内 ScanNet 达到全监督性能的 78%（mAP@0.5），SUN RGB-D 达到 90%，室外 KITTI 汽车检测达到 96%，大幅超越先前稀疏监督方法。
- 原型标签与伪标签协同能显著恢复漏检，提升召回；原型的跨场景学习是关键，预热和动量策略保证了标签稳定性。
- 该方法在相同标注量下，性能优于部分半监督方法，展示了稀疏监督的高效性与可扩展性。

## 7. 优点：方法或实验设计上的亮点
- **场景统一性**：首次实现室内外统一的稀疏监督 3D 检测，突破以往仅限室外的限制。
- **原型驱动的创新**：用跨场景的类原型匹配代替局部 GT 采样，既解决类别覆盖问题，又无需增加测试开销。
- **多标签协同精炼**：简单高效地结合伪标签和原型标签，避免复杂阈值调整，有效减少漏检。
- **实验广泛且扎实**：覆盖两个室内和一个室外数据集，与大量现有方法对比，并进行了详细的消融和阈值分析。
- **性能与全监督高度接近**：在极低标注下取得令人瞩目的性能，验证了方法的实用潜力。

## 8. 不足与局限
- **算力信息缺失**：未提供 GPU 配置与训练耗时，难以评估实际落地成本。
- **类别不平衡和极稀类别**：实验主要针对常见类别，对极稀有类别或长尾分布的效果未专门探讨。
- **超参数敏感性**：原型数量、动量、预热轮数等需调优，可能在不同数据集上需要重新搜索（但论文中展示了较好的稳定性）。
- **仿真到现实**：仅在有标注的公开数据集上评估，未涉及无监督域适应或真实机器人平台上的在线测试。
- **原型更新方式**：基于动量更新的原型可能不适应动态变化的数据分布，且依赖批量统计，对非常大的数据集或流式场景的扩展性未讨论。
- **仅限制于一种基座检测器**：室内用 TR3D，室外用 Voxel-RCNN，并未迁移更多检测架构以证明通用性。

（完）
