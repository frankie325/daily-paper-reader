---
title: "ROD-MLLM: Towards More Reliable Object Detection in Multimodal Large Language Models"
title_zh: ROD-MLLM：面向多模态大语言模型中更可靠的目标检测
authors: "Yin, Heng, Ren, Yuqiang, Yan, Ke, Ding, Shouhong, Hao, Yongtao"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Yin_ROD-MLLM_Towards_More_Reliable_Object_Detection_in_Multimodal_Large_Language_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 9.0
evidence: MLLM中基于查询定位的可靠目标检测
tldr: 现有多模态大语言模型只能检测图片中存在的物体，无法拒绝不存在的目标，导致不可靠预测。本文提出ROD-MLLM，通过查询式定位机制提取底层特征，并对齐全局与物体级视觉信息至文本空间，利用大语言模型进行高层推理和定位决策，实现可拒绝虚构目标的可靠检测，拓展了MLLM的实用性。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yin-rod-mllm-towards-more-reliable-object-detection-in-multimodal-large-language-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 842, \"height\": 773, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yin-rod-mllm-towards-more-reliable-object-detection-in-multimodal-large-language-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1756, \"height\": 738, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yin-rod-mllm-towards-more-reliable-object-detection-in-multimodal-large-language-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 864, \"height\": 225, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yin-rod-mllm-towards-more-reliable-object-detection-in-multimodal-large-language-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 856, \"height\": 680, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yin-rod-mllm-towards-more-reliable-object-detection-in-multimodal-large-language-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 363, \"height\": 225, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yin-rod-mllm-towards-more-reliable-object-detection-in-multimodal-large-language-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1530, \"height\": 759, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yin-rod-mllm-towards-more-reliable-object-detection-in-multimodal-large-language-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 863, \"height\": 699, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yin-rod-mllm-towards-more-reliable-object-detection-in-multimodal-large-language-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 867, \"height\": 185, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yin-rod-mllm-towards-more-reliable-object-detection-in-multimodal-large-language-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1497, \"height\": 596, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yin-rod-mllm-towards-more-reliable-object-detection-in-multimodal-large-language-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1575, \"height\": 455, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yin-rod-mllm-towards-more-reliable-object-detection-in-multimodal-large-language-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1589, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yin-rod-mllm-towards-more-reliable-object-detection-in-multimodal-large-language-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 875, \"height\": 310, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yin-rod-mllm-towards-more-reliable-object-detection-in-multimodal-large-language-cvpr-2025-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 878, \"height\": 622, \"label\": \"Table\"}]"
motivation: MLLM在目标检测中无法拒绝不存在物体，预测不可靠。
method: 提出查询式定位机制，对齐视觉与文本信息，利用LLM决策。
result: 实现了可拒绝虚构目标的高可靠目标检测性能。
conclusion: ROD-MLLM提升了MLLM在检测任务中的可靠性和实用性。
---

## Abstract
Multimodal large language models (MLLMs) have demonstrated strong language understanding and generation capabilities, excelling in visual tasks like referring and grounding. However, due to task type limitations and dataset scarcity, existing MLLMs only ground objects present in images and cannot reject non-existent objects effectively, resulting in unreliable predictions. In this paper, we introduce ROD-MLLM, a novel MLLM for Reliable Object Detection using free-form language. We propose a query-based localization mechanism to extract low-level object features. By aligning global and object-level visual information with text space, we leverage the large language model (LLM) for high-level comprehension and final localization decisions, overcoming the language understanding limitations of normal detectors. To enhance language-based object detection, we design an automated data annotation pipeline and construct the dataset ROD. This pipeline uses the referring capabilities of existing MLLMs and chain-of-thought techniques to generate diverse expressions corresponding to zero or multiple objects, addressing the shortage of training data. Experiments across various tasks, including referring, grounding, and language-based object detection, show that ROD-MLLM achieves state-of the-art performance among MLLMs. Notably, in language-based object detection, our model achieves +13.7 AP improvement on D3 benchmark over existing MLLMs and surpasses most specialized detection models, especially in scenarios requiring complex language understanding.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）
*   **核心问题**：当前多模态大语言模型（MLLMs）在视觉定位（如指代表达理解）任务上表现突出，但**只能检测图像中实际存在的物体，无法有效拒绝不存在的目标**。当用户用自由形式的语言描述零个、一个或多个目标时，模型容易产生错误关联（如漏检、误检），导致预测不可靠。
*   **任务定位**：论文将这一新任务称为**基于语言的目标检测（Language-based Object Detection）**，其要求模型根据自然语言描述定位图像中所有符合条件的物体（可以为零个、一个或多个），并能拒绝不符合描述的物体。
*   **现有局限**：
    *   一般的指代表达理解（REC）任务假设描述对应唯一物体，忽略多目标或目标缺失场景。
    *   开放词汇检测（OVD）模型仅擅长处理简单类别短语，对复杂语义理解能力不足。
    *   缺乏专门针对该任务的大规模训练数据集。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式/算法流程
