---
title: Open-World Objectness Modeling Unifies Novel Object Detection
title_zh: 开放世界目标性建模统一新颖对象检测
authors: "Zhang, Shan, Ni, Yao, Du, Jinhao, Xue, Yuan, Torr, Philip, Koniusz, Piotr, van den Hengel, Anton"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Zhang_Open-World_Objectness_Modeling_Unifies_Novel_Object_Detection_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 9.0
evidence: 提出基于变分推断的类别无关目标性度量用于开放世界目标检测
tldr: 针对开放世界目标检测中未知对象常被误分类或过滤为背景的问题，本文提出类别无关的目标性度量，利用变分推断联合建模目标性与类别标签分布。理论分析揭示了传统KL散度失败原因，并提出自适应先验缓解未标注数据不足。实验表明该方法有效减少了已知类别偏见，提升了未知对象检测能力，统一了新颖对象检测的框架。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-open-world-objectness-modeling-unifies-novel-object-detection-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 858, \"height\": 569, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-open-world-objectness-modeling-unifies-novel-object-detection-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1711, \"height\": 677, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-open-world-objectness-modeling-unifies-novel-object-detection-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 861, \"height\": 284, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhang-open-world-objectness-modeling-unifies-novel-object-detection-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 879, \"height\": 414, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-open-world-objectness-modeling-unifies-novel-object-detection-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 874, \"height\": 481, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-open-world-objectness-modeling-unifies-novel-object-detection-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 876, \"height\": 421, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-open-world-objectness-modeling-unifies-novel-object-detection-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1812, \"height\": 721, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhang-open-world-objectness-modeling-unifies-novel-object-detection-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 871, \"height\": 401, \"label\": \"Table\"}]"
motivation: 开放世界检测中未知对象易被误分类或误判为背景，现有概率模型存在偏见。
method: 提出类别无关目标性度量，通过变分推断联合建模目标性与类别分布，并设计自适应先验。
result: 减少对已知类别的偏见，有效检测未知对象，统一新颖对象检测。
conclusion: 该方法为开放世界目标检测提供了理论驱动的解决方案，增强了泛化性。
---

## Abstract
The challenge in open-world object detection, similarly to few- and zero-shot learning, is to generalize beyond the class distribution of the training data. In this paper, we propose a general class-agnostic objectness measure to limit bias toward labeled samples. One issue in open-world detection is that previously unseen objects are often misclassified as known categories or filtered as background by classifiers. To prevent this, we explicitly model the joint distribution of objectness and category labels using variational approximation. However, without sufficient labeled data, minimizing the KL divergence between the estimated posterior and a static normal prior fails to converge. Our theoretical analysis identifies the root cause of this failure and motivates adopting a Gaussian prior with variance dynamically adapted to the estimated posterior as a surrogate. To further reduce misclassification, we introduce an energy-based margin loss that encourages unknown objects to move toward high-density regions of the distribution, thus reducing the uncertainty of unknown detections. Our Open-World OBJectness modeling (OWOBJ) boosts novel object detection, especially in low-data regimes. OWOBJ is a flexible plugin that outperforms baselines in Open-World, Few-Shot, and zero-shot Open-Vocabulary Object Detection.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **背景与动机**  
  开放世界目标检测（Open-World Object Detection, OWOD）要求模型既能识别训练集中已知的类别，又能发现未知/未见类别的物体，并在增量学习中逐步吸收新知识。现有检测器（如Faster R-CNN、DETR）过度依赖固定类别标签，对标注样本存在严重偏见，导致未知物体常被误分类为已知类或当成背景过滤掉，极大限制了在自动驾驶、机器人等真实开放场景中的应用。

- **研究问题**  
  核心挑战在于如何在**标签数据极少**（即低数据体制）的条件下，建立一种通用的、类别无关的“物体性”（objectness）度量，使得检测器能够摆脱已知类别分布的限制，可靠地区分前景物体与背景，并减少未知物体被错误分配到已知类别的现象。

- **整体含义**  
  本文主张**同时建模潜在物体性变量与类别标签的联合分布**，利用变分推断来显式地刻画物体性，从而统一解决OWOD、少样本目标检测（FSOD）和零样本开放词汇目标检测（OVOD）中的新颖物体检测问题。

## 2. 论文提出的方法论

