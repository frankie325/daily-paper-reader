---
title: "V2X-R: Cooperative LiDAR-4D Radar Fusion with Denoising Diffusion for 3D Object Detection"
title_zh: V2X-R：基于去噪扩散的协同激光雷达-4D雷达融合用于三维目标检测
authors: "Huang, Xun, Wang, Jinlong, Xia, Qiming, Chen, Siheng, Yang, Bisheng, Li, Xin, Wang, Cheng, Wen, Chenglu"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Huang_V2X-R_Cooperative_LiDAR-4D_Radar_Fusion_with_Denoising_Diffusion_for_3D_CVPR_2025_paper.pdf"
tags: ["query:obj-detect"]
score: 9.0
evidence: 协同激光雷达与4D雷达融合的三维目标检测
tldr: 针对恶劣天气下现有车联网系统性能下降问题，论文提出了首个融合激光雷达、摄像头和4D雷达的V2X-R仿真数据集，并设计了一种协同融合流水线，通过多模态融合策略和去噪扩散模型提升三维目标检测精度，为全天候自动驾驶感知提供了鲁棒方案。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-huang-v2x-r-cooperative-lidar-4d-radar-fusion-with-denoising-diffusion-for-3d-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 862, \"height\": 266, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-huang-v2x-r-cooperative-lidar-4d-radar-fusion-with-denoising-diffusion-for-3d-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 871, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-huang-v2x-r-cooperative-lidar-4d-radar-fusion-with-denoising-diffusion-for-3d-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 865, \"height\": 463, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-huang-v2x-r-cooperative-lidar-4d-radar-fusion-with-denoising-diffusion-for-3d-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1612, \"height\": 789, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-huang-v2x-r-cooperative-lidar-4d-radar-fusion-with-denoising-diffusion-for-3d-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 843, \"height\": 378, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-v2x-r-cooperative-lidar-4d-radar-fusion-with-denoising-diffusion-for-3d-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 875, \"height\": 377, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-v2x-r-cooperative-lidar-4d-radar-fusion-with-denoising-diffusion-for-3d-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 872, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-v2x-r-cooperative-lidar-4d-radar-fusion-with-denoising-diffusion-for-3d-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 875, \"height\": 380, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-v2x-r-cooperative-lidar-4d-radar-fusion-with-denoising-diffusion-for-3d-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1813, \"height\": 542, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-v2x-r-cooperative-lidar-4d-radar-fusion-with-denoising-diffusion-for-3d-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1812, \"height\": 433, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-v2x-r-cooperative-lidar-4d-radar-fusion-with-denoising-diffusion-for-3d-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 876, \"height\": 275, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-v2x-r-cooperative-lidar-4d-radar-fusion-with-denoising-diffusion-for-3d-cvpr-2025-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 875, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-v2x-r-cooperative-lidar-4d-radar-fusion-with-denoising-diffusion-for-3d-cvpr-2025-paper/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 881, \"height\": 490, \"label\": \"Table\"}]"
motivation: 现有V2X系统在恶劣天气下3D检测性能下降，4D雷达有望解决此挑战。
method: 提出首个LiDAR-4D雷达融合V2X数据集V2X-R，并设计协同融合流水线。
result: 融合流水线在恶劣天气下提升目标检测性能。
conclusion: 多模态协同融合有效增强自动驾驶全天候感知鲁棒性。
---

## Abstract
Current Vehicle-to-Everything (V2X) systems have significantly enhanced 3D object detection using LiDAR and camera data. However, they face performance degradation in adverse weather. Weather-robust 4D radar, with Doppler velocity and additional geometric information, offers a promising solution to this challenge. To this end, we present V2X-R, the first simulated V2X dataset incorporating LiDAR, camera, and 4D radar modalities. V2X-R contains 12,079 scenarios with 37,727 frames of LiDAR and 4D radar point clouds, 150,908 images, and 170,859 annotated 3D vehicle bounding boxes. Subsequently, we propose a novel cooperative LiDAR-4D radar fusion pipeline for 3D object detection and implement it with multiple fusion strategies. To achieve weather-robust detection, we additionally propose a Multi-modal Denoising Diffusion (MDD) module in our fusion pipeline. MDD utilizes weather-robust 4D radar feature as a condition to guide the diffusion model in denoising noisy LiDAR features.Experiments show that our LiDAR-4D radar fusion pipeline demonstrates superior performance in the V2X-R dataset. Over and above this, our MDD module further improved the foggy/snowy performance of the basic fusion model by up to 5.73%/6.70% and barely disrupting normal performance. The dataset and code will be publicly available.

---

## 论文详细总结（自动生成）

# V2X-R：基于去噪扩散的协同激光雷达-4D雷达融合三维目标检测

