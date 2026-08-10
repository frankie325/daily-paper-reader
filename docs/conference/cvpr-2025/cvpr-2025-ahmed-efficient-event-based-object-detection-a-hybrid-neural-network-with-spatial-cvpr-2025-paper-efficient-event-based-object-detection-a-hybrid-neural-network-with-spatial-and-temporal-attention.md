---
title: "Efficient Event-Based Object Detection: A Hybrid Neural Network with Spatial and Temporal Attention"
title_zh: 高效事件相机目标检测：具有时空注意力的混合神经网络
authors: "Ahmed, Soikat Hasan, Finkbeiner, Jan, Neftci, Emre"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Ahmed_Efficient_Event-Based_Object_Detection_A_Hybrid_Neural_Network_with_Spatial_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 8.0
evidence: 基于事件相机的目标检测，采用混合SNN-ANN注意力网络
tldr: 针对事件相机目标检测中SNN精度不足、ANN能耗高的问题，论文提出注意力混合SNN-ANN骨干网络，设计新颖的注意力桥接模块捕获SNN的稀疏时空关系并转为密集特征图供ANN处理，在保证精度的同时提高效率，为低功耗实时检测提供新思路。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-ahmed-efficient-event-based-object-detection-a-hybrid-neural-network-with-spatial-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1401, \"height\": 373, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-ahmed-efficient-event-based-object-detection-a-hybrid-neural-network-with-spatial-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1728, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-ahmed-efficient-event-based-object-detection-a-hybrid-neural-network-with-spatial-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 852, \"height\": 397, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-ahmed-efficient-event-based-object-detection-a-hybrid-neural-network-with-spatial-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1099, \"height\": 516, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-ahmed-efficient-event-based-object-detection-a-hybrid-neural-network-with-spatial-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 862, \"height\": 515, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-ahmed-efficient-event-based-object-detection-a-hybrid-neural-network-with-spatial-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 858, \"height\": 512, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-ahmed-efficient-event-based-object-detection-a-hybrid-neural-network-with-spatial-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 704, \"height\": 347, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-ahmed-efficient-event-based-object-detection-a-hybrid-neural-network-with-spatial-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 867, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-ahmed-efficient-event-based-object-detection-a-hybrid-neural-network-with-spatial-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 835, \"height\": 303, \"label\": \"Table\"}]"
motivation: SNN能效高但精度低，ANN精度高但能耗大。
method: 提出注意力桥接模块实现SNN到ANN的特征转换。
result: 混合网络在事件相机数据上兼顾精度与效率。
conclusion: 混合SNN-ANN架构有望实现低功耗高性能事件检测。
---

## Abstract
Event cameras offer high temporal resolution and dynamic range with minimal motion blur, making them promising for robust object detection. While Spiking Neural Networks (SNNs) on neuromorphic hardware are often considered for energy efficient and low latency event-based data processing, they often fall short of Artificial Neural Networks (ANNs) in accuracy and flexibility. Here, we introduce Attention-based Hybrid SNN-ANN backbones for event-based object detection to leverage the strengths of both SNN and ANN architectures. A novel Attention-based SNN-ANN bridge module proposed to captures sparse spatial and temporal relations from the SNN layer and converts them into dense feature maps for the ANN part of the backbone. Additionally, we present a variant that integrates DWConvLSTMs to the ANN blocks to capture slower dynamics. This multi-timescale network combines fast SNN processing for short timesteps with long-term dense RNN processing, effectively capturing both fast and slow dynamics.Experimental results demonstrate that our proposed method surpasses SNN-based approaches by significant margins, with results comparable to existing ANN and RNN-based methods. Unlike ANN-only networks, the hybrid setup allow us to implement the SNN blocks on digital neuromorphic hardware to investigate the feasibility of our approach.Extensive ablation studies and implementation on neuromorphic hardware confirm the effectiveness of our proposed modules and architectural choices.Our hybrid SNN-ANN architectures pave the way for ANN-like performance at a drastically reduced parameter, latency, and power budget.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义
- **研究背景**：事件相机具有高时间分辨率、高动态范围与极低运动模糊的优势，但其输出的稀疏异步事件流难以直接应用传统帧图像检测器。
- **核心矛盾**：脉冲神经网络（SNN）天然适配事件数据，能效高、延迟低，但检测精度远不及人工神经网络（ANN）；ANN 精度高，但参数量大、能耗高，难以部署在边缘或神经形态硬件。
- **解决思路**：提出混合 SNN‑ANN 骨干网络，通过一个新颖的注意力桥接模块，将 SNN 层提取的稀疏时空脉冲转换为密集特征图，再交由 ANN 进行高级语义提取，既保持高精度，又大幅降低参数量和计算开销，并可部分部署于神经形态芯片。该工作首次在大型事件相机检测基准（Gen1、Gen4）上验证混合架构的有效性。

