---
title: Visual Consensus Prompting for Co-Salient Object Detection
title_zh: 视觉共识提示用于共显著性目标检测
authors: "Wang, Jie, Yu, Nana, Zhang, Zihao, Han, Yahong"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Wang_Visual_Consensus_Prompting_for_Co-Salient_Object_Detection_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 8.0
evidence: 提出简洁的共显著性目标检测架构，采用基于提示的交互和参数高效微调
tldr: 针对现有共显著性目标检测方法中编码阶段缺乏共识指导、全参数微调效率低的问题，本文提出视觉共识提示的简洁架构。通过交互强化编码与共识提取，并采用参数高效微调保留基础模型知识。实验证明该方法在多个基准上以更少参数实现优异检测性能，为显著性检测任务提供了高效新框架。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-visual-consensus-prompting-for-co-salient-object-detection-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 849, \"height\": 581, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-visual-consensus-prompting-for-co-salient-object-detection-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 802, \"height\": 549, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-visual-consensus-prompting-for-co-salient-object-detection-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1786, \"height\": 574, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-visual-consensus-prompting-for-co-salient-object-detection-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 856, \"height\": 700, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-visual-consensus-prompting-for-co-salient-object-detection-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1755, \"height\": 1030, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-visual-consensus-prompting-for-co-salient-object-detection-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1802, \"height\": 864, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-visual-consensus-prompting-for-co-salient-object-detection-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1778, \"height\": 363, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-visual-consensus-prompting-for-co-salient-object-detection-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1750, \"height\": 377, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-visual-consensus-prompting-for-co-salient-object-detection-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1784, \"height\": 431, \"label\": \"Table\"}]"
motivation: 现有共显著性检测架构存在编码与共识提取脱节、全微调参数效率低的问题。
method: 提出视觉共识提示架构，增强编码与共识交互，并采用参数高效微调。
result: 在多个基准上以较少参数实现先进性能，有效保留基础模型知识。
conclusion: 该方法通过交互强化和高效微调显著提升了共显著性检测的效率和效果。
---

## Abstract
Existing co-salient object detection (CoSOD) methods generally employ a three-stage architecture (i.e., encoding, consensus extraction & dispersion, and prediction) along with a typical full fine-tuning paradigm. Although they yield certain benefits, they exhibit two notable limitations: 1) This architecture relies on encoded features to facilitate consensus extraction, but the meticulously extracted consensus does not provide timely guidance to the encoding stage. 2) This paradigm involves globally updating all parameters of the model, which is parameter-inefficient and hinders the effective representation of knowledge within the foundation model for this task. Therefore, in this paper, we propose an interaction-effective and parameter-efficient concise architecture for the CoSOD task, addressing two key limitations. It introduces, for the first time, a parameter-efficient prompt tuning paradigm and seamlessly embeds consensus into the prompts to formulate task-specific Visual Consensus Prompts (VCP). Our VCP aims to induce the frozen foundation model to perform better on CoSOD tasks by formulating task-specific visual consensus prompts with minimized tunable parameters. Concretely, the primary insight of the purposeful Consensus Prompt Generator (CPG) is to enforce limited tunable parameters to focus on co-salient representations and generate consensus prompts. The formulated Consensus Prompt Disperser (CPD) leverages consensus prompts to form task-specific visual consensus prompts, thereby arousing the powerful potential of pre-trained models in addressing CoSOD tasks. Extensive experiments demonstrate that our concise VCP outperforms 13 cutting-edge full fine-tuning models, achieving the new state of the art (with 6.8% improvement in F_m metrics on the most challenging CoCA dataset). Source code has been available at https://github.com/WJ-CV/VCP.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义
- **研究动机**：共显著性目标检测（CoSOD）旨在从一组相关图像中找出共同出现的显著物体。现有主流方法采用“编码 → 共识提取与传播 → 预测”的三阶段架构和全参数微调（full fine‑tuning）范式。
- **核心问题**：
  - **交互不足**：共识提取依赖编码特征，但提取出的共识却无法及时反馈指导编码阶段，编码与共识之间缺乏有效交互，限制了潜力发挥。
  - **参数低效**：全参数微调需要调整整个模型（包括大规模预训练基础模型）的所有参数，计算和存储开销大，且微调数据的质量和数量会制约预训练知识在大任务上的表征效果。
- **整体含义**：本文提出一种交互高效且参数高效的简洁架构，首次将参数高效的提示微调（prompt tuning）范式引入 CoSOD，把“共识”嵌入提示中，形成任务专属的视觉共识提示（Visual Consensus Prompts, VCP），以最少可调参数诱导冻结的预训练模型更好地完成 CoSOD 任务。

### 2. 论文提出的方法论
- **核心思想**：冻结预训练的基础模型（SegFormer），仅训练少量与任务相关的可调参数，这些参数专门用于挖掘组内共显著表征并生成共识提示，再用这些提示引导模型逐层自适应地处理 CoSOD 任务。
- **关键组件**：
  - **共识提示生成器（Consensus Prompt Generator, CPG）**：
    - 利用可学习的显著性种子（saliency seeds），通过聚类生成组内显著对象的原型表示。
    - 生成显著性估计图，进一步提取像素级“共识种子”，选出组内相关性最高的 top‑k 像素嵌入作为代表共识种子。
    - 将共识种子映射回原始嵌入空间，形成**共识提示 \(P_{Co}\)**。
  - **共识提示分发器（Consensus Prompt Disperser, CPD）**：
    - 将共识提示与嵌入提示 \(P_{Em}\) 结合，形成**嵌入共识提示 \(P_{Co}^{Em}\)**。
    - 同时引入基于快速傅里叶变换的手工特征提示 \(P_{Hand}\)，并与共识提示结合得到**手工共识提示 \(P_{Co}^{Hand}\)**。
    - 融合上述两种提示得到**视觉共识提示 \(P_{Co}^{Visual} = [P_{Em}+P_{Co}, P_{Hand}+P_{Co}]\)**。
    - 采用不同阶段不共享的线性层和阶段内共享的线性层，将 \(P_{Co}^{Visual}\) 自适应地注入冻结的 Transformer 层，实现逐层调优。
  - **预测头与损失**：设计轻量预测头（ASPP + FPN‑like + 线性分类器），损失函数组合包括 BCE、IoU 损失（对最终预测和四阶段中间显著性估计图）以及分类交叉熵损失。
