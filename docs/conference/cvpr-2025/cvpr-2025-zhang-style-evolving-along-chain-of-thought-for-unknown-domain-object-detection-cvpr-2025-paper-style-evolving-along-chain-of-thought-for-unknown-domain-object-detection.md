---
title: Style Evolving along Chain-of-Thought for Unknown-Domain Object Detection
title_zh: 面向未知域目标检测的思维链风格演化
authors: "Zhang, Zihao, Wu, Aming, Han, Yahong"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Zhang_Style_Evolving_along_Chain-of-Thought_for_Unknown-Domain_Object_Detection_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 9.0
evidence: 基于思维链风格演化的单域泛化目标检测
tldr: 为了解决单域泛化目标检测中复杂风格（如雨天+夜晚）下性能弱的问题，本文提出一种基于思维链的风格演化方法。通过逐步演化文本提示，使模型能够自适应多种未知域的风格变化，增强检测器泛化能力。实验表明，该方法在多个未知域上显著优于单步提示方法，提升了跨域目标检测的鲁棒性。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-style-evolving-along-chain-of-thought-for-unknown-domain-object-detection-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 783, \"height\": 739, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-style-evolving-along-chain-of-thought-for-unknown-domain-object-detection-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1724, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-style-evolving-along-chain-of-thought-for-unknown-domain-object-detection-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 782, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-style-evolving-along-chain-of-thought-for-unknown-domain-object-detection-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1728, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-style-evolving-along-chain-of-thought-for-unknown-domain-object-detection-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1719, \"height\": 583, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-style-evolving-along-chain-of-thought-for-unknown-domain-object-detection-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 863, \"height\": 564, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-style-evolving-along-chain-of-thought-for-unknown-domain-object-detection-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 874, \"height\": 433, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-style-evolving-along-chain-of-thought-for-unknown-domain-object-detection-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 870, \"height\": 409, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-style-evolving-along-chain-of-thought-for-unknown-domain-object-detection-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 871, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-style-evolving-along-chain-of-thought-for-unknown-domain-object-detection-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 871, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-style-evolving-along-chain-of-thought-for-unknown-domain-object-detection-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 872, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-style-evolving-along-chain-of-thought-for-unknown-domain-object-detection-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 871, \"height\": 221, \"label\": \"Table\"}]"
motivation: 单域泛化目标检测中，单步文本提示难以处理复杂组合风格，导致泛化性能下降。
method: 提出思维链风格演化方法，通过逐步演化文本提示来适配未知域的复杂风格。
result: 在多个未知域测试中超越现有单步提示方法，有效提升了检测泛化能力。
conclusion: 思维链风格演化策略能更好地应对未知域复杂风格变化，推动目标检测泛化研究。
---

## Abstract
Recently, a task of Single-Domain Generalized Object Detection (Single-DGOD) is proposed, aiming to generalize a detector to multiple unknown domains never seen before during training. Due to the unavailability of target-domain data, some methods leverage the multimodal capabilities of vision-language models, using textual prompts to estimate cross-domain information, enhancing the model's generalization capability. These methods typically use a single textual prompt, referred to as the one-step prompt method. However, when dealing with complex styles, such as the combination of rain and night, we observe that the performance of the one-step prompt method tends to be relatively weak. The reason may be that many scenes incorporate a single style and a combination of multiple styles. The one-step prompt method may not effectively synthesize combined information involving various styles. To address this limitation, we propose a new method, i.e., Style Evolving along Chain-of-Thought, which aims to progressively integrate and expand style information along the chain of thought, enabling the continual evolution of styles. Specifically, by progressively refining style descriptions and guiding the diverse evolution of styles, this method enhances the simulation of various style characteristics, enabling the model to learn and adapt to subtle differences more effectively. Additionally, it exposes the model to a broader range of style features with different data distributions, thereby enhancing its generalization capability in unseen domains. The significant performance gains over five adverse-weather scenarios and the Real to Art benchmark demonstrate the superiorities of our method. Our code is available at https://github.com/ZZ2490/SE-COT.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义
- **核心问题**：单域泛化目标检测（Single‑DGOD）仅使用一个源域（如晴天日间图像）训练检测器，要求其泛化到多个未见过的目标域（如雨夜、雾天或艺术风格图像）。现有基于文本提示的方法通常采用**单步提示**（one‑step prompt），一次性地用一句描述估计跨域信息。
- **关键挑战**：真实场景常常是**多种风格的组合**（例如“雨天 + 夜晚”）。单步提示很难有效合成这种多风格融合信息，导致在复杂组合场景下检测性能下降。
- **整体含义**：作者提出“**思维链风格演化**”（Style Evolving along Chain‑of‑Thought），通过由简到繁、由粗到精的逐步文本提示，渐进式地融合和扩展风格信息，使模型在训练中接触更丰富的风格分布，从而提升在未知域的泛化能力。

