---
title: "SEEN-DA: SEmantic ENtropy guided Domain-aware Attention for Domain Adaptive Object Detection"
title_zh: SEEN-DA：语义熵引导的域感知注意力用于域自适应目标检测
authors: "Li, Haochen, Zhang, Rui, Yao, Hantao, Zhang, Xin, Hao, Yifan, Song, Xinkai, Peng, Shaohui, Zhao, Yongwei, Zhao, Chen, Wu, Yanjun, Li, Ling"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Li_SEEN-DA_SEmantic_ENtropy_guided_Domain-aware_Attention_for_Domain_Adaptive_Object_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 8.0
evidence: 使用语义熵进行域自适应目标检测
tldr: 针对域自适应目标检测中语义信息未充分利用的问题，提出语义熵引导的域感知注意力（SEEN-DA），通过量化视觉特征中的语义信息并引导注意力学习，提升跨域检测性能，为无监督域适应提供新思路。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-seen-da-semantic-entropy-guided-domain-aware-attention-for-domain-adaptive-object-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1796, \"height\": 561, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-seen-da-semantic-entropy-guided-domain-aware-attention-for-domain-adaptive-object-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1765, \"height\": 486, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-seen-da-semantic-entropy-guided-domain-aware-attention-for-domain-adaptive-object-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1721, \"height\": 633, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-seen-da-semantic-entropy-guided-domain-aware-attention-for-domain-adaptive-object-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 678, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-seen-da-semantic-entropy-guided-domain-aware-attention-for-domain-adaptive-object-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 687, \"height\": 463, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-seen-da-semantic-entropy-guided-domain-aware-attention-for-domain-adaptive-object-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1620, \"height\": 790, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-seen-da-semantic-entropy-guided-domain-aware-attention-for-domain-adaptive-object-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1796, \"height\": 566, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-seen-da-semantic-entropy-guided-domain-aware-attention-for-domain-adaptive-object-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 868, \"height\": 228, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-seen-da-semantic-entropy-guided-domain-aware-attention-for-domain-adaptive-object-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 862, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-seen-da-semantic-entropy-guided-domain-aware-attention-for-domain-adaptive-object-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 866, \"height\": 275, \"label\": \"Table\"}]"
motivation: 现有方法忽视语义信息在引导视觉特征学习适应中的作用。
method: 设计语义熵量化视觉特征语义，并构建域感知注意力自适应优化特征。
result: 在多个域适应目标检测任务上取得优于现有方法的性能。
conclusion: SEEN-DA有效利用语义信息，增强跨域检测的鲁棒性。
---

## Abstract
Domain adaptive object detection (DAOD) aims to generalize detectors trained on an annotated source domain to an unlabelled target domain. Traditional works focus on aligning visual features between domains to extract domain-invariant knowledge, and recent VLM-based DAOD methods leverage semantic information provided by the textual encoder to supplement domain-specific features for each domain.However, they overlook the role of semantic information in guiding the learning of visual features that are beneficial for adaptation.To solve the problem, we propose semantic entropy to quantify the semantic information contained in visual features, and design SEmantic ENtropy guided Domain-aware Attention (SEEN-DA) to adaptively refine visual features with the semantic information of two domains.Semantic entropy reflects the importance of features based on semantic information, which can serve as attention to select discriminative visual features and suppress semantically irrelevant redundant information.Guided by semantic entropy, we introduce domain-aware attention modules into the visual encoder in SEEN-DA.It utilizes an inter-domain attention branch to extract domain-invariant features and eliminate redundant information, and an intra-domain attention branch to supplement the domain-specific semantic information discriminative on each domain.Comprehensive experiments validate the effectiveness of SEEN-DA, demonstrating significant improvements in cross-domain object detection performance.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体意义（研究动机和背景）

