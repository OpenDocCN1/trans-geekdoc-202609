
- Wu, K.; Peng, H.; Chen, M.; Fu, J.; Cao, H. Rethinking and Improving Relative Position Encoding for Vision Transformer. In *Proceedings of the IEEE/CVF International Conference on Computer Vision (ICCV)*, Montreal, QC, Canada, 10–17 October 2021; pp. 10033–10041.

- Srinivas, A.; Lin, T.Y.; Parmar, N.; Shlens, J.; Abbeel, P.; Vaswani, A. Bottleneck Transformers for Visual Recognition. In *Proceedings of the 2021 IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)*, Nashville, TN, USA, 20–25 June 2021; pp. 16514–16524. [CrossRef]

- Sun, J.; Xu, Z.; Shum, H.Y. Gradient Profile Prior and Its Applications in Image Super-Resolution and Enhancement. *IEEE Trans. Image Process.* **2011**, *20*, 1529–1542. [CrossRef] [PubMed]

- Cai, J.; Zeng, H.; Yong, H.; Cao, Z.; Zhang, L. Toward real-world single image super-resolution: A new benchmark and a new mode. In *Proceedings of the IEEE/CVF International Conference on Computer Vision (ICCV)*, Long Beach, CA, USA, 15–20 June 2019; pp. 3086–3095.

- Zhang, X.; Chen, Q.; Ng, R.; Koltun, V. Zoom to learn, learn to zoom. In *Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)*, Long Beach, CA, USA, 15–20 June 2019; pp. 3762–3770.

- Luo, C.; Jin, L.; Sun, Z. Moran: A multi-object rectified attention network for scene text recognition. *Pattern Recognit.* **2019**, *90*, 109–118. [CrossRef]

- Honda, K.; Fujita, H.; Kurematsu, M. Multi-Task Learning-Based Attentional Feature Fusion Network for Scene Text Image Super-Resolution. *New Trends Intell. Softw. Methodol. Tools Tech.* **2022**, *355*, 334–345. [CrossRef]

- Lai, W.S.; Huang, J.B.; Ahuja, N.; Yang, M.H. Deep Laplacian Pyramid Networks for Fast and Accurate Super-Resolution. In *Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)*, Honolulu, HI, USA, 21–26 July 2017; pp. 5835–5843. [CrossRef]

- Raffel, C.; Shazeer, N.; Roberts, A.; Lee, K.; Narang, S.; Matena, M.; Zhou, Y.; Li, W.; Liu, J.P. Exploring the limits of transfer learning with a unified text-to-text transformer. *J. Mach. Learn. Res.* **2020**, *21*, 1–67. Available online: http://jmlr.org/papers/v21/20-074.html (accessed on 8 November 2022).

这些方法仅考虑图像的全局信息，而忽略了细节。Retinex 理论基于色彩一致性，可以将彩色图像分解为反射部分和光照部分。如公式 (1) 所示：

$$S = R \circ I$$

(1)

其中 $\circ$ 表示逐像素乘法运算。$S$ 表示彩色图像，其中每个区域的光照不同。$R$ 表示反射部分，它是物体的固有物理属性，物体的真实颜色与亮度无关。$I$ 表示光照部分，它反映了拍摄对象的曝光程度。

### 2.1. 周围 Retinex 方法

单尺度 Retinex (SSR) 使用周围函数的卷积和输入图像来获取光照部分。SSR 算法的表达式如公式 (2) 所示：

$$R_i(x,y) = \lg \frac{L_i(x,y)}{L_i(x,y)} = \lg I_i(x,y) - \lg [F(x,y) * I_i(x,y)]$$

(2)

$$F(x,y) = \frac{1}{2 \pi \sigma^2} \cdot e^{-\frac{(x^2+y^2)}{\sigma^2}}$$

(3)

其中 $i$ 表示不同的 RGB 通道，$I_i(x,y)$ 表示输入图像，$L_i(x,y)$ 表示入射部分，由 $F(x,y)$ 和 $I_i(x,y)$ 的卷积场定义。$R_i(x,y)$ 表示反射部分。$F(x,y)$ 表示周围函数，如方程 (3) 所示，其中 $\sigma$ 是尺度参数；$\sigma$ 的大小决定了图像增强的效果 [15]。

