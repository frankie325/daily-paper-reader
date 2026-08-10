---
title: "ViKIENet: Towards Efficient 3D Object Detection with Virtual Key Instance Enhanced Network"
title_zh: ViKIENet：面向高效3D目标检测的虚拟关键实例增强网络
authors: "Yu, Zhuochen, Qiu, Bijie, Khong, Andy W. H."
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Yu_ViKIENet_Towards_Efficient_3D_Object_Detection_with_Virtual_Key_Instance_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 8.0
evidence: 多模态融合的3D目标检测
tldr: 针对点云稀疏和语义信息不足问题，提出虚拟关键实例增强网络（ViKIENet），通过高效多模态特征融合提升3D目标检测效率，减少计算开销和噪声，在自动驾驶等场景有应用价值。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yu-vikienet-towards-efficient-3d-object-detection-with-virtual-key-instance-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 867, \"height\": 789, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yu-vikienet-towards-efficient-3d-object-detection-with-virtual-key-instance-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1810, \"height\": 534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yu-vikienet-towards-efficient-3d-object-detection-with-virtual-key-instance-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1711, \"height\": 762, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yu-vikienet-towards-efficient-3d-object-detection-with-virtual-key-instance-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 861, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yu-vikienet-towards-efficient-3d-object-detection-with-virtual-key-instance-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 865, \"height\": 392, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yu-vikienet-towards-efficient-3d-object-detection-with-virtual-key-instance-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 864, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yu-vikienet-towards-efficient-3d-object-detection-with-virtual-key-instance-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 579, \"height\": 283, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yu-vikienet-towards-efficient-3d-object-detection-with-virtual-key-instance-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 860, \"height\": 400, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yu-vikienet-towards-efficient-3d-object-detection-with-virtual-key-instance-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 859, \"height\": 507, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yu-vikienet-towards-efficient-3d-object-detection-with-virtual-key-instance-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 740, \"height\": 158, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yu-vikienet-towards-efficient-3d-object-detection-with-virtual-key-instance-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 853, \"height\": 270, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yu-vikienet-towards-efficient-3d-object-detection-with-virtual-key-instance-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 794, \"height\": 185, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yu-vikienet-towards-efficient-3d-object-detection-with-virtual-key-instance-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 819, \"height\": 260, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yu-vikienet-towards-efficient-3d-object-detection-with-virtual-key-instance-cvpr-2025-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 861, \"height\": 151, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yu-vikienet-towards-efficient-3d-object-detection-with-virtual-key-instance-cvpr-2025-paper/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 743, \"height\": 319, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yu-vikienet-towards-efficient-3d-object-detection-with-virtual-key-instance-cvpr-2025-paper/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 860, \"height\": 189, \"label\": \"Table\"}]"
motivation: 点云稀疏和深度补全噪声导致现有融合方法计算开销大，且未充分利用图像语义。
method: 提出虚拟关键实例增强网络，通过关键实例特征融合实现高效多模态3D检测。
result: 在多个基准上取得高效3D检测性能，推理速度显著提升。
conclusion: ViKIENet在精度和效率间取得平衡，为实时3D检测提供新方案。
---

## Abstract
The sparsity of point clouds and inadequacy of semantic information pose challenges to current LiDAR-only 3D object detection methods. Recent methods alleviate these challenges by converting RGB images into virtual points via depth completion to be fused with LiDAR points. Although these methods have shown outstanding results, they often introduce significant computation overhead due to the high density of virtual points and noise due to inaccurate depth completion. Besides, they do not thoroughly leverage semantic information from images. In this work, we propose the virtual key instance enhanced network (ViKIENet), a highly efficient and effective multi-modal feature fusion framework that fuses the features of virtual key instances (VKIs) and LiDAR points through multiple stages. Our contributions include three main components: semantic key instance selection (SKIS), virtual-instance-focused fusion (VIFF), and virtual-instance-to-real attention (VIRA). We also propose the extended version ViKIENet-R with VIFF-R which includes rotationally equivariant features. Experiment results show that ViKIENet and ViKIENet-R achieve significant improvements in detection performance on the KITTI, JRDB, and nuScenes datasets compared to existing works. On the KITTI dataset, ViKIENet and ViKIENet-R operate at 22.7 and 15.0 FPS, respectively. As of CVPR submission (Nov. 15th, 2024), ViKIENet ranks first on the car detection and orientation estimation leaderboard, while ViKIENet-R ranks second (compared with officially published papers) on the 3D car detection leaderboard.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究背景**：纯激光雷达（LiDAR）3D 目标检测因点云稀疏和语义信息不足，对远距离、遮挡或小目标检测效果有限。
- **现有方案的不足**：将 RGB 图像通过深度补全转化为密集虚拟点并与 LiDAR 点融合，虽提升了性能，但带来大量虚拟点造成的计算开销和深度补全不准确引入的噪声；同时未能充分利用图像的语义信息。
- **整体含义**：提出一种高效的多模态特征融合框架 ViKIENet，仅利用虚拟“关键实例”而非全部虚拟点，在保持甚至提升检测精度的同时大幅降低计算量，更好地利用语义信息。

