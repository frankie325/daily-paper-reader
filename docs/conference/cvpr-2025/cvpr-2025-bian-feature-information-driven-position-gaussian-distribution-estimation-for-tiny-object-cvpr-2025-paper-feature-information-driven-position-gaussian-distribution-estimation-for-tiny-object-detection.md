---
title: Feature Information Driven Position Gaussian Distribution Estimation for Tiny Object Detection
title_zh: 特征信息驱动的位置高斯分布估计用于微小目标检测
authors: "Bian, Jinghao, Feng, Mingtao, Dong, Weisheng, Wu, Fangfang, Luo, Jianqiao, Wang, Yaonan, Shi, Guangming"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Bian_Feature_Information_Driven_Position_Gaussian_Distribution_Estimation_for_Tiny_Object_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 9.0
evidence: 通过像素信息熵增强的微小目标检测
tldr: 针对微小目标因像素极少导致表示弱、检测性能骤降的问题，本文提出一种即插即用的增强架构，首次从像素信息量视角出发，通过最小化信息熵损失生成信息图突出弱激活区域，并辅助高斯分布估计，有效提升了微小目标的检测精度。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-bian-feature-information-driven-position-gaussian-distribution-estimation-for-tiny-object-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 862, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-bian-feature-information-driven-position-gaussian-distribution-estimation-for-tiny-object-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1801, \"height\": 534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-bian-feature-information-driven-position-gaussian-distribution-estimation-for-tiny-object-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 845, \"height\": 578, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-bian-feature-information-driven-position-gaussian-distribution-estimation-for-tiny-object-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1812, \"height\": 250, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-bian-feature-information-driven-position-gaussian-distribution-estimation-for-tiny-object-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 870, \"height\": 317, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-bian-feature-information-driven-position-gaussian-distribution-estimation-for-tiny-object-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1810, \"height\": 561, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-bian-feature-information-driven-position-gaussian-distribution-estimation-for-tiny-object-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 623, \"height\": 340, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-bian-feature-information-driven-position-gaussian-distribution-estimation-for-tiny-object-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1566, \"height\": 565, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-bian-feature-information-driven-position-gaussian-distribution-estimation-for-tiny-object-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 920, \"height\": 509, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-bian-feature-information-driven-position-gaussian-distribution-estimation-for-tiny-object-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 915, \"height\": 446, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-bian-feature-information-driven-position-gaussian-distribution-estimation-for-tiny-object-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 694, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-bian-feature-information-driven-position-gaussian-distribution-estimation-for-tiny-object-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1129, \"height\": 220, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-bian-feature-information-driven-position-gaussian-distribution-estimation-for-tiny-object-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 597, \"height\": 191, \"label\": \"Table\"}]"
motivation: 微小目标像素表示弱，导致通用检测器性能大幅下降。
method: 提出基于信息熵损失的无监督信息图增强弱区域。
result: 在微小目标检测基准上性能显著提升。
conclusion: 像素信息驱动增强有效改善微小目标检测困境。
---

## Abstract
Tiny object detection remains challenging in spite of the success of generic detectors. The dramatic performance degradation of generic detectors on tiny objects is mainly due to the the weak representations of extremely limited pixels. To address this issue, we propose a plug-and-play architecture to enhance the extinguished regions. We for the first time exploit the regions to be enhanced from the perspective of pixel-wise amount of information. Specifically, we model the entire image pixels feature information by minimizing Information Entropy loss, generating an information map to attentively highlight weak activated regions in an unsupervised way. To effectively assist the above phase with more attention to tiny objects, we next introduce the Position Gaussian Distribution Map, explicitly modeled using a Gaussian Mixture distribution, where each Gaussian component's parameters depend on the position and size of object instance labels, serving as supervision for further feature enhancement. Taking the information map as prior knowledge guidance, we construct a multi-scale position gaussian distribution map prediction module, simultaneously modulating the information map and distribution map to focus on tiny objects during training. Extensive experiments on three public tiny object datasets demonstrate the superiority of our method over current state-of-the-art competitors.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：微小目标检测（物体仅占 2–32 个像素）时，通用检测器的性能急剧下降。主要原因是极少的像素导致特征图经过多次下采样后，微小目标的表示变得极弱、与背景难以区分，即使使用尺度感知融合或注意力机制，也未能从根本上解决“信息丢失区域”的弱表示问题。
- **整体含义**：本文首次从像素级**信息量**的视角出发，提出一种即插即用的特征增强架构，旨在自适应地识别并增强那些因信息丢失而弱激活的区域，从而显著提升微小目标检测的判别力。

