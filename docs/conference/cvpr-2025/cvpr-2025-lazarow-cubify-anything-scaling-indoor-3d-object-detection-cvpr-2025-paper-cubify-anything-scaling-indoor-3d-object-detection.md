---
title: "Cubify Anything: Scaling Indoor 3D Object Detection"
title_zh: Cubify Anything：扩展室内3D目标检测规模
authors: "Lazarow, Justin, Griffiths, David, Kohavi, Gefen, Crespo, Francisco, Dehghan, Afshin"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Lazarow_Cubify_Anything_Scaling_Indoor_3D_Object_Detection_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 10.0
evidence: 提出Cubify Transformer (CuTR)，基于2D特征的完全Transformer室内3D目标检测基线
tldr: 针对现有室内3D目标检测数据集规模、精度和多样性不足的问题，本文构建了包含40万标注对象的Cubify-Anything 1M (CA-1M)数据集，并提出完全Transformer基线模型CuTR，直接从2D特征预测3D框。实验表明，CuTR在手持设备采集的RGB-D数据上实现了优越的3D检测性能，证明了大规模数据和Transformer架构在3D目标检测中的有效性，为室内场景理解提供了新基准。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-lazarow-cubify-anything-scaling-indoor-3d-object-detection-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1751, \"height\": 826, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-lazarow-cubify-anything-scaling-indoor-3d-object-detection-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1791, \"height\": 604, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-lazarow-cubify-anything-scaling-indoor-3d-object-detection-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 822, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-lazarow-cubify-anything-scaling-indoor-3d-object-detection-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 889, \"height\": 182, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-lazarow-cubify-anything-scaling-indoor-3d-object-detection-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 823, \"height\": 318, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-lazarow-cubify-anything-scaling-indoor-3d-object-detection-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1424, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-lazarow-cubify-anything-scaling-indoor-3d-object-detection-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1768, \"height\": 871, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-lazarow-cubify-anything-scaling-indoor-3d-object-detection-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1719, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-lazarow-cubify-anything-scaling-indoor-3d-object-detection-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 645, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-lazarow-cubify-anything-scaling-indoor-3d-object-detection-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1778, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-lazarow-cubify-anything-scaling-indoor-3d-object-detection-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 893, \"height\": 350, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-lazarow-cubify-anything-scaling-indoor-3d-object-detection-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 644, \"height\": 201, \"label\": \"Table\"}]"
motivation: 现有室内3D目标检测数据集存在规模小、精度低、对象多样性不足等局限。
method: 构建CA-1M大规模数据集，并提出Cubify Transformer直接从2D特征预测3D框。
result: 在手持设备RGB-D数据上实现领先的3D目标检测精度。
conclusion: 该数据集和Transformer基线显著推动了室内3D目标检测的研究边界。
---

## Abstract
We consider indoor 3D object detection with respect to a single RGB(-D) frame acquired from a commodity handheld device. We seek to significantly advance the status quo with respect to both data and modeling. First, we establish that existing datasets have significant limitations to scale, accuracy, and diversity of objects. As a result, we introduce the Cubify-Anything 1M (CA-1M) dataset, which exhaustively labels over 400K 3D objects on over 1K highly accurate laser-scanned scenes with near-perfect registration to over 3.5K handheld, egocentric captures. Next, we establish Cubify Transformer (CuTR), a fully Transformer 3D object detection baseline which rather than operating in 3D on point or voxel-based representations, predicts 3D boxes directly from 2D features derived from RGB(-D) inputs. While this approach lacks any 3D inductive biases, we show that paired with CA-1M, CuTR outperforms point-based methods, accurately recalling over 62% of objects in 3D, and is significantly more capable at handling noise and uncertainty present in commodity LiDAR-derived depth maps while also providing promising RGB only performance without architecture changes. Furthermore, by pre-training on CA-1M, CuTR can outperform point-based methods on a more diverse variant of SUN RGB-D, supporting the notion that while inductive biases in 3D are useful at the smaller sizes of existing datasets, they fail to scale to the data-rich regime of CA-1M. Overall, this dataset and baseline model provide strong evidence that we are moving towards models which can effectively Cubify Anything.

---

## 论文详细总结（自动生成）

## 论文结构化总结

### 1. 核心问题与研究动机
- 现有室内 3D 目标检测数据集普遍存在 **规模小、标注精度低、对象多样性不足** 的问题（通常仅标注大件家具，且因基于噪声深度重建而存在投影偏差）。
- 主流检测方法依赖 **点云或体素等 3D 表示**，内置了强 3D 归纳偏置和稀疏计算等复杂操作，虽然在 SUN RGB‑D 等小规模数据集上领先，但难以扩展到更大规模、更高精度的标注数据，且对消费级深度噪声敏感。
- 作者认为：若能提供 **像素完美、与传感器解耦** 的大规模 3D 框标注，并采用 **无 3D 归纳偏置** 的纯图像域 Transformer 架构，就有可能突破现有瓶颈，实现真正的“万物可立方体化”（Cubify Anything）。

### 2. 方法论：Cubify‑Anything‑1M (CA‑1M) 数据集与 Cubify Transformer (CuTR)
#### 2.1 CA‑1M 数据集
- **数据基础**：复用 ARKitScenes 的原始 iPad Pro 采集（>1K 场景，约 3.5K 段手持视频）和高精度 FARO 激光扫描。
- **标注方式**：在 FARO 扫描点云上 **穷举式、类别无关** 地标注 9‑DOF 3D 框（即尺寸 + 位置 + 完整 3 维旋转），总计 **>439K 个物体**。
- **像素完美投影**：利用高精度相机‑扫描仪配准，把世界坐标系下的 3D 框 **渲染** 到每一帧，生成准确反映视角、遮挡的 2D/3D 框，避免了传统方法仅对噪声重建标注再反投影的畸变。
- 最终得到 **>15M 帧（含至少一个 GT 实例）** 的训练数据，均为从手持设备采集的**单帧图像级** 标注（而非场景级拼接）。

