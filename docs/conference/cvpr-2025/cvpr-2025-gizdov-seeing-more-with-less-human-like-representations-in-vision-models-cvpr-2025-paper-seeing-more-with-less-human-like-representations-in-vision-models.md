---
title: "Seeing More with Less: Human-like Representations in Vision Models"
title_zh: Seeing More with Less：视觉模型中的人类化表示
authors: "Gizdov, Andrey, Ullman, Shimon, Harari, Daniel"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Gizdov_Seeing_More_with_Less_Human-like_Representations_in_Vision_Models_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 4.0
evidence: 将中央窝采样应用于MDETR等Transformer模型，改善像素预算下的目标检测
tldr: "受人类视觉中央窝机制启发，本文提出对大型多模态模型（如MDETR、BLIP2）使用可变分辨率的中央窝采样方法，在有限像素预算下提升视觉任务效率。实验表明，在GQA、SEED-Bench和VQAv2等数据集上，目标检测和问答准确率比均匀采样最高提升2.7%。该方法表明无需均匀高分辨率处理，可通过仿生采样实现更高效的视觉信息处理，为模型设计提供了新思路。"
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-gizdov-seeing-more-with-less-human-like-representations-in-vision-models-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1793, \"height\": 657, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-gizdov-seeing-more-with-less-human-like-representations-in-vision-models-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1769, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-gizdov-seeing-more-with-less-human-like-representations-in-vision-models-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 864, \"height\": 683, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-gizdov-seeing-more-with-less-human-like-representations-in-vision-models-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 861, \"height\": 931, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-gizdov-seeing-more-with-less-human-like-representations-in-vision-models-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 854, \"height\": 1303, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-gizdov-seeing-more-with-less-human-like-representations-in-vision-models-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1762, \"height\": 820, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-gizdov-seeing-more-with-less-human-like-representations-in-vision-models-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 913, \"height\": 338, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-gizdov-seeing-more-with-less-human-like-representations-in-vision-models-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 720, \"height\": 337, \"label\": \"Table\"}]"
motivation: 现有大型多模态模型均匀处理全部视野，导致非关键区域处理精度冗余，效率低下。
method: 受中央窝视觉启发，对现有Transformer架构应用可变分辨率采样方法。
result: "在GQA等视觉任务中目标检测和问答准确率提升高达2.7%。"
conclusion: 中央窝采样在减少像素开销的同时提高了检测性能，验证了仿生设计的有效性。
---

## Abstract
Large multimodal models (LMMs) typically process visual inputs with uniform resolution across the entire field of view, leading to inefficiencies when non-critical image regions are processed as precisely as key areas. Inspired by the human visual system's foveated approach, we apply a sampling method to leading architectures such as MDETR, BLIP2, InstructBLIP, LLaVA, and ViLT, and evaluate their performance with variable (foveated) resolution inputs. Results show that foveated sampling boosts accuracy in visual tasks like question answering and object detection under tight pixel budgets, improving performance by up to 2.7% on the GQA dataset, 2.1% on SEED-Bench, and 2.0% on VQAv2 compared to uniform sampling. Furthermore, we show that indiscriminate resolution increases yield diminishing returns, with models achieving up to 80% of their full capability using just 3% of the pixels, even on complex tasks. Foveated sampling prompts more human-like processing within models, such as neuronal selectivity and globally acting self-attention in vision transformers. This paper provides a foundational analysis of foveated sampling's impact on existing models, suggesting that more efficient architectural adaptations, mimicking human visual processing, are a promising research venue for the community. Potential applications of our findings center low power minimal bandwidth devices (such as UAVs and edge devices), where compact and efficient vision is critical.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究动机**：当前大型多模态模型（LMMs）在处理视觉输入时对整个视野采用统一分辨率，导致非关键区域与关键区域同样精细，造成计算资源浪费，尤其在低带宽边缘设备（如无人机）上不实用。
- **背景与灵感**：人类视觉系统采用中央窝（foveation）机制，仅在注视中心高分辨率，周边逐渐降低，从而以少量光感受器实现高效感知。论文试图考察在现有 LMM 中引入仿人可变分辨率采样的效果。
- **核心问题**：
  1. 从信息论角度，可变分辨率采样能否在有限像素预算下提升模型性能？
  2. 提高图像分辨率是否存在边际收益递减？
  3. 可变采样是否能在模型中诱导出更“人类化”的表征（如注意力机制和神经元选择性）？

## 2. 论文提出的方法论

- **核心思想**：在保持总采样点数（像素数）相同的前提下，比较两种采样方式：可变（中央窝）采样与均匀采样，以此揭示信息分布方式对模型性能的影响，而非信息总量。
- **关键技术细节**：
  - 定义采样映射 \(S: [W]\times[H]\to\{0,1\}\)，总采样点数 \(N\)。
  - 分别生成可变采样映射 \(S_{var}\)（中心高密度，随离心率线性降低）和均匀采样映射 \(S_{uni}\)（对数极坐标下等密度），满足 \(N\) 相等，构成“信息匹配图像对”。
  - 采样后的稀疏像素经双线性插值恢复到原始空间尺寸，供现有架构直接处理，**不改动模型结构**。
  - 可变采样的空间分布依据 Wilson & Bergen 以及 Poggio 等提出的人类视觉模型。
  - 注视点默认选在图像中心，并对角落注视点做了消融实验。