### 2. 论文提出的方法论
- **核心思想**：利用信息熵理论无监督地生成一幅“信息图”，突出含信息量高的显著区域（包括微小目标）；同时，引入标签信息构建“位置高斯分布图”，对微小目标施加更强的响应，两幅图共同指导特征增强。
- **关键技术细节**：
    - **像素特征信息建模（PFIM）**：
        1. 对特征图 \(P_2\) 量化（加均匀噪声），假设每个像素独立服从高斯分布，用一个轻量 CNN 预测均值 \(\mu\) 和标准差 \(\sigma\)。
        2. 计算每个位置的编码成本 \(R_{\hat{y}_i} = -\log_2 p_{\hat{y}_i}(\hat{y}_i|\mu_i,\sigma_i)\)，将信息熵损失 \(\mathcal{L}_{IE}\) 定义为所有位置编码成本之和。
        3. 最小化 \(\mathcal{L}_{IE}\) 会迫使网络对目标区域（出现概率低、信息量大）分配更大的 \(\sigma\)，对平滑背景分配更小的 \(\sigma\)，因此**尺度图 \(\sigma\)（信息图）**自然高亮需要增强的显著区域。
        4. 增强特征：\(y_1 = y \otimes (1 + \bar{\sigma})\)，其中 \(\bar{\sigma}\) 为通道平均后的图。
    - **位置高斯分布图预测（PGDP）**：
        1. **生成真值分布图**：用高斯混合分布建模特征图，每个物体对应一个二维高斯，均值取边界框中心，协方差矩阵与物体面积相关的缩放因子（2–8 像素用 4，8–16 用 6，16–32 用 8，更大用 10）调整，使微小物体获得更高峰值；再经阈值后处理增强前景背景对比。
        2. **多尺度预测**：将信息图 \(\sigma\) 下采样后分别注入 \(P_2, P_3, P_4\)，通过卷积+转置卷积网络预测三个尺度的分布图 \(M_2^{pd}, M_3^{pd}, M_4^{pd}\)，并用加权 MSE 损失（正样本权重 10）进行深层监督。
        3. 增强特征：\(y_2 = y \otimes (1 + M_2^{pd})\)。
    - **融合与总损失**：\(y_1\) 和 \(y_2\) 各自经过 CBAM 注意力模块后逐元素相加，得到增强后的 \(P_2'\)，送入检测头。总损失 \(\mathcal{L} = \mathcal{L}_{det} + \lambda_1 \mathcal{L}_{IE} + \lambda_2 \mathcal{L}_{pred}\)。

### 3. 实验设计
- **数据集 / 场景**：VisDrone2019（无人机城市监控）、AI‑TOD（航拍图像，平均目标大小 12.8 像素）、AI‑TODv2（难度更高的微小目标数据集）。
- **评价指标**：AP、AP₅₀、AP₇₅，以及按像素数划分的 AP_vt（very tiny）、AP_t（tiny）、AP_s（small）。
- **对比方法**：Faster R‑CNN、Cascade R‑CNN、DetectoRS 等基线，以及 NWD‑RKA、RFLA、CEASC、PKS R‑CNN、Salience DETR、SR‑TOD 等当前最优的微小目标检测方法。实验证明所提插件方法在多个基线及 RFLA 上均带来稳定提升，其中 Faster R‑CNN 在 VisDrone 上的 AP_t 提升 5.8 点，在 AI‑TOD 上 DetectoRS+本方法取得整体最优。

### 4. 资源与算力
- **硬件**：所有实验在一张 **NVIDIA RTX 4090** GPU 上进行。
- **训练配置**：采用 SGD 优化器（动量 0.9，权重衰减 0.0001），batch size = 2，共训练 12 个 epoch，初始学习率 0.005 并在第 8、11 个 epoch 衰减。**未给出具体的单次或总训练时长**；由于 batch size 小且模型即插即用，推断计算开销不大。
- **代码框架**：基于 MMDetection 实现，骨干网络为 ImageNet 预训练的 ResNet‑50‑FPN。

### 5. 实验数量与充分性
- **实验组数**：
    - 三个数据集（VisDrone2019、AI‑TOD、AI‑TODv2）上的全面对比实验（约 8‑10 种对比方法）。
    - 消融实验：验证 PFIM、PGDP 两个模块的有效性；对比不同的分布建模方式（固定 α、二值掩膜、自注意力生成权重图）；不同信息图引导方式（相乘、相加、拼接）；不同增强特征融合策略（乘、拼接、相加）。
    - 定性分析：信息图、预测分布图、增强特征图、最终检测结果的可视化；比特每像素（bpp）与场景密集程度的统计关系；归一化特征图分析。
- **充分性**：实验覆盖了多个公开基准、多种基线架构，消融实验涵盖了建模方式、先验利用、融合策略等关键设计，定性分析充分解释了模块行为，整体实验设计较为充分、客观、公平。

### 6. 论文的主要结论与发现
- 从**像素信息量**角度增强信息缺失区域，能有效弥补微小目标因下采样导致的表示退化。
- 无监督生成的**信息图**能够准确捕捉目标空间结构，与有监督的**位置高斯分布图**形成互补，二者联合调制使特征对微小目标的关注显著提升。
- 该方法**即插即用**，可灵活集成到任何具有 FPN 结构的检测器中，且在不显著增加计算开销的前提下，在多个渺小目标数据集上取得新的最优性能。

### 7. 优点
- **创新视角**：首次将信息熵理论引入极小目标检测，用无监督方式定位需要增强的弱激活区域，理论动机清晰。
- **灵巧高效**：信息图仅由轻量密度估计模块生成，分布图预测复用多尺度特征，整体实现简单，具备插件特性。
- **互补设计**：信息图提供数据驱动的显著区域高亮，分布图利用标签将微小目标“凸显”，两者相互引导、相互促进。
- **实验扎实**：在三个主流微小目标数据集上与多种 anchor‑based、anchor‑free、注意力、模仿学习等方法对比，消融和分析完整，可视化直观。
- **统一损失**：将检测损失、信息熵损失及分布预测损失联合优化，端到端训练。

### 8. 不足与局限
- **真值分布图依赖标签**：位置高斯分布图需要实例级标注进行监督，在弱监督或无监督场景下无法使用。
- **尺度扩展有限**：增强仅作用于 P₂ 层（检测极小目标的主层），对于需要更高层特征处理的中等尺度或更大目标，帮助可能不明显。
- **计算与内存开销**：虽然实现了即插即用，但增加了密度估计分支、多尺度预测网络以及 CBAM，作者未详细对比推理时间的增加量。
- **背景干扰**：信息图在高度杂乱背景中可能会错误高亮非目标纹理，尽管分布图起到了纠正作用，极端场景下仍存在风险。
- **与其他先进方法的融合验证不足**：虽然已与 Salience DETR 等 Transformer 方法对比，但未与更多基于 DETR 的微小目标检测专门设计（如 QueryDet 等）直接对比，通用性验证略受限。
- **仅限像素量级定义**：微小目标的定义基于像素计数，在分辨率可变或不同摄影距离的场景下泛化性未论证。

（完）