### 2.1 核心思想
- 将物体性视作**隐变量**，通过**变分近似**联合建模物体性分布 \(q_\phi(o|x)\) 和观测数据的类别分布。
- 利用**证据下界（ELBO）** 分解为两项：交叉熵（指导分类器利用物体性伪标签）和KL散度（防止隐空间坍缩）。
- 在低数据条件下，传统KL散度（与固定先验 \(\mathcal{N}(0,1)\) 匹配）因隐变量方差 \(\sigma^2\) 趋近于零而发散。作者从理论上找到了根源，并提出**动态高斯先验** \(\mathcal{N}(0, \sigma^2+\beta^2)\) 来稳定训练。
- 引入**基于能量的间隔损失**，迫使未知物体向分类器高密度区域移动，降低检测不确定性。

### 2.2 关键技术细节

#### 物体性建模模块（Objectness Modeling）
- 将查询嵌入（DETR 的 queries 或 Faster R-CNN 的 proposals）建模为多变量高斯分布 \(\mathcal{N}(\boldsymbol{\mu},\sigma^2\mathbf{I})\)。
- 用**指数移动平均（EMA）** 更新均值 \(\boldsymbol{\mu}\) 和对角协方差 \(\sigma^2\mathbf{I}\)，针对所有查询嵌入计算。
- 对于已知匹配的查询（即确实对应真实物体的查询），通过最小化**马氏距离**来最大化其似然：
  \[
  d_M(\mathbf{q}) = (\mathbf{q}-\boldsymbol{\mu})^\top \Sigma^{-1}(\mathbf{q}-\boldsymbol{\mu})
  \]
  损失项为 \(\mathcal{L}_{\text{obj}} = \sum_{i\in \text{matched}} d_M(\mathbf{q}_i)\)。
- 利用马氏距离生成**物体性分数** \(S_{\text{obj}} = \exp(-d_M(\mathbf{q}))\)，作为未匹配查询（可能是未知物体或背景）的软标签，监督 \(Z+1\) 维分类器中的“未知/背景”维度。
- 动态高斯先验下的KL散度：
  \[
  D_{\text{KL}}(q_\phi(o|x) \| g_\phi(x,\epsilon)) = \log \frac{\sqrt{\sigma^2+\beta^2}}{\sigma} + \frac{\sigma^2+\mu^2}{2(\sigma^2+\beta^2)} - \frac{1}{2}
  \]
  其中 \(\beta\) 控制适应性，避免 \(\log(1/\sigma)\) 发散。

#### 能量间隔损失（Energy-based Margin Loss）
- 已知类别的能量：\(E_k = -\frac{1}{|Q|}\sum_{k\in Q} \log\sum_{i=1}^{Z} e^{f_i^{\text{cls}}(\mathbf{q}_k)}\)。
- 未知/背景维度的能量：\(E_u = -\frac{1}{|\bar{Q}|}\sum_{u\in \bar{Q}} \log \left(Z\cdot e^{f_{Z+1}^{\text{cls}}(\mathbf{q}_u)}\right)\)。
- 损失 \(\mathcal{L}_{\text{energy}} = (E_u - E_k + \delta)_+\)，其中 \(\delta\) 为间隔超参数（默认0.2）。该损失推动未知对象能量升高、已知对象能量降低，减少未知物体被误判为已知类。

#### 架构整合
- 以 D-DETR 为基础管线，保留原有编码器、解码器、边界框回归头和分类头，增加概率物体性预测分支 \(f_{\text{obj}}^{\text{pr}}\)。
- 训练总损失：\(\mathcal{L}_{\text{cls}} + \mathcal{L}_{\text{reg}} + \mathcal{L}_{\text{obj}} + \mathcal{L}_{\text{KL}} + \mathcal{L}_{\text{energy}}\)。

### 2.3 算法流程
1. 提取多尺度特征，通过解码器生成查询嵌入。
2. 匈牙利匹配获得匹配集（已知物体）和未匹配集。
3. 用EMA更新物体性分布参数。
4. 计算马氏距离与物体性分数，生成未匹配查询的软伪标签。
5. 计算所有损失项进行反向传播。

## 3. 实验设计

