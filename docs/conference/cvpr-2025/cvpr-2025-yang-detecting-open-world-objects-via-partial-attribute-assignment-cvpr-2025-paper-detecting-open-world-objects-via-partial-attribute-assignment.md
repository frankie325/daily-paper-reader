---
title: Detecting Open World Objects via Partial Attribute Assignment
title_zh: 通过部分属性分配检测开放世界对象
authors: "Yang, Muli, Goenawan, Gabriel James, Qin, Huaiyuan, Han, Kai, Peng, Xi, Yang, Yanhua, Zhu, Hongyuan"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Yang_Detecting_Open_World_Objects_via_Partial_Attribute_Assignment_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 9.0
evidence: 提出部分属性分配方法用于开放世界目标检测，学习细粒度类别无关属性
tldr: 针对现有视觉基础模型在检测开放世界未知对象时易将其误判为背景的问题，本文提出部分属性分配（PASS）方法，自动从大量属性中选择与优化少量相关属性，以可解释的方式学习细粒度、类别无关的属性表示，从而检测已知和未知对象。实验表明，该方法能有效提升开放世界目标检测性能，减少对训练类别的偏见，增强了模型的泛化能力。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yang-detecting-open-world-objects-via-partial-attribute-assignment-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 867, \"height\": 837, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yang-detecting-open-world-objects-via-partial-attribute-assignment-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1786, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yang-detecting-open-world-objects-via-partial-attribute-assignment-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1726, \"height\": 1487, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yang-detecting-open-world-objects-via-partial-attribute-assignment-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 864, \"height\": 635, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yang-detecting-open-world-objects-via-partial-attribute-assignment-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1811, \"height\": 803, \"label\": \"Table\"}]"
motivation: 现有开放世界目标检测方法依赖概率模型学习目标性，但缺乏对未知对象的可解释检测机制。
method: 提出部分属性分配（PASS），自动选择并优化一个小的相关属性子集，以类别无关方式建模。
result: 能够检测已知和未知对象，减少误分类为背景，性能优于传统方法。
conclusion: PASS以可解释的方式实现了开放世界目标检测，对未知对象具有较强泛化能力。
---

## Abstract
Despite being trained on massive data, today's vision foundation models still fall short in detecting open world objects. Apart from recognizing known objects from training, a successful Open World Object Detection (OWOD) system must also be able to detect unknown objects never seen before, without confusing them with the backgrounds. Unlike prevailing prior works that rely on probability models to learn "objectness", we focus on learning fine-grained, class-agnostic attributes, allowing the detection of both known and unknown objects in an explainable manner. In this paper, we propose Partial Attribute Assignment (PASS), aiming to automatically select and optimize a small, relevant subset of attributes from a large attribute pool. Specifically, we model attribute selection as a Partial Optimal Transport (POT) problem between known visual objects and the attribute pool, in which more relevant attributes signify more transported mass. PASS follows a curriculum schedule that progressively selects and optimizes a targeted subset of attributes during training, promoting stability and accuracy. Our method enjoys end-to-end optimization by minimizing the POT distance and the classification loss on known visual objects, demonstrating high training efficiency and superior OWOD performance among extensive experimental evaluations.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义
- **研究背景**：开放世界目标检测（OWOD）要求模型不仅要识别训练中见过的已知类，还须检测从未见过的未知物体，并将其与背景区分开。现有视觉基础模型尽管在封闭世界上表现优异，但在开放世界中表现不足。
- **核心问题**：现有方法多基于概率模型学习“物体性”（objectness），缺乏可解释性，且容易将背景误判为未知物体。本文认为，通过学习细粒度、类别无关的**属性**（如形状、颜色、功能等自然语言描述），可以同时检测已知和未知物体，且具备更强的可解释性和鲁棒性。
- **整体含义**：如何从大型属性池中自动、高效地筛选出与任务最相关的一小部分属性，并用这些属性来检测开放世界中的物体，是实现可解释 OWOD 的关键挑战。

