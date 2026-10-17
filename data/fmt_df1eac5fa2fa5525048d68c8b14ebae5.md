
Rosa `et al` \[110\] employed artificial neural networks to characterize LI and MA pixels in 55 ultrasonography CCA images. To extract features from the LI‑MA interface, the authors used trained autoencoders \[107\]. Autoencoders are neural networks programmed to replicate the input. They are commonly used for unsupervised learning to uncover complex relationships in images. Given an input  ∈ \[0,1\]^(*d**x*)inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-2244-7ch9ieqn63.gif"/, using one or more hidden layers, the autoencoder converts it to a compressed representation `Y` ∈ \[0,1\]^(*d**y*)inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-2244-7ch9ieqn64.gif"/, with the mapping function similar to equation 9.3. Finally, the compressed image is resized back to its original dimensions. This is done to understand the basic structures and relationships of the input vector and to enable training for regeneration. The characteristics are represented by a compressed representation of neighboring pixels. Figure 9.6(i) shows a representation of the autoencoder. The ROI extraction method is similar to that used by \[92\]. The authors used five ground‑truth images to train two autoencoders. The two autoencoders were trained on the neighborhood pixels of the LI and MA interfaces. Two ANNs for pixel characterization were trained using the LI and MA characteristics. Finally, the LI and MA boundaries were extracted from the offline CCA images, and superfluous LI and MA pixels were removed via post‑processing. The classification’s cIMT bias was 0.0499 ± 0.0498 mm. The model is shown in figure 9.6 (ii) while the outcomes are shown in figure 9.6(iii).

![Figure 9.6. (i) An autoencoder, (ii) process model, and (iii) image outputs. ((i) and (ii) Reproduced with permission of Springer from \[162\]. Copyright 2021 Society for Imaging Informatics in Medicine. (iii) Reproduced with permission from \[110\]. Copyright 2015 Elsevier.)](images/bk978-0-7503-2244-7ch9f6_online.jpg)

