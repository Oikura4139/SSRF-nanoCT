---
tags:
  - papers/CT
  - papers/medical-imaging
aliases:
  - "GaSpCT 中文全文翻译"
date: 2024-04-04
doi: 10.48550/arXiv.2404.03126
arxiv_id: 2404.03126
document_type: full_translation
---

# GaSpCT：用于新颖 CT 投影视图合成的高斯泼溅（全文中文翻译）

> [!info] 翻译说明
> 本文根据作者提供的 `arXiv:2404.03126v1` PDF 完整翻译。保留原文的章节、公式编号、图表编号和文献编号；参考文献的书目信息及英文题名按原文保留，以避免改动可检索信息。原 PDF 中的模板残留文字（如页眉中的“Abbreviated paper title”和小节标题后的 `[H]`）不属于论文内容，译文不再重复。

## 题目、作者与机构

**题目：** GaSpCT：用于新颖 CT 投影视图合成的高斯泼溅

**作者：** Emmanouil Nikolakakis¹、Utkarsh Gupta²、Jonathan Vengosh²、Justin Bui²、Razvan Marinescu²

1. 加利福尼亚大学圣克鲁兹分校，电气与计算机工程系
2. 加利福尼亚大学圣克鲁兹分校，计算机科学与工程系

## 摘要

我们提出 `GaSpCT`，这是一种用于为计算机断层成像（CT）扫描生成新投影视图的新颖视图合成与三维场景表示方法。我们对高斯泼溅框架进行改造，使其能够在不依赖运动恢复结构（SfM）方法的情况下，仅根据有限数量的二维图像投影完成 CT 新颖视图合成。因此，我们可以减少扫描总时长以及扫描过程中患者接受的辐射剂量。我们针对这一应用调整了损失函数，通过两个促进稀疏性的正则项——`Beta` 损失和全变分（TV）损失——强化背景与前景的区分。最后，我们利用关于视野内脑部预期位置的均匀先验分布，在三维空间中初始化高斯的位置。我们使用帕金森病进展标志物计划（PPMI）数据集中的脑部 CT 扫描评估模型性能。结果表明，渲染得到的新视图与模拟扫描的原始投影视图高度一致，而且性能优于其他隐式三维场景表示方法。此外，与基于神经网络的稀疏视角 CT 图像重建合成方法相比，我们在实验中观察到训练时间缩短。最后，与等效的体素网格图像表示相比，高斯泼溅表示的内存需求降低了 `17%`。

**关键词：** 高斯泼溅；稀疏视角 CT 重建；新颖视图合成

## 1 引言

神经辐射场（NeRF）[14] 等隐式场景表示模型已经对计算机视觉和计算机图形学应用产生了显著影响。这类技术把一个像素的坐标 $[X,Y,Z]$ 以及描述相机观察方向的极角 $[\phi,\theta]$ 映射到 `RGB` 值和透明度值，由此前馈神经网络的权重能够隐式容纳三维表示，并从新的观察角度渲染图像。高斯泼溅 [10] 是近期出现的一种隐式三维场景表示模型，它使用被称为“泼溅基元”的三维高斯来编码依赖视角的颜色值。这类模型更适合保持低细节视觉结构，可有效减轻图像颗粒感和运动引起的伪影。与 [2] 等先进 `NeRF` 模型相比，它们所需的训练时间显著更短，但内存占用更大。

新颖视图合成和三维场景表示非常适合用于医学成像系统，尤其是计算机断层成像。这是因为原始 CT 信号以投影正弦图的形式采集，随后可将其转换为各个角度的二维放射投影图像 [7]。为了减少扫描过程中患者接受的总剂量 [15]，一种典型做法是减少投影视图的数量。机器学习技术已经被用于低剂量 CT 重建：部分方法旨在去除因每个投影视图检测到的光子数减少而产生的颗粒状统计噪声 [3,22,6]；另一些方法则在二维图像域 [24,9,19] 或正弦图投影域 [5,11,8] 中处理稀疏视角重建。

