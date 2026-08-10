---
title: "MI-DETR: An Object Detection Model with Multi-time Inquiries Mechanism"
title_zh: MI-DETR：一种具有多时间查询机制的目标检测模型
authors: "Nan, Zhixiong, Li, Xianghong, Dai, Jifeng, Xiang, Tao"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Nan_MI-DETR_An_Object_Detection_Model_with_Multi-time_Inquiries_Mechanism_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 10.0
evidence: DETR目标检测采用并行多时间查询机制
tldr: 针对现有DETR级联解码器仅沿级联方向更新、信息学习受限的问题，本文提出MI-DETR，采用并行多时间查询（MI）机制，使目标查询能并行多次学习图像特征，更充分利用特征信息，从而在小目标、严重遮挡等困难场景中取得明显性能提升。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-nan-mi-detr-an-object-detection-model-with-multi-time-inquiries-mechanism-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 864, \"height\": 477, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-nan-mi-detr-an-object-detection-model-with-multi-time-inquiries-mechanism-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1796, \"height\": 959, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-nan-mi-detr-an-object-detection-model-with-multi-time-inquiries-mechanism-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 870, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-nan-mi-detr-an-object-detection-model-with-multi-time-inquiries-mechanism-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 875, \"height\": 386, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-nan-mi-detr-an-object-detection-model-with-multi-time-inquiries-mechanism-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1811, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-nan-mi-detr-an-object-detection-model-with-multi-time-inquiries-mechanism-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 869, \"height\": 438, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-nan-mi-detr-an-object-detection-model-with-multi-time-inquiries-mechanism-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1562, \"height\": 1120, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-nan-mi-detr-an-object-detection-model-with-multi-time-inquiries-mechanism-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 805, \"height\": 329, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-nan-mi-detr-an-object-detection-model-with-multi-time-inquiries-mechanism-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1553, \"height\": 505, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-nan-mi-detr-an-object-detection-model-with-multi-time-inquiries-mechanism-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 663, \"height\": 116, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-nan-mi-detr-an-object-detection-model-with-multi-time-inquiries-mechanism-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 773, \"height\": 418, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-nan-mi-detr-an-object-detection-model-with-multi-time-inquiries-mechanism-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 678, \"height\": 284, \"label\": \"Table\"}]"
motivation: DETR级联解码器限制查询特征学习，影响困难目标检测。
method: 提出并行多时间查询解码器，让查询多次学习特征。
result: 在困难场景下检测性能超过传统DETR模型。
conclusion: 多时间查询机制有效增强了DETR的特征利用能力。
---

## Abstract
Based on analyzing the character of cascaded decoder architecture commonly adopted in existing DETR-like models, this paper proposes a new decoder architecture. The cascaded decoder architecture constrains object queries to update in the cascaded direction, only enabling object queries to learn relatively-limited information from image features. However, the challenges for object detection in natural scenes (e.g., extremely-small, heavily-occluded, and confusingly mixed with the background) require an object detection model to fully utilize image features, which motivates us to propose a new decoder architecture with the parallel Multi-time Inquiries (MI) mechanism. MI mechanism is very simple, enabling object queries to parallelly perform multi-time inquiries to learn more comprehensive information from image features. Our MI based model, MI-DETR, outperforms all existing DETR-like models on COCO benchmark under different backbones and training epochs, achieving +2.3 AP and +0.6 AP improvements compared to the most representative model DINO and SOTA model Relation-DETR under ResNet-50 backbone.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义
**研究动机和背景**
- 现有的 DETR 类检测模型普遍采用级联的解码器架构，对象查询（object queries）只能沿级联方向逐层更新，从图像特征中学习的信息相对有限。
- 自然场景中目标存在极度微小、严重遮挡、与背景混淆等挑战，要求模型更充分地利用图像特征，而级联架构制约了特征利用的深度和广度。
- 受到传统 CNN 方法中并行分支增强特征利用的启发，本文提出一种新的**并行多时间查询（Multi-time Inquiries, MI）**解码器架构，以挖掘多模式、互补的信息，提升检测性能。

### 2. 论文提出的方法论
**核心思想**  
- 在解码器的每一层，令对象查询通过多个**参数独立**的查询头（inquiry heads）并行地多次与图像特征交互，学习不同模式的信息，并融合这些信息，从而获得更全面丰富的特征表示。

**关键技术细节**
- **多时间查询（MI）**：在 i 层解码器中，对象查询 \(Q_{i-1}\) 同时输入 \(M\) 个独立查询头，每个头包含自注意力（SA）、交叉注意力（CA）和前馈网络（FFN），与对应的编码器特征 \(E_j\) 交互，得到 \(M\) 组更新的查询 \(Q_i^k\)。随后通过拼接和线性投影融合成 \(Q_i\)。
- **U 型特征交互（UFI）**：受 U-Net 启发，将编码器各层特征 \(\{E_1,...,E_L\}\) 与最后一层特征 \(E_L\) 融合（\(E_j = \text{Linear}(\text{Concat}(E_j, E_L))\)），并作为第 \(i\) 层解码器（对应编码器第 \(j = L-i+1\) 层）的 Key&Value，促进低层细节和高层抽象信息的复用。
- **Lite-MI**：为降低参数量，多个查询头共享自注意力层，仅保留独立 CA 和 FFN。

