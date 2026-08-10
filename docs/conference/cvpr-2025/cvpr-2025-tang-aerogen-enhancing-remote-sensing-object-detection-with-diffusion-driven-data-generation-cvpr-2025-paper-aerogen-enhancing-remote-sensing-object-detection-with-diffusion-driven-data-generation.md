---
title: "AeroGen: Enhancing Remote Sensing Object Detection with Diffusion-Driven Data Generation"
title_zh: AeroGen：利用扩散驱动数据生成增强遥感目标检测
authors: "Tang, Datao, Cao, Xiangyong, Wu, Xuan, Li, Jialin, Yao, Jing, Bai, Xueru, Jiang, Dongsheng, Li, Yin, Meng, Deyu"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Tang_AeroGen_Enhancing_Remote_Sensing_Object_Detection_with_Diffusion-Driven_Data_Generation_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 9.0
evidence: 基于扩散模型的遥感目标检测数据增强
tldr: 针对遥感图像目标检测标注数据稀缺问题，本文提出布局可控的扩散生成模型AeroGen，支持水平与旋转边界框条件生成。该模型能够合成高质量训练样本，显著缓解数据不足，尤其是在稀有类别上性能提升明显。实验表明，AeroGen在多个遥感检测数据集上有效提升了检测精度，为遥感目标检测提供了新的数据增强范式。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-tang-aerogen-enhancing-remote-sensing-object-detection-with-diffusion-driven-data-generation-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1784, \"height\": 586, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-tang-aerogen-enhancing-remote-sensing-object-detection-with-diffusion-driven-data-generation-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1592, \"height\": 918, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-tang-aerogen-enhancing-remote-sensing-object-detection-with-diffusion-driven-data-generation-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1653, \"height\": 647, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-tang-aerogen-enhancing-remote-sensing-object-detection-with-diffusion-driven-data-generation-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1319, \"height\": 1028, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-tang-aerogen-enhancing-remote-sensing-object-detection-with-diffusion-driven-data-generation-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 780, \"height\": 613, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-tang-aerogen-enhancing-remote-sensing-object-detection-with-diffusion-driven-data-generation-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 873, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-tang-aerogen-enhancing-remote-sensing-object-detection-with-diffusion-driven-data-generation-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1499, \"height\": 439, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-tang-aerogen-enhancing-remote-sensing-object-detection-with-diffusion-driven-data-generation-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 557, \"height\": 275, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-tang-aerogen-enhancing-remote-sensing-object-detection-with-diffusion-driven-data-generation-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 556, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-tang-aerogen-enhancing-remote-sensing-object-detection-with-diffusion-driven-data-generation-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 804, \"height\": 128, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-tang-aerogen-enhancing-remote-sensing-object-detection-with-diffusion-driven-data-generation-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 642, \"height\": 290, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-tang-aerogen-enhancing-remote-sensing-object-detection-with-diffusion-driven-data-generation-cvpr-2025-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 727, \"height\": 326, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-tang-aerogen-enhancing-remote-sensing-object-detection-with-diffusion-driven-data-generation-cvpr-2025-paper/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 708, \"height\": 412, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-tang-aerogen-enhancing-remote-sensing-object-detection-with-diffusion-driven-data-generation-cvpr-2025-paper/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 557, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-tang-aerogen-enhancing-remote-sensing-object-detection-with-diffusion-driven-data-generation-cvpr-2025-paper/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 674, \"height\": 139, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-tang-aerogen-enhancing-remote-sensing-object-detection-with-diffusion-driven-data-generation-cvpr-2025-paper/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 609, \"height\": 194, \"label\": \"Table\"}]"
motivation: 遥感目标检测面临标注数据稀缺，现有数据增强方法受限于高质量标注数据且对稀有类别效果不佳。
method: 提出布局可控扩散模型AeroGen，根据边界框条件生成遥感检测训练样本。
result: 在典型遥感检测数据集上，使用AeroGen生成的样本训练后，检测性能特别是稀有类别显著提升。
conclusion: AeroGen能有效解决遥感目标检测的数据稀缺问题，推动数据驱动的检测算法发展。
---