然而，由于输入数据本身由二维投影组成，隐式表示模型有可能被用于一种新的 CT 重建形式：直接在图像域渲染新的投影视图，从而自然补偿投影视角不足的问题；而投影视角不足通常会产生条纹等结构性伪影。`MedNeRF` [4] 对 `GRAF` [18] 进行了改造，建立了用于 CT 重建的条件生成对抗网络（GAN），并允许以单幅二维 X 射线图像为输入，合成扫描的完整 `360°` 视图。不过，在此之前还没有工作将高斯泼溅用于 CT 新颖视图合成。

高斯泼溅适合用于 CT 有以下几个原因。第一，鉴于 CT 成像中的放射密度具有各向异性变化 [13]，高斯是表示 CT 图像的一种理想方式。第二，虽然 `NeRF` 模型能够更忠实地重建精细细节和较高频率成分，但它们经常产生“漂浮物”，即由运动引起的伪影 [21]。高斯泼溅更适合由低频成分组成的平滑图像，也较少产生类似伪影。最后，基于高斯泼溅的场景表示训练速度快得多，这一点对医学成像非常关键；而其较大的内存占用在这一领域并不是主要约束。

在本研究中，我们提出 `GaSpCT`，这是一种专门针对脑部 CT 成像应用增强的高斯泼溅模型。该模型只需使用全部投影视图的一半或更少作为训练集，就能准确编码一次 CT 扫描的三维信息。重建的三维场景能够在视野范围内任意相机位姿下以较高精度保持信号。在我们的实验中，训练过程需要 `5–10` 分钟；三维数据以多边形文件格式保存时占用 `27–42 MB`，小于其他基于体素网格或网格表面的方法。本文贡献概括如下：

- 我们提出 `GaSpCT`，一种隐式三维场景表示与新颖视图合成模型，可以从有限的投影数据集渲染新的脑部 CT 投影。该模型的内存占用较小，而且生成新视图的计算成本较低。
- 在 CT 成像中，未被患者占据的像素预期应具有空值或背景强度。为了提升合成视图的平滑性和稀疏性，我们在高斯泼溅基线损失中加入全变分损失和 `Beta` 分布负对数似然损失。
- 我们编写了一个脚本，从重建图像的医学数字成像和通信（DICOM）元数据中提取 CT 相机参数，并将其近似为针孔相机参数。这样便不再需要运动恢复结构（SfM）[17]；由于 CT 放射投影缺少清晰边缘，`SfM` 在这类图像上的表现很差 [1]。此外，我们还用表示预期患者脑部体积的三维椭球点云初始化模型。
- 我们首次在脑部 CT 投影图像上验证隐式三维场景表示，并向医学成像研究社区提供研究所使用的全部数据集。

## 2 方法

### 2.1 GaSpCT

我们的模型以高斯泼溅为基础。高斯泼溅与 `NeRF` 类似，是一种隐式三维场景表示模型。我们针对脑部 CT 扫描对其进行改造：在损失函数中加入两个促进稀疏性的正则项，并把点云初始化为与训练图像中的预期脑部结构相似的椭球。模型概览见图 1。

![图 1](images/page_003_fig_fig_1.png)
*图 1：以椭球形式初始化的三维高斯优化过程。利用从 DICOM 元数据中提取的相机位姿，可以通过可微高斯光栅化器完成前向传播和反向传播。*

### 2.2 高斯泼溅

在原始高斯泼溅模型中，一个三维场景被编码为一组三维高斯，即泼溅基元。每个高斯包含 `38` 个参数，用来编码其位置、协方差、颜色和不透明度。优化期间，从训练数据分布中采样一幅二维图像及其相机位姿。利用可微高斯光栅化器，从点云中按照该位姿渲染对应图像。随后计算渲染图像与真值之间的损失，并使用 `Adam` 优化器根据损失函数梯度执行反向传播。原始高斯泼溅模型优化下列损失函数：

$$
\mathcal{L}_{\mathrm{Original}}
=(1-\lambda)\mathcal{L}_1
+\lambda\mathcal{L}_{\mathrm{D\text{-}SSIM}}.
\tag{1}
$$

该损失由促进稀疏性的 $L_1$ 损失和动态结构相似性指数（D-SSIM）项组合而成，后者鼓励给定相机位姿下渲染图像与真值图像之间的相似性。利用这一损失，可以反向传播各项高斯属性的梯度，从而优化隐式表示。

#### 全变分正则化