**算法流程**  
1. 图像经 backbone 和 L 层编码器提取多尺度特征 \(E=\{E_1,...,E_L\}\)。  
2. 在每一解码器层，利用 UFI 生成融合特征 \(E_j\)。  
3. 对象查询 \(Q_{i-1}\) 通过 \(M\) 个并行查询头（SA + CA + FFN）分别计算 \(Q_i^k\)。  
4. 将 \(M\) 组查询沿特征维拼接，经线性层融合得到 \(Q_i\)。  
5. 最后一层输出用于预测边界框和类别。

### 3. 实验设计
**数据集与基准**
- 使用 COCO 2017 数据集，train2017（118k）训练，val2017（5k）验证。
- 评价指标为标准 AP、AP\(_{50}\)、AP\(_{75}\)、AP\(_S\)、AP\(_M\)、AP\(_L\)。

**对比方法**
- 与 2023 年后提出的众多 DETR 变体对比，包括 DINO、Stable-DINO、Rank-DETR、Align-DETR、DDQ-DETR、DAC-DETR、H-DETR、Group-DETR、MS-DETR、Relation-DETR 等。
- 对比涵盖不同 backbone（ResNet-50、Swin-L）和训练时长（12 epoch、24/36 epoch）。

### 4. 资源与算力
- **GPU 使用**：ResNet-50 实验采用 RTX3090，Swin-L 实验采用 A100。
- **训练配置**：优化器为 AdamW，学习率 \(1\times10^{-4}\)，权重衰减 \(1\times10^{-4}\)，训练 12 或 24 个 epoch（根据方法收敛情况调整）。
- 未明确提及单次训练的具体 GPU 小时数，但给出了不同配置下的 GFLOPS 和参数量（如 6 层 4 头约 299 GFLOPS、75M 参数）。

### 5. 实验数量与充分性
**主要实验模块**
- **主对比实验**：不同 backbone、不同训练 epoch 下与 10+ 种方法的性能对比（表 1、3）。
- **消融实验**：验证 MI、Lite-MI、UFI 各组件的贡献（表 2）；测试查询头数量（1–5）对性能的影响（表 4）；分析不同查询头组合的效果（表 5）；将 MI 插入 DINO 和 Relation-DETR 以考察稳健性（表 3）。
- **复杂度分析**：对比增加解码器层数与增加查询头数对性能-参数的影响（表 6），证明性能提升来自 MI 而非单纯增加参数。
- **可视化**：通过 t-SNE 展示不同查询头学习到的查询分布差异；可视化各查询头及融合后的检测结果，分析互补性（图 4–6）。

**充分性与公平性评价**
- 实验覆盖多种主流对比方法、不同 backbone 和训练设定，多组消融证实了各组件的有效性。
- 复杂度对比实验排除了“性能提升仅因参数增加”的误解，增强了结论的可信度。
- 整体实验设计较为充分、客观。

### 6. 论文的主要结论与发现
- 提出的并行 MI 解码器使对象查询能学习多模式互补信息，显著提升特征利用效率。
- MI-DETR 在 COCO 上达到领先水平，ResNet-50 下 12 epoch 获得 52.4 AP，24 epoch 获得 52.7 AP，相比 DINO 提升 2.3 AP，相比 Relation-DETR 提升 0.6 AP；Swin-L 下 12 epoch 达到 58.2 AP。
- MI 可方便插入现有 DETR 模型，带来一致且明显的增益。
- 查询头数量不宜过多（过多反而有干扰），独立参数带来真正的并行学习，优于以往共享参数的伪并行方案。
- UFI 通过复用编码器多层特征进一步强化了解码器输入。

### 7. 优点
- **创新性强**：将解码器的“级联查询”改为“并行多查询”，思路新颖，直接针对特征利用不足的问题。
- **即插即用，通用性好**：MI 解码器结构简单，可轻松嵌入 DINO、Relation-DETR 等现有模型。
- **性能提升显著**：在多个 baseline 和骨干网络上均取得最优，且在小目标、遮挡等困难场景有更佳的定性结果。
- **分析透彻**：通过查询头组合实验、可视化分析以及复杂度对比，充分阐释了 MI 的机理，排除了简单参数堆积的干扰。
- **辅助模块合理**：UFI 使得高低层特征直接对接，符合编码-解码的信息流动直觉。

### 8. 不足与局限
- **实验场景局限**：仅在 COCO 数据集上测试，未验证在其他目标检测数据集（如 Objects365、Pascal VOC）或迁移到分割、跟踪任务的泛化能力。
- **查询头选择敏感**：实验显示头数过多（≥5）性能下降，但最佳头数可能因数据集和模型规模而异，缺乏自适应机制或指导原则。
- **计算开销**：虽然对比实验证明并非纯粹堆参数，但仍比基础模型增加了计算量（如 6 层 4 头需 299 GFLOPS, 75M 参数），实时性要求较高的场景需进一步轻量化。
- **解释性有限**：尽管可视化展示了不同查询头关注的模式不同（大/小目标等），但受限于神经网络的“黑箱”，无法清晰定义每个头具体学习了何种固定模式，合作机制的解释仍属推断。
- **未讨论与最新 tricks 的结合**：如去噪训练（DN-DETR）等技术是否与 MI 正交兼容，文中未深入探讨。

（完）
