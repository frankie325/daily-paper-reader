---
title: Multiple Object Tracking as ID Prediction
title_zh: 将多目标跟踪视为ID预测
authors: "Gao, Ruopeng, Qi, Ji, Wang, Limin"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Gao_Multiple_Object_Tracking_as_ID_Prediction_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 4.0
evidence: 将目标跟踪视为ID预测，依赖于目标检测
tldr: 传统多目标跟踪依赖手工设计的关联启发式方法，适应性有限。本文提出将跟踪视为上下文ID预测的新视角，让模型直接从数据中学习最优追踪能力，简化的流程可能为检测与跟踪的联合优化提供新思路，但核心贡献在于跟踪，检测仅为组件。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-gao-multiple-object-tracking-as-id-prediction-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 789, \"height\": 601, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-gao-multiple-object-tracking-as-id-prediction-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1637, \"height\": 658, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-gao-multiple-object-tracking-as-id-prediction-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 787, \"height\": 337, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-gao-multiple-object-tracking-as-id-prediction-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 811, \"height\": 1083, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-gao-multiple-object-tracking-as-id-prediction-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 799, \"height\": 782, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-gao-multiple-object-tracking-as-id-prediction-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 793, \"height\": 547, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-gao-multiple-object-tracking-as-id-prediction-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 844, \"height\": 480, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-gao-multiple-object-tracking-as-id-prediction-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 839, \"height\": 565, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-gao-multiple-object-tracking-as-id-prediction-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 820, \"height\": 394, \"label\": \"Table\"}]"
motivation: 手工设计的跟踪关联规则缺乏灵活性。
method: 将多目标跟踪建模为上下文ID预测任务。
result: 在多个跟踪基准上取得有竞争力的性能。
conclusion: ID预测范式简化了跟踪流程，提升了自适应性。
---

## Abstract
Multi-Object Tracking (MOT) has been a long-standing challenge in video understanding. A natural and intuitive approach is to split this task into two parts: object detection and association. Most mainstream methods employ meticulously crafted heuristic techniques to maintain trajectory information and compute cost matrices for object matching. Although these methods can achieve notable tracking performance, they often require a series of elaborate handcrafted modifications while facing complicated scenarios. We believe that manually assumed priors limit the method's adaptability and flexibility in learning optimal tracking capabilities from domain-specific data. Therefore, we introduce a new perspective that treats Multiple Object Tracking as an in-context ID Prediction task, transforming the aforementioned object association into an end-to-end trainable task. Based on this, we propose a simple yet effective method termed MOTIP. Given a set of trajectories carried with ID information, MOTIP directly decodes the ID labels for current detections to accomplish the association process. Without using tailored or sophisticated architectures, our method achieves state-of-the-art results across multiple benchmarks by solely leveraging object-level features as tracking cues. The simplicity and impressive results of MOTIP leave substantial room for future advancements, thereby making it a promising baseline for subsequent research. Our code and checkpoints are released at https://github.com/MCG-NJU/MOTIP.

---

## 论文详细总结（自动生成）

好的，以下是对论文《Multiple Object Tracking as ID Prediction》的详细中文总结。

### 1. 论文的核心问题与整体含义（研究动机和背景）
*   **核心问题**：多目标跟踪（MOT）的传统主流方法通常将任务拆分为检测和关联两部分。在关联阶段，这些方法依赖大量手工设计的启发式规则和成本矩阵来进行目标匹配，这限制了模型从特定领域数据中学习最优跟踪能力的适应性和灵活性。
*   **研究动机**：作者认为手工设定的先验知识在复杂场景下效果有限，且每次改进都需要大量的人为分析和超参数微调。近年来基于DETR的端到端方法虽然取得了进展，但检测与跟踪查询在统一的解码过程中会产生冲突，损害性能。
*   **整体含义**：论文提出一个全新的视角，将多目标跟踪中的对象关联问题重新定义为一种 **“上下文ID预测”（In-context ID Prediction）** 任务。核心思想是，对于一个目标，只需要根据其历史轨迹所携带的ID信息来预测其在当前帧的ID标签，而非学习一个全局固定的标签。这一转变将对象关联变成一个端到端可训练的分类问题。