我们在损失函数中加入全变分正则项。全变分会惩罚相邻像素之间的大幅变化，从而增强图像平滑性，并降低噪声伪影的影响。我们按照文献 [16] 实现全变分损失：

$$
\mathcal{L}_{\mathrm{TV}}
=\lambda_{\mathrm{TV}}
\sum_{i,j}^{N,M}
\left(
|p_{i+1,j}-p_{i,j}|+|p_{i,j+1}-p_{i,j}|
\right).
\tag{2}
$$

其中，$p$ 表示坐标 $(i,j)$ 处的像素值，$N$ 和 $M$ 分别为图像的高度和宽度。

#### Beta 分布正则化

我们采用文献 [12] 使用的 `Beta(0.5,0.5)` 分布负对数似然。该损失通过把背景值推向零并增强前景像素强度来促进稀疏性：

$$
\mathcal{L}_{\mathrm{beta}}
=\frac{1}{P}\sum_p
\left[
\log\left(I_{\alpha}(p)\right)
+\log\left(1-I_{\alpha}(p)\right)
\right].
\tag{3}
$$

其中，$P$ 为图像中像素 $p$ 的总数，$I_{\alpha}$ 为图像不透明度。

#### 总损失函数

我们把全变分正则项与 `Beta` 分布正则项组合起来，得到总损失函数：

$$
\mathcal{L}_{\mathrm{Final}}
=\lambda_1\mathcal{L}_1
+\lambda_{\mathrm{D\text{-}SSIM}}\mathcal{L}_{\mathrm{D\text{-}SSIM}}
+\lambda_{\mathrm{beta}}\mathcal{L}_{\mathrm{beta}}
+\lambda_{\mathrm{TV}}\mathcal{L}_{\mathrm{TV}}.
\tag{4}
$$

## 3 实验

### 3.1 数据集

#### 数字重建放射影像

我们使用帕金森病进展标志物计划（PPMI）研究提供的、已经去除身份信息的脑部 CT 扫描。原始数据是 `DICOM` 格式的三维图像，我们将其输入合成放射影像生成软件 `Plastimatch`，由该软件生成数字重建放射影像（DRR）。通过指定从 `DICOM` 元数据中取得的视野、患者和扫描仪参数，我们把三维 `DICOM` 图像作为输入模体来模拟一次 CT 扫描。`DRR` 的输出是一组新的投影图像。

我们生成 `360` 个投影视图，角分辨率为 `1°`，图像尺寸为 $128\times128$。总计使用这一流程为 `20` 名不同患者的脑部 CT 扫描生成 `DRR`，以涵盖不同受试者之间的解剖差异。

![图 2](images/page_005_fig_fig_2.png)
*图 2：上排为从 PPMI 数据集中获得的原始三维体素 DICOM 图像；该图像作为 DRR 算法的输入，用于生成投影视图。下排为生成的投影视图，角度依次为 0°、90° 和 180°。*

#### 在 CT 图像上使用运动恢复结构的困难

高斯泼溅要求把 `SfM` 软件的输出作为训练脚本输入。这些输出包括相机内参、相机外参，以及表示三维场景中已识别特征的点云。然而，将 `SfM` 应用于 CT 图像尤其困难，这是因为重建投影图像中的放射密度是逐渐变化的。因此，图像明显缺少能够支持准确、稳健特征提取的锐利边缘和精细细节。

#### CT 图像的相机外参与内参

由于高斯泼溅的梯度优化需要输入图像在三维场景中的相机位姿，我们利用 `DICOM` 元数据提供的 CT 扫描参数先验，以数学方式生成相机内参和外参。我们提取的变量包括成像空间的视野、探测器阵列尺寸、射线源到探测器的距离，以及射线源到患者的距离。

这些变量用于计算每个相机位姿的笛卡尔坐标 $(x,y,z)$。相邻位姿之间的极角按照 CT 数据集的角分辨率递增；由于我们把世界坐标原点设在 CT 视野中心，因此方位角固定为 $0$。

### 3.2 实验设置

