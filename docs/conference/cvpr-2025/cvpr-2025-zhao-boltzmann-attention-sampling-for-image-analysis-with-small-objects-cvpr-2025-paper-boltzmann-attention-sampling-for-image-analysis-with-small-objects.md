---
title: Boltzmann Attention Sampling for Image Analysis with Small Objects
title_zh: 用于小目标图像分析的玻尔兹曼注意力采样
authors: "Zhao, Theodore, Kiblawi, Sid, Usuyama, Naoto, Lee, Ho Hin, Preston, Sam, Poon, Hoifung, Wei, Mu"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Zhao_Boltzmann_Attention_Sampling_for_Image_Analysis_with_Small_Objects_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 10.0
evidence: 基于变压器的BoltzFormer用于小目标检测与分割
tldr: 传统Transformer在检测极小目标时因冗余注意力计算导致效率低下和性能退化。本文提出BoltzFormer，利用玻尔兹曼分布建模不确定性进行动态稀疏注意力，自适应聚焦相关区域，在医学影像等小目标检测与分割任务上取得显著提升，为Transformer在高分辨率小目标分析中的应用开辟了新路径。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-boltzmann-attention-sampling-for-image-analysis-with-small-objects-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1686, \"height\": 798, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-boltzmann-attention-sampling-for-image-analysis-with-small-objects-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 860, \"height\": 832, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-boltzmann-attention-sampling-for-image-analysis-with-small-objects-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 819, \"height\": 329, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-boltzmann-attention-sampling-for-image-analysis-with-small-objects-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 815, \"height\": 388, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-boltzmann-attention-sampling-for-image-analysis-with-small-objects-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 867, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-boltzmann-attention-sampling-for-image-analysis-with-small-objects-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1779, \"height\": 751, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-boltzmann-attention-sampling-for-image-analysis-with-small-objects-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 749, \"height\": 147, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-boltzmann-attention-sampling-for-image-analysis-with-small-objects-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 856, \"height\": 144, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-boltzmann-attention-sampling-for-image-analysis-with-small-objects-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 884, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-boltzmann-attention-sampling-for-image-analysis-with-small-objects-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 886, \"height\": 146, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-boltzmann-attention-sampling-for-image-analysis-with-small-objects-cvpr-2025-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 625, \"height\": 146, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-boltzmann-attention-sampling-for-image-analysis-with-small-objects-cvpr-2025-paper/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 754, \"height\": 145, \"label\": \"Table\"}]"
motivation: 小目标检测因区域占比极低，Transformer冗余注意力导致性能下降。
method: 提出基于玻尔兹曼分布的动态稀疏注意力BoltzFormer。
result: BoltzFormer在小目标检测分割上性能优于传统方法。
conclusion: 动态稀疏注意力有效解决了Transformer在小目标任务中的局限性。
---

## Abstract
Detecting and segmenting small objects, such as lung nodules and tumor lesions, remains a critical challenge in image analysis. These objects often occupy less than 0.1% of an image, making traditional transformer architectures inefficient and prone to performance degradation due to redundant attention computations on irrelevant regions. Existing sparse attention mechanisms rely on rigid hierarchical structures, which are poorly suited for detecting small, variable, and uncertain object locations. In this paper, we propose BoltzFormer, a novel transformer-based architecture designed to address these challenges through dynamic sparse attention. BoltzFormer identifies and focuses attention on relevant areas by modeling uncertainty using a Boltzmann distribution with an annealing schedule. Initially, a higher temperature allows broader area sampling in early layers, when object location uncertainty is greatest. As the temperature decreases in later layers, attention becomes more focused, enhancing efficiency and accuracy. BoltzFormer seamlessly integrates into existing transformer architectures via a modular Boltzmann attention sampling mechanism. Comprehensive evaluations on benchmark datasets demonstrate that BoltzFormer significantly improves segmentation performance for small objects while reducing attention computation by an order of magnitude compared to previous state-of-the-art methods.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义
- **核心挑战**：在图像分析中，小目标（如肺结节、肿瘤病变）通常仅占图像的0.1%以下，传统Transformer架构因对无关区域进行大量冗余注意力计算而导致效率低下且性能退化。
- **现有方法的局限**：已有的稀疏注意力机制依赖刚性的层次化结构，难以应对小目标位置高度可变且不确定的特点。
- **论文目标**：提出BoltzFormer，一种基于Transformer的新型架构，通过**动态稀疏注意力**自适应地聚焦于相关区域，在提升小目标分割精度的同时显著降低计算量，实现文本提示下的端到端检测与分割。