多尺度 Retinex (MSR) 是多个尺度上 SSR 输出的加权和 [16]。MSR 算法的表达式如公式 (4) 所示：

$$R_{MSR}(x,y) = \sum_{i=1}^{N} \omega_n \cdot R_{ni}(x,y)$$

(4)

其中 $\omega_n$ 是权重值，$N$ 是尺度数量。$R_{ni}(x,y)$ 表示第 $n$ 个尺度的反射图像。$R_{ni}(x,y)$ 的周围函数表达式如公式 (5) 所示：

$$F_n(x,y) = \frac{1}{2 \pi \sigma^2} \cdot e^{-\frac{(x^2+y^2)}{\sigma^2}}$$

(5)

MSRCR 算法添加了一个颜色恢复因子 $C_i$，用于改善由 MSR 算法引起的色彩偏差问题 [17]，MSRCR 的表达式如公式 (6) 所示：

$$R_{MSR C R}(x,y) = C_i(x,y) R_{MSR_i}(x,y)$$

(6)

其中 $C_i(x,y)$ 表示 R、G 和 B 中第 $i$ 个通道的颜色恢复因子，其表达式如方程 (7) 所示：

$$C_i(x,y) = \beta \ln \left[ \alpha \cdot \frac{I_i(x,y)}{\sum_{j=1}^{S} I_j(x,y)} \right]$$

(7)

其中 $\beta$ 表示增益系数，$\alpha$ 表示非线性控制强度因子。根据 [18]，$\beta = 46$ 且 $\alpha = 125$。$S$ 表示光谱通道，$S = 1$ 表示灰度图像，$S = 3$ 表示 RGB 彩色图像。

### 2.2. Retinex-Net 模型

大多数现有的基于 Retinex 的图像增强方法依赖于对约束和参数的手动精心设计。因此，当这些方法应用于不同场景时，可能会受到模型容量的限制。Retinex-Net 可以自动学习输入弱光照图像的特征，解决了传统算法依赖手动设置参数的问题。Retinex-Net 的模型结构如图 1 所示。它由三部分组成：分解模型、调整模型和重构。也就是说，Decom-Net 和 Enhance-Net 构成了 Retinex-Net 的主网络。

![](img/e4200cc4308edaf8913e513b0f96dbb6_537_0.png)

Decom-Net 使用 $3 \times 3$ 卷积层来生成输入图像的特征，并使用线性整流函数 ReLU 作为激活函数。经过五个带有 ReLU 的 $3 \times 3$ 卷积层后，RGB 图像被分解为反射图像和光照图像。低光照图像 $S_{low}$ 和匹配的常光图像 $S_{normal}$ 分别输入到 Decom-Net 模型中，网络参数由这两张图像共享，并分解为相应的反射部分 ($R_{low}, R_{normal}$) 和光照部分 ($I_{low}, I_{normal}$)。比较图 1 中分解模型的输出图像可以看出，在常光和低光下的反射部分 $R_{low}$ 和 $R_{normal}$ 相对相似。相比之下，$I_{low}$ 和 $I_{normal}$ 之间光照部分的大差异表明，反射部分是图像的固有属性，不容易受原始拍摄光照强度的影响。光照部分决定了人眼观察图像时的视觉感知。

在反射图像的降噪过程中，主要使用三维块匹配算法 (BM3D) [19] 来减少反射部分的噪声，以获得降噪后的反射图像 $R_{low}'$。BM3D 的主要思想是在图像中以步长 $s$ 找到一个参考块，在参考块附近搜索，并找到一些与参考块差异较小的块。然后，这些块将被集成到一个三维矩阵中进行滤波，最后使用逆变换将结果融合到二维图像中，以获得降噪图像。

