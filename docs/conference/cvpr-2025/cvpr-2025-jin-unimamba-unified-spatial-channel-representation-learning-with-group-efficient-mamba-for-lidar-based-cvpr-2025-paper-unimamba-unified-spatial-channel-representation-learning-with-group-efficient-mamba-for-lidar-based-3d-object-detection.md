---
title: "UniMamba: Unified Spatial-Channel Representation Learning with Group-Efficient Mamba for LiDAR-based 3D Object Detection"
title_zh: UniMamba：面向LiDAR 3D目标检测的统一空间-通道表征学习与分组高效Mamba
authors: "Jin, Xin, Su, Haisheng, Liu, Kai, Ma, Cong, Wu, Wei, HUI, Fei, Yan, Junchi"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Jin_UniMamba_Unified_Spatial-Channel_Representation_Learning_with_Group-Efficient_Mamba_for_LiDAR-based_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 8.0
evidence: 基于Mamba架构的LiDAR 3D目标检测
tldr: 针对Transformer在LiDAR 3D检测中破坏空间结构和感受野受限的问题，提出统一Mamba网络（UniMamba），无缝集成空间-通道表征学习，高效捕捉全局依赖，在多个3D检测基准上取得竞争性能。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-jin-unimamba-unified-spatial-channel-representation-learning-with-group-efficient-mamba-for-lidar-based-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 825, \"height\": 706, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-jin-unimamba-unified-spatial-channel-representation-learning-with-group-efficient-mamba-for-lidar-based-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1787, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-jin-unimamba-unified-spatial-channel-representation-learning-with-group-efficient-mamba-for-lidar-based-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1787, \"height\": 1017, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-jin-unimamba-unified-spatial-channel-representation-learning-with-group-efficient-mamba-for-lidar-based-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1811, \"height\": 735, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-jin-unimamba-unified-spatial-channel-representation-learning-with-group-efficient-mamba-for-lidar-based-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1799, \"height\": 330, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-jin-unimamba-unified-spatial-channel-representation-learning-with-group-efficient-mamba-for-lidar-based-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1835, \"height\": 717, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-jin-unimamba-unified-spatial-channel-representation-learning-with-group-efficient-mamba-for-lidar-based-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 861, \"height\": 233, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-jin-unimamba-unified-spatial-channel-representation-learning-with-group-efficient-mamba-for-lidar-based-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 878, \"height\": 461, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-jin-unimamba-unified-spatial-channel-representation-learning-with-group-efficient-mamba-for-lidar-based-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 865, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-jin-unimamba-unified-spatial-channel-representation-learning-with-group-efficient-mamba-for-lidar-based-cvpr-2025-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 842, \"height\": 237, \"label\": \"Table\"}]"
motivation: Transformer序列化破坏3D空间结构，且计算复杂度高导致感受野有限。
method: 提出UniMamba，整合Mamba模块实现统一空间-通道表征学习。
result: 在主流LiDAR 3D检测数据集上达到先进水平，计算效率更高。
conclusion: UniMamba为3D检测提供了一种高效的特征建模新范式。
---

## Abstract
Recent advances in LiDAR 3D detection have demonstrated the effectiveness of Transformer-based frameworks in capturing the global dependencies from point cloud spaces, which serialize the 3D voxels into the flattened 1D sequence for iterative self-attention. However, the spatial structure of 3D voxels will be inevitably destroyed during the serialization process. Besides, due to the considerable number of 3D voxels and quadratic complexity of Transformers, multiple sequences are grouped before feeding to Transformers, leading to a limited receptive field. Inspired by the impressive performance of State Space Models (SSM), in this paper, we propose a novel Unified Mamba (UniMamba), which seamlessly integrates the merits of 3D convolution and SSM in a concise multi-head manner, aiming to perform "local and global" spatial context aggregation efficiently and simultaneously. Specifically, a UniMamba block is designed which mainly consists of spatial locality modeling, complementary Z-order serialization and local-global sequential aggregator. The spatial locality modeling module integrates 3D submanifold convolution to capture the dynamic spatial position embedding before serialization. Then the efficient Z-order curve is adopted for serialization both horizontally and vertically. Furthermore, the local-global sequential aggregator adopts the channel grouping strategy to efficiently encode both "local and global" spatial inter-dependencies using multi-head SSM. Additionally, an encoder-decoder architecture with stacked UniMamba blocks is formed to facilitate multi-scale spatial learning hierarchically. Extensive experiments are conducted on three popular datasets: nuScenes, Waymo and Argoverse 2. Particularly, our UniMamba achieves 70.2 mAP on the nuScenes dataset.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有基于Transformer的激光雷达（LiDAR）3D目标检测方法虽然能捕捉全局依赖，但存在两个主要缺陷：
  - **空间结构破坏**：将3D体素展平为1D序列时，不可避免地丢失了体素间的空间局部拓扑关系。
  - **感受野受限**：由于Transformer的二次复杂度，必须将大量体素分组处理后送入模型，导致原本可以建模全局关系的Transformer实际上只能获得受限的窗口感受野。