- **涉及模型**：包括 MDETR、BLIP2、InstructBLIP、LLaVA、ViLT（VQA）；以及目标检测所用 DETR、Mask-RCNN。为研究学习到的表征，还对 DETR（及 ResNet101 骨干）进行了从头训练。

## 3. 实验设计

- **数据集与 Benchmarks**：
  - 视觉问答（VQA）：VQAv2，GQA，SEED-Bench。
  - 目标检测：COCO。
- **对比方法**：
  - **基线**：原始全分辨率图像。
  - **均匀采样**：在总采样密度为 3%（和 10% 等）下的均匀稀疏采样 + 插值。
  - **可变采样（中央窝）**：相同采样密度，中心高密度、周边低密度。
- **训练范式**：
  - 多数 LMMs 只评估，未重新训练（直接使用预训练权重），仅在输入图像层面做变换。
  - DETR 及 MDETR 则分别使用 3% 采样密度（可变的/均匀的）**从头训练**，包括骨干网络的预训练。

## 4. 资源与算力

- 论文未明确提及使用的 GPU 型号、数量、训练时长等具体算力信息。仅说明因模型规模较大而未对多数 LMM 进行训练，只评估了预训练模型；对于 MDETR 及其骨干网络则进行了训练，但未给出硬件配置细节。

## 5. 实验数量与充分性

- **实验组数**：
  - VQA 任务上，在 VQAv2、GQA、SEED-Bench 三个数据集上测试了 ViLT、MDETR、BLIP2、InstructBLIP、LLaVA 等模型，对比全分辨率、3% 均匀、3% 可变三种条件。
  - 对采样密度进行了从 3% 到 100% 的**扩展分析**（如 LLaVA 和 MDETR 在 VQAv2、GQA 上的性能曲线）。
  - 为排除注视点偏差，进行了**角落注视点消融实验**（MDETR 在 GQA 上）。
  - 目标检测任务上，通过 COCO 的“高阶分辨率包含度分箱”实验和等采样点数控制实验，验证可变采样的优势与注视点位置无关。
  - 对 MDETR 的可解释性分析：注意力距离、CNN 神经元对不同分辨率的选择性等。
- **充分性与公平性**：
  - 实验设计较为全面，覆盖多种模型架构、数据集、采样密度以及消融设置，信息匹配置保证了比较公平。
  - 但由于大多数 LMM 未在可变采样图像上重新训练，仅做推理评估，可能会低估可变采样的潜力，同时也避免了因训练带来的额外偏差。

## 6. 论文的主要结论与发现

- 在同等像素预算下，可变（中央窝）采样一致优于均匀采样：
  - GQA 上最高提升 **2.7%** ，SEED-Bench 上 **2.1%** ，VQAv2 上 **2.0%**（均在 3% 采样密度）。
  - 目标检测（COCO）上可变采样比均匀采样提升约 **2.2%**（AP/AR）。
- 分辨率提升存在**显著边际收益递减**：模型仅使用 **3% 的像素** 即可达到全分辨率约 **80% 的性能**，复杂任务亦如此。
- 可变采样促使模型学习到更“人类化”的内部表征：
  - **Transformer 的全局自注意力增强**：可变采样训练的模型在中心区域和周边区域均表现出更大的注意力距离，促进中心-周边信息融合。
  - **CNN 神经元出现分辨率选择性**：深层神经元有的对高分辨率区域响应强，有的对低分辨率区域响应强，类似于人脑的功能特化。
- 注视点位置的影响较小：角落注视点同样优于均匀采样，优势不依赖于图像中心偏好。

## 7. 优点

- **信息论驱动的公平比较**：通过“信息匹配图像”设计，剥离了信息总量变化的影响，仅考察信息分布的作用。
- **不改动架构**：在原有模型结构上直接应用可变采样，结论可直接适用于现有 LMM，推动后续架构自适应研究。
- **多维度验证**：涵盖 VQA 与目标检测任务，多个主流模型和数据集，且包含消融与控制实验，结果稳健。
- **可解释性分析**：深入探究注意力距离和神经元选择性，为理解可变采样如何影响模型内部表征提供了机制性解释。
- **实际应用导向**：论证了在极小带宽下高效视觉的可能性，对边缘计算、低功耗设备有启发意义。

## 8. 不足与局限

- **单一注视点**：仅使用一个注视点（通常为中心），而人类通常需多次注视，多注视点策略未探索，可能低估了可变采样的能力上限。
- **未进行架构适配训练**：大多数 LMM 是直接使用全分辨率预训练权重在可变采样图像上评测，性能可能未充分释放；仅 MDETR 进行了重训练。
- **注视点选择简单**：固定中心或角落，未采用显著性驱动的动态注视点选择，实际应用中需要更智能的注视点策略。
- **未涉及效率的硬件实测**：虽提出带宽节省的理论依据，但未在真实边缘设备上测量延迟、功耗等计算效率，也未定制可变分辨率处理算子。
- **可解释性分析范围有限**：仅对 MDETR 的 Transformer 和 ResNet101 做了部分分析，其他模型（BLIP2、LLaVA 等）的内部表征变化未涉及。
- **训练细节与算力信息缺失**：未提供训练所需 GPU、时间等资源信息，复现性受影响。
- **可能存在数据集偏向**：尽管通过角落注视点消融说明优势不单纯由摄影师中心构图造成，但 COCO、VQA 等数据集本身的目标分布可能仍对中心注视有一定倾向，需在更非中心分布的数据上进一步验证。

（完）
