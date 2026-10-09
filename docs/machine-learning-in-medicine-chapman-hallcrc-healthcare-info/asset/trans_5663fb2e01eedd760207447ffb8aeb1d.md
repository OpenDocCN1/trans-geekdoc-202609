

## 5.1 引言

激活函数以及 $\beta$ 是一个可训练参数。当 $\beta$ 趋近于无穷大时，sigmoid 激活函数趋近于 ReLU 函数。当 $\beta$ 为零时，Swish 变为缩放线性函数 $f(x)=x/2$。根据作者的观点，Swish 可以被视为一个光滑函数，它在线性函数和 ReLU 函数之间进行非线性插值。在实验中，Swish 始终优于 ReLU 和其他非线性函数。

另一个可学习的激活函数是墨西哥 ReLU（MeLU），由 Maguolo 等人 [25] 提出，因其形状类似于著名的墨西哥帽小波而得名。MeLU 是一种分段线性激活函数，是 PReLU 和多个墨西哥帽函数之和。这个分段函数拥有许多参数（ collectively 视为超参数），其取值范围从零到无穷大，并具有许多理想特性：
- 其梯度很少平坦
- 在任何方向上都不会发生饱和
- 当参数数量趋于无穷大时，它可以近似紧集上的任何连续函数
- 修改单个参数仅在小区间内改变激活函数，从而简化优化过程

在本章中，我们基于 MeLU 提出了一种新的激活函数，一种高斯型学习单元，我们称之为（GaLU），因为它是一种分段线性激活函数，是 PReLU 和多个一阶高斯小波之和。我们使用三种不同的 CNN 架构（Vgg16 [26]、ResNet50 [27] 和 DenseNet201 [28]）在 13 个中小型生物医学数据集上比较了若干种先进激活函数与 GaLU，结果表明激活函数的集成显著优于每个单独的函数。

本章其余部分组织如下。在第 5.2 节中，我们描述了本工作中测试的八种先进激活函数以及此处提出的新方法。在第 5.3 节中，我们在 13 个不同的数据集上评估了所有九种激活函数。最后，在第 5.4 节中，我们通过提出一些未来研究建议来结束本章。

## 5.2 三种 CNN 的激活函数

为了将我们的方法与文献中提出的一些性能最佳的激活函数进行比较，我们将它们替换到三个著名的在 ImageNet 上预训练的 CNN 中：Vgg16 [26]、ResNet50 [27] 和 DenseNet201 [28]。ResNet50 是一个具有 50 层的 CNN，以其跳跃连接 [6] 而闻名，这些连接直接将给定的第 $n$ 层连接到某个第 $n+k$ 层。与标准 CNN 中卷积后接激活的方式不同，在跳跃连接中，块的输入加到其输出上，这一过程促进了梯度的传播。DenseNet201 [28] 与 ResNet 相似，但每一层都是相互连接的，这种架构也导致了强烈的梯度流动。VGG16 [26] 是一个 CNN，其中输入通过由堆叠卷积滤波器组成的块传递，这些块具有与较大卷积滤波器相同的效果，但由于涉及的参数较少，因此效率更高。

本研究中比较的九种激活函数是引言中简要提到的八种（ReLU [16]、Leaky ReLU [29]、ELU [19]、SELU [20]、PReLU [14]、APLU [21]、SReLU [30] 和 MeLU [25]）以及此处提出的方法 GaLU。这些激活函数在本节其余部分中详细说明。

### 5.2.1 ReLU

ReLU [16]（见图 5.1）定义为

$$y_i = f(x_i) = \begin{cases} 0, & x_i < 0 \\ x_i, & x_i \geq 0. \end{cases}$$

![](img/6554116edbb19a8210b75a29243fd6ec_79_0.png)

图 5.1 ReLU (a)、Leaky ReLU (b) 和 ELU (c)。

ReLU 的梯度为

$$\frac{dy_i}{dx_i} = f'(x_i) = \begin{cases} 0, & x_i < 0 \\ 1, & x_i \geq 0. \end{cases}$$

### 5.2.2 Leaky ReLU

Leaky ReLU [18]（见图 5.1）定义为

$$y_i = f(x_i) = \begin{cases} ax_i, & x_i < 0 \\ x_i, & x_i \geq 0 \end{cases}$$

其中 $a$ 是一个小实数（此处 $a = 0.01$）。如引言中所述，与 ReLU 不同，该函数没有梯度为零的点：

$$\frac{dy_i}{dx_i} = f'(x_i) = \begin{cases} a, & x_i < 0 \\ 1, & x_i \geq 0 \end{cases}$$

### 5.2.3 ELU

指数线性单元（ELU）[19]（见图 5.1）定义为

$$y_i = f(x_i) = \begin{cases} a(\exp(x_i)-1), & x_i < 0 \\ x_i, & x_i \geq 0 \end{cases}$$

其中 $a$ 是一个实数（此处 $a = 1$）。

ELU 是可微的，其梯度始终为正（与 Leaky ReLU 一样），并且有下界 $-a$。ELU 的梯度由下式给出

$$\frac{dy_i}{dx_i} = f'(x_i) = \begin{cases} a \exp(x_i), & x_i < 0 \\ 1, & x_i \geq 0 \end{cases}$$

### 5.2.4 SELU

其中 *a* 和 *s* 都是实数（此处 *a*=1.6733 和 *s*=1.0507；这些值与参考文献 [20] 中使用的值相同，并选择用于将均值为零、方差为单位的随机变量映射为均值为零、方差为单位的随机变量）。

请注意，SELU 基本上与 ELU 相同，但额外乘以缩放参数 *s* 以防止梯度消失或爆炸。SELU 的梯度由下式给出

