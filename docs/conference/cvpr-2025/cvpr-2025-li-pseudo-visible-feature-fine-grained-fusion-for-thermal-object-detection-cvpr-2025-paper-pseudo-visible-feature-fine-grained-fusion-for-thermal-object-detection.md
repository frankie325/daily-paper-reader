---
title: Pseudo Visible Feature Fine-Grained Fusion for Thermal Object Detection
title_zh: 伪可见特征细粒度融合用于热红外目标检测
authors: "Li, Ting, Ye, Mao, Wu, Tianwen, Li, Nianxin, Li, Shuaifeng, Tang, Song, Ji, Luping"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Li_Pseudo_Visible_Feature_Fine-Grained_Fusion_for_Thermal_Object_Detection_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 9.0
evidence: 提出伪可见特征细粒度融合用于热红外目标检测，利用跨模态图融合
tldr: 针对热红外目标检测中可见光信息利用不充分的问题，本文提出伪可见特征细粒度融合（PFGF）方法。先通过热到可见光（T2V）转换生成伪可见特征，再构建图结构融合多层次热特征与伪可见特征，充分挖掘互补信息。实验表明PFGF在多个热检测数据集上达到最优性能，证明了细粒度跨模态融合对提升热红外目标检测精度的有效性。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-pseudo-visible-feature-fine-grained-fusion-for-thermal-object-detection-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 925, \"height\": 736, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-pseudo-visible-feature-fine-grained-fusion-for-thermal-object-detection-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1706, \"height\": 1048, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-pseudo-visible-feature-fine-grained-fusion-for-thermal-object-detection-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 862, \"height\": 844, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-pseudo-visible-feature-fine-grained-fusion-for-thermal-object-detection-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 870, \"height\": 838, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-pseudo-visible-feature-fine-grained-fusion-for-thermal-object-detection-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 869, \"height\": 641, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-pseudo-visible-feature-fine-grained-fusion-for-thermal-object-detection-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 859, \"height\": 339, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-pseudo-visible-feature-fine-grained-fusion-for-thermal-object-detection-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 747, \"height\": 398, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-pseudo-visible-feature-fine-grained-fusion-for-thermal-object-detection-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 819, \"height\": 437, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-pseudo-visible-feature-fine-grained-fusion-for-thermal-object-detection-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 812, \"height\": 179, \"label\": \"Table\"}]"
motivation: 现有热检测模型未充分利用T2V转换生成的可见光互补信息。
method: 提出PFGF，构建图节点融合多层次热特征与伪可见特征，实现细粒度跨模态融合。
result: 在多个热检测数据集上达到最先进性能。
conclusion: 细粒度融合互补模态信息显著提升了热红外目标检测的精度。
---

## Abstract
Thermal object detection is a critical task in various fields, such as surveillance and autonomous driving. Current state-of-the-art (SOTA) models always leverage a prior Thermal-To-Visible (T2V) translation model to obtain visible spectrum information, followed by a cross-modality aggregation module to fuse information from both modalities. However, this fusion approach does not fully exploit the complementary visible spectrum information beneficial for thermal detection. To address this issue, we propose a novel cross-modal fusion method called Pseudo Visible Feature Fine-Grained Fusion (PFGF). Specifically, a graph is constructed with nodes generated from multi-level thermal features and pseudo-visual latent features produced by the T2V model. Each level of features corresponds to a subgraph. An Inter-Mamba block is proposed to perform cross-modality fusion between nodes at the lowest level; while a Cascade Knowledge Integration (CKI) strategy is used to fuse low-level fused information to high-level subgraphs in a cascade manner. After several iterations of graph node updating, each subgraph outputs an aggregated feature to the detection head respectively. Unlike previous cross-modal fusion methods, our approach explicitly models high-level relationships between cross-modal data, effectively fusing different granularity information. Experimental results demonstrate that our method achieves SOTA detection performance. Code is available at https://github.com/liting1018/PFGF.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义
- **研究背景**：热红外目标检测在夜间、雾天等低光照/恶劣条件下具有可见光图像不可比拟的鲁棒性，但热成像缺乏纹理细节，尤其在白天性能下降。已有方法借助“热转可见”（Thermal‑to‑Visible, T2V）生成模型获取伪可见信息，再通过跨模态聚合模块（如通道/空间注意力）进行融合。
- **核心问题**：现有融合策略（如图1(a)）未能充分挖掘伪可见特征与热特征之间的细粒度、多层次互补关系，且伪可见图像本身存在不可靠性与噪声，简单融合难以有效去除冗余、增强有益信息。
- **整体含义**：论文提出一种基于图神经网络与Mamba选择机制的细粒度跨模态融合框架（PFGF），显式建模不同粒度特征间的高阶关系，实现高效、鲁棒的伪可见知识融合，在仅使用热图像进行推理的条件下，将热目标检测性能推向最优。

### 2. 方法论
#### 2.1 整体框架
- 以YOLOX为基线检测器，训练和测试均只输入热图像。
- 训练一个热转可见生成模型Pearl‑GAN，将热图\(x^t\)转换为伪可见图像\(x^v\)，并得到潜在编码\(z\)（生成特征）。
- 骨干网络CSPDarknet接收拼接后的\(x^t\)和\(x^v\)，输出多级判别性特征\(c3, c4, c5\)，经VMamba块增强得到\(f^3, f^4, f^5\)。
- 核心模块**Graph‑Mamba Fusion (GMF)** 对生成特征\(z\)与判别特征\(f^3,f^4,f^5\)进行细粒度融合，输出\(g^3,g^4,g^5\)，再与原始特征残差连接后送入Neck和检测头。