## 2. 论文提出的方法论
### 2.1 核心思想：部分属性分配 (Partial Attribute Assignment, PASS)
- 将属性选择问题建模为**部分最优传输 (Partial Optimal Transport, POT)** 问题，在已知物体视觉嵌入与属性池嵌入之间进行非完全匹配，传输质量越大的属性越相关。
- 通过**课程学习**策略逐步筛选并优化属性子集，最终得到一个高质量、高覆盖率的精简属性集。
- 所选属性通过可学习的映射矩阵与已知类关联，同时用于检测未知物体。

### 2.2 关键技术细节
- **部分最优传输 (POT) 建模**  
  - 设视觉物体嵌入为 `V ∈ R^{D×M}`，属性嵌入为 `A ∈ R^{D×N}`，经 L2 归一化。  
  - 定义视觉分布 `V`（均匀）和属性分布 `A` 加入冗余率 `α = N/N'`（`N'` 为目标属性数），使属性侧允许运输部分质量。  
  - 求解带有熵正则化的 POT 距离：  
    `d_{POT,ϵ}(V,A;C) = min_{T∈Π(V,A)} ⟨T,C⟩_F - ϵ h(T)`  
    其中 `C` 为余弦距离成本矩阵，`Π` 为弱化的边缘约束（视觉端等式、属性端不等式）。  
  - 通过 Sinkhorn 算法快速求解运输计划 `T`。

- **课程属性选择**  
  - 定义属性 ID 分数 `s_n = (Nα / 1?) ... ` （根据传输质量归一化），表示属性与视觉对象的内部分布相关性。  
  - 分 `η` 个步骤，每一步按比例 `1/α` 保留分数最高的属性，逐步收紧属性集，训练平稳且选择更准。

- **对象类别预测**  
  - 用 ID 分数对选中的属性嵌入 `Â` 进行软加权：`A' = s ⊙ Â`。  
  - 学习映射矩阵 `W ∈ R^{N'×K}`，通过 softmax 计算已知类概率 `p(O_k|v)`。  
  - 损失函数：交叉熵 `L_CE` + POT 距离 `λ d_{POT,ϵ}` 端到端优化。

- **推理阶段**  
  - 未知物体得分 `p_{unk} = p_ID · p_OOD`，其中 `p_ID` 为视觉嵌入与属性最大相似度，`p_OOD` 为 1 减去最大已知类概率。

### 2.3 整体算法流程
1. 初始化 `Â = A`，`ˆN = N`，随机初始化 `W`，设定 `α = (N/N')^{1/η}`。
2. 每轮训练：
   - 求解 POT 获得 `T` 和 `s`。
   - 若达到选择周期，按 `1/α` 比例保留 `Â` 和 `W` 中对应行/列。
   - 计算分类损失，联合损失更新 `Â` 和 `W`。

## 3. 实验设计
- **数据集**：基于真实世界目标检测基准，包含 5 个少样本数据集：
  - Aquatic（水下生物）
  - Aerial（航拍结构）
  - Game（游戏截图形象）
  - Medical（手部 X 光骨骼）
  - Surgery（神经外科手术器械）
- **评估协议**：
  - 每个数据集按常见/不常见类别分为 Task 1 和 Task 2。
  - Task 1：已知（K）为常见类，未知（U）为不常见类，评测 U‑mAP 和 K‑mAP。
  - Task 2：先前已知（PK）+ 新引入已知（CK），评测 PK‑mAP 和 CK‑mAP。
  - 默认 few‑shot 设置为 100 张/类。
- **对比方法**：
  - 零样本基线：BASE‑ZS（通用 prompt）、BASE‑ZS+IN（ImageNet 类名）、BASE‑ZS+LLM（LLM 预测类名）、BASE‑ZS+GT（真实类名，上界）。
  - 少样本基线：BASE‑FS（视觉样例平均嵌入）。
  - 当前 SOTA：FOMO（基于属性选择但需多阶段处理）。
  - 消融实验：去掉 POT 损失、去掉属性选择、去掉 ID 分数重加权。