- **研究动机**：状态空间模型（尤其Mamba架构）在保持线性复杂度的同时，能直接对完整序列进行建模，有望突破Transformer的局限，但直接应用时仍面临局部性缺失和空间多样性不足的挑战。
- **整体含义**：论文提出一种统一Mamba（UniMamba）架构，将3D稀疏卷积与双向状态空间模型高效融合，以低计算代价同时捕捉局部细节和全局上下文，为LiDAR 3D检测提供一种新的骨干网络范式。

### 2. 论文提出的方法论

UniMamba是一种体素化的3D骨干网络，核心模块为UniMamba Block，其主要设计包括：

- **空间局部性建模（Spatial Locality Modeling, SLM）**
  - 在将3D体素序列化之前，使用3D子流形稀疏卷积（`SubConv3D`）对非空体素进行动态位置嵌入，补偿序列化过程中的局部空间信息损失。
  - 实验表明，引入SLM后，即使使用随机扫描也能获得接近空间填充曲线的效果，且计算开销极低。

- **互补式Z阶序列化（Complementary Z-order Serialization）**
  - 采用计算高效的Z阶曲线（Z-order curve）将3D体素坐标映射为1D索引。
  - 为增强空间邻近保留，提出互补式Z阶：分别以X轴和Y轴为主序生成不同的序列，分别在两个Mamba层中使用，从水平和垂直两个方向强化局部拓扑保持。

- **局部‑全局序列聚合器（Local-Global Sequential Aggregator, LGSA）**
  - 核心思想：利用通道分组策略，在同一层内并行编码不同感受野的特征。输入特征沿通道维度分为`M`组，其中`J`组分配给**全局序列编码器（Global Sequential Encoder, GSE）**，其余分配给**局部序列编码器（Local Sequential Encoder, LSE）**，最后沿通道拼接并通过FFN进行交互。
  - **GSE**：将所有非空体素视为一个完整序列，利用双向Mamba直接建立全局感受野，无需窗口划分。
  - **LSE**：将体素划分为不重叠的3D窗口，在每个窗口内利用互补式Z阶序列化并使用双向Mamba编码局部细节，窗口间独立处理以保持局部紧凑性。

- **多尺度层次化骨干网络**
  - 采用编码器‑解码器结构堆叠多个UniMamba Block，通过步长{1,2,2}的下/上采样实现多尺度空间特征学习。
  - 整体检测器直接替换基线方法（如LION、SAFDNet）的骨干网络，保持BEV骨干和检测头不变。

公式与流程文字说明：
- Mamba的离散SSM：`ht = Ā h_{t-1} + B̄ x_t`，`y_t = C h_t`，其中`Ā`、`B̄`、`C`为输入依赖的参数。
- GSE处理：先按X轴Z阶排序得`F_X`，通过第一个Mamba层；再按Y轴Z阶重排得`F_Y`，通过第二个Mamba层，输出全局特征`F_G`。
- LSE处理：在窗口内按局部坐标进行Z阶扫描，组内双向Mamba，然后拼接所有组的输出`F_L`。
- LGSA聚合：`F_A = Concat[F_{G1},..., F_{GJ}, F_{L,J+1},..., F_{L,M}]`，后接 LayerNorm 和 FFN。

### 3. 实验设计

- **数据集与场景**：
  - **nuScenes**：700训练/150验证/150测试，10类交通参与物，重点评估mAP与NDS。
  - **Waymo Open Dataset (WOD)**：798训练/202验证，约16万样本，车辆、行人、骑行者，按点云数量划分L1/L2难度，使用mAP和mAPH。
  - **Argoverse 2**：1000个序列，200m×200m超长距离检测，26个类别，使用mAP评估。
