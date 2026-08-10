---
title: "Search and Detect: Training-Free Long Tail Object Detection via Web-Image Retrieval"
title_zh: 搜索与检测：基于网页图像检索的免训练长尾目标检测
authors: "Sidhu, Mankeerat, Chopra, Hetarth, Blume, Ansel, Kim, Jeonghwan, Reddy, Revanth Gangi, Ji, Heng"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Sidhu_Search_and_Detect_Training-Free_Long_Tail_Object_Detection_via_Web-Image_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 9.0
evidence: SearchDet：无需训练的尾部长尾目标检测，通过网页图像检索提升开放词汇检测
tldr: "针对长尾和开放词汇目标检测中尾部类别标注稀缺的问题，本文提出无需训练的SearchDet框架。通过检索网页上的正负样本图像并嵌入，计算加权查询以检测所需概念。在ODinW和LVIS上分别提升16.81%和59.85% mAP，显著超越GroundingDINO等模型。该方法简单稳定，展示了基于检索范例的检测范式在消除对人工标注依赖方面的潜力。"
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-sidhu-search-and-detect-training-free-long-tail-object-detection-via-web-image-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 836, \"height\": 767, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-sidhu-search-and-detect-training-free-long-tail-object-detection-via-web-image-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1815, \"height\": 1260, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-sidhu-search-and-detect-training-free-long-tail-object-detection-via-web-image-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 691, \"height\": 708, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-sidhu-search-and-detect-training-free-long-tail-object-detection-via-web-image-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 905, \"height\": 574, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-sidhu-search-and-detect-training-free-long-tail-object-detection-via-web-image-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 642, \"height\": 538, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-sidhu-search-and-detect-training-free-long-tail-object-detection-via-web-image-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1582, \"height\": 381, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-sidhu-search-and-detect-training-free-long-tail-object-detection-via-web-image-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 713, \"height\": 601, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-sidhu-search-and-detect-training-free-long-tail-object-detection-via-web-image-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 790, \"height\": 107, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-sidhu-search-and-detect-training-free-long-tail-object-detection-via-web-image-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 749, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-sidhu-search-and-detect-training-free-long-tail-object-detection-via-web-image-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 874, \"height\": 272, \"label\": \"Table\"}]"
motivation: 长尾分布导致尾部类别检测性能差，现有方法依赖大量标注数据或复杂训练。
method: 提出SearchDet，通过检索网页正负例图像并嵌入为加权查询实现免训练检测。
result: "在ODinW和LVIS上mAP分别提升16.81%和59.85%，显著优于强基线。"
conclusion: 基于网页检索的免训练检测为开放词汇和长尾检测提供了高效新途径。
---

## Abstract
In this paper, we introduce SearchDet, a training-free long-tail object detection framework that significantly enhances open-vocabulary object detection performance. SearchDet retrieves a set of positive and negative images of an object to ground, embeds these images, and computes an input image--weighted query which is used to detect the desired concept in the image. Our proposed method is simple and training-free, yet achieves over 16.81% mAP improvement on ODinW and 59.85% mAP improvement on LVIS compared to state-of-the-art models such as GroundingDINO. We further show that our approach of basing object detection on a set of Web-retrieved exemplars is stable with respect to variations in the exemplars, suggesting a path towards eliminating costly data annotation and training procedures.

---

## 论文详细总结（自动生成）

# 详细总结

## 1. 研究动机与核心问题
- **核心问题**：在开放词汇目标检测中，类别分布呈长尾形态，尾部（罕见）类别标注数据稀缺，导致现有模型性能严重不足。
- **背景**：当前主流方法（如 GroundingDINO、GLIP）依赖大规模预训练或针对特定任务的微调，训练成本高昂，且难以覆盖所有长尾概念。
- **整体含义**：提出一种无需训练的推理阶段框架，利用网页作为不断扩展的外部记忆，通过检索图像范例直接进行目标检测，从而绕过昂贵的数据标注和重复训练，显著提升长尾类别的检测精度。

## 2. 方法论
### 2.1 核心思想
将目标检测转化为一个基于范例的匹配问题：对每个待检测类别，从网络检索若干正、负示例图像，提取视觉嵌入，通过注意力机制生成一个加权查询向量，再结合 SAM 区域提议和相似性热图实现无训练的精准定位。

### 2.2 关键技术细节
- **正负范例检索**  
  使用 Google 搜索标签名称获取 10 张正支持图像；利用大语言模型（Phi‑3‑mini）自动生成负概念词（如“冲浪板”的负概念为“海浪”“沙滩”），并同样检索 10 张负支持图像。所有图像经 DINOv2 编码为嵌入向量。

- **注意力加权查询生成**  
  对输入图像（查询嵌入 \(q\)）与正、负嵌入集合分别计算余弦相似度，经 softmax 得到注意力权重，再分别对正、负嵌入加权求和，最终得到调整后的查询嵌入：  
  \[
  q_{\text{adjusted}} = \text{加权正嵌入和} - \text{加权负嵌入和}
  \]
  该机制可增强对象特有特征并抑制背景或干扰物。