## 2. 论文提出的方法论
- **整体架构**  
  - 事件输入先被转换为时间‑空间张量 `Events[tk-1, tk] ∈ RT×2×H×W`，极性分两通道计数。  
  - 混合骨干由三部分组成：  
    - `fsnn`：多个卷积 SNN 块（Conv → BN → PLIF 神经元），以高时间分辨率提取低层时空特征。  
    - `βasab`：注意力桥接模块，将 SNN 输出的脉冲 `Espike` 转化为密集特征图 `Fout`。  
    - `fann`：多个人工卷积块，从 `Fout` 中提取高层空间特征。  
  - 检测头采用 YOLOX，输出目标框与分类。
- **Attention‑based SNN‑ANN Bridge (βasab)**  
  - **Spatial‑aware Temporal (SAT) 注意力**  
    - **Channel‑wise Temporal Grouping**：将输入脉冲形状 `RT×C×H′×W′` 重组为 `RC×T×H′×W′`。  
    - **Time‑wise Separable Deformable Convolution (TSDC)**：对每个时间步独立使用可变卷积（卷积组数等于时间步数 T），以不规则采样核捕获稀疏空间结构。  
    - **Temporal Attention**：对 TSDC 输出的空间上下文进行多头自注意力，沿时间维度捕捉不同时刻的关系，最后加权求和得到空间特征 `Aout`。  
  - **Event‑rate Spatial (ERS) 注意力**  
    - 对 `Espike` 在时间维度求和，得到事件率 `Srate`，经 Sigmoid 生成空间注意力权重，与 SAT 的输出逐元素相乘，产生最终密集特征 `Fout`。
- **RNN 变体**  
  - 在 ANN 块中嵌入两个 Depth‑Wise Separable ConvLSTM，SNN 处理短时间步长的快速动态，βasab 提取较长时间步的特征，再由 ConvLSTM 捕捉慢动态，形成多时间尺度网络。
