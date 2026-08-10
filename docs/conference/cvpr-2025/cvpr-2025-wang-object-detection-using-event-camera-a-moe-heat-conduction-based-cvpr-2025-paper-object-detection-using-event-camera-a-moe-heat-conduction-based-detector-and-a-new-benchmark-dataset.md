---
title: "Object Detection using Event Camera: A MoE Heat Conduction based Detector and A New Benchmark Dataset"
title_zh: 事件相机目标检测：基于混合专家热传导的检测器与新基准数据集
authors: "Wang, Xiao, Jin, Yu, Wu, Wentao, Zhang, Wei, Zhu, Lin, Jiang, Bo, Tian, Yonghong"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Wang_Object_Detection_using_Event_Camera_A_MoE_Heat_Conduction_based_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 9.0
evidence: 提出一种新颖的事件相机目标检测算法，平衡精度与效率
tldr: 针对事件相机目标检测现有架构（脉冲神经网络、Transformer、CNN）存在的性能、计算开销或感受野限制，本文提出一种新颖的基于混合专家（MoE）热传导的目标检测算法，通过事件数据嵌入和MoE模块平衡准确性与计算效率。还贡献了新的基准数据集。实验表明该方法在低光照、运动模糊等挑战场景下具有优越性能，为事件相机目标检测提供了高效新方案。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-object-detection-using-event-camera-a-moe-heat-conduction-based-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1614, \"height\": 684, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-object-detection-using-event-camera-a-moe-heat-conduction-based-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1522, \"height\": 830, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-object-detection-using-event-camera-a-moe-heat-conduction-based-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 833, \"height\": 838, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-object-detection-using-event-camera-a-moe-heat-conduction-based-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 700, \"height\": 288, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-object-detection-using-event-camera-a-moe-heat-conduction-based-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1799, \"height\": 704, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-object-detection-using-event-camera-a-moe-heat-conduction-based-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 803, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-object-detection-using-event-camera-a-moe-heat-conduction-based-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 860, \"height\": 166, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-object-detection-using-event-camera-a-moe-heat-conduction-based-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 477, \"height\": 202, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-object-detection-using-event-camera-a-moe-heat-conduction-based-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 776, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-object-detection-using-event-camera-a-moe-heat-conduction-based-cvpr-2025-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 543, \"height\": 205, \"label\": \"Table\"}]"
motivation: 现有事件相机检测器在性能、计算开销或局部感受野方面各有局限，难以兼顾精度与效率。
method: 提出基于混合专家（MoE）热传导的目标检测算法，先经主干网络嵌入事件数据，再通过创新的MoE模块处理。
result: 在低光照、运动模糊等条件下实现优越性能，并贡献新基准数据集。
conclusion: 该方法显著平衡了准确性与计算效率，推动了事件相机目标检测的发展。
---

## Abstract
Object detection in event streams has emerged as a cutting-edge research area, demonstrating superior performance in low-light conditions, scenarios with motion blur, and rapid movements. Current detectors leverage spiking neural networks, Transformers, or convolutional neural networks as their core architectures, each with its own set of limitations including restricted performance, high computational overhead, or limited local receptive fields. This paper introduces a novel MoE (Mixture of Experts) heat conduction-based object detection algorithm that strikingly balances accuracy and computational efficiency. Initially, we employ a stem network for event data embedding, followed by processing through our innovative MoE-HCO blocks. Each block integrates various expert modules to mimic heat conduction within event streams. Subsequently, an IoU-based query selection module is utilized for efficient token extraction, which is then channeled into a detection head for the final object detection process. Furthermore, we are pleased to introduce EvDET200K, a novel benchmark dataset for event-based object detection. Captured with a high-definition Prophesee EVK4-HD event camera, this dataset encompasses 10 distinct categories, 200,000 bounding boxes, and 10,054 samples, each spanning 2 to 5 seconds. We also provide comprehensive results from over 15 state-of-the-art detectors, offering a solid foundation for future research and comparison.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，我将以Markdown形式，对您提供的论文进行结构化、深入、客观的总结。

### 1. 论文的核心问题与整体含义

*   **研究动机与背景**：
    *   事件相机在低光照、运动模糊和高速移动等挑战性场景下表现出色，但其数据形式（异步事件流）与传统图像不同，为目标检测任务带来了新的挑战。
    *   现有的事件流目标检测器主要基于**脉冲神经网络（SNN）**、**Transformer**或**卷积神经网络（CNN）**，但各有显著缺陷：
        *   **CNN**：感受野有限，难以捕捉长距离依赖关系。
        *   **Transformer**：计算复杂度高，可解释性差。
        *   **SNN**：虽然能效高，但检测精度普遍低于基于人工神经网络（ANN）的方法。
    *   因此，研究的核心问题是如何设计一个能同时实现**高效性、高性能和可解释性**的事件相机目标检测算法。