### 2. 论文提出的方法论：核心思想、关键技术细节、算法流程
*   **核心思想**：MOT中轨迹的ID标签仅表示时序上的一致性，不需要特定语义。因此，可以为历史轨迹随机分配临时的上下文ID（1到K），然后让模型根据这些上下文提示来预测当前检测目标应属于哪个ID。这解决了传统分类模型在推理时面对新ID的泛化难题。
*   **整体架构（MOTIP）**：方法由三个核心组件构成，简洁直观。
    1.  **DETR检测器**：采用 **Deformable DETR** 作为检测器。输入图像后，其Transformer解码器直接输出目标检测边界框和分类置信度，同时直接使用解码器的输出嵌入作为目标的**对象级特征**，避免了RoI等复杂特征提取。
    2.  **可学习的ID字典**：为表示离散的身份信息，创建了一个包含 `K+1` 个可学习嵌入的字典。其中 `K` 个常规词元代表特定身份，1个特殊词元 `i_spec` 代表“新出生”目标。
    3.  **ID解码器**：使用一个标准的 **Transformer解码器**。它将过去 `T` 帧的历史轨迹信息（对象特征与对应的ID词元拼接而成的轨迹片段）作为Key和Value，对当前帧的检测目标查询（对象特征与特殊词元拼接）进行解码，最后通过一个线性分类头预测该目标对应哪个上下文ID。
*   **训练过程**：
    *   **损失函数**：整个模型可以端到端训练，目标关联部分使用标准**交叉熵损失（L_id）** 进行监督，联合检测损失（分类、回归、IoU）形成统一损失函数。
    *   **轨迹增强（Trajectory Augmentation）**：在训练时模拟推理中可能出现的错误，提高模型鲁棒性。
        *   **随机遮挡（λ_occ）**：以一定概率随机丢弃历史轨迹中的某些特征词元，模拟目标被遮挡的情况。
        *   **随机切换（λ_sw）**：以一定概率随机交换同一帧内两个轨迹的ID词元，模拟ID分配错误的情况。
*   **推理过程**：
    1.  为每条活跃轨迹按顺序分配1到K的唯一ID，并用对应的ID嵌入表示。当ID超出K时，回收已消失轨迹的ID。
    2.  对当前帧检测到的目标，ID解码器预测其属于每个ID的概率。
    3.  选择置信度最高且大于阈值 `λ_id` 的ID作为预测结果。若目标无有效ID且检测置信度大于 `λ_new`，则视为新目标并分配新ID。
    4.  当同一帧出现重复ID预测时，仅保留置信度最高的那个。

### 3. 实验设计：数据集、基准比对方法
*   **数据集**：选取了多个具有挑战性的基准，以验证方法的泛化能力。
    *   **DanceTrack**：群舞视频数据集，侧重频繁遮挡、不规则运动和相似外观。
    *   **SportsMOT**：体育赛事数据集，侧重快速相机运动、运动员高速移动和互动。
    *   **BFT**：鸟类跟踪数据集，目标具有高度动态的三维运动和相似外观。
*   **评估指标**：主要采用 **HOTA**（平衡检测和关联精度），同时参考 **AssA**（关联精度）、**MOTA** 和 **IDF1**。
*   **对比方法**：对比了大量主流方法，包括：
    *   **跟踪-检测范式**：FairMOT、ByteTrack、OC-SORT、StrongSORT、Hybrid-SORT、C-BIoU等。
    *   **跟踪-传播范式（基于查询的方法）**：TransTrack、TrackFormer、MOTR系列（MOTRv2、MOTRv3）、MeMOTR、CO-MOT等。
    *   其他端到端或基于学习的方法：CenterTrack、QDTrack等。对比时特别强调了与同样使用Deformable DETR + ResNet-50骨干网络的方法（如CO-MOT）进行公平比较。