## 1. 论文的核心问题与整体含义
- **核心问题**：现有车联网（V2X）协同感知系统主要依赖 LiDAR 和相机，但这两种传感器在雨、雾、雪等恶劣天气下性能严重退化，导致三维目标检测失效。4D 雷达具有天气鲁棒性、可提供多普勒速度等优势，但缺乏包含 4D 雷达的协同感知数据集及相应的融合方法。
- **研究动机**：利用 4D 雷达的天气穿透能力和多智能体协同带来的空间多样性，提升全天候下的 3D 目标检测精度，并解决多智能体场景中 LiDAR 噪声因通信而加剧的问题。
- **整体含义**：该工作通过构建首个带有 4D 雷达的 V2X 仿真数据集 V2X‑R，设计协同 LiDAR-4D 雷达融合流水线，并提出多模态去噪扩散模块（MDD），为天气鲁棒型协同感知提供了新的基准与方法框架。

## 2. 论文提出的方法论
### 2.1 协同 LiDAR-4D 雷达融合流水线
- 流水线包含四个阶段：
  1. **各智能体独立编码**：使用共享编码器将 LiDAR 和 4D 雷达点云分别编码为特征图 \(F_i^j\)，其中 \(i\in\{L,R\}\) 表示模态，\(j\in\{C,E,I\}\) 表示智能体（连接车辆、自车、路侧单元）。
  2. **智能体融合**：对同一模态的特征进行跨智能体融合，得到多智能体特征 \(F^i_A\)。可替换为多种中期融合方法（如自注意力、Transformer 等）。
  3. **模态融合**：LiDAR 特征 \(F^L_A\) 先经过 MDD 模块去噪得到 \(\tilde{F}^L_A\)，再与 4D 雷达特征 \(F^R_A\) 融合生成多模态特征 \(F_{MA}\)。
  4. **框预测**：使用检测头输出 3D 边界框。
- **两种扩展融合策略**：
  - **SA2MA（单智能体多模态→多智能体多模态）**：将已有的单智能体 LiDAR-4D 雷达融合方法（如 InterFusion、L4DR）扩展为多智能体版本，在阶段 2 加入自注意力融合模块。
  - **SM2MM（多智能体单模态→多智能体多模态）**：将已有的多智能体 LiDAR 方法（如 AttFuse、CoBEVT 等）扩展为多模态版本，先在 LiDAR 和 4D 雷达上分别进行智能体融合，再在 BEV 空间拼接模态特征。

### 2.2 多模态去噪扩散模块（MDD）
- **设计动机**：多智能体通信虽能扩大感知范围，但会使恶劣天气下产生的 LiDAR 噪声相互叠加，形成更密集的噪声。传统点级分割去噪耗时不兼容特征融合，而直接学习去噪因噪声分布复杂而难以拟合。
- **核心思想**：利用扩散模型的重参数化，将原始天气噪声分布映射为易于拟合的高斯分布，并以天气鲁棒的 4D 雷达特征作为条件引导多步去噪过程，恢复清晰 LiDAR 特征。
- **算法流程**（Algorithm 1）：
  - **扩散过程**：设初始噪声 LiDAR 特征为 \(F_{init}=F^L_A\)，按公式 \(F_T=\sqrt{\alpha_T}F_{init}+\sqrt{1-\alpha_T}\epsilon\)（\(\epsilon\sim\mathcal{N}(0,I)\)）前向加噪，将复杂噪声分布重参数化为高斯分布 \(\delta_{gau}\sim\mathcal{N}(\sqrt{\alpha_T}\delta_{raw},\sqrt{1-\alpha_T})\)。
  - **去噪过程**：在 \(t=T,T-1,...,1\) 步中，将当前特征 \(F_t\) 与 4D 雷达特征 \(F^R_A\) 拼接后输入 U‑Net 去噪器 \(U_\theta\)，预测 \(F_{t-1}\)。最终 \(F_0=\tilde{F}^L_A\) 即为去噪后的清晰 LiDAR 特征。
  - **损失函数**：使用 MSE 损失比较去噪特征与从干净点云提取的真值特征，并引入随 epoch 非线性衰减的权重 \(\gamma(e,\psi)=(1-\tanh(\frac{e}{\tau}-\varphi))\cdot\psi\)，使模型早期关注去噪任务，后期侧重检测任务。
  - 总损失：\(L_{all}=\beta_{cls}L_{cls}+\beta_{loc}L_{loc}+L_{MDD}\)。

## 3. 实验设计
- **数据集**：
  - 自建 **V2X‑R**：基于 CARLA + OpenCDA 模拟，包含 12,079 个场景，37,727 帧 LiDAR/4D 雷达点云，150,908 张图像，170,859 个标注车辆框。每个智能体配有 4 相机、64 线 LiDAR、4D 雷达（120°水平 FOV，30°垂直 FOV，150m 距离）。对 LiDAR 点云应用基于物理的雾、雪仿真生成恶劣天气条件。
  - 真实数据集 **K‑Radar**：验证 MDD 在单智能体真实恶劣天气下的有效性。
