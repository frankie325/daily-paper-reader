---
title: Revisiting Generative Replay for Class Incremental Object Detection
title_zh: 重访生成重放用于类增量目标检测
authors: "Zhang, Shizhou, Lv, Xueqiang, Xing, Yinghui, Wu, Qirui, Xu, Di, Zhang, Yanning"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Zhang_Revisiting_Generative_Replay_for_Class_Incremental_Object_Detection_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 9.0
evidence: 利用生成重放的类增量目标检测
tldr: 针对类增量目标检测中遗忘问题，本文观察到分类子任务遗忘更严重，提出利用Stable Diffusion生成图像级重放数据，结合旧检测器与分阶段检测器生成边界框标签。该方法在多个增量检测设置下有效缓解灾难性遗忘，为类增量目标检测提供了一种简单而有效的生成重放方案。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-revisiting-generative-replay-for-class-incremental-object-detection-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 810, \"height\": 694, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-revisiting-generative-replay-for-class-incremental-object-detection-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1798, \"height\": 681, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-revisiting-generative-replay-for-class-incremental-object-detection-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 822, \"height\": 548, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-revisiting-generative-replay-for-class-incremental-object-detection-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 868, \"height\": 452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-revisiting-generative-replay-for-class-incremental-object-detection-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 848, \"height\": 497, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-revisiting-generative-replay-for-class-incremental-object-detection-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1622, \"height\": 805, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-revisiting-generative-replay-for-class-incremental-object-detection-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1690, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-revisiting-generative-replay-for-class-incremental-object-detection-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 853, \"height\": 589, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-revisiting-generative-replay-for-class-incremental-object-detection-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1543, \"height\": 275, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-revisiting-generative-replay-for-class-incremental-object-detection-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 808, \"height\": 321, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-revisiting-generative-replay-for-class-incremental-object-detection-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 784, \"height\": 319, \"label\": \"Table\"}]"
motivation: 类增量目标检测中生成重放应用有限，主要挑战在于生成复杂图像和精确空间布局，且遗忘主要体现在分类子任务。
method: 采用标准Stable Diffusion生成图像级重放数据，通过旧检测器和分阶段检测器获取边界框标签，聚焦缓解分类遗忘。
result: 在标准类增量检测基准上表现优异，有效减轻了灾难性遗忘，证明了生成重放在该领域的潜力。
conclusion: 生成重放可有效解决类增量目标检测中的分类遗忘，为持续学习目标检测提供新思路。
---

## Abstract
Generative replay has gained significant attention in class-incremental learning; however, its application to Class Incremental Object Detection (CIOD) remains limited due to the challenges in generating complex images with precise spatial arrangements. In this study, motivated by the observation that the forgetting of prior knowledge is predominantly present in the classification sub-task as opposed to the localization sub-task, we revisit the generative replay method for class incremental object detection. Our method utilize a standard Stable Diffusion model to generate image-level replay data for all old and new tasks. Accordingly, the old detector and a stage-wise detector are conducted on the synthetic images respectively to determine the bounding box positions through pseudo-labeling. Furthermore, we propose to use a Similarity-based Cross Sampling mechanism to select more valuable confusing data between old and new tasks to more effectively mitigate catastrophic forgetting and reduce the false alarm rate for the new task. Finally, all synthetic and real data are integrated for current-stage detector training, where the images generated for previous tasks are highly beneficial in minimizing the forgetting of existing knowledge, while those synthesized for the new task can help bridge the domain gap between real and synthetic images. We conducted extensive experiments on PASCAL VOC 2007 and MS COCO benchmark datasets in multiple settings to showcase the efficacy of our proposed approach, which achieves state-of-the-art results. The code are available at https://github.com/qiangzai-lv/RGR-IOD.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：类增量目标检测（Class Incremental Object Detection, CIOD）中，现有生成重放（Generative Replay）方法需要生成具有精确空间布局的复杂多目标图像，难度大、成本高，限制了其在 CIOD 中的广泛应用。
- **关键观察**：论文发现 CIOD 中的灾难性遗忘主要发生在**分类子任务**，而定位（边界框回归）子任务遗忘程度较轻（即使分类精度降为 0，目标仍能被正确定位）。这意味着无需费力生成复杂场景，只需生成能缓解分类遗忘的图像级数据即可。
- **整体含义**：**重访**生成重放策略，利用现成的 Stable Diffusion 模型，只需生成图像级（单目标为主）重放数据，配合伪标签与相似性交叉采样，即可高效减轻旧知识遗忘、降低新任务的误检率，并在多个基准上达到最优性能。