#### 2.2 Graph‑Mamba Fusion（GMF）模块
- **图构建**：
  - 对每个特征（\(z, f^3, f^4, f^5\)）通过金字塔池化、卷积和上采样生成\(n=3\)个多粒度节点（\(f_i^j, z^j\)），形成四个子图。
  - 子图内，节点间边定义为可学习的差异卷积\(e_{j,k}^i = \text{Conv}(f_i^j - f_i^k)\)，仅在同一特征内部构建边以控制计算量。
- **消息传递**：节点聚合其邻居的加权消息，权重由Sigmoid边值决定。
- **跨模态融合（Inter‑Mamba）**：\(z\)子图与\(f^3\)子图的节点通过Inter‑Mamba块交互。先将节点特征序列化，分别经SSM提取隐藏状态，再通过门控机制（来自\(f^3\)的线性投影+Sigmoid）融合两种状态，最后残差连接。
- **级联知识集成（CKI）**：
  - 每个子图内用GRU更新节点特征，并用VMamba块精炼，然后通过拼接和VMamba得到“leader节点”特征\(g^i\)。
  - 低层leader节点\(g^i\)通过注意力（全局平均池化+Sigmoid）调制下一层子图的节点，实现从\(f^3\)到\(f^5\)的层次化知识传递。
- 最终输出\(g^3,g^4,g^5\)作为融合后的特征。

### 3. 实验设计
- **数据集**：
  - FLIR‑aligned：5142对热‑可见光图像，训练4129对，测试1013对，含person、car、bicycle三类。
  - LLVIP：15488对，极暗环境，单类person。
  - Autonomous Vehicles (AV)：6009对训练，1503对测试，含bike、car等5类，场景更复杂。
- **基准与对比方法**：
  - **单模态热方法**（仅热图像测试）：Faster R‑CNN、SSD、RetinaNet、YOLOv3、YOLOX‑L、IAH、DIP、TIRDet、IDA等。
  - **多光谱方法**（训练和测试均需可见+热）：CFR3、GAFF、YOLOFusion、CMX、IGT、DATFF、RSDet、Fusion‑Mamba等。
- **评价指标**：mAP、mAP50、mAP75。

### 4. 资源与算力
- 论文未明确说明所用GPU型号、数量及实际训练时长。
- 实现细节仅提及：使用MMDetection工具箱，SGD优化器，batch size=4，初始学习率5e‑4，输入尺寸640×640，训练8个epoch，随机种子0。未给出台式服务器或GPU卡消耗数据。

### 5. 实验数量与充分性
- 实验量较为充足，覆盖全面：
  - **3个主流热检测数据集**上的性能对比。
  - **消融实验**：逐一移除Pearl‑GAN、MEM、GMF、Inter‑Mamba、CKI，验证各组件贡献。
  - **不同融合策略对比**：加法、拼接、CMA、MMFT、GIM、FMB vs GMF，证明图‑Mamba融合的优越性。
  - **VMamba有效性**：将VMamba替换为Transformer（GMTF），比较参数量、FLOPs及精度。
  - **leader节点有效性**：有无leader节点的可视化对比。
- 对比方法覆盖热单模态与多模态主流模型，指标一致，保证了客观性与公平性。

### 6. 主要结论与发现
- PFGF在FLIR、LLVIP、AV三个数据集上均取得最优mAP，超越所有热单模态方法（如TIRDet、IDA），并优于多数多光谱方法，特别在mAP75上优势显著。
- 图‑Mamba融合模块能有效建模跨模态细粒度关系，Inter‑Mamba有效过滤伪可见噪声，CKI策略实现了从低层到高层语义的级联集成。
- VMamba相比Transformer在保持甚至提升精度的同时，参数量和计算量分别减少约7%和32%，更具效率。

### 7. 优点
- **方法新颖**：首次将图神经网络与Mamba结合，用于伪可见特征多层次细粒度融合，显式构建跨模态高阶关系。
- **设计精巧**：Inter‑Mamba借助SSM的门控机制有效抑制噪声；CKI以轻量级leader节点实现级联传递，避免全连接边带来的计算开销。
- **性能显著**：在三个数据集上均达到SOTA，不仅优于热单模态方法，也超越众多多光谱融合方法。
- **效率优势**：相较于Transformer，VMamba方案参数更少、FLOPs更低。
- **开源代码**，利于复现。

### 8. 不足与局限
- **算力信息缺失**：未报告任何GPU/训练时间数据，难以评估实际资源需求。
- **依赖T2V模型质量**：Pearl‑GAN需先行训练，其生成的伪可见质量可能成为瓶颈；文中虽在LLVIP上比较了不同Pearl‑GAN模型的效果，但未深入分析T2V失败情况下的影响。
- **两阶段训练**：流程分为T2V预训练和检测器训练，增加了训练复杂度。
- **数据集规模与多样性**：FLIR和LLVIP主要为行人、车辆等有限类别，AV也仅5类，在更开放场景下的泛化性尚未验证。
- **实时性未评估**：虽效率优于Transformer，但添加图‑Mamba模块后的推理速度（FPS）未给出，实际部署性能未知。
- **仅限于热红外对象检测**：方法虽可推广至其他跨模态任务，但论文未展开讨论。

（完）
