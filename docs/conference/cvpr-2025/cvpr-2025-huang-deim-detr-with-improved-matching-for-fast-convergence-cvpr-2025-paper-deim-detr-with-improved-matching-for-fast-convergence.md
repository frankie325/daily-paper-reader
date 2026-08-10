---
title: "DEIM: DETR with Improved Matching for Fast Convergence"
title_zh: DEIM：基于改进匹配的DETR快速收敛方法
authors: "Huang, Shihua, Lu, Zhichao, Cun, Xiaodong, Yu, Yongjun, Zhou, Xiao, Shen, Xi"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Huang_DEIM_DETR_with_Improved_Matching_for_Fast_Convergence_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 10.0
evidence: DEIM通过密集一对一匹配和可匹配性感知损失加速DETR检测变压器收敛
tldr: 针对DETR（基于Transformer的检测器）一对一双边匹配造成的稀疏监督和收敛缓慢问题，本文提出DEIM训练框架。该框架采用密集一对一匹配策略增加正样本数量，并设计可匹配性感知损失（MAL）优化不同质量级别的匹配。实验表明，DEIM显著加速了实时Transformer目标检测的收敛速度，同时保持或提升了检测精度，为DETR的高效训练提供了新方案。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-huang-deim-detr-with-improved-matching-for-fast-convergence-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1755, \"height\": 665, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-huang-deim-detr-with-improved-matching-for-fast-convergence-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1803, \"height\": 921, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-huang-deim-detr-with-improved-matching-for-fast-convergence-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 860, \"height\": 360, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-huang-deim-detr-with-improved-matching-for-fast-convergence-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 863, \"height\": 415, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-deim-detr-with-improved-matching-for-fast-convergence-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1682, \"height\": 735, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-deim-detr-with-improved-matching-for-fast-convergence-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1611, \"height\": 934, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-deim-detr-with-improved-matching-for-fast-convergence-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 809, \"height\": 161, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-deim-detr-with-improved-matching-for-fast-convergence-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 878, \"height\": 414, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-deim-detr-with-improved-matching-for-fast-convergence-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 566, \"height\": 138, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-deim-detr-with-improved-matching-for-fast-convergence-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 788, \"height\": 422, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-deim-detr-with-improved-matching-for-fast-convergence-cvpr-2025-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 701, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-deim-detr-with-improved-matching-for-fast-convergence-cvpr-2025-paper/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 646, \"height\": 176, \"label\": \"Table\"}]"
motivation: DETR模型中一对一匹配造成稀疏监督，导致收敛缓慢，影响实时目标检测应用。
method: 提出密集一对一匹配策略增加正样本，并设计可匹配性感知损失优化匹配质量。
result: 实验显示DEIM加速了DETR收敛，并在实时检测中保持高精度。
conclusion: DEIM通过改进匹配机制有效解决了DETR收敛慢的问题，推动了Transformer检测的实际应用。
---

## Abstract
We introduce DEIM, an innovative and efficient training framework designed to accelerate convergence in real-time object detection with Transformer-based architectures (DETR). To mitigate the sparse supervision inherent in one-to-one (O2O) matching in DETR models, DEIM employs a Dense O2O matching strategy. This approach increases the number of positive samples per image by incorporating additional targets, using standard data augmentation techniques. While Dense O2O matching speeds up convergence, it also introduces numerous low-quality matches that could affect performance. To address this, we propose the Matchability-Aware Loss (MAL), a novel loss function that optimizes matches across various quality levels, enhancing the effectiveness of Dense O2O. Extensive experiments on the COCO dataset validate the efficacy of DEIM. When integrated with RT-DETR and D-FINE, it consistently boosts performance while reducing training time by 50%. Notably, paired with RT-DETRv2, DEIM achieves 53.2% AP in a single day of training on an NVIDIA 4090 GPU. Additionally, DEIM-trained real-time models outperform leading real-time object detectors, with DEIM-D-FINE-L and DEIM-D-FINE-X achieving 54.7% and 56.4% AP at 124 and 78 FPS on an NVIDIA T4 GPU, respectively, without the need for additional data. We believe DEIM sets a new baseline for advancements in real-time object detection. Our code and pre-trained models are available at https://www.shihuahuang.cn/DEIM/.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：基于 Transformer 的端到端目标检测器（DETR）虽然消除了非极大值抑制（NMS），但其一对一（O2O）匹配策略仅给每个目标分配一个正样本，导致**监督信号稀疏**，训练收敛极慢。
- **研究动机**：与同时期 YOLO 系列采用的一对多（O2M）密集监督相比，DETR 的正样本数量严重不足；此外，DETR 中查询（query）缺乏空间先验，产生大量低质量匹配，现有损失函数难以有效优化，进一步拖慢收敛。
- **整体含义**：本文旨在 **加速 DETR 收敛**，使它既能保持端到端无 NMS 的特性，又能达到甚至超越 YOLO 等实时检测器的精度与速度，为实时应用提供新的基准。

### 2. 论文提出的方法论

- **核心思想**：通过**密集一对一（Dense O2O）匹配**在不改变匹配结构的前提下增加正样本数量，并设计**可匹配性感知损失（MAL）**来优化各类匹配质量，两者结合实现快速收敛。