---

### 2. 论文提出的方法论

- **核心思想**：使用标准 Stable Diffusion 为**所有新旧类**生成图像级重放数据；通过旧检测器（\(M_{t-1}\)）和分阶段检测器（\(M_{s}^t\)，仅用当前任务数据训练）分别产生伪标签确定边界框；提出“相似性交叉采样（Similarity-based Cross Sampling, SCS）”挑选易混淆的难样本，从而有效保留旧知识并抑制新任务的假阳性。

- **关键技术细节**：
  1. **图像级生成重放（Image-Level Generative Replay, IGR）**  
     - 对旧类 \(cls_j \in C_{1:t-1}\)，用模板“A realistic clear photo of \(cls_j\)”生成图像。  
     - 用 \(M_{t-1}\) 检测，保留至少有一个检测实例且最低置信度 \(\ge \tau\) 的图像（公式 (1)），构成 \(D_{gen-(1:t-1)}\)。
  2. **相似性交叉采样（SCS）**  
     - **旧类侧**：对 \(D_{gen-(1:t-1)}\) 使用 \(M_{s}^t\)（只认识新类）预测，保留高置信度框（公式 (2)）；计算这些框与 \(M_{t-1}\) 伪标签框之间的最小 IoU（公式 (4)），若 IoUmin > \(\eta\)，则认为该图是易混淆的难样本，优先作为重放数据。  
     - **新类侧**：同时为新任务 \(T_t\) 合成部分数据 \(D_{gen-t}\)，与真实数据混合训练，以**弥合合成域与真实域的差异**，避免模型仅凭域信息判别。
  3. **当前阶段训练**  
     - **伪标签修正**：对真实数据 \(D_t\)，用 \(M_{t-1}\) 生成伪标签，但计算每个伪框与当前任务真实框的最大 IoU（公式 (5)），若 \(> \gamma\) 则丢弃该伪框，防止错误标签干扰新类学习。  
     - **损失函数**：总损失 \(L = L_{synth} + L_{real}\)，合成数据损失用较小权重 \(\lambda\)，且分类损失权重大于回归损失（因定位知识遗忘少）。
  4. **整体流程**：IGR 生成新旧数据 → SCS 筛选易混淆样本 → 合并所有合成与真实数据训练 \(M_t\)。

---

### 3. 实验设计

- **数据集**：  
  - PASCAL VOC 2007（20 类，训练/验证共约 5000 张，测试约 5000 张）  
  - MS COCO 2017（80 类，训练 118k，验证 5k）
- **增量场景设置**：  
  - **单步增量（PASCAL VOC）**：19-1、15-5、10-10、5-15  
  - **多步增量（PASCAL VOC）**：10-5（3 次）、5-5（4 次）、10-2（6 次）、15-1（6 次）  
  - **COCO 增量**：40-40（40 基础类 + 40 新增类）、70-10（70 基础 + 10 新增）
- **评估指标**：  
  - VOC：mAP@0.5  
  - COCO：AP@[0.5:0.95]、AP50、AP75
- **对比方法**（均为最新 SOTA 或经典基线）：  
  - 基线：Fine-tuning、Joint Training  
  - 基于示例重放（标记*）：ORE\*、ILOD-Meta\*、OW-DETR\*、ABR\*  
  - 无重放方法：Faster ILOD、PPAS、MVC、MMA、PseudoRM、PROB、BPF 等