- **Benchmark 与对比方法**：
  - **协同 LiDAR 方法**：AttFuse、V2X‑ViT、CoBEVT、CoAlign、Where2comm、AdaFusion、SCOPE、SICP。
  - **协同 4D 雷达方法**：将 PFA‑Net、RTNH 扩展为多智能体版，或将 LiDAR 方法改为 4D 雷达输入。
  - **协同 LiDAR‑4D 雷达融合**：用 SA2MA 和 SM2MM 策略实现 InterFusion、L4DR、AttFuse、CoBEVT 等方法的融合版本。
  - 评价指标：3D mAP（IoU=0.3/0.5/0.7），在自车相机 FOV 内评估。

## 4. 资源与算力
- 文中未明确提及 GPU 型号、数量或训练时长。
- 仅说明使用 Adam 优化器（lr=1e-3，β1=0.9，β2=0.999），并在 MDD 模块推理时报告了额外耗时约 32 ms（仍可维持约 20 FPS），但未提供硬件平台细节。

## 5. 实验数量与充分性
- 实验内容极其丰富：
  - **表 2、3、4**：分别对 8 种纯 LiDAR、12 种纯 4D 雷达、11 种 LiDAR‑4D 雷达融合方法在 V2X‑R 的验证/测试集上进行了全面评测。
  - **表 5**：在正常、雾、雪三种天气下对比了纯 LiDAR、融合模型以及带 MDD 的模型，展示天气鲁棒性提升。
  - **表 6**：在真实数据集 K‑Radar 上验证 MDD 模块，覆盖 Sedan 和 Bus 两类，并统计整体/恶劣/正常天气的 mAP。
  - **表 7**：消融实验，逐步分析扩散过程、U‑Net、4D 雷达条件三个组件对去噪性能的贡献。
  - **表 8**：超参数敏感性实验，探索扩散层数 T、损失权重类型及 σ 值的影响。
- **评价**：实验设计充分且公平，既涵盖仿真多天气、多模态、多基线，又包含真实场景验证，消融和超参分析逻辑清晰，能有力支撑论文结论。

## 6. 论文的主要结论与发现
- 协同 LiDAR‑4D 雷达融合在所有评价指标下均优于单一模态方案，如 CoBEVT 融合模型在 IoU=0.7 时较纯 LiDAR 提升 5.86%。
- MDD 模块显著提升了融合模型在雾天、雪天等恶劣天气下的检测精度（最高提升 5.73%/6.70%），而对正常天气性能几乎无影响（下降不超过 0.16%）。
- 在多智能体条件下，4D 雷达点云的实例占有率和点数在中远距离大幅增加，证明协同可弥补 4D 雷达分辨率低的缺陷。
- 在真实数据集 K‑Radar 上，MDD 在恶劣天气下也带来 5% 以上的 mAP 增益，验证了方法的跨域有效性。
- 扩散模型的重参数化和条件引导策略能有效解决多智能体 LiDAR 噪声分布复杂、难以直接拟合的问题。

## 7. 优点
- **首个包含 4D 雷达的 V2X 数据集**：填补业界空白，为后续研究提供数据基础。
- **创新的去噪范式**：首次在协同感知中引入扩散模型进行特征级去噪，巧妙地将复杂天气噪声转化为标准高斯分布，并利用 4D 雷达条件提升鲁棒性，且对正常性能几乎无损伤。
- **全面的基准构建**：提供了十余种主流方法的 LiDAR、4D 雷达、融合三种模态的详细评测，极大方便社区对比开发。
- **实现两种融合扩展策略**（SA2MA、SM2MM），展示了如何将已有单/多模态方法适配到协同融合框架，具有通用性。
- **实验坚实**：仿真+真实、多种天气、详细消融，结论可信度高。

## 8. 不足与局限
- **仿真域差距**：V2X‑R 为纯仿真数据集，尽管对 LiDAR 做了雾雪物理建模，但 4D 雷达的仿真可能无法完全复现真实传感器的噪声特性、多径效应等，模型迁移到真实场景仍需进一步验证（仅 K‑Radar 做了部分验证）。
- **类别单一**：当前仅标注车辆 class，未包含行人、非机动车等其他道路使用者，限制了应用范围。
- **4D 雷达利用不充分**：尽管强调了多普勒速度信息，但文中并未明确在特征或网络设计中显式利用速度通道，融合方式仍较初级（BEV 拼接或自注意力），如何更深度地提取 4D 雷达的独特信息值得探索。
- **计算开销**：MDD 引入 T=3 步扩散，推理延迟增加约 32 ms，虽能保持实时，但在资源受限的平台可能仍需优化。
- **智能体数量固定**：实验设定智能体数量在 2~5 之间，未讨论更大规模或动态变化的拓扑对性能的影响。
- **损失权重设计依赖经验**：γ(e,ψ) 中的 τ、φ 需手动调整，超参敏感性可能在不同数据集上需要重新搜索。

（完）