$$\frac{dy_{i}}{dx_{i}} = f^{\prime}\left(x_{i}\right) = \begin{cases} sa \ \exp \left(x_{i}\right), \ x_{i} < 0 \\ s, \ x_{i} \geq 0 \end{cases}$$

### 5.2.5 PReLU

参数 ReLU（PReLU）[14] 定义为

$$y_{i} = f \left(x_{i}\right) = \begin{cases} a_{c}x_{i}, \ x_{i} < 0 \\ x_{i}, \ x_{i} \geq 0 \end{cases}$$

其中 *aᵢ* 包含针对输入每个通道都不同的实数。PReLU 与 Leaky ReLU 相同，除了参数 *aᵢ* 是可学习的。

PReLU 的梯度为

$$\frac{dy_{i}}{dx_{i}} = f^{\prime \prime}\left(x_{i}\right) = \begin{cases} a_{c}, \ x_{i} < 0 \\ 1, \ x_{i} \geq 0 \end{cases} \quad \text{and} \quad \frac{dy_{i}}{da_{c}} = \begin{cases} x_{i}, \ x_{i} < 0 \\ 0, \ x_{i} \geq 0 \end{cases}$$

请注意，左侧斜率均初始化为 0。

### 5.2.6 SReLU

S 形 ReLU（SReLU）[30] 由三个分段线性函数组成，由四个可学习参数表示，因此

$$y_{i} = f \left(x_{i}\right) = \begin{cases} t^{l} + a^{l}\left(x_{i} - t^{l}\right), \ x_{i} < t^{l} \\ x_{i}, \ t^{l} \leq x_{i} \leq t^{r} \\ t^{r} + a^{r}\left(x_{i} - t^{r}\right), \ x_{i} > t^{r} \end{cases} \quad, \quad$$

其中 \( t^{l} \)、\( t^{r} \)、\( a^{l} \) 和 \( a^{r} \) 是四个可学习的实数参数（初始化为 \( a^{l} \)=0，\( t^{l} \)=0，且 \( t^{r} \)=maxInput，其中 maxInput 是一个超参数）。SReLU 相当大的参数数量带来了高的表示能力。

SReLU 的梯度由下式给出

![](img/6554116edbb19a8210b75a29243fd6ec_82_0.png)

![](img/6554116edbb19a8210b75a29243fd6ec_82_1.png)

![](img/6554116edbb19a8210b75a29243fd6ec_82_2.png)

### 5.2.7 APLU

自适应分段线性单元（APLU）[21] 定义为

![](img/6554116edbb19a8210b75a29243fd6ec_82_3.png)

其中 \( a_{c} \) 和 \( b_{c} \) 是实数，对于输入的每个通道都不同。APLU 是一个分段线性函数，能够近似如引言中所述的紧集上的任何连续函数。

APLU 的梯度由 ReLU 的梯度以及和中包含的函数的梯度之和给出。关于参数 \( a_{c} \) 和 \( b_{c} \)，梯度为

![](img/6554116edbb19a8210b75a29243fd6ec_82_4.png)

在本研究中，参数 \( a_{c} \) 初始化为 0，而点则随机初始化。在参数 \(a_{c}\) 的范数上添加了 0.001 \( L^{2} \) 惩罚。因此，损失函数中包含了另一项，定义为

$$ L^{reg} = \sum_{c=1}^{n} |a_c|^{2} $$

还针对这些参数添加了相对学习率：\(maxInput\) 乘以网络其余部分使用的最小学习率。因此，如果 \(\lambda\) 是全局学习率，参数 \(a_{c}\) 的学习率 \(\lambda^{c}\) 将是

$$ \lambda^{c} = \frac{\lambda}{maxInput} $$

### 5.2.8 MeLU

为了理解墨西哥 ReLU（MeLU）[25]，令 \(\phi^{a,\lambda}(x) = \max(\lambda - |x-a|, 0)\) 为“墨西哥帽型”函数，其中 \(a\) 和 \(\lambda\) 是实数。当 \(|x-a| > \lambda\) 时，函数 \(\phi^{a,\lambda}(x)\) 为零，但在 \(a\) 和 \(a-\lambda\) 之间以导数 1 持续增加，并在 \(a\) 和 \(a+\lambda\) 之间以导数 \(-1\) 减少。

上述函数充当 MeLU 的构建块，其定义为

$$ y_{i} = \text{MeLU}(x_{i}) = \text{PReLU}^{c_{0}}(x_{i}) + \sum_{j=1}^{k-1} c_{j} \phi^{a_{j},\lambda_{j}}(x_{i}) $$

其中 \(k\) 是每个可学习参数的数量（每个通道一个 PReLU 参数和墨西哥帽函数和中 \(k-1\) 个系数；此处 \(k=4\) 或 8），\(c_{j}\) 是可学习参数，\(c_{0}\) 是 PReLU 中的参数向量，\(a_{j}\) 和 \(\lambda_{j}\) 均为固定值并递归选择。

首先，设置参数 \(maxInput\)。第一个墨西哥帽函数在 \(2 \cdot maxInput\) 处达到最大值，在 0 和 \(4 \cdot maxInput\) 处为零。接下来的两个函数选择在区间 \([0, 2 \cdot maxInput]\) 和 \([2 \cdot maxInput, 4 \cdot maxInput]\) 外部为零，要求它们在 \(maxInput\) 和 \(3 \cdot maxInput\) 处达到最大值（表 5.1）。

由于墨西哥帽函数是连续的且分段可微，因此 MeLU 也是如此。如果所有 \(c_{i}\) 可学习参数都初始化为零，