### 2. 论文提出的方法论
- **核心思想**：通过图像语义分割筛选出关键实例，生成带有语义得分的虚拟关键实例（VKIs），并在多个阶段与 LiDAR 特征进行聚焦式融合，以减轻噪声并提高效率。
- **三大核心模块**：
  - **语义关键实例选择（SKIS）**：使用深度补全模型获取深度图，语义分割模型获取分割掩膜，选择属于前景实例的像素，将其转换为带有语义分数的虚拟点（VKIs）。
  - **虚拟实例聚焦融合（VIFF）**：包含 BEV 特征融合和 RoI 特征融合。
    - BEV 融合：将多尺度 3D 特征压缩为 BEV 特征，通过拼接、通道注意力、VKI 空间注意力融合两个模态。
    - RoI 融合：对 RoI 网格提取 LiDAR 和 VKI 特征，先后经自注意力、双向交叉注意力、最大池化，最后与 LiDAR 自注意力特征拼接，得到最终融合特征。
  - **虚拟实例到真实注意力（VIRA）**：利用 LiDAR 点云的精确深度来修正 VKIs 的噪声特征。通过将两个模态特征投影到共享图像坐标，找到与 VKI 对应的 LiDAR 特征，进行交叉注意力校准。
- **扩展版本 ViKIENet-R**：对 VKIs 和 LiDAR 点施加 2N 次旋转变换，并使用变换等变稀疏卷积提取多视角特征，再用交叉注意力融合（VIFF-R），以较小的额外计算代价提升旋转等变性。

### 3. 实验设计
- **数据集与基准**：
  - **KITTI**：官方检测 benchmark（7481 训练/7518 测试），评估汽车、行人、骑行者 3D AP（R40，IoU=0.7/0.5/0.5），包含 BEV、2D AP 和 AOS。
  - **nuScenes**：大规模自动驾驶数据集，使用 mAP 评估，验证可移植性（结合 MVP 虚拟点生成）。
  - **JRDB**：室内外行人检测数据集，选取 7 个序列作为验证集，IoU 阈值 0.3，评估 3D AP 和 BEV AP。
- **对比方法**：包括纯 LiDAR 方法（PV-RCNN、Voxel-RCNN、BtcDet 等）、多模态融合方法（LoGoNet、SFD、VirConv-L/T、TED、VPFNet 等）以及旋转等变方法（TSSTDet、VirConv-T 等）。

### 4. 资源与算力
- 训练使用 **1 块 NVIDIA GeForce RTX 3090** GPU，批次大小为 4，训练 40 个 epoch（KITTI），初始学习率 0.01 并采用 one-cycle 调度。
- 推理速度测试：在 KITTI 上 ViKIENet 达 **22.7 FPS**，ViKIENet-R 达 **15.0 FPS**；在 JRDB 上使用 Tesla V100 测试速度。
- 未提及多 GPU 并行或集群训练。

### 5. 实验数量与充分性
- **多数据集验证**：在 KITTI、nuScenes、JRDB 三个差异较大的数据集上进行实验。
- **消融实验**：
  - 逐一添加 VIFF（BEV 融合、RoI 融合）和 VIRA，验证各模块贡献（表 6）。
  - 在 VirConv-L 基础上加入 ViKIENet 模块，验证对全虚拟点方法的增强效果（表 7）。
  - 多类别（汽车、行人、骑行者）检测对比（表 8）。
  - 按距离和遮挡程度分析增益（表 9）。
- **可移植性实验**：在 nuScenes 上将 MVP 方法与 ViKIENet 结合。
- 实验对比方法丰富，消融逻辑清晰，结论可靠，实验设计客观公平。

### 6. 论文的主要结论与发现
- ViKIENet 仅利用虚拟关键实例便可与使用全部虚拟点的方法达到同等甚至更高的检测精度，同时大幅降低计算量。
- 所提出的 SKIS、VIFF、VIRA 模块可有效融合语义和空间信息，抑制深度噪声，增强远距离和遮挡目标的检测。
- 旋转等变版本 ViKIENet-R 进一步提升性能，但在推理速度上仍有优势（15 FPS）。
- 方法在不同数据集上表现出良好的泛化能力和可移植性。

### 7. 优点
- **高效虚拟点利用**：仅选取关键实例，虚拟点数量减少约 90%，显著降低计算开销。
- **针对性的融合设计**：BEV+Rol 两级融合、双向交叉注意力和 VIRA 校准，充分考虑了多模态特征的不一致性。
- **旋转等变扩展**：ViKIENet-R 以较轻代价集成了旋转等变性，达到先进性能。
- **全面的实验验证**：涵盖多个基准、多类别、距离和遮挡分析，消融详尽。
- **开源与可复现**：使用常用公开数据集，提供对比基线。

### 8. 不足与局限
- **依赖深度补全与分割模型**：SKIS 需要额外的预训练模型，其精度影响 VKIs 质量；若分割漏检，VKI RoI 特征可能为空（论文采用拼接 LiDAR 特征缓解）。
- **应用场景受限**：主要适用于自动驾驶等结构化道路场景，对复杂光照或极端天气的鲁棒性未讨论。
- **ViKIENet-R 仍有速度代价**：对比非等变版本，推理速度从 22.7 降到 15.0 FPS，实时性略受影响。
- **参数量与内存未充分披露**：论文未提供模型参数量和显存占用对比。
- **检测类别有限**：主要关注车辆和行人，对多类别复杂场景的评估较少。

（完）
