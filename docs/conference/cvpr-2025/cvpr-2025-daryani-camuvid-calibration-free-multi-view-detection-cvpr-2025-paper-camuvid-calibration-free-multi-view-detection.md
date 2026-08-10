---
title: "CaMuViD: Calibration-Free Multi-View Detection"
title_zh: CaMuViD：免标定的多视角检测
authors: "Daryani, Amir Etefaghi, Bhutta, M. Usman Maqbool, Hernandez, Byron, Medeiros, Henry"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Daryani_CaMuViD_Calibration-Free_Multi-View_Detection_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 8.0
evidence: 免标定的多视角目标检测
tldr: 针对多视角检测依赖标定和鸟瞰图表示的问题，提出CaMuViD，直接在图像空间学习灵活变换和跨视角特征融合，实现免标定的多视角目标检测，在密集场景取得高精度。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-daryani-camuvid-calibration-free-multi-view-detection-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 681, \"height\": 758, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-daryani-camuvid-calibration-free-multi-view-detection-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 693, \"height\": 766, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-daryani-camuvid-calibration-free-multi-view-detection-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1766, \"height\": 657, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-daryani-camuvid-calibration-free-multi-view-detection-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1771, \"height\": 599, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-daryani-camuvid-calibration-free-multi-view-detection-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 825, \"height\": 279, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-daryani-camuvid-calibration-free-multi-view-detection-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1714, \"height\": 660, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-daryani-camuvid-calibration-free-multi-view-detection-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 811, \"height\": 433, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-daryani-camuvid-calibration-free-multi-view-detection-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 838, \"height\": 362, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-daryani-camuvid-calibration-free-multi-view-detection-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 869, \"height\": 216, \"label\": \"Table\"}]"
motivation: 传统多视角检测需要相机标定和BEV表示，过程复杂。
method: 提出可在图像空间直接操作的免标定多视角检测框架，学习灵活变换融合特征。
result: "在Wildtrack和MultiviewX数据集上分别取得95.0%和96.5%的MODA分数。"
conclusion: CaMuViD简化了多视角检测流程，并实现了高精度。
---

## Abstract
Multi-view object detection in crowded environments presents significant challenges, particularly for occlusion management across multiple camera views. This paper introduces a novel approach that extends conventional multi-view detection to operate directly within each camera's image space. Our method finds objects bounding boxes for images from various perspectives without resorting to a bird's eye view (BEV) representation. Thus, our approach removes the need for camera calibration by leveraging a learnable architecture that facilitates flexible transformations and improves feature fusion across perspectives to increase detection accuracy. Our model achieves Multi-Object Detection Accuracy (MODA) scores of 95.0% and 96.5% on the Wildtrack and MultiviewX datasets, respectively, significantly advancing the state of the art in multi-view detection. Furthermore, it demonstrates robust performance even without ground truth annotations, highlighting its resilience and practicality in real-world applications. These results emphasize the effectiveness of our calibration-free, multi-view object detector.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究动机**：密集场景中的多视角目标检测长期受困于遮挡问题，传统方法严重依赖相机精确标定，将多个视角的图像特征投影到鸟瞰图（BEV）上进行行人生成检测。
- **现有方法的局限**：
  - 相机标定过程繁琐，且需要预知相机内外参。
  - BEV投影会引入几何失真，尤其对远距离行人影响较大，导致特征提取困难。
  - 标定参数固定的模型容易过拟合特定场景与相机配置，泛化能力差。
- **本文的解决思路**：提出一种**免标定的多视角检测框架（CaMuViD）**，直接在相机图像空间学习跨视角的特征映射与融合，完全规避对 BEV 表示和相机参数的依赖，使得模型更灵活、更易部署。

## 2. 论文提出的方法论

- **整体架构**：包含特征提取、学习性投影矩阵估计、多视角特征融合、反向投影与特征细化、2D 检测头五部分。
- **关键技术细节**：
  - **骨干网络**：使用基于可变形卷积的 InternImage‑t，提取各相机视图的特征图 \(F_i \in \mathbb{R}^{C_f\times H_f\times W_f}\)。
  - **投影矩阵学习**：
    - 用全连接网络 \(N_p\) 从 \(F_i\) 预测投影矩阵 \(A^p_i \in \mathbb{R}^{C_f\times C_f}\)，将特征从本视图“投影”到公共表示空间：\(P_i = A^p_i \times F_i\)（通道维度矩阵乘法）。
    - 同时用另一全连接网络 \(N_b\) 预测反向投影矩阵 \(A^b_i\)，要求 \(A^b_i \approx (A^p_i)^{-1}\)。
  - **特征融合**：在公共空间将所有视角的 \(P_i\) 沿通道拼接，再经 1×1 卷积降维融合，得到融合特征 \(P_f\)。
  - **反向投影**：利用 \(A^b_i\) 将融合特征投影回各视图图像空间：\(\hat{F}_i = A^b_i \times P_f\)。
  - **投影一致性损失**：通过 \(\mathcal{L}_{vp} = \sum_{i=1}^{N} |A^b_i \times P_i - F_i|\) 约束投影与逆投影的可逆性。
  - **特征细化**：经历一个 FRM 模块（大核卷积 + ReLU + 卷积），得到最终用于检测的特征图。
  - **检测头**：采用级联 RCNN，直接输出每个视图的 2D 行人包围框。