- **对比方法**：与三大类骨干网络进行综合比较：
  - 稀疏卷积类：CenterPoint、VoxelNeXt、HEDNet、LargeKernel3D、SAFDNet等。
  - Transformer类：DSVT、FlatFormer、SST、OcTr等。
  - Mamba/SSM类：LION‑Mamba、VoxelMamba等。
- **实验设置**：
  - 基于LION框架实现，仅替换3D骨干，其余配置（体素尺寸、BEV骨干、检测头、损失函数）与基线完全一致。
  - 通道分组数`M=4`，其中`J=2`组使用GSE，其余用LSE。
  - 无测试时增强（TTA）和模型集成。

### 4. 资源与算力

- 文中明确说明所有实验在**8块Tesla A800 GPU**上进行。
- 优化器为**AdamW**，其他训练超参与基线保持一致。
- 未给出具体的单次训练时长，但提供了计算量对比：UniMamba在Waymo上实现75.40 L2 mAP时计算量为**61.9 GFlops**，参数量为**1.6M**，相较于DSVT（110.2 GFlops）大幅降低。

### 5. 实验数量与充分性

- 论文在三大数据集上分别进行了完整的测试集/验证集性能比较，总计约**12‑14组主流方法对比**，覆盖不同架构类型。
- 设计了系统的**消融实验**，数量充足且针对核心模块：
  - **空间局部性模块**：对比有无SLM、不同序列化曲线（随机、Hilbert、Z‑order、互补Z‑order）的性能与时耗。
  - **LGSA设计**：对比纯LSE、纯GSE、不同通道分组数（1/2/4/8）及LSE/GSE比例的影响。
  - **聚合方式**：对比顺序式、并行式和通道分组式的性能与延迟。
  - **效率分析**：与CenterPoint、FlatFormer、DSVT比较计算量、参数量与精度。
- 所有对比均基于统一基准（LION或Transfusion‑L）和相同数据集，保证公平性；消融实验控制变量严格，能充分反映每个模块的贡献。

### 6. 论文的主要结论与发现

- UniMamba成功将Mamba架构引入LiDAR 3D骨干网络，并通过SLM与互补Z阶序列化有效克服了局部空间信息丢失问题。
- 提出的局部‑全局序列聚合器（LGSA）可以同步捕获细粒度局部细节与远距离全局上下文，且通过通道分组以几乎零额外成本实现。
- 在nuScenes测试集上首次达到**70.2 mAP**，验证集上**68.5 mAP / 72.6 NDS**，全面超越此前的稀疏卷积、Transformer和纯Mamba方法。
- 在Waymo和Argoverse 2上均取得**当时最优（SOTA）**性能，对小目标（行人、骑行者）的提升尤为显著，验证了灵活感受野的重要性。
- 计算效率具有明显优势：性能超越DSVT的同时，GFlops仅约其一半。

### 7. 优点

- **架构统一且简洁**：将3D卷积的空间归纳偏置与SSM的长距离建模能力无缝整合，设计清晰。
- **高效感受野设计**：通过通道分组实现“局部‑全局”并行聚合，无需额外时序开销，延迟甚至低于传统串行方式。
- **局部性补偿机制**：SLM降低了对手动序列化曲线的依赖，使低成本的Z阶曲线能达到与高成本Hilbert曲线相当的精度。
- **全面且强劲的实验验证**：在三个主流大规模数据集上均取得顶尖结果，并且对大小目标均有稳定提升。
- **良好的即插即用性**：可方便替换现有检测器的3D骨干，无需修改检测头或训练策略。

### 8. 不足与局限

- **训练时长未明确**：虽给出了推理算力，但未报告完整的训练耗时或显存占用，难以直接估量训练成本。
- **超参数敏感性**：通道分组数`M`及GSE/LSE比例是基于nuScenes调节的，其他数据集可能需要重新调整（论文未讨论跨数据集的通用设定）。
- **长尾类别/极端场景**：Argoverse 2虽覆盖26类，但部分罕见类（如轮椅、动物等）AP仍很低，模型在小样本类别上的鲁棒性未深入探讨。
- **实时性受限**：虽然计算量优于部分Transformer，但61.9 GFlops对于边缘端车辆部署仍偏高，未讨论进一步轻量化或量化可能性。
- **缺乏自监督/预训练实验**：未探索该架构在大规模预训练或跨域迁移中的潜力。
- **序列化的潜在瓶颈**：Z阶序列的建立与重排可能成为纯C++部署时的工程难点，文中未提供物理部署的延迟评估。

（完）