*   **核心思想**：将语言目标检测**解耦为底层定位和高层理解**，利用开放词汇检测器作为底层定位器提取候选对象，再由大语言模型（LLM）结合全局与局部视觉信息进行高级推理，做出最终定位决策（含拒绝不存在物体）。
*   **关键技术细节**：
    *   **基于查询的定位机制（Query-based Localization）**：
        *   从用户查询中提取目标短语（N-gram），作为文本查询输入底层定位器（如 OWLv2）。
        *   底层定位器输出候选框集合 \( B = L(I, O_{query}, O_{common}) \)，\( O_{common} \) 为 COCO 常用类别，用于无查询对象时的一般感知增强。
    *   **多粒度视觉输入**：
        *   全局图像嵌入：通过视觉编码器（CLIP ViT-L）提取多层特征，取倒数第二层经 MLP 投影得到。
        *   区域特征：对候选框构建三层特征金字塔，使用 \( 8\times8 \) ROI Align 提取区域特征，再划分为 \( 2\times2 \) 小块，每块经 MLP 映射为一个文本 token，使 LLM 获得更细粒度局部信息。
        *   为每个区域分配一个**区域锚点 token `<a_i>`**，用于聚合区域信息并在文本中引用。
    *   **高层理解**：
        *   采用 Vicuna-7B 作为 LLM，接收多粒度视觉 tokens 与用户指令，判断每个区域是否符合描述，输出定位结果（单个/多个框或 `None`）。
        *   **置信度计算**：输出区域锚点 token 时，将其 logits 经 softmax 归一化作为该预测框的置信度 \( C_{t^*_m} \)。
    *   **统一任务格式**：将指代表达、接地、检测、区域描述等任务统一为特殊标签格式（`<p>` `</p>` 包裹描述，`<box>[]</box>` 包裹锚点 token，无目标时输出 `None`）。
    *   **自动化数据标注流水线（ROD 数据集）**：
        *   **基于检测数据集**（Objects365）：先生成目标描述（用 InternVL2-76B），再通过思维链（COT）将描述分解为多个条件，利用 MLLM 判断每个物体是否满足所有条件，生成正/负样本。
        *   **基于接地数据集**（Flickr30k Entities）：将实体短语扩展为含属性、状态、关系的描述性短语；同时生成混淆的缺失目标描述（如负语义、相似但不同关系的物体），增强拒绝能力。

### 3. 实验设计：使用了哪些数据集/场景，它的 benchmark 是什么，对比了哪些方法
*   **评估基准**：
    *   **基于语言的目标检测**：OmniLabel、\( D^3 \)。
    *   **指代表达理解（REC）**：RefCOCO/+/g。
    *   **泛化指代表达理解（GREC）**：gRefCOCO。
    *   **区域描述生成**：RefCOCOg、Visual Genome。
*   **对比方法**：
    *   专门化检测/接地模型：RegionCLIP、OWLv2、GLIP、Grounding DINO、FIBER、UNINEXT、MDETR 等。
    *   通用 MLLMs：InternVL2（8B/76B）、Griffon（13B）、Groma（7B）、Ferret、Shikra、Pink、Qwen-VL 等。