我们的实现基于高斯泼溅的开源 Git 仓库。模型的全部训练和渲染均在 `Linux Ubuntu 20.04 Focal Fossa` 上完成。所有过程都运行在一张配备 `16 GB GDDR6 SDRAM` 的 `NVIDIA RTX A4000` 上。通过考察训练期间的学习损失曲线，我们决定在所有 `GaSpCT` 测试中执行 `20K` 次迭代。

## 4 结果

![图 3](images/page_006_fig_fig_3.png)
*图 3：四个不同角度的视图，分别为（a）0°、（b）90°、（c）180°、（d）270°。上排为真值图像，下排为等效相机位姿下的渲染图像。*

![图 4](images/page_006_fig_fig_4.png)
*图 4：在分别使用全部图像的（a）50%、（b）25%、（c）10% 和（d）5% 进行测试时，同一投影视图的四种渲染结果。*

我们在 `20` 名不同受试者的 `20` 组投影视图扫描上运行模型。训练时，我们使用 `360` 幅图像中的 `180` 幅，其余图像用于测试。为了根据留出的真值评价渲染图像质量，我们使用以下指标：峰值信噪比（PSNR）、结构相似性指数（SSIM）[20]，以及采用 `VGG` 网络计算的学习感知图像块相似度（LPIPS）[23]。全部指标见表 1。

每组扫描的优化过程耗时 `5–10` 分钟。训练过程中优化的参数总数介于 $4.6\times10^5$ 与 $6.2\times10^5$ 之间。最后，每个输出多边形文件（PLY）占用的存储空间为 `27–42 MB`。

![表 1](images/page_007_fig_table_1.png)
*表 1：使用训练数据集中 50% 的视图时，GaSpCT 在脑部 CT 数据集上的性能及其与其他模型的比较。*

| 指标 | MedNeRF | MipNeRF360 | Gaussian Splatting | GaSpCT |
|---|---:|---:|---:|---:|
| PSNR ↑ | $30.36\pm0.33$ | $27.67\pm0.23$ | $40.79\pm1.06$ | **$43.17\pm1.03$** |
| SSIM ↑ | $0.558\pm0.055$ | $0.14\pm0.03$ | $0.99\pm0.002$ | **$0.993\pm0.0014$** |
| LPIPS ↓ | $0.341\pm0.031$ | $0.9\pm0.05$ | $0.017\pm0.0037$ | **$0.0059\pm0.0015$** |

![表 2](images/page_007_fig_table_2.png)
*表 2：在不同投影视图比例用于评估时，GaSpCT 在脑部数据集上的性能。*

| 指标 | 50% 视图 | 25% 视图 | 10% 视图 | 5% 视图 |
|---|---:|---:|---:|---:|
| PSNR ↑ | $43.17\pm1.03$ | $42.03\pm0.95$ | $38.5\pm1.21$ | $34.01\pm1.59$ |
| SSIM ↑ | $0.993\pm0.0014$ | $0.994\pm0.0015$ | $0.976\pm0.0015$ | $0.936\pm0.017$ |
| LPIPS ↓ | $0.0059\pm0.0015$ | $0.01\pm0.0028$ | $0.037\pm0.0089$ | $0.08\pm0.016$ |

在表 1 中，我们把本方法的指标与高斯泼溅基线模型进行比较。高斯泼溅要求由 `SfM` 软件提供相机位姿，但由于无法从 CT 数据集中提取足够特征，`SfM` 会失败。因此，我们向基线高斯泼溅自动提供全部 CT 投影的相机位姿向量，对其加以增强。我们的模型优于这一高斯泼溅基线。定量评价指标表明，超参数优化、在椭球范围内初始化泼溅基元，以及针对 CT 数据定制损失函数，共同使合成的三维视图更接近真值观测。两个模型都训练了 `20K` 次迭代。

此外，我们还把结果与 `MedNeRF` 和 `MipNeRF360` 进行比较。据我们所知，`MedNeRF` 是另一种使用隐式场景表示合成二维 CT 投影图像的开源模型；`MipNeRF360` 则使我们能够与能力很强的隐式三维场景表示方法进行比较。