#### 2.2 CuTR 模型
- **整体框架**：单阶段、单尺度 Transformer 检测器，完全在 **2D 图像域** 操作，无需将输入提升到 3D 空间。
- **Backbone**：
  - RGB‑D 变体：采用 **MultiMAE**，分别对高分辨率 RGB（如 1024×768）和低分辨率深度（256×192）进行分块 token 化，联合编码。
  - RGB 变体：采用 **Depth‑Anything** 作为骨干，无需任何度量尺度先验。
- **3D 框预测器**：借鉴 Plain DETR，解码器在标准 2D 框预测之外添加一个 MLP 头，直接回归：
  - 投影的 3D 中心 (x, y) 和深度 z
  - 3D 尺寸 (l, w, h)
  - 方向角（仅偏航角 yaw，假设重力对齐）
- **深度尺度恢复**（仅 RGB‑D）：根据输入的 LiDAR 深度图计算出仿射统计量 μ, σ，用 `z′ = σ·z + μ` 与 `(l′, w′, h′) = (σ·l, σ·w, σ·h)` 将预测尺度对齐到真实世界。
- **损失与匹配**：使用 **倒角距离 (Chamfer loss)** 监督预测 3D 框的 8 个角点；基于 2D 框的匈牙利匹配进行真值分配，**完全避免 NMS 后处理**。
- **可访问性**：仅依赖 MLP 和标准 Transformer 算子，无需稀疏卷积或体素化，可直接在 Apple Silicon、Neural Engine、ONNX 等架构上加速。

### 3. 实验设计
#### 3.1 评估数据集
- **SUN RGB‑D**（传统 10 类 + Omni3D 38 类）：代表小规模、多类别场景。
- **ScanNet++**：用于验证预训练效果。
- **CA‑1M**：大规模、类别无关、单帧目标检测。

#### 3.2 基准方法与对比
- **3D 点/体素方法**：ImVoxelNet (RGB‑only)、FCAF、TR3D、TR3D+FF（均使用深度点云）。
- **2D 图像域方法**：Cube R‑CNN（单目 RGB）、作者提出的 **CuTR (RGB‑D)** 和 **CuTR (RGB only)**。
- 所有方法均限制 **最多 100 个检测输出**，使用 3D IoU 阈值 0.25 和 0.50 下的平均精确率 (AP) 和平均召回率 (AR) 进行评价（类别无关时视为单一类别）。

### 4. 资源与算力
- 论文正文及附录 **未明确给出** GPU 型号、数量、训练时长等具体算力配置，仅说明模型在多种消费级加速器上可高效运行。

### 5. 实验数量与充分性
- **主要实验组**：
  - 在 **传统 SUN RGB‑D**、**Omni3D SUN RGB‑D**、**CA‑1M** 三个数据集上的对比实验（多模型）。
  - 使用 **地面真值深度 (FARO)** 替代 LiDAR 深度的消融实验。
  - 利用 **CA‑1M 作为预训练**，再微调至 Omni3D SUN RGB‑D，其与**从 ARKitScenes、ScanNet++ 预训练** 的对比。
  - 定性可视化对比。
- 共约 **5 张表格**，涵盖多方法、多数据集、多指标，消融充分，**对比公平**（统一检测数上限、统一评估代码）。实验规模足以支撑核心结论。

### 6. 主要结论与发现
- **CA‑1M 提供新的基准**：CuTR (RGB‑D) 在 CA‑1M 上召回率 **>62%**，比最强点方法高出约 10 个百分点；在 AP50 等指标上也明显领先。
- **点方法对深度噪声更敏感**：使用高精度深度时，点方法的差距大幅缩小，但仍不敌 CuTR，说明图像域方法能更好地处理消费级 LiDAR 的不确定性。
- **大规模预训练逆转了 SUN RGB‑D 上的劣势**：在 Omni3D SUN RGB‑D 上，仅用 CA‑1M 预训练后，CuTR 在所有指标上 **超越了** 所有点方法，而此前在传统小型数据集上点方法还略占优势。
- **3D 归纳偏置在小数据时有用，在大数据、高精度标注下反而失效**，图像域 Transformer 展现出更好的扩展性。

### 7. 优点
- 数据集层面：**首度提供** 像素完美、类别无关、穷举标注的单帧 3D 目标检测数据集，解耦了标注与传感器噪声。
- 模型设计：**完全 2D 图像域** 的简洁架构，无 NMS，不依赖特殊加速器，兼具 RGB‑D 和 RGB‑only 能力，易于部署。
- 实验结果：在多个数据集上均具竞争力，**通过系统消融有力证明了架构与数据规模的影响**。
- 开源计划：承诺公开数据集与 CuTR 模型，促进社区研究。

### 8. 不足与局限
- **任务范围**：仅针对单帧 3D 检测，未利用多帧时序或多视角融合，不一定代表全场景重建视角的性能。
- **语义缺失**：CA‑1M 为类别无关标注，CuTR 当前仅输出检测框，不做语义分类。
- **方向简化**：仅预测偏航角，忽略 pitch、roll，对非重力对齐物体（如翻倒的椅子）可能不适用。
- **深度分辨率**：仅使用 256×192 的稀疏 LiDAR 深度，可能损失精细几何信息。
- **对比方法**：点方法骨干较早期（如 TR3D/FCAF），未与最新点 Transformer 等更先进架构对比。
- **数据集代表性**：仅基于 iPad Pro 和特定场景（Apple 采集），泛化到其他传感器或极端环境仍需验证。

（完）