*   **核心问题**：当前的域自适应目标检测（DAOD）方法，无论是基于传统特征对齐还是基于视觉语言模型（VLM），都忽略了**语义信息在指导视觉特征学习适应过程中的潜在作用**。传统方法使用语义无关的类别标签（如 one-hot 编码）优化视觉编码器，可能导致：
    *   无法过滤掉与类别语义无关的冗余信息（如颜色、纹理），这些冗余特征虽然两域共有，却会干扰域不变特征的对齐，造成错误迁移。
    *   丢弃了域特有的视觉特征，而这些特征中蕴含着丰富的域特定语义信息，对目标域的判别力至关重要。
*   **整体意义**：论文提出**语义熵（Semantic Entropy）** 这一新概念，用于量化视觉特征中包含的语义信息量，并将其作为注意力信号，引导视觉编码器自适应地筛选有利于适应的视觉特征，同时抑制语义无关的冗余，从而有效提升跨域目标检测性能。

## 2. 论文提出的方法论

*   **核心思想**：利用 VLM（如 CLIP）的文本编码器生成的文本嵌入所蕴含的丰富语义信息，为视觉特征定义“语义熵”，并以该熵值作为注意力权重，自适应地调整视觉特征在不同域上的重要性。
*   **关键技术细节与流程**：
    *   **语义熵定义**：对于视觉特征 \( f \)，通过与文本嵌入 \( T \) 的点积相似度计算其属于各个类别的概率 \( p(t_c, f) \)，进而定义信息熵：
        \[
        SE(T, f) = -\sum_c p(t_c, f) \log p(t_c, f)
        \]
        为了将其转化为注意力图，作者进一步设计了语义熵引导的注意力函数：
        \[
        SEAttention(T, f) = \sum_c p(t_c, f) \log p(t_c, f) + \log K
        \]
        该函数对低熵（语义明确）的特征给予高权重，对高熵（语义不确定/冗余）的特征给予低权重。
    *   **SEEN-DA 框架**：在冻结的视觉编码器（RegionCLIP）的多个视觉块后接入轻量级、可学习的**域感知注意力模块**。
    *   **域感知注意力模块结构**（每个模块包含两个平行分支）：
        *   **域间注意力分支**：
            1. 使用域共享的卷积层处理特征 \( f_d \)。
            2. 将特征投影到文本空间，利用域无关的文本嵌入（如 “A photo of [Class]”）计算语义熵注意力图 \( w \)。
            3. 用 \( w \) 加权特征并残差连接，输出域不变特征 \( f‘ \)，并通过域判别器进行对抗训练以对齐分布。
        *   **域内注意力分支**：
            1. 使用域共享的卷积层再次处理特征。
            2. 分别使用源域特异的可学习 prompt（如 “[vc][vs][Class]”）和目标域特异的 prompt 生成各自的文本嵌入，并利用各自独立的投影层和 SEEN 模块计算源域注意力图 \( w_s \) 和目标域注意力图 \( w_t \)。
            3. 将域内注意力图与域间分支输出的 \( f’ \) 进行融合（\( f’_s = f‘ + w_s \cdot f^c_s \)），从而为每个域补充独特的语义信息。
    *   **优化目标**：总损失 = 源域有监督分类损失 + 目标域伪标签分类损失 + 域间特征的对抗损失 + 回归损失。

## 3. 实验设计

*   **数据集与场景**：
    *   **跨天气适配**：Cityscapes (源) → Foggy Cityscapes (目标)。
    *   **跨视场角（FoV）适配**：KITTI (源) → Cityscapes (目标，仅“轿车”类别)。
    *   **仿真到真实适配**：SIM10K (源) → Cityscapes (目标，仅“轿车”类别)。
    *   **跨风格适配**：Pascal VOC (源) → Clipart (目标)。
