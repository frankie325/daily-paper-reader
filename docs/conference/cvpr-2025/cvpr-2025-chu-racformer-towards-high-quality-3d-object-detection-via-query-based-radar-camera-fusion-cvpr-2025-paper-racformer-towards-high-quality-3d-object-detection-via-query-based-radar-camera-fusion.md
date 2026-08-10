---
title: "RaCFormer: Towards High-Quality 3D Object Detection via Query-based Radar-Camera Fusion"
title_zh: RaCFormer：通过查询驱动的雷达-相机融合实现高质量3D目标检测
authors: "Chu, Xiaomeng, Deng, Jiajun, You, Guoliang, Duan, Yifan, Li, Houqiang, Zhang, Yanyong"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Chu_RaCFormer_Towards_High-Quality_3D_Object_Detection_via_Query-based_Radar-Camera_Fusion_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 10.0
evidence: 基于Transformer查询框架的雷达-相机3D目标检测
tldr: 针对雷达-相机融合3D目标检测中图像到BEV投影的深度误差导致的特征未对齐问题，本文提出查询驱动的Transformer架构RaCFormer。该方法自适应采样实例相关特征，并结合优化的查询初始化和BEV表示增强，在多个3D检测基准上性能领先，为多模态融合检测提供了新方案。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chu-racformer-towards-high-quality-3d-object-detection-via-query-based-radar-camera-fusion-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 794, \"height\": 422, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chu-racformer-towards-high-quality-3d-object-detection-via-query-based-radar-camera-fusion-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1696, \"height\": 773, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chu-racformer-towards-high-quality-3d-object-detection-via-query-based-radar-camera-fusion-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 834, \"height\": 773, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chu-racformer-towards-high-quality-3d-object-detection-via-query-based-radar-camera-fusion-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 857, \"height\": 346, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chu-racformer-towards-high-quality-3d-object-detection-via-query-based-radar-camera-fusion-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 827, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chu-racformer-towards-high-quality-3d-object-detection-via-query-based-radar-camera-fusion-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1725, \"height\": 638, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chu-racformer-towards-high-quality-3d-object-detection-via-query-based-radar-camera-fusion-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1800, \"height\": 521, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chu-racformer-towards-high-quality-3d-object-detection-via-query-based-radar-camera-fusion-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1804, \"height\": 509, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chu-racformer-towards-high-quality-3d-object-detection-via-query-based-radar-camera-fusion-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1806, \"height\": 300, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chu-racformer-towards-high-quality-3d-object-detection-via-query-based-radar-camera-fusion-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 866, \"height\": 233, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chu-racformer-towards-high-quality-3d-object-detection-via-query-based-radar-camera-fusion-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 870, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chu-racformer-towards-high-quality-3d-object-detection-via-query-based-radar-camera-fusion-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 873, \"height\": 230, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chu-racformer-towards-high-quality-3d-object-detection-via-query-based-radar-camera-fusion-cvpr-2025-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 872, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chu-racformer-towards-high-quality-3d-object-detection-via-query-based-radar-camera-fusion-cvpr-2025-paper/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 875, \"height\": 215, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chu-racformer-towards-high-quality-3d-object-detection-via-query-based-radar-camera-fusion-cvpr-2025-paper/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 873, \"height\": 372, \"label\": \"Table\"}]"
motivation: 雷达-相机融合中图像到BEV投影依赖深度估计，不准确对齐会损害检测性能。
method: 提出查询驱动的Transformer RaCFormer，自适应采样雷达和图像特征，并设计自适应循环查询初始化。
result: 在NuScenes等数据集上达到领先的3D检测精度，验证了查询驱动融合的有效性。
conclusion: 查询驱动融合架构有效避免了投影误差，为多模态3D目标检测开辟了新方向。
---