### 数据集与场景
- **OWOD**：在COCO、PASCAL VOC混合的M-OWODB基准和超级类别分离的S-OWODB基准上进行，共4个增量任务，每个任务新增20个已知类，其余作为未知。
- **FSOD**：COCO 60类作为基类，20类作为新类，在K=1,2,3,5,10,30 shot设置下微调。
- **零样本OVOD**：在OV-LVIS数据集上，用461个常见类和405个频繁类训练，测试稀有类的检测mAP（APr）。

### 对比方法
- OWOD：ORE, UC-OWOD, OCPL, 2B-OCD, OW-DETR, PROB, CAT, MEPU-FS等。
- FSOD：Meta R-CNN, TFA, MPSR, FSCE, KFSOD, TENET, DeFRCN等。
- OVOD：ViLD, OV-DETR, RegionCLIP, MEDet, Detic, OWL-ViT, RO-ViT, CORA等。

## 4. 资源与算力
- 论文正文及附录（所提供的文本）中**未明确提及**GPU型号、数量及训练时长等算力细节。作者仅提到遵循基线的实现细节（学习率、权重衰减、批量大小），但未给出硬件配置。

## 5. 实验数量与充分性

- 共在**三种不同任务设定**（OWOD, FSOD, OVOD）下进行了大量实验：
  - OWOD 部分包含 M-OWODB 和 S-OWODB 两张基准表，覆盖4个增量任务，且与多个现有方法比较未知召回率和已知mAP。
  - 在M-OWODB任务1和2上进行了**详细的消融实验**，逐步移除物体性分数、物体性损失、KL项、能量损失，验证每个组件的有效性。
  - 对动态先验中的 \(\beta\) 值进行了敏感度分析（图4）。
  - 进行了t-SNE可视化（图3）展示嵌入分布变化。
  - FSOD和零样本OVOD各有独立对比表格，证明了方法的通用性。
- 实验设计**较为全面**，覆盖主流基准和竞争方法，消融研究清晰展示了各模块贡献，对比公平（使用相同训练/测试流程和基线模型）。但OWOD部分对最新方法CAT、MEPU-FS的对比只出现在S-OWODB，M-OWODB中未显示，略显不完整。

## 6. 论文的主要结论与发现

- 联合建模物体性与类别标签的变分框架在低数据体制下显著提升了未知物体检测能力，在OWOD Task1未知召回率上超越PROB最高达5%以上。
- 理论分析揭示传统KL散度在低数据时因方差缩而导致发散，提出的动态高斯先验有效稳定了训练并保持嵌入多样性。
- 能量间隔损失有效抑制未知物体误分类，降低了A-OSE（未知物体被错分为已知的数量）。
- OWOBJ 可作为即插即用模块，在OWOD、FSOD、零样本OVOD三种不同任务上均取得一致提升，展现出强大的通用性。

## 7. 优点

- **理论深度**：从变分推断角度统一了物体性建模，并首次分析了低数据下KL项发散的理论原因，给出了动态先验的解决方案。
- **即插即用**：方法不改变原有检测器结构，易于集成到Faster R-CNN和DETR系列模型中。
- **多任务泛化**：在开放世界、少样本、零样本三个差异显著的任务上均有效，证明捕获通用物体性的优势。
- **精细的伪标签设计**：用连续概率（马氏距离）替代硬标签或随机软标签，提供了更可靠的未知物体监督信号。
- **能量视角的补充**：通过能量间隔损失进一步校准分类器置信度，从分类器输出的密度角度降低误判风险。

## 8. 不足与局限

- **算力信息缺失**：未报告训练所需的计算资源，难以评估实际部署成本。
- **对比公平性细节**：OWOD M‑OWODB表中未包含较新的MEPU‑FS单独结果，仅在S‑OWODB上与其组合汇报，可能影响与最强方法的直观比较。
- **超参数敏感度**：动态先验中的 \(\beta\) 和能量间隔 \(\delta\) 可能需要针对不同任务进行调整，文中仅给出了个别分析。
- **单模态仅视觉**：方法基于纯视觉检测器，未利用多模态信息（如图文预训练模型）进一步提升零样本场景性能；虽然在CORA上叠加有效，但未探索与其他视觉-语言模型的深度结合。
- **增量学习中的灾难性遗忘**：虽然OWOBJ在已知和未知检测上均有提升，但在OWOD的多次增量过程中如何持续保持物体性分布的质量，未做详细分析。

（完）