*   **整体含义**：
    *   本文提出了一种新颖的物理启发式检测框架，通过模拟热传导过程来更有效地建模视觉特征扩散，并引入混合专家（MoE）机制来增强模型对不同视觉模式的适应性。同时，通过发布一个新的大规模基准数据集，为事件相机目标检测领域提供了统一的评估平台，旨在推动该领域的进一步发展。

### 2. 论文提出的方法论

*   **核心思想**：
    *   将图像特征块视为“热源”，图像特征在空间上的交互和扩散过程类似于物理世界中的**热传导**。通过模拟这一过程来构建骨干网络（MvHeat），旨在以较低的计算复杂度实现有效的特征提取。

*   **关键技术细节**：
    *   **事件数据特征嵌入**：首先将异步事件流堆叠成事件帧，然后通过一个骨干网络（stem network）获取初始特征嵌入。
    *   **MoE-HCO（Mixture of Experts Heat Conduction Operator）模块**：这是本文方法的核心创新点。
        *   **混合专家（MoE）策略**：模块内部集成了三个专家变换分支：离散傅里叶变换（DFT）、离散余弦变换（DCT）和哈尔变换（HT）。一个带有Gumbel Softmax的策略网络负责为输入特征动态选择最合适的变换分支。其动机在于：DCT善于检测小目标，HT在复杂场景下更有效，DFT则具有更普遍的适用性。
        *   **热传导模拟**：将特征变换到频域后，引入一个可学习的**热扩散率 \( k \)**。该参数通过一个随机初始化的频率嵌入（Frequency Embeddings, FEs）由一个线性层预测得到。频域特征乘以 \( e^{-k(v_x^2+v_y^2)t} \) 来模拟热扩散过程，最后通过逆变换（IDFT、IDCT、IHT）还原到空间域，完成一次热传导操作。
        *   **边界条件**：考虑到图像的空间边界，引入了诺伊曼边界条件，这使得DCT和HT成为合理的变换选择。
    *   **IoU-引导的查询选择（IoU-based Query Selection, IQS）**：
        *   针对DETR类检测器中，分类置信度与定位精度不一致的问题（高分类分数但低IoU的预测框），本文在训练时将IoU得分融入到分类分支的损失函数中（如公式 \( L = L_{bbox} + L_{cls}(IoU, c, \hat{c}) \) 所示），引导模型学习到分类分数与IoU得分的一致性。这样，在推理时，即使仍基于分类分数进行前K个查询选择，也能筛选出定位更准确的查询，提升了检测性能。

*   **公式或算法流程**：
    1.  **输入**：事件流 → 事件帧 → 特征嵌入。
    2.  **骨干网络**：特征嵌入依次通过4个阶段的MvHeat编码器，每个阶段包含多个**MoE-HCO层**。
    3.  **查询选择与检测**：编码器输出的特征首先经过**IQS模块**，筛选出高质量的查询（queries），然后送入传统的Transformer解码器和检测头，进行最终的分类和边界框回归。

### 3. 实验设计

*   **数据集 / 场景**：
    1.  **EvDET200K（自建基准数据集）**：
        *   **设备**：高分辨率Prophesee EVK4-HD事件相机。
        *   **规模**：10,054个样本，20万个精确标注边界框，涵盖10个类别（人、轿车、自行车、电动车、篮球、乒乓球、鹅、猫、鸟、无人机）。每个样本时长2到5秒。
        *   **特点**：特别关注小目标检测（占比51%），并考虑了多视角、多光照、多运动、动态背景等多种挑战因素。数据集按6:1:3的比例分为训练、验证和测试集。
    2.  **N-Caltech101（公开的经典基准数据集）**：用于验证模型的泛化能力。

*   **基准/对比方法**：本文进行全面对比，涵盖了超过15种主流和先进的目标检测器，包括：
    *   **CNN类**：Faster R-CNN、Mask R-CNN、RetinaNet、DetectoRS、RED 等。
    *   **YOLO系列**：YOLOv6、YOLOv10等。
    *   **Transformer类**：DETR、Swin-Transformer、RVT、SAST、S5-ViT、vHeat 等。
    *   **SNN类**：SpikeYOLO、EMS-YOLO。

*   **评估指标**：
    *   **精度指标**：mAP@50:95, mAP@50, mAP@75，以及精确率（Precision）和召回率（Recall）。
    *   **效率指标**：参数量（Params）、计算量（FLOPs）和推理速度（FPS）。