- **关键公式**  
  - PLIF 神经元动态：  
    \[
    V[t] = V[t-1] + \frac{1}{\tau}(X[t] - (V[t-1] - V_{reset})), \quad \tau = \text{sigmoid}(w)^{-1}
    \]  
  - 事件张量构造：  
    \[
    \text{Events}[t_{k-1}, t_k](t,p,x,y) = \sum_{e_n \in E} \delta(p-p_n)\delta(x-x_n)\delta(y-y_n)\delta(t-t'_n)
    \]  
  - 时间注意力计算（略）。  
  - ERS 加权：  
    \[
    E_{feature} = \text{sigmoid}(S_{rate}) \odot A_{out}
    \]

## 3. 实验设计
- **数据集**：Gen1 Automotive Detection（304×240，39 小时）和 Gen4 Automotive Detection（720×1280，15 小时），标注类别包括汽车、行人，Gen4 额外包含两轮车。
- **评估指标**：均值平均精度 mAP（0.5:0.05:0.95）。
- **对比方法**  
  - ANN 类：Inception+SSD、RRC‑Events、Events‑RetinaNet、E2Vid‑RetinaNet、SparseConv、AEGNN、RVT‑B w/o LSTM 等。  
  - SNN 类：VGG‑11+SSD、MobileNet‑64+SSD、DenseNet121‑24+SSD、FP‑DAGNet、EMS‑RES10/18/34、SpikeFPN。  
  - RNN/Transformer 类：RED、ASTMNet、RVT‑B/S/T、S4D‑ViT‑B、S5‑ViT‑B/S 等。
- **训练细节**：事件箱 5 ms，检测间隔训练时 50 ms，推理可更短。Gen1 训练 50 个 epoch，Gen4 10 个 epoch，优化器 ADAM，学习率 OneCycle schedule。

## 4. 资源与算力
- **GPU 资源**：使用 4 张 NVIDIA RTX 3090。
- **训练时间**：Gen1 约 8 小时（batch size 24，学习率 2×10⁻⁴）；Gen4 约 1.5 天（batch size 8，学习率 3.5×10⁻⁴）。RNN 变体训练 40 万步，batch size 2，约需 6 天。
- **硬件部署**：将 SNN 块部署于 Intel Loihi 2，对 int8 量化后的 4 层 SNN，功耗约 1.7 W，每步约 1.9 ms，快于 5 ms 的实时要求，较 NVIDIA Jetson Orin Nano 功耗更低。

## 5. 实验数量与充分性
- **实验组数概览**  
  - 两大基准数据集（Gen1、Gen4）上的主流方法对比，涵盖 ANN、SNN、RNN/Transformer 三类共约 20 种方法。  
  - 消融实验表 4：5 种变体，分别移除时空注意力、可变卷积、ERS 模块或整个 ASAB 模块。  
  - 附加消融：不同 DWConvLSTM 配置（详见补充材料）。  
  - 复杂度分析表 6：对比全 ANN、无桥接模块、有桥接模块以及增加一个 SNN 层的混合版本。  
  - 硬件测试表 5：Loihi 2 上不同量化位宽的功耗与时间。
- **评价**：实验设计比较充分，同时对比了多种 SOTA 方法，并通过消融验证了桥接模块各组件的贡献；硬件实测证明了边缘部署的可行性；但由于多数方法未开源，部分对比数据依赖原文报告，公平性上略有不足；在 Gen4 上的精度虽然领先于对比的 SNN 和 ANN 方法，但仍显著低于 RNN‑Transformer 方法，文中未深入分析该差距。

## 6. 论文的主要结论与发现
- 提出的混合 SNN‑ANN 骨干网络在 Gen1 上以仅 6.6 M 参数取得 mAP 0.35，显著超越所有 SNN 方法，并与参数数倍至数十倍的 ANN 方法（如 Events‑RetinaNet 0.34，33 M）持平。  
- 引入的 βasab 桥接模块能有效保留稀疏时空特征，相较简单累积操作带来约 5% mAP 提升。  
- 多时间尺度 RNN 变体进一步匹配 RNN 方法的精度（Gen1 上 0.43 mAP），但参数和计算量更节省。  
- SNN 部分可在 Intel Loihi 2 上实现实时低功耗运行，验证了混合架构在边缘设备上的实用性。  
- 总体结论：混合 SNN‑ANN 架构有望以极低的参数和功耗预算，达到接近 ANN 的检测性能。

## 7. 优点
- **新颖的架构设计**：首次在事件相机大型检测基准上提出混合 SNN‑ANN 方案，并设计了精细的注意力桥接模块。  
- **双重注意力机制**：SAT 与 ERS 互补，分别处理时间关系和空间活动，有效将稀疏脉冲转化为信息丰富的密集特征。  
- **多尺度时间建模**：通过 SNN+ConvLSTM 同时捕获快速和慢速动态，扩展了模型的时间感受野。  
- **综合评估坚实**：覆盖多数据集、多类方法对比、消融实验、计算复杂度分析和硬件实测，验证了有效性与效率。  
- **边缘部署友好**：参数、MACs 较低，且 SNN 部分可在神经形态芯片上实时低功耗运行，为实际应用提供路径。

## 8. 不足与局限
- **性能上限**：与当前最优的 RNN‑Transformer 方法（如 RVT‑B、S5‑ViT‑B 在 Gen1 上达 0.48 mAP）仍有明显差距，未能展现出混合架构在精度上的竞争力。  
- **RNN 变体训练成本高**：ConvLSTM 版本需训练 6 天（batch size 2），训练效率较低，待优化。  
- **硬件评估不完整**：Loihi 2 上仅部署了 SNN 块，未给出完整混合模型的总功耗/延迟，实际部署的整体效益有待验证。  
- **对比公平性**：多数对比方法未开源，依赖原文报告；一些方法（如 ASTMNet 100 M）参数规模差异大。  
- **泛化性未充分验证**：仅在两个自动驾驶数据集上测试，缺少其他场景（如低光照、高速运动追踪）的评估。  
- **开源问题**：文中未提供代码链接，复现难度大。

（完）