Enhance-Net 采用编码器-解码器结构，并输入由 Decom-Net 获得的光照部分 $I_{low}$。通过多个下采样层获得尺寸较小的特征图，以便在 Enhance-Net 中以更大的尺度角度重新分配光强，从而调整亮度。Enhance-Net 通过上采样重构图像的光强，对局部较亮的位置分配较低的亮度，对局部较暗的位置分配较高的亮度。此外，上采样层的输出按通道数级联，以调整不同的局部光照，并保持图像的全局光照一致性。同时，使用逐元素求和来引导跳跃连接从一个下采样层到其对应的镜像上采样层，从而使网络学习残差。低光照部分 $I_{low}$ 经过 Enhance-Net 处理后生成增强后的光照部分 $I'_{low}$。最后，通过相乘两张图像的像素以及降噪后的反射部分 $R'_{low}$，重组增强后的光照部分 $I'_{low}$，形成作为网络输出的增强图像 $S'_{low}$。

### 2.3. 图像增强测试与分析

在本文中，选择低光照下的图像，并评估 SSR、MSR、MSRCR 和 Retinex-Net 算法的增强效果。图 2a 是一张待处理的暗图像，其亮度和对比度较低。图 2b–e 是基于 SSR、MSR、MSRCR 和 Retinex-Net 四种增强算法的效果图。图 3a–e 是这些图像的灰度直方图。

![](img/e4200cc4308edaf8913e513b0f96dbb6_538_0.png)

![](img/e4200cc4308edaf8913e513b0f96dbb6_538_1.png)

从图 3a–e 的灰度直方图中可以看出，增强图像的基本结构与原图有相当大的不同，表明图像的亮度显著提高。结合增强效果和灰度直方图，显示 SSR 仅保留了低频部分，虽然提高了整体亮度，但丢失了输入图像的重要高频部分。MSR 对高亮区域的敏感度较低，并丢失了图像的色彩特征。尽管 MSRCR 恢复了色彩，但色彩保持能力不够好，且图像出现过曝。虽然 Retinex-Net 具有最快的处理速度，并且可以在不手动设置参数的情况下获得更好的增强效果，但它存在噪声大和颜色失真的现象。因此，本文引入注意力机制，并添加降噪损失和颜色损失，以改良传统的 Retinex-Net，旨在解决 Retinex-Net 无法保留图像纹理细节和颜色特征这一缺点。

## 3. 改进的 Retinex-Net 模型

在卷积过程中，默认特征图中的每个通道具有相同的重要性，而面对实际问题时，不同通道的重要性是不同的。注意力机制可以在卷积过程中重新分配输入权重。在 Retinex-Net 中引入注意力机制可以减少网络对图像无关特征的关注，仅聚焦于图像的关键部分，如颜色、纹理和形状，从而提高图像亮度和细节的处理能力。

### 3.1. 注意力机制及其深层连接的介绍

ECA-Net（高效通道注意力网络）是一种高效的通道注意力机制 [20]，它避免了先前注意力机制中的特征维度缩减，并实现了通道间信息的有效交互。在

### 3.2. 子网络改进

通道级全局平均池化（GAP）不进行维度缩减，它使用一维稀疏卷积操作来捕获当前通道及其 $k$ 个领域通道信息。领域通道信息的交互显著减少了参数数量并提升了性能。图4展示了ECA模块的结构。将ECA模块嵌入Decom-Net中，可以自适应地学习每个特征通道的重要性。在去噪过程中，每个噪声点会被归一化和加权，从而自动去除噪声点，提高分解图像的清晰度，并减少关键特征的损失。

![](img/e4200cc4308edaf8913e513b0f96dbb6_539_0.png)

假设来自前一个卷积层的输入是一个总共包含 $C$ 个通道的 $H \times W \times C$ 特征图，然后通过公式（8）利用全局平均池化将每个二维特征通道映射到一个实数 $Z$。输出一个 $1 \times 1 \times C$ 的全局描述特征，映射关系如公式（8）所示：

$$Z = \frac{1}{H \times W} \sum_{i=1}^{H} \sum_{j=1}^{W} X_{C}(i, j) \tag{8}$$

