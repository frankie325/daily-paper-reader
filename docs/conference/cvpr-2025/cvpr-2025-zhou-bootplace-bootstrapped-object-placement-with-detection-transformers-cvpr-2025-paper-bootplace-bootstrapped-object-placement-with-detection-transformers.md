---
title: "BOOTPLACE: Bootstrapped Object Placement with Detection Transformers"
title_zh: BOOTPLACE：基于检测Transformer的引导式物体放置
authors: "Zhou, Hang, Zuo, Xinxin, Ma, Rui, Cheng, Li"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Zhou_BOOTPLACE_Bootstrapped_Object_Placement_with_Detection_Transformers_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 6.0
evidence: 使用检测Transformer进行物体放置
tldr: 针对物体放置学习中生成模型能力受限和稀疏对比损失导致放置不精确的问题，提出BOOTPLACE，将物体放置转化为检测问题，训练专用检测Transformer定位合适区域，实现更精确的图像合成。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhou-bootplace-bootstrapped-object-placement-with-detection-transformers-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 866, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhou-bootplace-bootstrapped-object-placement-with-detection-transformers-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1760, \"height\": 665, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhou-bootplace-bootstrapped-object-placement-with-detection-transformers-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1797, \"height\": 689, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhou-bootplace-bootstrapped-object-placement-with-detection-transformers-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1813, \"height\": 712, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhou-bootplace-bootstrapped-object-placement-with-detection-transformers-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1799, \"height\": 890, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhou-bootplace-bootstrapped-object-placement-with-detection-transformers-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1802, \"height\": 620, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhou-bootplace-bootstrapped-object-placement-with-detection-transformers-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1811, \"height\": 619, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhou-bootplace-bootstrapped-object-placement-with-detection-transformers-cvpr-2025-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1807, \"height\": 579, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhou-bootplace-bootstrapped-object-placement-with-detection-transformers-cvpr-2025-paper/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 482, \"height\": 273, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhou-bootplace-bootstrapped-object-placement-with-detection-transformers-cvpr-2025-paper/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 865, \"height\": 325, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhou-bootplace-bootstrapped-object-placement-with-detection-transformers-cvpr-2025-paper/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 865, \"height\": 258, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhou-bootplace-bootstrapped-object-placement-with-detection-transformers-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1791, \"height\": 260, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhou-bootplace-bootstrapped-object-placement-with-detection-transformers-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 863, \"height\": 227, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhou-bootplace-bootstrapped-object-placement-with-detection-transformers-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 863, \"height\": 165, \"label\": \"Table\"}]"
motivation: 现有物体放置方法依赖生成模型或稀疏对比损失，导致放置位置不精确。
method: 将物体放置形式化为放置即检测，训练检测Transformer识别插入区域。
result: 物体放置精度显著提高，合成图像更自然。
conclusion: 检测框架为物体放置提供了一种新颖有效的解决方案。
---

## Abstract
In this paper, we tackle the copy-paste image-to-image composition problem with a focus on object placement learning. Prior methods have leveraged generative models to reduce the reliance for dense supervision. However, this often limits their capacity to model complex data distributions. Alternatively, transformer networks with a sparse contrastive loss have been explored, but their over-relaxed regularization often leads to imprecise object placement. We introduce BOOTPLACE, a novel paradigm that formulates object placement as a placement-by-detection problem. Our approach begins by identifying suitable regions of interest for object placement. This is achieved by training a specialized detection transformer on object-subtracted backgrounds, enhanced with multi-object supervisions. It then semantically associates each target compositing object with detected regions based on their complementary characteristics. Through a boostrapped training approach applied to randomly object-subtracted images, our model enforces meaningful placements through extensive paired data augmentation. Experimental results on established benchmarks demonstrate BOOTPLACE's superior performance in object repositioning, markedly surpassing state-of-the-art baselines on Cityscapes and OPA datasets with notable improvements in IOU scores. Additional ablation studies further showcase the compositionality and generalizability of our approach, supported by user study evaluations. Code is available at https://github.com/RyanHangZhou/BOOTPLACE

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

本论文聚焦于**图像间的复制-粘贴合成任务中的物体放置学习问题**。背景是，现有的物体放置方法主要分为两类：

- **基于生成模型的方法**：通过生成模型（如GAN）避免对密集监督的依赖，但往往难以建模复杂的数据分布，限制了放置的精度和泛化性。
- **基于Transformer的回归方法**：使用稀疏对比损失学习物体与背景的关联，但其正则化过程过于松弛，容易导致放置位置不精确。

此外，部分方法需要人工标注正负复合样本，成本高且不可扩展。因此，论文的核心动机是：**如何在缺乏密集位置监督的条件下，实现精确、多样且符合场景语义的物体放置**。论文提出将物体放置重新形式化为一个“放置即检测”（placement-by-detection）问题，旨在利用检测网络的强定位能力来提升放置准确性。

## 2. 论文提出的方法论：核心思想、关键技术细节

BOOTPLACE 的核心思想是**先检测图像中适合放置物体的“兴趣区域”（region of interest，RoI），再将目标物体与检测到的区域进行匹配**。整个框架由两个模块组成：

1. **兴趣区域检测网络**：基于检测Transformer，在“物体被移除后的背景图像”上训练，使其学会定位可能容纳物体的关键区域。同时，为避免将新物体放置在已有物体之上，网络会显式编码场景中已存在物体的位置信息，引导检测过程。