- **关键技术细节**
  - **Dense O2O 匹配**  
    - 利用经典数据增强（Mosaic 和 Mixup）拼接或混合多个图像，使单张图像中包含的**目标数量 \(N\) 增加**，而保持每个目标仍只匹配一个查询（\(M_i=1\)），从而**成倍增加正样本数**，达到类似 O2M 的密集监督效果。  
    - 该方法**无需额外解码器或辅助头**，不引入额外计算开销。
  - **Matchability-Aware Loss（MAL）**  
    - 针对 VariFocal Loss（VFL）对低 IoU 匹配惩罚过小的问题，提出新的损失函数：  
      \[
      \text{MAL}(p, q, y) = 
      \begin{cases}
      -q^\gamma \log(p) + (1 - q^\gamma) \log(1-p) & y=1 \\
      -p^\gamma \log(1-p) & y=0
      \end{cases}
      \]
    - 通过将目标标签调整为 \(q^\gamma\)（\(q\) 为预测框与真值的 IoU），使损失对低质量匹配（低 IoU）的惩罚随置信度上升而**显著增大**，从而引导模型更有效地利用有限的正样本。  
    - 移除 VFL 中用于平衡正负样本的超参数 \(\alpha\)，形式更简洁，重点关注匹配的可优化性（matchability）。

### 3. 实验设计

- **数据集与场景**
  - **主要基准**：MS COCO 2017（val2017），分辨率 \(640\times640\)。
  - **补充数据集**：CrowdHuman（密集行人检测），以验证泛化能力。
- **对比方法**
  - **实时检测器**：YOLOv8‑L/X、YOLOv9‑C/E、YOLOv10‑L/X、YOLO11‑L/X、Gold‑YOLO‑L、RT‑DETR‑HG‑L/X、D‑FINE‑L/X 等。
  - **ResNet‑based DETR 变体**：DETR‑DC5、Anchor‑DETR、Conditional‑DETR、Efficient‑DETR、SMCA‑DETR、Deformable‑DETR、DAB‑Deformable‑DETR、DN‑Deformable‑DETR、DINO‑Deformable‑DETR、RT‑DETR、RT‑DETRv2 等。
- **评估指标**：AP、AP\(_{50}\)、AP\(_{75}\)、AP\(_S\)、AP\(_M\)、AP\(_L\)，以及参数量、GFLOPs、延迟（T4 GPU）。

### 4. 资源与算力

- **GPU 型号**：NVIDIA GeForce RTX 4090（单卡）。
- **训练时长**：
  - 基准 RT‑DETRv2‑R50（72 epochs）约需 **85 GPU 小时**；DEIM 版本（60 epochs）仅需 **71 GPU 小时**，且精度更高。
  - 在单卡 4090 上训练 24 epochs 即可达到 **53.2% AP**（约一天内完成）。
  - 从 Objects365 预训练微调时，DEIM 仅需 **24 epochs** 即优于 D‑FINE 的 32 epochs。
- 论文明确提到训练时间对比，未提及多卡并行。

### 5. 实验数量与充分性

- **实验组数**：实验覆盖全面，至少包含以下关键部分：
  - 与多版本 YOLO 和 DETR 实时模型的系统对比（表 1）。
  - 基于 ResNet‑50/101 的十余种 DETR 变体对比（表 2）。
  - CrowdHuman 数据集上的迁移实验（表 3）。
  - 消融实验：
    - Mosaic/Mixup 组合策略（表 4，12/24 epochs）。
    - MAL 中 \(\gamma\) 超参数搜索（表 5）。
    - Dense O2O 与 MAL 组件有效性验证（表 6）。
    - 训练速度对比（表 7）。
    - Objects365 预训练微调（表 8）。
- **充分性与公平性**：实验对比对象均为同期或近期 SOTA 模型，使用公开标准数据集和统一指标；消融设置细致，结论可靠。

### 6. 论文的主要结论与发现

- DEIM 通过 Dense O2O 和 MAL 显著加速 DETR 收敛，**在仅一半的训练轮数下即可超越原始基线**。
- 与 D‑FINE 结合后，**DEIM‑D‑FINE‑L/X 在 T4 GPU 上分别达到 54.7% 和 56.5% AP，延迟仅 8.07 ms 和 12.89 ms**，超越所有对比的 YOLO 和 DETR 实时检测器，成为新 SOTA。
- 方法对**小目标检测**提升尤为明显（DEIM‑RT‑DETRv2‑R101 小目标 AP 提高 2.1 点），弥补了 DETR 的弱项。
- 框架简单、即插即用，**无需增加推理延迟或额外结构**。

### 7. 优点

- **方法新颖且实用**：通过数据增强增加目标数量实现密集监督，思路直接，且不改变模型结构，兼容现有 DETR 变体。
- **针对性解决收敛瓶颈**：MAL 针对低质量匹配设计，有效利用困难正样本，使训练更高效。
- **实验扎实**：在两种架构（RT‑DETR、D‑FINE）和多种规模上均表现一致，并有详细的消融和迁移验证。
- **训练成本低**：单卡 4090 一天可训出高精度模型，对学术研究和实际部署友好。

### 8. 不足与局限

- **小目标精度仍有差距**：某些 YOLO 版本（如 YOLOv9‑E）在小目标 AP 上仍优于 DEIM 模型，论文亦指出 DETR 在小目标检测上的固有挑战尚未完全解决。
- **数据增强依赖**：Dense O2O 依赖 Mosaic 与 Mixup，若目标场景本身不适合这类增强（如极端稀疏或密集文字）可能效果受限。
- **评估场景有限**：仅在 COCO 和 CrowdHuman 两个数据集上测试，缺乏自动驾驶、遥感等多样化场景验证，泛化性需进一步检验。
- **调度敏感**：需精心设计数据增强 warmup 和衰减策略（如 50% 训练后关闭 Dense O2O），可能增加调参负担。

（完）