## Abstract
Remote sensing image object detection (RSIOD) aims to identify and locate specific objects within satellite or aerial imagery. However, there is a scarcity of labeled data in current RSIOD datasets, which significantly limits the performance of current detection algorithms. Although existing techniques, e.g., data augmentation and semi-supervised learning, can mitigate this scarcity issue to some extent, they are heavily dependent on high-quality labeled data and perform worse in rare object classes. To address this issue, this paper proposes a layout-controllable diffusion generative model (i.e. AeroGen) tailored for RSIOD. To our knowledge, AeroGen is the first model to simultaneously support horizontal and rotated bounding box condition generation, thus enabling the generation of high-quality synthetic images that meet specific layout and object category requirements. Additionally, we propose an end-to-end data augmentation framework that integrates a diversity-conditioned generator and a filtering mechanism to enhance both the diversity and quality of generated data. Experimental results demonstrate that the synthetic data produced by our method are of high quality and diversity. Furthermore, the synthetic RSIOD data can significantly improve the detection performance of existing RSIOD models, i.e., the mAP metrics on DIOR, DIOR-R, and HRSC datasets are improved by 3.7%, 4.3%, and 2.43%, respectively.

---

## 论文详细总结（自动生成）

### 1. 论文核心问题与整体含义
遥感图像目标检测（RSIOD）旨在定位和识别卫星或航拍图像中的特定物体，在环境监测、城市规划、灾害应急等领域具有重要价值。然而，当前主流 RSIOD 数据集普遍存在标注样本稀缺的问题，严重制约了深度学习检测器的性能。传统的解决思路如数据增强（翻转、缩放、复制-粘贴）和半监督学习只能有限缓解数据不足，且极度依赖高质量的初始标注，对稀有类别的提升尤为乏力。**本研究因此提出利用扩散生成模型来直接合成带有精确布局控制的遥感检测训练样本，从根本上扩充数据集，尤其提升稀有类别的表现。**

### 2. 方法论
论文提出名为 **AeroGen** 的布局可控扩散模型，并构建了一套端到端数据增强框架，包括布局生成、条件图像生成和质量过滤三个阶段。

*   **核心生成模型 (AeroGen)**
    *   **布局嵌入 (Layout Embedding)**：将水平和旋转边界框统一表示为包含 8 个坐标的列表 \( \mathbf{x} = [x_1, y_1, \dots, x_4, y_4] \)，使用傅里叶编码将坐标映射到频域，再与冻结的 CLIP 文本编码器获得的类别编码拼接后，通过线性层得到统一的布局控制令牌 \( \mathbf{h} = \text{Linear}([\gamma(\mathbf{x}); \mathbf{c}]) \)。
    *   **布局掩码注意力 (Layout Mask Attention)**：除了传统的令牌式控制，模型在去噪过程中引入掩码注意力机制。每个边界框被转化为 0/1 掩码 \( \mathbf{M}_i \)，通过掩码加权的交叉注意力（公式 \( \mathbf{Q} = \sum_{i=1}^n \mathbf{M}_i \cdot \text{softmax}(\frac{\mathbf{Q}\mathbf{K}_i^\top}{\sqrt{d_k}} + \mathbf{M}_i)\mathbf{V}_i \)）对局部噪声进行精准调控，提升小目标区域的生成控制力。
    *   **双交叉注意力架构**：模型同时接收全局文本条件（CLIP 编码的文本描述）和布局控制令牌，输出为 \( \text{Out} = \Psi(\mathbf{Q}, \mathbf{K}_g, \mathbf{V}_g) + \lambda \cdot \Psi(\mathbf{Q}, \mathbf{K}_l, \mathbf{V}_l) \)，其中 \( \Psi \) 代表交叉注意力，\( \lambda \) 平衡全局和局部条件。训练目标为常规的扩散去噪损失 \( \mathcal{L} = \mathbb{E}[ \| \epsilon - \epsilon_\theta(\mathbf{x}_t, t, \mathbf{c}_g, \mathbf{c}_l) \|^2 ] \)。

*   **端到端数据增强流水线**
    1.  **标签生成与筛选**：使用一个基于 DDPM 的生成器学习真实标签布局的分布，采样出多样化的布局矩阵 \( \mathbf{M}_L \)。再通过基于正态分布的过滤器约束生成边界框的面积等属性，使其符合真实统计特性，并结合平移、旋转等传统增强构建布局条件池。
    2.  **图像生成**：将生成的布局条件送入 AeroGen 模型，合成对应的遥感图像。
    3.  **图像质量过滤**：生成图像需通过 **语义一致性**（用 CLIP 分数评估）和 **布局一致性**（用 ResNet101 分类器的最小准确率评估）的双重筛选，仅保留超阈值的样本。
    4.  **数据融合**：筛选后的合成图像与原始真实图像混合，共同训练下游检测器。