`MedNeRF` 采用不同的新投影合成路线。它利用来自不同实验的大量 CT 扫描来训练一个基于 `GRAF` 的条件生成对抗网络，从而建立具有三维感知能力的潜在分布。当输入来自一次未见 CT 扫描的单幅 X 射线放射影像时，该模型会进一步迭代训练一个新生成器，并合成其余投影。我们使用来自 `20` 个数据集的全部投影图像，将基线 `GRAF` 生成器训练 `10K` 次迭代。之后，从每个数据集中提供一幅图像，并在该潜在分布上进一步训练 `10K` 次迭代，生成其余 `359` 个视图。

我们的指标优于 `MedNeRF`。这是可以预期的，因为 `GaSpCT` 针对单次三维 CT 扫描进行训练，而不是针对由多次扫描建立的广义潜在分布进行训练。

训练 `MipNeRF360` 后，我们发现，在 `80K` 次迭代、批量大小为 `4096` 条射线的设置下，脑部 CT 数据集仍未得到正确优化。如果延长训练时间，图像有可能变得准确；但 `MipNeRF360` 与 CT 数据集的兼容性还需要更深入的研究。

最后，我们还研究了在训练期间向模型隐藏更多数据时 `GaSpCT` 的性能，结果见表 2。从图 4 可以看出，即使只提供 `5%` 的投影图像，渲染视图仍与真值非常接近。这些结果为 CT 图像的三维隐式场景表示以及脑部 CT 放射影像的新颖视图合成建立了新的先进水平。

## 5 结论与未来工作

我们提出了 `GaSpCT`，即第一种用于脑部 CT 成像的隐式三维场景表示方法。我们对高斯泼溅基线模型进行改造，加入适当的稀疏正则项，并针对脑部 CT 放射影像调整点的初始化，同时消除了对 `SfM` 方法的依赖。我们使用由 `PPMI` 脑部图像作为模拟模体生成的 `20` 组 `DRR` 测试了该方法。结果表明，本方法优于该领域当前的先进方法。

我们的工作为进一步研究留下了许多空间。一个重要的下一步是编写一种与 CT 成像探测器阵列更相符的新型相机模型，该探测器阵列位于弯曲的正交平面上。这种近似会比当前使用的针孔相机近似准确得多。还值得研究并改造 `SfM` 方法中的边缘检测与特征提取，以准确定义初始点云。最后，我们计划探索用高斯泼溅表示建立多个医学扫描潜在表示的潜力。

## 致谢

我们使用了 `PPMI` 提供的开放获取脑部 CT 数据集。为了合成实验所需的 `DRR`，我们使用了开源医学图像计算软件 `Plastimatch`。最后，我们的模型实现以 `INRIA` 的高斯泼溅实现为基础。

## 参考文献