### 4. 资源与算力

*   **论文明确说明情况**：论文正文中**未明确提及**训练所使用的GPU型号、数量、批次大小或总训练时长等具体算力信息。
*   **补充信息**：只在致谢部分提到“感谢安徽大学高性能计算平台提供的计算资源”，这表明训练是在校内集群上完成的，但缺少可供复现的具体算力配置细节。

### 5. 实验数量与充分性

*   **实验数量**：实验设计相当详尽，可大致分为以下几类：
    1.  **主要性能对比**：
        *   在**EvDET200K**数据集上与超过15种SOTA方法进行全面对比（1组）。
        *   在**N-Caltech101**数据集上与现有事件点/帧方法进行对比（1组）。
    2.  **组件分析**：通过逐步添加 IQS、vHeat编码器、MoE策略等关键组件，验证每个部分对基准模型（DETR）性能的提升效果（1组）。
    3.  **消融实验**：深入探究了模型内部的多个关键设计选择和超参数，共计4组实验：
        *   骨干网络第三阶段中 **MHCO层的数量**。
        *   MoE策略中 **专家的数量**。
        *   **不同专家组合**方式（如DFT、DCT、HT单一或组合）。
        *   热扩散率 \( k \) 的不同设定方式（固定值、可学习参数、用FEs预测）。

*   **充分性与公平性评估**：
    *   **充分性**：实验非常充分。它不仅在自建和新数据集上证明了先进性，还在公开数据集上验证了泛化性。通过组件分析和多维度消融实验，清晰地展示了每个创新点和设计选择的贡献与影响。
    *   **公平性**：对比实验公平。在EvDET200K数据集上，所有对比方法都在相同的训练/测试集划分下进行了重新训练和评估，排除了数据差异造成的偏差，为未来研究提供了可靠的基准。

### 6. 论文的主要结论与发现

*   **算法有效性**：提出的**MvHeat-DET**在EvDET200K数据集上取得了最优的检测精度（mAP@50:95为52.9），显著优于包括YOLO、Faster R-CNN、DETR及其变体在内的所有对比方法，同时保持了较低的计算量和参数量，实现了精度与效率的优异平衡。
*   **泛化能力**：在N-Caltech101数据集上也达到了最佳的mAP（55.7），证明了模型具有良好的泛化性能。
*   **组件贡献**：
    *   基于热传导的骨干网络（vHeat/MvHeat）是性能提升的主要来源。
    *   IoU引导的查询选择（IQS）策略能有效提升DETR类检测器的性能。
    *   混合专家（MoE）策略通过融合不同变换的优势，进一步提升了模型的整体精度。
*   **数据集价值**：发布的**EvDET200K**数据集为事件相机目标检测领域提供了一个新的大规模、多样化、标注精良的基准，有助于推动该方向的标准化评估和算法研究。

### 7. 优点

*   **方法论创新**：将物理中的**热传导原理**与**MoE**结合应用于视觉骨干网络是一个独特且有效的新思路，为模型的设计提供了良好的物理可解释性。
*   **性能与效率的平衡**：MvHeat-DET在显著提升精度的同时，其计算复杂度 \( O(N^{1.5}) \) 低于传统Transformer，实现了性能与效率的良好折中，具有实际应用潜力。
*   **实验设计扎实**：包含多数据集评估、详尽的消融实验和组件分析，论证过程严谨，结论可信。
*   **社区贡献大**：提出并开源了一个带有15种以上检测器基准结果的大规模新数据集 **EvDET200K**，为领域发展提供了重要基石。研究代码也已开源，利于复现。

### 8. 不足与局限

*   **算力信息缺失**：未提供训练所需的GPU型号、数量和时间，降低了实验的可复现性和对资源需求的直观判断。
*   **MoE机制的开销**：论文虽然展示了MoE带来的精度提升，但未深入探讨引入多专家和策略网络所带来的额外计算开销和内存占用，这对于权衡效率至关重要。
*   **专家选择的局限性**：专家池（DFT, DCT, HT）的选择可能不是最优解，且基于单一策略网络的门控机制在面对极其多样化的场景时，其鲁棒性有待进一步检验。
*   **数据集泛化性**：EvDET200K数据集虽然规模较大，但仍是单一类型相机（Prophesee EVK4-HD）拍摄。模型在其他分辨率、其他厂商的事件相机数据上的泛化能力尚未验证。
*   **锚定特定架构**：MvHeat骨干网络的设计和IQS模块主要基于DETR框架。将这个核心思想（如MoE-HCO）轻松迁移到其他检测架构（如YOLO）的可能性及效果未作探讨。

（完）
