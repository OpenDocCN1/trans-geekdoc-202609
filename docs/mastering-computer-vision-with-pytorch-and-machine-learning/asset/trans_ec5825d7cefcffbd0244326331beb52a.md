

图 [9.4](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig4)(A) 中的二次曲线被用作原始图像，以在项目 [9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9ueqn7) 中演示 DDMP 从噪声生成图像的能力。四千批二次曲线被用于在 DDMP 系统中训练一个 `U-Net` 模型。图 [9.4](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig4)(A) 中的一批二次曲线是由单元格 01-03 中的代码生成的；这些代码在前几章中已被多次使用。每批有 64 条曲线，每条曲线上有 64 个点。正向过程的函数在单元格 04 中定义。该函数的超参数设置在该函数前面。对于这个简单的项目，总正向步数设置为 `T = 200`。模型训练的时间嵌入维度在单元格 04 的第 2 行设置为 100。采用线性调度，beta 值在 200 步内从 0.001 增加到 0.2（单元格 04 第 03 行）。那里还列出了许多其他超参数，例如 `α`、`ᾱ`、`√ᾱ` 和 `√(1 - ᾱ)`。仅使用一条原始曲线在时间步 `t = 1, 25, 50 和 199` 添加噪声，以便我们在图 [9.4](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig4)(B) 中查看正向过程。在过程结束时，`ᾱ₁₉₉ = 4.2 × 10^(−10)`。根据公式 ([9.2](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9eqn2))，原始图像对最后一个潜在图像 `x[199]` 的贡献可以忽略不计。最后一个潜在图像中仅存在标准高斯噪声 `ε`。根据经验法则，我们知道 99.7% 的高斯噪声值位于三个标准差以内。这就是为什么在图 [9.4](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig4)(B) 中 `x[199]` 的值沿 `y` 轴分布在 -3 和 3 之间。在单元格 04 中定义的 `q_sample` 函数中，一个 Pytorch 函数 `gather()` 对我们来说是新的。在一个额外的 VS code 单元格中运行以下代码，你将了解该函数如何根据另一个 1D 张量 `t` 从 1D 张量 `z` 中选取元素：`z = torch.tensor([1, 2, 3, 4, 9]); t = torch.tensor([2, 0]); z.gather(dim = −1, index = t)`。这些额外代码的输出是 `[3, 1]`，即 `[z[t[0]], z[t[1]]]`。

![](images/bk978-0-7503-6244-3ch9uf7_pr.gif)

![](images/bk978-0-7503-6244-3ch9uf7b_pr.gif)

![图 9.4. DDPM 的正向和反向过程。(A) 一批二次曲线（单元格 03 的输出）。(B) 正向过程中时间步 1、25、50 和 199 处的加噪图像或曲线（单元格 04 的输出）。(C) 从 `t = 199` 开始到 `t = 0` 结束的去噪图像（单元格 09 的输出）。](images/bk978-0-7503-6244-3ch9f4_online.jpg)

**图 9.4.** DDPM 的正向和反向过程。(A) 一批二次曲线（单元格 03 的输出）。(B) 正向过程中时间步 1、25、50 和 199 处的加噪图像或曲线（单元格 04 的输出）。(C) 从 `t = 199` 开始到 `t = 0` 结束的去噪图像（单元格 09 的输出）。

### 9.2.2 DDPM 中的反向过程

在物理世界中，混合两种材料比混合后再分离它们更容易。在 DDPM 的数字世界中也是如此。正向过程比反向过程容易得多。反向过程是另一个马尔可夫链，起始于纯噪声 `x[T] ∼ p[θ](x[T]) = N(x[T]; 0, I)`，并逐步向后进行以获得去噪的潜在图像：`x[T−1]…, x[t], x[t−1], …, x[0]`，其中 `θ` 代表 `U-Net` 的参数。图 [9.4](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9fig4)(C) 展示了从 `t = 199` 处纯噪声开始的反向过程结果。在时间步 `t−1`，潜在图像 `x[t−1]` 具有概率密度函数 (PDF) `p[θ](x[t−1]∣x[t]) = N(x[t−1]; μ[θ](x[t], t), β[t]I)`，其中 `μ[θ](x[t], t)` 来自训练好的 `U-Net` 模型。

反向 PDF `p[θ](x[t−1]∣x[t])` 对应于正向 PDF 的逆过程，且等于 `q(x[t−1]∣x[t], x[0])`，这被称为“正向过程后验分布”。详细推导见 DDPM 论文 (Ho *et al* [2020](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9bib1))。为求完整，以下公式 ([9.3](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9eqn3)) 和 ([9.4](#Chapter_9.xhtml#bk978-0-7503-6244-3ch9eqn4)) 来自附录 [I](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-I)

$$q(x_{t - 1}\mid x_{t},x_{0}) = \mathbb{N}(x_{t - 1};\widetilde{\mu}(x_{t},x_{0}),{\widetilde{\beta}}_{t}I) = q(x_{t}\mid x_{t - 1},x_{0})\frac{q(x_{t - 1}\mid x_{0})}{q(x_{t}\mid x_{0})}$$

(9.4)

$$\widetilde{\mu}\left( {x_{t},x_{0}} \right) = x_{t} - \frac{1 - \alpha_{t}}{\sqrt{1 - {\overline{\alpha}}_{t}}}\varepsilon$$

(9.5)

$${\widetilde{\beta}}_{t} = \frac{1 - {\overline{\alpha}}_{t - 1}}{1 - {\overline{\alpha}}_{t}}\beta_{t}$$

(9.6)

上述公式将用于模型训练的变分下界损失。反向过程的联合概率分布为：

$$p_{\theta}\left( x_{0:T} \right) = p_{\theta}\left( x_{T} \right)\prod\limits_{t = 1}^{T}{p_{\theta}\left( {x_{t - 1}\mid x_{t}} \right)} = p_{\theta}\left( {x_{0}\mid x_{1}} \right)p_{\theta}\left( {x_{1}\mid x_{2}} \right)\ldots p_{\theta}\left( {x_{T - 1}\mid x_{T}} \right)p_{\theta}\left( x_{T} \right)$$

(9.7)

由联合概率分布和 `∫q(x[0])dx[0] = 1`，我们得到系统用于模型训练的负对数似然（损失函数）：`L = −log (p[θ](x[0])) = −log ∫p[θ](x[0:T])dx[1:T]`

$$L = - \left( {\int q\left( x_{0} \right)dx_{0}} \right){\ \log\ }\int{q\left( {x_{1:T}\mid x_{0}} \right)}\frac{p_{\theta}\left( x_{0:T} \right)}{q\left( {x_{1:T}\mid x_{0}} \right)}dx_{1:T}$$

(9.8)

利用 Jensen 不等式，我们可以简化上述公式以得到系统的变分下界损失（附录 [I](#Appendix1.xhtml#bk978-0-7503-6244-3AppAsA-I)）

$$L < - \int q\left( x_{0} \right)dx_{0}\int q\left( {x_{1:T}\mid x_{0}} \right){\ \log\ }\frac{p_{\theta}\left( x_{0:T} \right)}{q\left( {x_{1:T}\mid x_{0}} \right)}dx_{1:T} = L_{VLB}$$