(i) 一个自动编码器， (ii) 过程模型， (iii) 图像输出。 ((i) 和 (ii) 经 Springer 许可复制 162。版权所有 2021 Society for Imaging Informatics in Medicine。 (iii) 经 Elsevier 许可复制 110。版权所有 2015 Elsevier。

## 9.4.2 全卷积网络用于 cIMT 区域估计

Biswas *et al* \[111\] 从 396 份超声心动图 CCA 图像中，通过三步恢复 LI 和 MA 边界。两位经验丰富的放射科医生使用通用追踪软件 AtheroEdge™ \[66, 113, 114\] 对 LI 和 MA 边界进行描绘，生成的二值图作为基准真值。图像在第一个多尺度阶段的每侧各裁剪 10%，以确保低对比度和无关部分不影响第二阶段的学习。这通常是由于显影剂不足或抓取时探头与颈部接触不良造成的。第二阶段采用全卷积网络（FCN）将 cIMT 区域与图像其余部分分离。FCN 系统由两个子系统组成：编码器和解码器，如图 9.7 (i) 所示。编码器包含 13 层卷积（两层 64（窗口大小 = 3×3）+ 两层 128（窗口大小 = 3×3）+ 三层 256（窗口大小 = 3×3）+ 三层 512（窗口大小 = 3×3）+ 三层 512（窗口大小 = 3×3）），以及五层最大池化层，用于生成图像的下采样特征图。Rosa *et al* \[92\] 在子章节 9.3.1 中阐述卷积过程，该子章节对卷积核在像素级应用于图像，以提取上下文信息和位置不变性属性。每个最大池化步骤之前使用 1×1 卷积压缩特征图为单图。解码器包含三个上采样层、两个中间跳跃操作以及一个 `softmax` 层，用于像素与像素的比较与基准真值。卷积运算数学定义如下：

```math
h(a,b) = I(a,b) ⊗ k(a,b) = Σ_{s = -m/2}^{m/2} Σ_{t = -m/2}^{m/2} I(a + s, b + t) × k(a,b),
```

其中 `h` 为输出，`I` 为图像，`k` 为大小为 `m` × `m` 的卷积核，(`a`, `b`) 表示像素位置，`s`、`t` 为占位变量。最大池化通过保留每块图像中最重要的信息来实现下采样。图 9.7 (i) 展示了所使用的 FCN 模型。为获得原图 1/32 大小的特征图，编码器执行 13 层卷积（红框所示）和五层最大池化（蓝框所示），如图 9.7 (i) 所示。解码器通过三个上采样层（灰色框）和中间跳跃操作（绿色框）实现像素级的密集 `softmax` 分类（橙色框），并与基准真值进行比较。上采样是卷积的逆运算，作用于编码器末端的特征图。为恢复图像至原始尺寸，使用三个上采样层。跳跃连接将编码器的压缩层特征图与解码器的中间层特征图结合，以恢复下采样过程中丢失的空间信息。对于像素级特征，交叉熵损失函数为：

```math
θ_{class}(α_1,α_2) = (1/|N|) Σ_{n∈N} Σ_{l∈L} α_2_n(l) log(α_1_n(l)),
```

其中 `α[1]` 表示预测，`α[2]` 表示金标准（GT），`L` 为类别总数，`N` 为图像总数。`softmax` 层用于最终特征，将像素分配给概率最高的类别，公式如下：

```math
P(z_i) = e^{z_i} / Σ_{j=1}^{N} e^{z_j},
```

其中 `z[i]` 表示第 `i` 类实例的归一化得分。将 DL 迭代次数固定为 20 000，可得到分割图像。最后，第三阶段利用校准和矩阵逆运算 \[115\] 对 MA 边界进行细化。图 9.7 (ii) 展示了 LI 和 MA 边界以及其基准真值。两个基准真值的 cIMT 偏差分别为 0.126 ± 0.134 mm 和 0.124 ± 0.10 mm。

![Figure 9.7. (i) FCN 模型，(ii) 使用 FCN 的 IMT 输出，(iii) 使用 FCN 的 TPA 输出。((i) 经 Springer 许可复制 [162]。版权所有 2021 Society for Imaging Informatics in Medicine。 (ii) 经 Elsevier 许可复制 [111]。版权所有 2018 Elsevier。 (iii) 经 Elsevier 许可复制 [103]。版权所有 2020 Elsevier.)](images/bk978-0-7503-2244-7ch9f7_online.jpg)

**Figure 9.7.** (i) FCN 模型，(ii) 使用 FCN 的 IMT 输出，(iii) 使用 FCN 的 TPA 输出。((i) 经 Springer 许可复制 162。版权所有 2021 Society for Imaging Informatics in Medicine。 (ii) 经 Elsevier 许可复制 111。版权所有 2018 Elsevier。 (iii) 经 Elsevier 许可复制 103。版权所有 2020 Elsevier。)

## 9.4.3 用于 PA 测量的 FCN

进入`/path/to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含它们的只读列表。

之后我们这样调用`cmd`命令：`cmd arg0 arg1 arg2`。

```
if (condVar > someVal) {console.log("xxx")}
```

## 9.4.4 Two-stage patching based AI model for cIMT and PA measurement

Biswas *et al* \[104\] recently used a two-stage DL based network to measure cIMT and PA. A CNN was employed in the first stage to extract the ROI, and an FCN identical to \[111\] was employed in the second stage to delineate the LI and MA boundaries and assess cIMT. A CNN differs from an FCN in that it uses a fully connected neural network for classification, whereas a trained FCN merely uses convolution and then up-sampling to build a feature map that represents semantic segmentation of the real image. Figure 9.8 (i) depicts a typical diagram of the two-layer CNN model. The image was finally characterized using the `softmax` classification function (equation 9.10). The scientists employed 22 deep layers \[116\] to extract high-level characteristics from the images in their study. The diabetic cohort initially had 250 CCA images collected. The AtheroEdge™ (AtheroPoint™, Roseville, CA) system was used to crop the image to remove background information and guarantee that the lumen region was in the center of the cropped CCA image. The cropped CCA image was split horizontally into two parts as a result. The bottom half of the image, which included the far wall, was removed and split horizontally. The wall information is in the upper half of the bottom half, while the tissue information is in the lower half. Both the upper and lower splits were separated into sixteen equal-sized patches on a column basis. The patches were used as input to the DL based two-stage system. To categorize the input images into wall and non-wall patches, an independent 22-layer CNN network \[116\] was used in the first stage. The accuracy of the CNN’s characterization performance was 99.5%. After the patches had been defined, the ROI segment was created by combining the wall patches patient by patient. Figure 9.8 (ii) depicts the preprocessing and DL stage 1 inputs and outputs. The second stage DL is trained using these ROI segments and their binary ground facts. The second stage DL system divides the ROI segment into plaque and non-plaque regions after it has been trained.

![Figure 9.8. (i) A CNN model, (ii) patching and reconstruction process, and (iii) outputs of the two-stage DL model. ((i) and (ii) Reproduced with permission of Springer from \[162\]. Copyright 2021 Society for Imaging Informatics in Medicine. (iii) Reproduced with permission from \[104\]. Copyright 2020 Elsevier.)](images/bk978-0-7503-2244-7ch9f8_online.jpg)

**Figure 9.8.** (i) A CNN model, (ii) patching and reconstruction process, and (iii) outputs of the two-stage DL model. ((i) and (ii) Reproduced with permission of Springer from \[162\]. Copyright 2021 Society for Imaging Informatics in Medicine. (iii) Reproduced with permission from \[104\]. Copyright 2020 Elsevier.)