### 2. 方法论
- **整体思路**：将Transformer解码器中的注意力计算限制在由**玻尔兹曼分布**动态采样得到的稀疏区域上，并通过**温度退火调度**平衡探索与利用。
- **玻尔兹曼注意力采样模块**：
  - **步骤1 - 构建玻尔兹曼分布**：给定当前层的潜在查询向量 `q`，通过MLP变换与语义特征图计算像素置信度 `Uxy`，然后以温度 `τ_ℓ` 构建玻尔兹曼分布：  
    \( p_{xy}(q) \propto \exp(U_{xy}(\text{MLP}(q)) / \tau_\ell) \)。
  - **温度退火**：`τ_ℓ = τ_0 / (1 + ℓ)`，层数 `ℓ` 增加时温度下降，使早期层采样范围广（探索），后期层聚焦于高置信度区域（利用）。
  - **步骤2 - 随机注意力采样**：从该分布中采样 `N` 个图像补丁（允许重复），得到注意力区域 `A`；查询向量仅对该区域内的视觉特征执行多头交叉注意力，更新自身。
  - **步骤3 - 查询间自注意力**：所有查询与文本嵌入一起通过自注意力层进行信息交互，并传递至下一层。
- **多查询集成与PiGMA聚合**：
  - 维持 `m` 个潜在查询向量，每个最终生成一个候选掩膜预测。
  - **PiGMA模块**：将多个预测平均后，与一个轻量级卷积网络（以原始图像像素为条件）输出的高分辨率校正结果取平均，经sigmoid得到最终概率掩膜。
- **文本条件先验**：初始查询通过自注意力与文本嵌入融合，获得语义先验。

### 3. 实验设计
- **数据集**：来自Medical Segmentation Decathlon (MSD)、LIDC-IDRI、AMOS22的7个公开医学分割数据集，使用GPT-4增强的文本提示（如“腹部MRI中的右肾”）。目标大小覆盖0.002%至20%以上图像面积。
- **基准对比方法**：
  - 分割基础模型解码器：SAM、SAM 2、SEEM（均定制为文本输入，搭配Hiera-S/BP主干）。
  - 预训练生物医学基础模型：BiomedParse。
  - 专家模型：nnU-Net（为每个数据集的每类目标单独训练一个二分类模型，共35个模型）。
- **评估指标**：Dice分数。

### 4. 资源与算力
- 论文未明确提供训练所用的GPU型号、数量或训练时长等算力信息。文中仅提到使用Hiera-S、Hiera-BP和Focal-L等主干网络进行实验，未涉及具体硬件配置或训练成本。

### 5. 实验数量与充分性
- **对比实验**：在7个数据集上与3类基线（共约10种配置）进行综合比较，并针对小目标（<1%面积）和大目标（≥1%面积）进行分层分析。
- **消融实验**：围绕6个关键设计要素开展消融研究：
  - 注意力机制类型（全注意力vs. 固定阈值掩膜 vs. 玻尔兹曼采样）
  - 基础温度 `τ_0`
  - 采样大小（占视觉特征比例）
  - 查询数量 `m`
  - 文本条件先验的有无
  - PiGMA模块的像素级校正效果
- **实验设计评价**：实验覆盖了多种架构、多尺度对象和多维消融，比较对象包括专门训练的专家模型和通用基础模型，设置较为公平、充分；针对小目标的专门分析凸显了方法的针对性优势。

### 6. 主要结论与发现
- **性能大幅领先**：BoltzFormer在所有数据集上的平均Dice分数显著优于SAM、SAM 2、SEEM等基础模型解码器（平均提升2.1~12.6个百分点），也优于BiomedParse和为每类单独训练的nnU-Net。
- **小目标优势突出**：在小目标（面积<1%）上的Dice达到71.4%，比SEEM（68.9%）有明显提升；而在大目标上优势微小，说明性能增益主要来自小目标的改进。
- **计算效率提升**：注意力计算量较先前最优方法降低约一个数量级（采样仅需5%~10%的视觉特征即可获得最优性能）。
- **采样行为可视化**：展示了从早期广泛探索到后期聚焦目标区域的动态过程，验证了退火策略的有效性。

### 7. 优点
- **新颖的动态稀疏注意力**：将玻尔兹曼分布与温度退火结合，首次在Transformer中实现基于概率采样的探索-利用平衡，创新性地解决了小目标的定位不确定性问题。
- **模块化且易于集成**：玻尔兹曼注意力采样作为即插即用模块，可无缝融入现有Transformer解码器架构。
- **多查询与PiGMA聚合**：通过多查询集成和像素级校正，有效降低了随机采样的方差，提升了最终预测的稳定性。
- **系统性实验验证**：在医学影像小目标分割这一挑战性任务上，设计了全面的对比与消融实验，证明了方法的有效性和各组件的贡献。

### 8. 不足与局限
- **实验领域单一**：仅在医学图像（CT/MRI）数据集上进行评估，其在自然图像或更通用场景下的泛化性尚未验证。
- **依赖文本提示**：模型需要用户提供物体描述文本，端到端流程完全依赖语言编码器的性能，对描述模糊或开放词汇场景的鲁棒性未知。
- **失败案例分析**：论文提及了1.4%的完全漏检率，主要是极微小目标、低对比度或存在其他干扰物体的情况，说明方法仍有提升空间。
- **算力消耗未披露**：未给出训练所需的GPU资源、时间等信息，难以评估其实际部署的硬件门槛和训练成本。
- **与专家模型比较的公平性**：虽然BoltzFormer以统一文本驱动模型超越了为每个任务单独训练的nnU-Net，但文本提示本身可能引入了额外的语义信息，严格对比时需考虑信息量的差异。

（完）