- **训练技巧**：在标准检测损失基础上加入投影一致性损失（权重 2e‑4），输入图像下采样至 640×1338，训练 20 个 epoch，初始学习率 1e‑4。

## 3. 实验设计

- **数据集**：
  - **Wildtrack**：真实场景，7 个相机，覆盖 12×36 米区域，480×1440 地面网格，平均每帧约 20 人。
  - **MultiviewX**：合成场景，6 个相机，16×25 米区域，相同地面网格分辨率。
- **评价基准**：沿用多视角检测的 MODA、MODP，以及 Precision、Recall、F1 分数。评估时适配图像空间检测：多视角下的同一行人在任一视图匹配即算 TP，多余检测投影到世界平面聚类后计为 FP。
- **对比方法**：RCNN & clustering、POM-CNN、DeepMCD、Deep‑Occlusion、MVDet、SHOT、MVDeTr、MVAug、3DROM、MVFP、TrackTacular 等十余种前沿方法。

## 4. 资源与算力

- 文中仅提及使用 InternImage‑t 作为骨干网络，基于 MS COCO 预训练权重，训练 20 个 epoch，但**未明确说明使用的 GPU 型号、数量或具体训练时长**，无法准确评估其算力需求。

## 5. 实验数量与充分性

- **主要实验组数**：
  1. Wildtrack 和 MultiviewX 上的主结果对比（共对比 11 种方法）。
  2. 跨数据集泛化实验（MultiviewX 训练 → WildTrack 测试，对比 8 种方法）。
  3. 相机消除性能分析（在 Wildtrack 上逐步减少相机数量，×7 组配置）。
  4. 消融实验（融合方式：求和 vs. 拼接；是否使用 FRM，×3 组）。
  5. 几何投影 vs. 无标定投影的特征图可视化对比。
- **充分性与公平性**：
  - 评估指标全面，比较对象涵盖了近年主流方法。
  - 跨数据集测试验证了泛化能力，消融实验清晰揭示了各模块的贡献。
  - 所有对比均使用相同数据划分和评估协议，实验设计客观、公平。
  - 尽管算力细节缺失，但实验数量和质量足以支撑论文结论。

## 6. 论文的主要结论与发现

- CaMuViD 在不利用任何相机标定参数的前提下，在 Wildtrack 上取得了 **95.0% MODA**，在 MultiviewX 上取得 **96.5% MODA**，均刷新了当时的最先进水平。
- 该方法在跨数据集测试中表现出极强的泛化能力，优于所有依赖标定的对比方法。
- 即使在部分行人缺少真值标注的情况下，模型仍能正确检测，体现了对真实场景的鲁棒性。
- 消融实验证明，特征拼接融合和 FRM 对性能提升均有正面贡献，可学习的投影‑反投影机制显著优于固定几何投影。

## 7. 优点

- **完全免标定**：彻底摆脱相机内外参依赖，简化了多视角系统的部署流程。
- **直接在图像空间检测**：避免了 BEV 投影带来的特征畸变，特别有利于远距离行人检测。
- **创新的可学习投影框架**：通过矩阵乘法实现特征域的空间映射，并用一致性损失保证可逆性，设计新颖。
- **强特征融合与细化**：拼接融合保留多视角信息，FRM 提升特征质量，整体结构简洁有效。
- **开源代码**：提供代码仓库，便于复现和后续研究。
- **优异的泛化性能**：从合成数据迁移到真实场景仍保持高精度，实用性突出。

## 8. 不足与局限

- **依赖多相机同步图像**：仍需所有相机观测同一区域且时间同步，对于相机数量或位姿骤变的情况需要重新训练或适应。
- **算力信息缺失**：未报告 GPU 类型、内存占用和推理速度，难以评估其对边缘设备的实时性。
- **MODP 指标在跨数据集测试时较低**：仅 60.7%，因为图像空间检测在真实场景下受行人尺寸变化影响，IoU 精度不及世界平面直接度量。
- **可能产生额外假阳性**：在部分行人无 GT 时虽能检出，但这类检测可能被计为 FP，影响精度。
- **技术报告性细节不足**：未讨论模型在不同相机数量动态变化下的处理方式，也未评估小目标或极端密集场景下的特定表现。
- **依赖大量训练数据**：学习投影矩阵需要足够的视角配对数据，若相机布置与训练集差异过大，可能仍需重训练。

（完）