2. **物体到区域的关联网络**：将检测到的候选区域特征与待放置物体查询（object queries）进行关联。不同于简单的点积相似度，**该关联采用负相关（语义互补）机制**，即避免将物体放置在与背景物体特征相似的区域，而是寻找结构与语义上互补的位置。关联分数通过softmax转换为概率分布，训练时最大化真实物体-区域配对的对数似然。

**关键技术细节**：
- **图像分解与数据增强**：使用实例分割和图像修复技术，将原始图像分解为“物体移除后的背景”和“完整物体块”，并随机选择部分物体重新合成背景，生成大量的“随机物体移除图像”以扩充训练数据（Bootstrapped训练策略）。
- **关联损失**：定义了一种可微的关联代价函数，结合分类概率和边界框回归损失，通过匈牙利算法求解最优匹配，进而同时训练检测器和关联网络。
- **公式化流程**（文字描述）：
  - 检测网络输出N个兴趣区域，每个区域包含位置bi和分类分数si。
  - 物体查询qk与区域特征fi计算负余弦相似度gi = -qk·fi/μ，经softmax得到关联概率PΛ(α=i|F)。
  - 训练目标是最小化检测损失（分类+L1+GIoU）和关联损失（负对数似然）之和。

## 3. 实验设计：数据集/场景、基准方法和评估指标

**数据集**：
- **Cityscapes**：城市街景语义分割数据集。通过panoptic分割提取物体实例，并利用LaMa修复模型移除物体及其阴影，构建了包含2,953张训练图像（22,270个物体）和372张测试图像（2,713个物体）的多物体放置数据集。
- **OPA**：基于COCO的人工标注物体放置数据集，仅使用正样本，从62,074训练/11,396测试中筛选出21,350训练和3,566测试对。

**对比方法**：
- PlaceNet (ECCV 2020)
- GracoNet (ECCV 2022) （仅在OPA上评估）
- SAC-GAN (IEEE TVCG 2022)
- TopNet (CVPR 2023)

**评估指标**：
- 物体重定位（同一图像内物体放回原位）：Top-1和Top-5的IoU以及IoU50（%）。
- 物体放置（跨图合成）：用户主观合理性评分（20人参与）、放置多样性（边界框尺度与中心的方差），以及在Mapillary Vistas上的跨域泛化实验。

## 4. 资源与算力

文中明确提到，训练BOOTPLACE时：
- **硬件**：单块NVIDIA TITAN RTX GPU。
- **训练时长**：在Cityscapes数据集上约需12小时，在OPA数据集上约需8小时。
- **优化器**：AdamW，初始学习率0.0004（骨干网络0.00005），权重衰减0.0001。

## 5. 实验数量与充分性

论文进行的实验组数较多，设计全面且充分，主要包括：
- **两个标准数据集**（Cityscapes和OPA）上的物体**重定位**定量对比。
- **Cityscapes上的物体放置**（跨图合成）定性及定量对比，包括泛化到Mapillary Vistas的测试。
- **消融实验**：针对高斯平滑、数据增强、关联方式（正/负相关性）、单/多物体监督、位置编码器（location encoder）的五个变体进行对比。
- **用户调研**：20人对合成图像真实度的主观评价。
- **可视化分析**：解码器注意力可视化、边界框分布图等。

实验对比方法涵盖了该领域从2020年至2023年的多个代表性工作，评估指标客观（IoU）和主观（用户调研）结合，且消融实验验证了各模块的作用，实验设计公平、充分。

## 6. 论文的主要结论与发现

- BOOTPLACE 通过“放置即检测”范式，在物体重定位和跨图放置任务上均显著优于现有方法，尤其在Cityscapes上的Top-5 IoU提升了约4个百分点。
- 多物体监督、位置编码器、负相关关联机制和bootstrapped数据增强对性能提升至关重要。
- 模型能够学习到类别相关的检测注意力模式（如车在路边、行人在人行道），实现了语义合理的放置。
- 定性结果显示，所生成合成图像的物体尺度和位置更加合理，避免了对象的碰撞或不适当的遮挡。

## 7. 优点：方法或实验设计上的亮点

- **新颖的范式转换**：将开放式的回归问题转化为“检测+关联”的结构化预测问题，利用检测Transformer的精确定位能力，本质上提供了更强的监督和约束。
- **无需人工标注负样本**：通过图像分解和bootstrapped训练自动生成大量训练对，减少了标注成本且提升了数据多样性。
- **语义互补的关联机制**：采用负相关score，使模型学会避让背景中已存在的物体，而非简单匹配，更符合组合规律。
- **多物体监督与位置编码**：可以同时处理多个物体的放置，并通过注入场景物体位置信息避免碰撞，增强实用性。
- **实验扎实**：在两个数据集、多个指标上进行了详尽的定量和定性评估，消融实验覆盖全面，并补充了用户调研，论证充分。

## 8. 不足与局限

- **并行放置的限制**：检测头并行输出所有兴趣区域，无法处理需要序列决策的放置场景（如多个物体间存在复杂遮挡或依赖性），文中已承认此问题，并提及可能采用自回归模型改进。
- **缺少3D几何建模**：未考虑物体的透视变换和平面外旋转，合成结果在真实感上仍有不足。
- **对修复质量的依赖**：训练数据需要基于修复模型生成无物体背景，修复瑕疵可能引入偏差，尽管使用了高斯平滑缓解，但模型仍可能对修复痕迹有过拟合风险（论文报告IoU50时过拟合率低于5%）。
- **评价指标的局限性**：虽结合了用户调研，但合成图像的质量评价仍较难以完全自动化，论文指出FID/LPIPS等常用指标无法很好地反映区域边界瑕疵，因此更依赖IoU和主观评分，可复现性稍受限制。

（完）