### 3. 实验设计
*   **数据集**：
    *   **DIOR**（水平边界框，HBB）：23,463 张图像，192,518 个目标，20 类。
    *   **DIOR-R**（旋转边界框，OBB）：与 DIOR 共享图像，但采用旋转框标注。
    *   **HRSC**（旋转边界框，OBB）：专用于舰船检测，1,061 张图像，2,976 个目标，19 类。
    *   此外，在跨数据集实验中也使用了 **DOTA1.0**。
*   **对比方法**：
    *   **生成质量对比**：与 LostGAN、ReCo、LayoutDiffusion、GLIGEN 等经典布局到图像生成模型，在 FID（越低越好）、分类得分 CAS（越高越好）、YOLO 得分（衡量生成目标的可检测性）上进行对比。
    *   **数据增强对比**：与 Flip（翻转）、Copy-Paste（复制粘贴）等传统增强策略比较下游检测性能。
    *   **检测框架**：在 YOLOv8、Oriented RCNN、ReDet、Faster RCNN 等多种检测模型上验证合成数据的增益。
*   **评价指标**：图像质量用 FID，布局一致性用 CAS 和 YOLO Score，检测性能用 mAP 和 mAP50。

### 4. 资源与算力
论文中**未明确说明**训练时使用的 GPU 型号、数量或总训练时长/GPU小时。仅提到模型在各自数据集上训练 100 个 epoch，使用 AdamW 优化器，学习率 1e-5，并基于 LDM 在遥感数据上的微调权重进行训练（仅更新 UNet 的注意力层和新增的 Layout Mask Attention）。

### 5. 实验数量与充分性
实验设计**较为充分，且具备客观性与公平性**：
*   **生成质量评估**：在 DIOR、DIOR-R、HRSC 三个数据集上对比了 5 种方法，覆盖 HBB 和 OBB 两种模态，提供了全面的定量和定性结果（Tab.2, Fig.4）。
*   **数据增强效果**：验证了多种合成数据量（10k, 20k, 50k）对 DIOR/DIOR-R 的提升效果，以及 2k, 4k, 10k 对 HRSC 的增益。
*   **消融实验**：进行了模型组件消融（LMA、DCA）、增强策略对比（vs. Flip, CopyPaste）、生成流水线中各过滤模块的消融，以及跨检测框架和少样本场景的扩展实验，分析全面。
*   **公平性**：对比的生成方法均使用相同的 SD1.5 基座权重、相同数据集和训练轮数，保证了比较基准的公平。

### 6. 主要结论与发现
*   AeroGen 是**首个**同时支持水平和旋转边界框布局控制的遥感图像扩散生成模型。
*   生成的合成数据具有高视觉质量和高布局一致性，**显著优于**现有布局生成方法。
*   将合成数据加入训练集后，在 **DIOR、DIOR-R、HRSC** 三个主流基准上的 mAP 分别**提升 3.7%、4.3% 和 2.43%**。
*   数据增强对**稀有类别**的增益尤为显著，例如 GF、DAM、APO 类别的 mAP 分别提升 **17.8%、14.7% 和 12.6%**。
*   所提流水线中的多样性条件生成器和双重重过滤机制（标签过滤+图像过滤）对于保证数据质量有效性至关重要。

### 7. 优点
*   **技术首创性**：首次实现针对遥感目标检测的水平框和旋转框的统一布局可控生成，填补领域空白。
*   **系统性方案**：不仅提出了单一模型，更构建了从布局生成、图像合成到质量筛选的完整端到端数据增强框架，避免手工粘贴实例。
*   **精准控制机制**：融合布局嵌入与布局掩码注意力，实现了对生成图像中目标空间位置和类别的精细控制，尤其对小目标生成友好。
*   **显著的实际增益**：在多个数据集、多种检测器、多组实验设定下均取得一致的性能提升，尤其在数据稀疏和稀有类别问题上效果突出，实用性强。

### 8. 不足与局限
*   **计算成本不透明**：未披露模型训练和图像合成所需的硬件资源与时间，不利于复现成本评估。
*   **生成质量与真实性的上限**：虽然相比其他生成方法质量更高，但生成图像与真实遥感图像在域分布上仍可能存在差距（如个别类别性能略有下降），可能导致模型学习到虚假的生成伪影。
*   **过滤策略的泛化性**：标签过滤依赖对属性分布的正态假设，图像过滤依赖预训练 CLIP 和分类器，这些超参数和阈值设置对最终效果敏感，在不同类型遥感数据上的迁移适应可能需要额外调参。
*   **类别局限性**：实验仅覆盖了 DIOR、HRSC 等数据集定义的类别，对于更广泛或更复杂的遥感地物类别（如细小物体、密集场景）的生成能力尚未探讨。
（完）