## Abstract
We propose Radar-Camera fusion transformer (RaCFormer) to boost the accuracy of 3D object detection by the following insight. The Radar-Camera fusion in outdoor 3D scene perception is capped by the image-to-BEV transformation-if the depth of pixels is not accurately estimated, the naive combination of BEV features actually integrates unaligned visual content. To avoid this problem, we propose a query-based framework that enables adaptive sampling of instance-relevant features from both the bird's-eye view (BEV) and the original image view. Furthermore, we enhance system performance by two key designs: optimizing query initialization and strengthening the representational capacity of BEV. For the former, we introduce an adaptive circular distribution in polar coordinates to refine the initialization of object queries, allowing for a distance-based adjustment of query density. For the latter, we initially incorporate a radar-guided depth head to refine the transformation from image view to BEV. Subsequently, we focus on leveraging the Doppler effect of radar and introduce an implicit dynamic catcher to capture the temporal elements within the BEV. Extensive experiments on nuScenes and View-of-Delft (VoD) datasets validate the merits of our design. Remarkably, our method achieves superior results of 64.9% mAP and 70.2% NDS on nuScenes. RaCFormer also secures the state-of-the-art performance on the VoD dataset. Code is available at https://github.com/cxmomo/RaCFormer.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **问题背景**：在自动驾驶场景的3D目标检测中，纯相机+毫米波雷达的方案因成本优势备受关注，但其检测精度仍与激光雷达方案存在较大差距。
- **核心痛点**：现有性能领先的雷达-相机融合方法多在鸟瞰视角（BEV）下融合特征，但图像的BEV变换高度依赖像素深度估计；当深度预测不准确时，投影得到的相机BEV特征会发生畸变，导致融合时多模态特征无法精确对齐。
- **研究动机**：原始透视图像特征富含语义且不含投影失真，若能同时利用BEV和图像视图的特征，可能缓解视图变换引入的对齐误差。因此，作者提出一个问题：何种融合范式能不受特征密度差异影响，同时有效利用不同视图的信息？
- **整体含义**：本文提出一种基于查询（query）的雷达-相机融合框架RaCFormer，通过可学习的对象查询自适应地从 BEV 和原始图像视图中采样实例相关特征，从而规避对精确深度估计的强依赖，并进一步提升融合质量。

## 2. 论文提出的方法论

### 2.1 整体框架
- 采用 **查询驱动的 Transformer 解码器** 作为特征融合与检测的核心。
- 输入：多帧多视角的相机图像与多帧雷达点云。
- 关键模块：图像编码器、柱状编码器（Pillar Encoder）、雷达引导的深度头部、LSS 视图变换、隐式动态捕获器、以及包含环状初始化和射线采样的 Transformer 解码器。

### 2.2 雷达感知的深度预测与相机 BEV 生成
- **雷达投影预处理**：由于车载雷达垂直角分辨率低，原始 z 坐标误差大。方法将所有雷达点 z 固定为 1 后投影到图像平面，并将投影点的垂直坐标扩展到整幅图像高度，形成粗糙的雷达深度图。
- **特征增强**：对投影点的深度值采用间距递增离散化，并将雷达散射截面积（RCS）和像素位置嵌入后，与 16 倍下采样的图像特征拼接，送入深度头部。
- **相机 BEV 生成**：利用增强后的深度概率分布和图像特征，通过标准的 Lift-Splat-Shoot（LSS）方法生成相机 BEV 特征。