## 2. 论文提出的方法论
- **核心思想**：利用思维链（Chain‑of‑Thought）引导文本描述从单词 → 短语 → 完整句子的**分层演进**，生成多层次的文本特征，指导视觉风格特征进行渐进式演化。同时解耦内容与风格，避免语义信息丢失。
- **关键技术细节**：
  - **链式思维引导的风格演化（CGSE）**：
    1. 从源域图像生成关键词（如晴天、日间、真实），用 ChatGPT 生成多个词汇表（天气、时间、风格、动作、细节），随机选取单词提取文本特征 \(F^1_t\)。
    2. 用 ChatGPT 将选中单词组合为短语 \(P_r\)（如“Driving down the road on a rainy night”），提取特征并与 \(F^1_t\) 融合得 \(F^2_t\)。
    3. 再补充细节，形成完整句子 \(S_r\)，提取特征并与 \(F^2_t\) 融合得 \(F^3_t\)。
    4. 利用源域第一层视觉特征 \(F_s\)，通过 AdaIN 形式学习一对可学习参数 \(\mu_t, \sigma_t\)，使得风格迁移后的特征 \(F_i = \sigma_t F'_s + \mu_t\) 与 \(F^3_t\) 的余弦相似度最大化（最小化一致性损失 \(L_{tc}\)）。这些参数随后用于在线训练中的风格迁移。
  - **风格解缠模块（SDM）**：用独立的特征提取器从第一层特征中解耦出风格特征 \(F_s\) 和内容特征 \(F_c\)。通过对比损失 \(L_d\) 强制两者差异最大化，并用源域文本特征 \(F_{st}\) 与 \(F_s\) 的一致性损失 \(L_{sc}\) 约束风格解缠。
  - **类特定原型聚类模块（CPCM）**：在高维特征上通过 2‑范数归一化、卷积和 SoftMax 计算像素对 K 个（=类别数）原型的软分配概率，计算加权残差，经全连接层重塑后与输入特征拼接卷积，得到原型增强内容特征 \(F_p\)，并用下采样后的 \(F_p\) 监督内容特征（\(L_{gc}\)）。该模块增强类别语义，并辅助解缠。
  - **训练流程**：先独立训练风格演化参数（多次重复），再在检测训练中冻结风格参数，随机选取一组 \(\mu_t, \sigma_t\) 对解耦的风格特征进行迁移，融合增强后的内容特征，送入后续骨干网络和 RPN。
- **公式说明**（文字描述）：
  - 文本特征逐步融合：\(F^1_t = \sum E_{text}(W_{ir})\)，\(F^2_t = E_{text}(P_r) + F^1_t\)，\(F^3_t = E_{text}(S_r) + F^2_t\)。
  - 风格迁移与损失：\(F_i = \sigma_t \frac{F_s - \mu(F_s)}{\sigma(F_s)} + \mu_t\)，\(L_{tc} = 1 - \text{sim}(F_i, F^3_t)\)。
  - 解耦损失：对比损失 \(L_d = -\log\frac{\exp(\text{sim}(F_1,F_s)/\tau)}{\sum_{j=0}^1 \exp(\text{sim}(F_1,P[j])/\tau)}\)（\(P=[F_s,F_c]\)），风格一致性 \(L_{sc}=1-\text{sim}(F_s,F_{st})\)，内容原型一致性 \(L_{gc}=1-\text{sim}(\text{Down}(F_p),F_c)\)。

## 3. 实验设计
- **数据集 / 场景**：
  - **多样化驾驶天气场景**：源域为日间晴天（19,395张训练图像），四个目标域为 Clear Night (26,158)、Dusk Rainy (3,501)、Night Rainy (2,494)、Day Foggy (3,775)，共7类（公交、自行车、汽车、摩托车、行人、骑手、卡车）。
  - **从现实到艺术泛化基准**：训练集 PASCAL VOC 2007+2012，测试集 Clipart1k (20类)、Watercolor2k (6类)、Comic2k (6类)。
- **对比方法**：
  - Baseline：Faster R‑CNN (ResNet‑101)。
  - 域泛化/单域泛化方法：SW、IBN‑Net、IterNorm、ISW、S‑DGOD、C‑Gap、PDOC、UFR、DIV。
  - 本文方法在不同骨干网络（ResNet‑50、ResNet‑101、Swin‑Transformer）上评估。
- **评价指标**：mAP@IoU=0.5。

## 4. 资源与算力
- 训练硬件：**单张 NVIDIA 3090 GPU**。
- 风格演化阶段使用 SGD 优化器，学习率 1.0，动量 0.9，权重衰减 0.0005；检测训练阶段 batch size 为 2。
- 论文**未报告具体训练总时长**，也未提及多 GPU 或分布式训练。

## 5. 实验数量与充分性
- **实验组数大致统计**：
  - 主结果表 Table 1（多种方法 × 多个目标天气域，含不同骨干）。
  - 艺术泛化结果 Table 2（VOC→三个艺术域）。
  - 每类结果 Table 3（Day Foggy）、Table 4（Dusk Rainy）、Table 5（VOC→Comic）。
  - 消融实验 Table 6（逐步添加各模块，并对比 one‑step prompt）。
  - 思维链层级分析 Figure 6（不同层级的影响）。
  - 可视化分析 Figure 4、Figure 5（热力图和检测结果对比）。
- **充分性与公平性**：
  - 覆盖了**五个天气域 + 三个艺术域**，多骨干验证，与多个最新方法（含未发表的同期工作如 DIV、PDOC 等）对比，消融实验完整，因此实验较为充分。
  - 对比方法均基于 Faster R‑CNN 和相同的数据划分，指标统一，公平性较高。
  - 但模型的泛化仅在同一类别空间下验证，未讨论类别不一致或开集条件下的效果。

## 6. 论文的主要结论与发现
- 提出的**思维链风格演化方法**在多个未知域（恶劣天气、艺术风格）上均显著优于单步提示方法和现有单域泛化检测器。
- 渐进的风格演化使模型能接触更多样化的数据分布，逐步学习并适应风格间的细微差异，从而增强泛化能力。
- 风格解缠与类特定原型能有效保留语义信息，避免风格迁移带来的灾难性语义损失。

## 7. 优点：方法或实验设计上的亮点
- **新颖的思维链风格演化**：将语言模型的多步推理引入视觉风格模拟，比单步提示更细腻地组合多种风格。
- **与视觉‑语言模型的有机关联**：利用 CLIP 文本编码器与 ChatGPT 生成描述，巧妙地桥接视觉与语言。
- **风格‑内容解缠与原型增强**：设计了对齐约束的对比学习和原型聚类，保真了物体类别信息。
- **实验扎实**：跨多个域（天气 + 艺术）、多骨干、细粒度类目分析，充分验证了方法有效性和组件贡献。
- **开源代码**：有利于复现和后续研究。

## 8. 不足与局限
- **依赖外部大语言模型**：风格演化严重依赖 ChatGPT 生成描述，可能引入语言模型的偏差或不可控的生成质量。
- **词汇表与提示设计的先验性**：词汇表划分和提示模板需人工设计，泛化到全新风格（如医学图像、卫星图等）时可能需重新定制。
- **计算开销未明**：虽声称单卡可用，但未给出明确训练时间，难以评估实际效率。
- **类别闭集假设**：仅在同一类别空间进行跨域泛化，未涉及开放词汇或新类别场景。
- **真实风格保真度未知**：风格演化基于文本生成，生成的风格分布与真实目标域分布之间的差距未进行定量评估。
- **仅限图像域**：未探索在视频或其他模态上的拓展。

（完）