- **关键公式举例**：
  - 软分配得分 \(S_{soft} = \nu(\text{Softmax}(\text{conv}(L2(P_{em}))))\)
  - 残差与种子更新、显著性估计图生成。
  - 共识种子得分计算及 top‑k 选取。
  - 视觉共识提示构建及多层线性映射：\(P_{n}^{S} = \text{MLP}_{up}(\text{gelu}(\text{MLP}_{n}^{S}(P_{Co}^{Visual})))\)

### 3. 实验设计
- **数据集/场景**：
  - **测试集**：CoCA、CoSOD3k、CoSal2015（最常用的三个 CoSOD 基准）。
  - **训练集**：DUT‑class (D)、COCO‑9k (C)、COCO‑SEG (S)，文中采用 D+C 和 D+S 两种组合以对齐不同方法的设置。
- **对比方法**：13 个近三年的 SOTA 方法，包括全微调的 SCED、MCCL、GCoNet+、GEM、CADC++、CoPR、DMT 等，以及基于简单视觉提示的 EVP。
- **评估指标**：MAE、Mean‑\(E_m\)、\(E_m^{\max}\)、\(S_m\)、Mean‑\(F_m\)、\(F_m^{\max}\)。

### 4. 资源与算力
- **硬件**：单张 NVIDIA 3090 GPU。
- **训练时长**：使用 D+C 训练集时，训练 100 个 epoch，总训练时间约 9 小时；D+S 训练集为 200 个 epoch。学习率从 \(5\times10^{-4}\) 余弦衰减至 \(1\times10^{-4}\)（或更低），输入统一缩放为 \(288\times288\)。
- **推理速度**：约 65.3 FPS。
- **可调参数量**：最终模型仅 4.94 M 可调参数，模型文件大小 19 MB，显著低于全微调方法（例如 392.85 M 参数）。

### 5. 实验数量与充分性
- **主要定量实验**：表 1 展示在三个测试集上对 13 个 SOTA 方法的全面比较，同时报告可调参数量和模型大小。
- **消融实验**（表 2‑4）：
  - 组件消融（基线、仅预测头、增加手工提示、增加共识提示、连接方式）；
  - 辅助组件消融（分类损失、中间监督、预测头设计、MLP 共享策略）；
  - 与其他主流视觉提示方法（Adaptformer、VPT、EVP）的对比，以及不同降维比例 \(r\) 的影响。
- **定性实验**：可视化对比四种挑战场景（正常、多显著干扰、微小目标、目标外观变化）。
- 实验设计公平（采用相同的训练数据组合，统一输入尺寸），消融丰富，充分验证了各组件的有效性和设计的合理性。

### 6. 论文的主要结论与发现
- VCP 在参数极少的条件下（4.94 M），全面超越 13 种全微调 SOTA 方法，在最具挑战性的 CoCA 数据集上 \(S_m\) 和 \(F_m\) 分别提升 5.6% 和 6.8%。
- 将共识提取与分发嵌入提示，有效解决了编码‑共识交互不足的问题，同时无需更新基础模型参数，保留了大规模预训练知识。
- 相比简单视觉提示（如 EVP），专门为 CoSOD 设计的共识提示能带来大幅性能提升。
- 该方法可作为现有全微调范式的有力替代方案，兼具高性能与高参数效率。

### 7. 优点
- **架构简洁、交互有效**：通过提示形式实现编码与共识的动态交互，彻底告别传统的三阶段串行范式。
- **参数效率极高**：仅需微调不到 5 M 参数，存储与计算开销极小，便于实际部署。
- **方法通用性强**：不依赖额外的大规模显著性预训练数据，仅用标准 CoSOD 训练集；与多种预训练模型兼容（文中使用 SegFormer）。
- **实验扎实**：在多个数据集上进行全面定量、定性比较，消融实验覆盖所有核心设计，对比方法多且新，证据充分。
- **性能显著**：尤其在难度高、干扰多的 CoCA 数据集上取得领先优势，体现出强鲁棒性。

### 8. 不足与局限
- **基础模型依赖**：实验仅基于 SegFormer，未在更多种类的视觉 Transformer（如 Swin、ViT‑Adapter）或更大规模模型上验证泛化性。
- **图像组大小影响**：训练时采样组内图像数量（≤16），对图像组规模很大的场景（如视频流或超长序列）的可扩展性未讨论。
- **跨域能力未评估**：仅在标准 CoSOD 数据集上测试，未涉及域偏移（如医学影像、遥感影像）时的表现。
- **手工特征的必要性**：傅里叶特征带来的增益有限，但依然增加了额外的计算步骤，其设计是否可被更简单的替代未深入探讨。
- **模型容量限制**：虽然当前参数量极少，但随着基础模型规模持续增长（如大模型），极低的可调参数是否能始终捕捉复杂的组内共识仍是一个开放问题。

（完）