1. Allaire, S., Kim, J. J., Breen, S. L., Jaffray, D. A., Pekar, V. *Full orientation invariance and improved feature selectivity of 3D SIFT with application to medical image analysis*. 2008 IEEE Computer Society Conference on Computer Vision and Pattern Recognition Workshops, 1–8. IEEE, 2008.
2. Barron, J. T., Mildenhall, B., Verbin, D., Srinivasan, P. P., Hedman, P. *Mip-NeRF 360: Unbounded anti-aliased neural radiance fields*. Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, 5470–5479, 2022.
3. Chen, H., Zhang, Y., Kalra, M. K., Lin, F., Chen, Y., Liao, P., Zhou, J., Wang, G. *Low-dose CT with a residual encoder-decoder convolutional neural network*. IEEE Transactions on Medical Imaging, 36(12), 2524–2535, 2017.
4. Corona-Figueroa, A., Frawley, J., Bond-Taylor, S., Bethapudi, S., Shum, H. P., Willcocks, C. G. *MedNeRF: Medical neural radiance fields for reconstructing 3D-aware CT-projections from a single X-ray*. 2022 44th Annual International Conference of the IEEE Engineering in Medicine & Biology Society, 3843–3848. IEEE, 2022.
5. Dong, X., Vekhande, S., Cao, G. *Sinogram interpolation for sparse-view micro-CT with deep learning neural network*. Medical Imaging 2019: Physics of Medical Imaging, 10948, 692–698. SPIE, 2019.
6. Gao, Q., Shan, H. *CocoDiff: A contextual conditional diffusion model for low-dose CT image denoising*. Developments in X-Ray Tomography XIV, 12242. SPIE, 2022.
7. Gopalakrishnan, V., Golland, P. *Fast auto-differentiable digitally reconstructed radiographs for solving inverse problems in intraoperative imaging*. Workshop on Clinical Image-Based Procedures, 1–11. Springer, 2022.
8. Guan, B., Yang, C., Zhang, L., Niu, S., Zhang, M., Wang, Y., Wu, W., Liu, Q. *Generative modeling in sinogram domain for sparse-view CT reconstruction*. IEEE Transactions on Radiation and Plasma Medical Sciences, 2023.
9. Han, Y., Ye, J. C. *Framing U-Net via deep convolutional framelets: Application to sparse-view CT*. IEEE Transactions on Medical Imaging, 37(6), 1418–1429, 2018.
10. Kerbl, B., Kopanas, G., Leimkühler, T., Drettakis, G. *3D Gaussian Splatting for real-time radiance field rendering*. ACM Transactions on Graphics, 42(4), 2023.
11. Lee, H., Lee, J., Kim, H., Cho, B., Cho, S. *Deep-neural-network-based sinogram synthesis for sparse-view CT image reconstruction*. IEEE Transactions on Radiation and Plasma Medical Sciences, 3(2), 109–119, 2018.
12. Lombardi, S., Simon, T., Saragih, J., Schwartz, G., Lehrmann, A., Sheikh, Y. *Neural Volumes: Learning dynamic renderable volumes from images*. arXiv:1906.07751, 2019.
13. McCollough, C. H., Yu, L., Kofler, J. M., Leng, S., Zhang, Y., Li, Z., Carter, R. E. *Degradation of CT low-contrast spatial resolution due to the use of iterative reconstruction and reduced dose levels*. Radiology, 276(2), 499–506, 2015.
14. Mildenhall, B., Srinivasan, P. P., Tancik, M., Barron, J. T., Ramamoorthi, R., Ng, R. *NeRF: Representing scenes as neural radiance fields for view synthesis*. Communications of the ACM, 65(1), 99–106, 2021.
15. Power, S. P., Moloney, F., Twomey, M., James, K., O’Connor, O. J., Maher, M. M. *Computed tomography and patient risk: Facts, perceptions and uncertainties*. World Journal of Radiology, 8(12), 902, 2016.
16. Rudin, L. I., Osher, S. *Total variation based image restoration with free local constraints*. Proceedings of the 1st International Conference on Image Processing, 1, 31–35. IEEE, 1994.
17. Schönberger, J. L., Frahm, J. M. *Structure-from-Motion revisited*. Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, 4104–4113, 2016.
18. Schwarz, K., Liao, Y., Niemeyer, M., Geiger, A. *GRAF: Generative radiance fields for 3D-aware image synthesis*. Advances in Neural Information Processing Systems, 33, 20154–20166, 2020.
19. Shu, Z., Entezari, A. *Sparse-view and limited-angle CT reconstruction with untrained networks and deep image prior*. Computer Methods and Programs in Biomedicine, 226, 107167, 2022.
20. Wang, Z., Bovik, A. C., Sheikh, H. R., Simoncelli, E. P. *Image quality assessment: From error visibility to structural similarity*. IEEE Transactions on Image Processing, 13(4), 600–612, 2004.
21. Warburg, F., Weber, E., Tancik, M., Holynski, A., Kanazawa, A. *NeRFBusters: Removing ghostly artifacts from casually captured NeRFs*. arXiv:2304.10532, 2023.
22. Yang, Q., Yan, P., Zhang, Y., Yu, H., Shi, Y., Mou, X., Kalra, M. K., Zhang, Y., Sun, L., Wang, G. *Low-dose CT image denoising using a generative adversarial network with Wasserstein distance and perceptual loss*. IEEE Transactions on Medical Imaging, 37(6), 1348–1357, 2018.
23. Zhang, R., Isola, P., Efros, A. A., Shechtman, E., Wang, O. *The unreasonable effectiveness of deep features as a perceptual metric*. Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, 586–595, 2018.
24. Zhang, Z., Liang, X., Dong, X., Xie, Y., Cao, G. *A sparse-view CT reconstruction method based on combination of DenseNet and deconvolution*. IEEE Transactions on Medical Imaging, 37(6), 1407–1417, 2018.