其中 $X_{C}(i, j)$ 表示输入特征图中的第 $C$ 个二维矩阵，它表示该层 $C$ 个特征图的数值分布，$Z$ 表示获得的全局信息。随后，卷积核大小为 $k$ 的一维卷积捕获局部跨通道交互信息，通过 Sigmoid 激活函数获得归一化权重，并作用于之前的特征图。为了使模型更轻量紧凑，ECA模型简化了先前注意力机制中SE模块的密集连接模式，避免了复杂的通道依赖或结合额外的空间注意力，仅考虑相邻通道中的信息交互。权重计算公式如公式（9）所示：

$$\omega_{i} = \sigma(\sum_{j=1}^{k} \omega_{i}^{j} y_{i}^{j}), y_{i}^{j} \in \Omega_{i}^{k} \tag{9}$$

其中 $\sigma$ 表示 Sigmoid 函数，$y_{i}$ 表示通道。$\omega_{i}$ 是通道 $y_{i}$ 的权重，$\omega_{i}^{k}$ 是 $y_{i}$ 的第 $k$ 个相邻通道集合，$k$ 是卷积核大小，表示局部跨通道交互的覆盖范围，即有多少个邻近通道参与该通道的注意力预测。同时，为避免手动调整 $k$ 的值，ECA模块会自适应地确定 $k$。具有卷积核大小 $k$ 的一维卷积可以实现有效的通道注意力模块，如公式（10）所示：

$$\omega = \sigma(\text{CID}_{k}(y)) \tag{10}$$

其中 $\text{CID}_{k}$ 表示卷积核为 $k$ 的一维卷积操作，$y$ 表示通道。跨通道信息交互的覆盖范围（即一维卷积的卷积核大小 $k$）与通道维度 $C$ 成正比。$k$ 和 $C$ 之间存在映射关系 $\varphi$。由于线性映射关系对某些相关特征存在局限性，映射关系 $\varphi$ 采用非线性映射。考虑到通道维度通常是2的指数倍，线性映射关系被引入到非线性映射关系中。通道维度 $C$ 与卷积核大小 $k$ 之间映射关系的表达式如公式（11）所示，其中 $\eta$ 和 $b$ 是代表线性映射关系的常数，取 $\eta=2, b=1$ [18]。

$$k = \varphi(C) = \left\lfloor \frac{\log _{2}(C)}{\eta} + \frac{b}{\eta} \right\rfloor _{odd} \quad (11)$$

尽管注意力机制在许多图像处理任务中发挥了良好作用，但它每次局限于当前特征，未能充分利用注意力机制。DCA-Net（深度连接注意力网络）可以在相邻的ECA注意力模块之间建立跳跃连接，使得信息在每个注意力模块之间交互，并且所有注意力模块共同训练 [21]。这提高了注意力机制学习图像重要特征的能力，并优化了 Retinex-Net 提取反射图像特征和恢复光照图像及颜色的性能。DCA模块即插即用，在不改变 Retinex-Net 模型内部结构的情况下提高了注意力性能。

DCA 使用由三部分组成的通用注意力框架：上下文提取、变换和融合，网络结构如图5所示。首先，ECA模块通过提取器 $g$ 利用全局平均池化从输入特征图 $X$ 中提取特征 $G$，其中 $X \in R^{H \times W \times C}$，$\omega_{g}$ 是提取操作的相关参数。提取器 $g$ 确定了相关参数，不再需要 $\omega_{g}$。然后，利用一维卷积核和激励函数，将提取的特征块转换为新的非线性注意力空间 $T$，输出 $T$ 可以表示为 $T=t(G, \omega_{t})$。$t$ 定义为特征变换操作，$\omega_{t}$ 是变换操作中使用的参数。最后，注意力图与原始卷积块特征融合，输出为 $X'=T \otimes X$。$\otimes$ 表示特征融合模式，当设计为缩放时，融合函数执行元素乘法，否则执行元素加法。综上所述，通用注意力模块的模型可以表示为公式（12）：