- **SAM 区域提议与频率自适应阈值**  
  利用 SAM（Segment Anything）生成图像中所有可能的物体掩码。计算每个掩码的嵌入（DINOv2 CLS token）与调整后查询嵌入的欧氏距离。引入一种频率自适应阈值算法（算法1）：
  * 将所有掩码‑查询距离排序后等距分箱，若某掩码在单个箱中出现频率超过 80%，则选为候选掩码。
  * 利用各查询嵌入对之间的欧氏距离构建参考分布，若候选掩码的平均距离偏离参考分布均值超过 3 个标准差，则拒绝该掩码，从而降低误检。

- **热图生成与联合定位**  
  独立计算输入图像补丁特征与查询嵌入的余弦相似度，生成二值化热图（阈值 50）。最后取 SAM 筛选出的掩码与热图的交集，输出最终检测框，实现掩码边界不精确时的互补。

## 3. 实验设计
- **数据集与基准**  
  - COCO val2017（80 类）  
  - LVIS minival v1.0（1203 类，分 frequent、common、rare）  
  - ODinW（35 类）  
  - Roboflow‑100 验证集  
  - 少样本设置：COCO 2014（10‑shot）

- **评估指标**：mAP（IoU=0.5），少样本实验也使用 mAP。

- **对比方法**  
  - 开放词汇检测：GLIP‑L、DINOv、GroundingDINO‑L、T‑Rex2（文本提示与视觉提示）  
  - 少样本检测：Meta‑RCNN、FSCE、CrossTransformer、DE‑ViT 等十余种方法。

## 4. 资源与算力
- **训练阶段**：方法完全免训练，无训练算力消耗。
- **推理阶段**：使用单张 NVIDIA‑V100 GPU。  
  单张图像总耗时约 3.58 秒，其中图像下载 2.9 秒、SAM 分割 2.5 秒（并行）；距离计算与阈值处理 0.57 秒，热图生成 0.68 秒（并行）。  
  （若同一查询已被缓存，图像下载时间可省略。）

## 5. 实验数量与充分性
- **实验组数**：  
  - 4 个常用长尾/开放词汇检测基准上的主实验对比（表1）  
  - 少样本 COCO 检测对比（表2）  
  - 支持图像数量变化的稳定性测试（表3）  
  - 检索图像相似度稳定性分析（图5）  
  - 标签描述粒度影响实验（图4）  
  - 3 项关键消融实验（仅正例、无热图细化、均值池化）（表4）  
  - 推理时间分解（表5）
- **充分性与公平性**：实验覆盖多个标准基准，对比方法全面，且消融实验清晰验证了负例、注意力加权和热图组件的贡献。所有对比均在相同输入数据和评测协议下进行，具有较强公平性。但未对检索间隔、图像分辨率变化等做详细测试。

## 6. 主要结论与发现
- SearchDet 在 ODinW 上较 GroundingDINO 提升 16.81% mAP，在 LVIS 上提升 59.85% mAP，在 Roboflow‑100 上提升尤为显著（最高 236.27%）。
- 在 LVIS 的罕见（rare）子集上大幅超越所有训练型模型，证明了网页检索对长尾概念的有效性。
- 仅凭 10 张网络图像即可实现稳健检测，即使只用 1 张支持图像也能获得 49.70 mAP，且性能随图像数量稳步增长。
- 正、负图像嵌入在不同日期的检索中保持高度相似，说明方法对网络动态变化具有鲁棒性。

## 7. 优点
- **完全免训练**：无需微调或持续预训练，直接利用预训练 DINOv2 和 SAM，部署成本低。
- **创新性地利用网页作为动态外部记忆**：用检索代替参数记忆，天然适应新类别，尤其适合长尾目标。
- **负例与注意力机制**：通过 LLM 生成负查询并采用软加权，有效抑制背景干扰，提高查询精度。
- **自适应阈值算法**：频率驱动的掩码筛选机制结合统计验证，减少固定阈值或固定数量带来的误检。
- **热图与 SAM 互补**：弥补了 SAM 边界不完整或遗漏的问题，提升检测完整性。
- **强实证结果**：在多个长尾基准上取得大幅领先，特别是稀有类检测，体现了方法的实用价值。

## 8. 不足与局限
- **推理速度较慢**：单图 3.5 秒，瓶颈在图像下载和 SAM 分割，不利于实时应用。
- **对外部服务依赖性强**：依赖 Google 搜索和 LLM，可能受网络环境、检索质量及版权限制；负类生成质量直接影响性能。
- **在常见类上的表现仍然弱于训练模型**：LVIS frequent/common 子集上不及 T‑Rex2 等，反映出检索特征对分布内高频类别优势有限。
- **实验覆盖的局限性**：未与基于检索的无需训练方法（如 REACT）直接比较；未分析不同 LLM 或搜索引擎的影响；缺少大规模开放世界场景的测试。
- **潜在的数据泄漏风险**：检索图像可能与测试集存在重叠，文中未做脱漏分析，可能高估性能。
- **透明度与可复现性**：虽称代码公开，但依赖在线搜索引擎，检索结果随时间变化，难以完全复现。

（完）