*   **评估基准**：以 Mean Average Precision (mAP) @ IoU=0.5 作为主要指标，并与该领域当前最优方法（SOTA）进行对比。
*   **对比方法**：包含了三大类主流 DAOD 方法，共计 20 余种，包括：
    *   特征对齐类：DA-Faster, SCSAN, TIA, SIGMA++ 等。
    *   半监督/伪标签类：MTM, AT, SOCCER 等。
    *   VLM 类：DA-Pro, RegionCLIP 等。

## 4. 资源与算力

*   文中明确说明“**所有实验部署在 8 块 Tesla V100 GPU 上**”，但未提及单次训练的时长或总算力消耗。
*   检测器基于 Faster-RCNN、骨干网络为 RegionCLIP (ResNet-50)，每次迭代输入源域和目标域各 8 张图像。

## 5. 实验数量与充分性

*   **实验数量**：论文进行了多维度的实验验证，约合 10 组以上主要实验/消融：
    *   **主结果对比**：在 4 个域适配场景下与大量 SOTA 方法比较（见 3 个大型表格）。
    *   **消融实验**：
        *   标准注意力（自注意力、交叉注意力）与域感知注意力的对比。
        *   域感知注意力模块内部组件（域间分支、域内分支、对抗损失）的有效性分解。
        *   计算效率（参数量与性能对比）。
        *   注意力模块数量对性能的影响。
        *   SEEN 模块中投影方向（V2T, T2V 等）的消融。
    *   **定性分析**：提供了检测结果和注意力图的可视化对比。
*   **充分性与公平性**：实验设计较为全面和严谨。对比方法覆盖了近年顶会/顶刊工作，消融实验清晰地论证了各模块的贡献，确保了评估的客观与公平。

## 6. 论文的主要结论与发现

1.  提出的**语义熵**能够有效量化视觉特征中的语义信息，高熵对应冗余、低熵对应有助于迁移的前景特征。
2.  基于语义熵构建的**域感知注意力模块**，通过域间分支提取干净域不变特征，通过域内分支补充域特有语义，显著提升了域自适应目标检测的性能。
3.  该方法在多个跨域检测基准上均取得了**当前最佳性能（SOTA）**，例如在 Cityscapes → Foggy Cityscapes 上达到 57.5% mAP，超越此前的 VLM 方法 DA-Pro 1.6 个百分点。
4.  该方法具有较高的**参数效率**，仅需训练极少量的参数（1.875M）即可获得显著性能提升。

## 7. 优点

*   **创新性**：首次将视觉特征的语义不确定性建模为“语义熵”，并创新性地将其用作视觉编码器内部的注意力向导，为利用 VLM 优化视觉特征给出了一条新路径。
*   **方法设计精巧**：域间/域内双分支结构清晰地解耦了域不变学习与域特定特征补充两个子任务，逻辑严谨。
*   **性能突出且轻量**：在多个标准且具有挑战性的基准上大幅刷新 SOTA，同时保持了很高的参数效率。
*   **可解释性强**：通过可视化注意力图，直观展示了模型如何聚焦于语义丰富的前景区域，抑制背景干扰。

## 8. 不足与局限

*   **VLM 依赖与域偏差**：方法性能高度依赖于预训练 VLM（如 CLIP）的文本编码器的质量及其对目标域语义的覆盖能力。对于 CLIP 未见过的、语义差异极大的域，其文本嵌入可能无法提供有效的引导。
*   **目标域伪标签依赖**：训练需使用目标域的伪标签，伪标签的质量不可避免地会影响模型在目标域上的监督效果，论文未深入讨论该因素的敏感性。
*   **框架通用性验证有限**：实验仅在基于 RegionCLIP + Faster-RCNN 的一类两阶段检测器上验证，未展示该方法对单阶段检测器或检测 Transformer（DETR-like）等其他检测框架的通用性。
*   **算力开销未详述**：虽参数量少，但训练过程中需前向文本编码器生成域相关嵌入，且部署于 8 卡 V100，实际训练时间成本未明确，可能比纯视觉方法高。

（完）