*   **评估指标**：
    *   OmniLabel：AP-d（描述平均精度），细分为 AP-dP、AP-dS/M/L（不同长度描述）。
    *   \( D^3 \)：Pres（存在描述）、Abs（缺失描述）、Full 综合 AP。
    *   REC：Acc@0.5。
    *   GREC：Pr@(F1=1, IoU≥0.5) 及 N-acc（拒绝不存在指代的准确率）。
    *   区域描述：METEOR、CIDEr。

### 4. 资源与算力
*   文中未明确提及训练所使用的 **GPU 型号、数量及具体训练时长**。
*   仅给出训练配置：两阶段训练，预训练对齐（2 个 epoch，学习率 1e-4，batch size 128），指令微调（1 个 epoch，相同学习率和 batch size），引入 LoRA（秩 128，alpha 256）。

### 5. 实验数量与充分性
*   **实验组数**：至少包含20+组对比与消融结果，覆盖4大类任务、多项基准。
*   **消融实验**：
    *   不同底层定位器（OWLv2 vs. Grounding DINO-T）。
    *   不同候选框抽取方式（仅常用物体 vs. 仅查询物体 vs. 混合）。
    *   ROD 数据集不同构造来源（仅检测数据、仅接地数据、混合数据）及有无 ROD 的影响。
*   **实验充分性与公平性**：
    *   对比广泛，涵盖专门化模型与通用 MLLMs，参数量也从 7B 至 76B 不等。
    *   零样本评估严格，指标细致（如区分存在/缺失描述、描述长度、F1 精确匹配等）。
    *   消融实验系统验证了各模块的有效性。未发现明显的不公平设计。

### 6. 论文的主要结论与发现
*   ROD-MLLM 能可靠完成基于自由形式语言的目标检测，支持多目标定位与缺失目标拒绝。
*   在 \( D^3 \) 基准上，ROD-MLLM（7B）较现有 MLLMs 提升 **13.7 AP**，并超越多数专用检测模型。
*   在 OmniLabel 上，AP-d 较同尺度 MLLMs 提升 **9.7 点**，尤其在长语句和负样本描述上优势显著。
*   在传统 REC 和 GREC 任务上仍保持领先，证明架构不影响原有接地能力，且在复杂描述理解上超越专用模型。
*   消融实验证明 ROD 数据集、查询定位机制及 LLM 高层推理对性能提升至关重要。

### 7. 优点：方法或实验设计上有哪些亮点
*   **任务创新**：首次在 MLLM 中实现能拒绝不存在物体的可靠检测，填补任务空白。
*   **解耦设计**：底层定位与高层理解分离，既保留专业检测器的精度，又发挥 LLM 的语义理解能力，可灵活替换底层定位器。
*   **多粒度区域表征**：将区域划分为多 token 输入 LLM，为模型提供更丰富的局部信息。
*   **自动化数据流水线**：无需人工成本即可生成包含多目标、零目标及混淆负样本的大规模训练数据（500K 对），且利用 COT 提高标注质量。
*   **评估全面**：覆盖多项接地与检测任务，指标的细粒度（如描述长度、存在/缺失）能深刻反映模型进步。

### 8. 不足与局限：包括实验覆盖、偏差风险、应用限制等
*   **模型规模与算力**：未报告具体训练资源，外部复现存在不确定性。
*   **底层定位器依赖**：虽然可替换，但仍依赖开放词汇检测器的召回能力，若候选框中遗漏目标，LLM 无法弥补。
*   **数据集偏差**：ROD 数据集依赖已有检测/接地数据集的分布，以及 InternVL2 等模型的生成质量，可能存在一定的分布偏差或错误标注。
*   **任务局限**：当前仅处理静态图像中的物体定位，未涉及视频、关系推理等更复杂的时空场景。
*   **效率考量**：多粒度区域 token 增加了 LLM 的输入长度，可能影响推理速度。
*   **对比范围**：虽对比了许多 MLLMs，但未与更庞大的模型（如 GPT-4V）进行直接对比，仅将 InternVL2-76B 置灰标记。

（完）