### 2.3 隐式动态捕获器与雷达 BEV 生成
- **雷达 BEV 编码**：将雷达点 z 坐标置零后采用 Pillar-based 方法编码，得到初始雷达 BEV 特征。
- **隐式动态捕获器（IDC）**：利用 ConvGRU 对连续多帧的雷达 BEV 特征进行时序建模，累积隐藏状态，并通过卷积层融合当前帧与隐藏状态，从而在 BEV 层面捕捉由多普勒效应隐含的运动信息。
- 公式表示：\( h_t = \text{ConvGRU}(x_t, h_{t-1}) \)，\( x'_t = \text{Conv2D}(h_t \oplus x_t) \)。

### 2.4 查询初始化与跨视角采样
- **线性递增环状查询分布**：提出在极坐标下使用同心圆初始化查询。内圈分配 \(n\) 个查询点，每向外一圈查询数线性乘以增长因子 \(\alpha\)，使远处查询密度不至于过稀。总查询数 \(N = (1+\alpha+\dots+\alpha^{k-1})\times n\)。当 \(\alpha=1\) 时退化为等角间距的射线分布。
- **射线采样**：每个查询定义一段射线（径向相邻圆环的间隔），在该段内自适应选取采样点，并通过可变形注意力既在时序对齐的历史 BEV 特征上采样，也在多帧多相机图像上投影采样，最终利用自适应混合器聚合跨通道、跨点的特征。
- **解码器结构**：包含 6 层权重共享的 Transformer 层，每层依次执行尺度自适应自注意力、BEV 射线采样、图像射线采样及自适应混合。

## 3. 实验设计

- **数据集与场景**：
  - **nuScenes**：包含 1000 个场景，分 700/150/150 用于训练/验证/测试，提供相机、雷达、激光雷达等数据。评价指标为 mAP、NDS 以及五个子指标（mATE, mASE, mAOE, mAVE, mAAE）。
  - **View-of-Delft (VoD)**：包含 8693 帧同步的 64 线 LiDAR、立体相机和 3+1D 雷达数据，标注了行人、自行车、汽车。评价沿用 KITTI 的 3D AP 指标，区分整个标注区域和感兴趣区域（ROI）。
- **对比方法**：
  - 相机-only 方法：StreamPETR、RayFormer、PolarFormer 等。
  - 雷达-相机融合方法：CRN、RCBEVDet、HVDetFusion、HyDRa 等。
  - 激光雷达-only 方法：CenterPoint、VoxelNeXt 等（作为上限参考）。
- **实现设置**：nuScenes 上使用 8 帧历史序列（0.5s 间隔），BEV 范围为半径 65m 圆，\(k=6\) 个同心圆，内圈 \(n=80\)，增长因子 \(\alpha=1.25\)，总查询 900。VoD 上感知扇区半径 55m，\(k=8\)，内圈 \(n=30\)，总查询 600。默认 ResNet-50/101 或 V2-99 作为图像骨干，训练 24 或 36 个 epoch，优化器 AdamW，余弦退火，全局 batch size 8。

## 4. 资源与算力

- 文中**未明确给出训练时使用的 GPU 数量与型号**，仅提及全局 batch size 为 8（可能采用单卡或多卡训练，无详细说明）。
- 轻量实时版本在 **单张 RTX 3090** 上推理达到 12 FPS，可作为算力参考，但此并非完整训练配置。
- 整体训练时长、计算量（如 GFLOPs）等信息亦未提供，资源透明度有限。

## 5. 实验数量与充分性

- **总计实验组数较多**，主要包括：
  - 在 nuScenes 验证集上不同骨干、分辨率的对比实验（表1）。
  - nuScenes 测试集上与多种方法的全面对比（表2）。
  - VoD 数据集上的对比实验（表3）。
  - 消融实验：特征解码方式与视图选择（表4）、雷达深度/RCS 嵌入（表5）、隐式动态捕获器在不同速度对象上的影响（表6）、环形查询超参数（表7）、天气光照场景分析（表8）、传感器失效鲁棒性实验（表9）。
  - 推理速度与轻量模型性能测试。
- **实验充分性**：消融实验覆盖了所提核心组件，并在多个维度（精度、子指标、速度、鲁棒性）进行了评估。对比方法涵盖同时期的最优融合方法和单模态基线，且在相同设置下重训或引用官方结果，比较较为公平。对速度、运动、天气等特定场景的分析增强了结论的可靠性。
- **潜在薄弱点**：未对雷达深度头的具体设计（如离散化函数）、IDC模块的卷积核大小等进行进一步消融；鲁棒性测试只给出了car类AP，未展示mAP等综合指标；没有与更近期的融合方法（如论文发表同期可能存在的）进行对比，但限于时间线属正常。

## 6. 论文的主要结论与发现

- 查询驱动的跨视角雷达-相机融合可以有效避免 BEV 融合中因深度误差导致的特征未对齐问题。
- 雷达感知的深度预测、线性递增环状查询初始化以及利用ConvGRU捕获雷达时序信息的隐式动态捕获器，三者均对检测精度有显著贡献。
- RaCFormer 在 nuScenes 测试集上达到 64.9% mAP、70.2% NDS，超越所有相机-雷达融合方法，并在不使用 LiDAR 的情况下部分弥补了与 LiDAR 方法的差距。
- 在 VoD 数据集上同样取得最优成绩（ROI 区域 mAP 78.57%），且对雨天、黑夜等恶劣场景以及传感器失效情况表现出更强的鲁棒性。

## 7. 优点

- **融合范式新颖**：将查询作为桥梁直接采样图像和 BEV 特征，绕过了严格的 BEV 对齐要求，具备跨视角信息交互的优势。
- **雷达信息利用深入**：不仅用于深度增强，还通过 RCS 嵌入等充分利用雷达的语义属性；利用多普勒效应设计 IDC 模块捕捉运动，改善了速度估计。
- **查询初始化合理**：提出的线性递增环状分布更符合远景目标稀疏、近景密集的感知特性，且对齐了相机透视投影原理。
- **实验证明充分**：在两大主流数据集上取得 SOTA，并通过多维度的消融和鲁棒性实验充分论证了各组件的有效性。
- **兼顾实时性**：提供了轻量变体，可在消费级 GPU 上实时运行并保持较高精度，实用性强。

## 8. 不足与局限

- **算力成本不明**：未给出训练所需 GPU 资源和确切训练时间，不利于复现和工程落地评估。
- **对雷达高度误差的处理较为粗糙**：投影时强行置 z=1 并扩展到全图高度，虽缓解了雷达点落出目标的问题，但可能引入大量背景噪声，当雷达点稀疏时此策略的增益可能下降。
- **动态捕获器依赖多帧**：IDC 模块隐含了连续帧时间间隔的假设，对帧率不稳定或大运动场景的泛化性未做深入探讨。
- **仅关注单模态缺失的鲁棒性**：传感器失效测试仅提供了 car 类的 AP，缺乏整体性能分析；未评估雷达噪声、丢帧等更复杂的退化情况。
- **查询数量的手工设定**：环形查询的参数（圆数、增长因子）需要根据感知范围和数据集调整，可能增加调参成本，缺乏自适应机制。

（完）