### 4. 资源与算力
*   **硬件配置**：使用 **8块NVIDIA RTX 4090 GPU** 进行训练。
*   **训练耗时**：方法并行度高且对GPU友好。例如，在 **DanceTrack** 数据集上的训练耗时**不到一天**。

### 5. 实验数量与充分性
论文进行了较为充分的实验来验证方法和各组件的有效性。
*   **主要结果实验**：在 **3个** (DanceTrack, SportsMOT, BFT) 不同场景的大型数据集上，与 **30余种** 现有方法进行了比较，涵盖了不使用额外数据的设定和使用额外数据的设定（表1、表2、表3）。
*   **消融实验**：主要在DanceTrack数据集上，设计了一系列消融研究：
    1.  **匈牙利算法**：探究在ID预测框架下，标准匈牙利匹配算法是否必要（表4）。
    2.  **ID解码器中的自注意力层**：验证自注意力机制对全局最优解和身份信息交换的关键作用（表4）。
    3.  **与ReID管线的对比**：将所提出的ID预测方案与两种典型的ReID训练/推理方式进行了详细比较（表5），证明了ID预测范式的优越性。
    4.  **轨迹增强技术的超参数**：探讨了遮挡概率`λ_occ`和ID切换概率`λ_sw`对性能的影响，并找到了最佳参数组合（表6）。
实验设计客观、公平，特别是在对比时考虑了检测器、骨干网络等变量的影响。

### 6. 论文的主要结论与发现
*   将多目标跟踪模型化为**上下文ID预测**问题，在训练和推理上均是简单且高效。
*   基于此提出的**MOTIP**，是一个极简但强大的基线模型，它在多个挑战性基准上**全部达到了最优性能**，尤其是在关联精度（AssA）上提升显著。
*   模型展现出强大的**泛化能力**，能从特定领域数据中学习最优跟踪策略，而不依赖于动的人为设计。
*   ID预测范式比传统的ReID管线更灵活、更强大，模型能直接基于历史轨迹上下文做出最优关联决策。

### 7. 优点：方法或实验设计上的亮点
*   **视角新颖**：创造性地将关联问题转化为依赖上下文的分类问题，解决了传统分类模型无法泛化到新ID的难题。
*   **方法简洁端到端**：架构极其简单，仅由检测器、ID字典和标准Transformer解码器组成，没有复杂的后处理或手工匹配规则，易于实现和扩展。
*   **性能突出**：以简洁的设计在多个复杂数据集（舞蹈、体育、鸟类）上均取得了**最先进（SOTA）** 的结果，充分证明了新范式的巨大潜力。
*   **公平的对比设计**：在实验中注意控制变量（如使用相同的DETR检测器和骨干网络），使结果更具说服力。
*   **有效的训练增强**：提出的轨迹随机遮挡和ID随机切换技术，有效地模拟了推理阶段的挑战，提升了模型的鲁棒性。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等
*   **模型深度设计的局限性**：作者明确指出，方法的初衷是验证“ID预测”这一简单理念的可行性，并未在ID解码器设计、多线索融合（如运动、深度）、轨迹建模等方面进行深度定制，这既是优点（简单），也意味着未来还有很大的改进空间。
*   **ID字典容量（K）限制**：在极其拥挤的场景中，可用的ID标签数量K可能不足。论文虽然提到大多数情况下K的利用率低于40%，但承认在极端场景下可能需要调高K值。
*   **推理分配的简化**：推理过程中使用简单的取最大值和“新出生”阈值策略，虽然有效，但可能并非最优。作者也提及，更高级的分配策略（如匈牙利算法）可能带来进一步提升，但未进一步探索。
*   **对检测器的依赖**：作为一个检测-跟踪分离的框架，其整体性能高度依赖于前端DETR检测器的性能。

（完）