## 4. 资源与算力
- 论文提到使用**一块 NVIDIA RTX A6000 GPU** 进行实验，但未明确说明训练所需的具体时长或 batch size 等细节。
- 核心计算主要在于 Sinkhorn 求解 POT，效率较高；具体的训练持续时间依赖于数据集大小和 epoch 数（文中未给出，补充材料可能包含）。

## 5. 实验数量与充分性
- **主实验**：在 5 个数据集、2 个任务、2 个 backbone（B/16 和 L/14）上进行了全面对比，总计 **20 个子设置**（5×2×2？实际表格分为 B/16 和 L/14，每个包含 5 个数据集的 Task1 和 Task2），结果非常详细。
- **消融实验**：表 1 在两个代表性数据集上对 POT 损失、属性选择、ID 重加权进行了消融，每个模块的贡献清晰。
- **定性分析**：图 3 给出了各数据集样例的可视化及被激活的 Top 属性，增强了可解释性。
- **额外实验**：文中提到补充材料有不同 few‑shot 数量的结果、更多消融和实现细节。
- **公平性**：所有对比方法基于相同的 backbone 和 few‑shot 设置，评估指标统一，实验设计客观公平。

## 6. 论文的主要结论与发现
- PASS 可以**端到端**地从大型属性池中自动筛选并优化出一小组代表性属性，无需繁琐的多阶段处理。
- 该方法在多个真实世界数据集上均**显著优于当前 SOTA（FOMO）**，尤其在未知物体检测和已知类增量学习上表现出色。
- 最小化 POT 距离能有效对齐视觉与属性模态，大幅提升属性泛化性；课程选择与软重加权进一步稳定训练、提升精度。
- 学习到的属性具有强可解释性，例如能利用“背鳍形状”等细粒度特征检测未知鱼类。

## 7. 优点
- **形式清晰、可解释**：将 OWOD 转化为属性‐视觉匹配问题，利用自然语言属性增强检测的可解释性。
- **端到端优化**：通过 POT 将属性筛选与任务损失统一，避免了传统多阶段方法中的误差累积。
- **课程策略巧妙**：渐进式选择不仅稳定训练，还降低了计算开销（逐步减少属性数量）。
- **实验扎实**：覆盖 5 个真实应用场景，既有定量对比又有定性属性激活展示，说服力强。
- **模块贡献明确**：消融实验清楚证明了 POT 损失、属性选择、ID 重加权各自的价值。

## 8. 不足与局限
- **属性池依赖外部 LLM**：属性质量受限于 GPT‑3.5 生成的描述，若 LLM 不能提供足够区分性的属性，性能可能受限。
- **训练细节未充分公开**：文中未说明具体训练时长、优化器设置等，复现可能需要参考补充材料。
- **少样本设定下的上界比较**：与 GT 属性上界仍有差距，尤其在 Aerial 等复杂场景中 U‑mAP 提升有限（L/14 上 Aerial U‑mAP 为 8.4，而上界为 1.0？此处可能数据有疑，实际应为 1.0 是 GT 的 U‑mAP？表显示 BASE‑ZS+GT 的 U‑mAP 在 Aerial 上为 1.0，奇怪，可能是特定指标表明 GT 零样本效果差，但不影响整体结论）。
- **未知物体检测机制仍较简单**：最终依赖 `p_ID · p_OOD` 的乘积，在极度稀疏或罕见未知物体上可能不够鲁棒。
- **应用范围局限**：实验仅覆盖五个特定领域数据集，未在更通用的 COCO‑OWOD 等基准上验证（文中解释 COCO 基准已趋于饱和，但仍可质疑领域迁移能力）。

（完）