---

### 4. 资源与算力

- 论文**未明确说明**具体的 GPU 型号、数量、训练时长等算力信息。  
- 仅提及使用 Stable Diffusion 1.5 进行生成（并分别在 COCO 或 VOC 上微调以适应目标数据集风格），检测器基于 Faster R-CNN + ResNet-50，用 SGD 优化器，batch size 8，基础/增量学习率分别为 0.01 / 0.005。算力需求与同类生成重放方法相当，但具体开销不可知。

---

### 5. 实验数量与充分性

- **实验总览**：  
  - 在 PASCAL VOC 上完成 **4 种单步增量 + 4 种多步增量**共 8 组设置。  
  - 在 COCO 上完成 **2 种增量设置**。  
  - 消融实验：验证 IGR、SCS 等主要组件的贡献（3 种设置）；对关键超参数 \(\tau\) 和 \(\eta\) 分别进行敏感性分析（各 2 种设置）。  
  - 类别级性能对比图（图 5）展示相似类间的遗忘缓解。
- **充分性与公平性**：  
  - 与大量现有 SOTA 方法比较，且对基于旧数据存储的方法（示例重放）单独标注，保证公平对比。  
  - 沿用前人实验协议（固定类序、只标注当前类），结果可靠。  
  - 消融实验覆盖主要创新点，参数分析给出推荐值，实验设计**充分、客观、公平**。

---

### 6. 论文的主要结论与发现

- CIOD 中**分类遗忘远大于定位遗忘**，因此无需复杂布局生成，图像级单目标重放足以应对核心难题。
- 所提 **RGR 方法**（IGR + SCS + 伪标签修正）在 PASCAL VOC 和 MS COCO 所有增量设置下均**达到最优性能**，显著超越 BPF 等强基线，尤其多步增量场景中提升明显（如 5-5 设置 mAP 提升 6.1%）。
- SCS 通过挑选跨任务易混淆样本，有效**降低新类误检率**并加强旧类保持能力。
- 同时生成新类合成数据有助于**桥接域差异**，进一步提升泛化。

---

### 7. 优点（方法或实验设计上的亮点）

- **问题洞察新颖**：从分类/定位遗忘不对称性出发，重新定义生成重放需求，极大简化了生成难度。
- **方法简洁高效**：直接使用预训练 SD 模型，无需对扩散模型增加布局或几何控制，工程代价低。
- **SCS 机制巧妙**：利用新旧检测器交叉评估相似性，自动筛选高价值难例，同时针对分类混淆进行优化。
- **伪标签处理细致**：通过 IoU 过滤掉可能与新类 GT 重叠的旧类伪标签，减少对新任务学习的干扰。
- **实验全面，代码开源**：覆盖多种增量形式、主流数据集和众多对比方法，可复现性强。

---

### 8. 不足与局限

- **生成图像单一**：主要生成单目标图像，缺乏多目标交互和背景多样性，可能限制了在复杂场景下的定位性能提升（尽管作者认为定位遗忘低，但复杂背景下的泛化未深入探讨）。
- **依赖 SD 微调**：生成模型需在与目标数据集相关的数据上微调，若目标域与 SD 预训练域差异过大，微调数据本身可能不可得，影响生成质量。
- **仅针对双阶段检测器**：所有实验基于 Faster R-CNN，未在单阶段或 Transformer 检测器上验证，通用性待补充。
- **未分析长序列累积效应**：在多步增量中，生成数据质量是否随任务增多而下降，以及如何持续控制误差累积，论文未讨论。
- **算力信息缺失**：无法评估实际资源消耗与部署可行性。
- **伪标签修正依赖真实 GT**：IoU 过滤需使用当前任务的真实框，若未来任务无 GT 标注，该方法不能直接迁移到无监督 CIOD。

（完）
