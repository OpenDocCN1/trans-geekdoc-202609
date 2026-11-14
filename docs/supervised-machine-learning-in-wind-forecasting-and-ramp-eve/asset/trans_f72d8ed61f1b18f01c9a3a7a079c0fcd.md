

![](img/b53e39e35231af65df8ccaa99eb28bee_32_0.png)

图 2.1 2017年巴西 Praia Formosa 风速数据的频率分布。

涉及两个峰值的分布。文献中还引用了雷利分布和对数正态分布等多种其他分布。研究表明，两分量威布尔分布适用于双峰风速分布。与威布尔分布类似，也已提出混合密度函数 [11]。图 2.1 展示了巴西 Praia Formosa 风电场风速数据的频率分布图。

从图中可以观察到，频率分布有两个风速峰值，从而表明存在双峰分布。风速数据涵盖从 2017 年 1 月 1 日至 2017 年 4 月 30 日的四个月时间。频率分布图有助于从最大值、最小值和平均风速等方面研究风况的统计特性。

## 2.3.1 风速概率密度函数

概率密度函数在统计学及其他计算领域中广泛应用，其中风速等随机变量的发生概率在数学上被描述。然而，风速不是影响风力涡轮机捕获功率的唯一变量。风速与风向之间的相关性同样重要。文献还显示混合密度函数的实现，即由多个概率密度函数组合而成，每个函数都关联一个权重 [12]。

## 2.3.1.1 威布尔分布

最常用的风速 PDF 是威布尔分布，它适用于几乎所有风况。两参数（$k$ 和 $\lambda$）威布尔 PDF 表示为

$f(v; k, \lambda) = \frac{k}{\lambda}(\frac{v}{\lambda})^{k-1} e^{-(\frac{v}{\lambda})^k},$ (2.2)

其中 $k, \lambda > 0$，且 $v > 0$ 是称为风速（单位：m/s）的随机变量；$k$ 称为形状参数。威布尔参数可通过最大似然法 [13] 进行估计。同样，联合威布尔 PDF 可用于建模双峰风况的风电场。两分量联合威布尔 PDF 可表示为

$$f_i(v; k_i, \lambda_i) = \frac{k_i}{\lambda_i}(\frac{v}{\lambda_i})^{k_i-1} e^{-(\frac{v}{\lambda_i})^{k_i}}, \quad i=1, 2,$$
$$f(v; k, \lambda) = w_1 f_1(v; k_1, \lambda_1) + (1 - w_1) f_2(v; k_2, \lambda_2), \quad (2.3)$$

其中 $k_1, \lambda_1$ 和 $k_2, \lambda_2$ 分别表示各个 PDF 的形状和尺度参数，进而可通过最大似然估计（MLE）进行估计。

### 使用最大对数似然进行参数估计

威布尔分布的参数估计 $\hat{\theta} = (\hat{k}, \hat{\lambda})$ 可根据最大似然原理，针对唯一风速数据进行确定。根据图 2.2 和 (2.2) 给出的威布尔 PDF，对数似然函数为

$L(v|k, \lambda) = n\log(k) - nk\log(\lambda) + (k-1) \sum_{i=1}^n \log(v_i) - \sum_{i=1}^n (\frac{v_i}{\lambda})^k . \quad (2.4)$

进一步，为了求解估计量，对参数 $k$ 和 $\lambda$ 对对数似然函数求导：

![](img/b53e39e35231af65df8ccaa99eb28bee_34_0.png)

图 2.2 \(\lambda = 1\) 及不同形状参数值的威布尔 PDF。

\(\frac{\partial L(v|k, \lambda)}{\partial \lambda} = \frac{-n\lambda}{k} + \frac{\lambda}{k} \sum_{i=1}^n \left(\frac{v_i}{\lambda}\right)^k, \quad (2.5)\)

\(\frac{\partial L(v|k, \lambda)}{\partial k} = \frac{n}{k} - n \log(\lambda) + \sum_{i=1}^n v_i - \sum_{i=1}^n \left(\frac{v_i}{\lambda}\right)^k \log\left(\frac{v_i}{\lambda}\right). \quad (2.6)\)

根据 (2.5) 和 (2.6) 的解，可以估计参数 $k$ 和 $\lambda$。观察 (2.4)，可通过最小化对数似然函数的负值来获得参数。由于这是一个优化问题，可采用多种进化技术，如遗传算法（GA）、粒子群优化（PSO）和萤火虫算法（FA），以获得准确的参数估计。图 2.3 展示了威布尔分布拟合。

### 2.3.1.2 风速林德利分布

单峰风况可由威布尔分布和伽马分布描述 [11]。在极低和极高风区，据报道威布尔及其他 PDF 表现不佳，此类情况下建议采用林德利分布函数 [14]。林德利分布有两种版本，即广义林德利和幂林德利，如 [14] 所述。对于随机风速变量 \( \upsilon \)，广义林德利 \( f_{gl} \) 和幂林德利 \( f_{pl} \) PDF 可表示为

\( f_{gl}(\upsilon) = \frac{\alpha \beta^2}{\beta + 1}(1 + \upsilon)\left(1 - \frac{1 + \beta + \beta \upsilon^2}{1 + \beta}e^{-\beta \upsilon}\right)^{\alpha - 1}e^{-\beta \upsilon}, \quad (2.7) \\ f_{pl}(\upsilon) = \frac{\alpha \beta^2}{\beta + 1}(1 + \upsilon^\alpha)\upsilon^{\alpha - 1}e^{-\beta \upsilon^\alpha}, \quad (2.8) \)

其中 \( \alpha \) 和 \( \beta \) 分别表示形状和尺度参数。

广义林德利分布的累积 PDF 表示为

\( f_{gl}(\upsilon) = \left[1 - \left(\frac{1 + \beta + \beta \upsilon}{\beta + 1}\right)e^{-\beta \upsilon}\right]^\alpha. \quad (2.9) \)

![](img/b53e39e35231af65df8ccaa99eb28bee_35_0.png)

图 2.3 实时风速数据的威布尔分布拟合。

[15] 描述了随机变量的扩展广义林德利分布及其相对于广为人知的威布尔、雷利、两分量威布尔和广义林德利 PDF 的优越性。

图 2.4 展示了用于建模风速分布的广义林德利 PDF 图。形状和尺度参数 $\alpha$ 和 $\beta$ 控制分布的峰值和尾部结构。广义林德利 PDF 特别适用于建模风速方面风况较弱的风能资源。额定功率在 100–500 kW 范围内的小型风电场在低风速下运行，其分布可能呈偏态。

### 林德利 PDF 参数估计

林德利 PDF 是一个两参数分布类，其中 $\hat{\theta} = (\hat{\alpha}, \hat{\beta})$ 根据对数似然原理确定。林德利 PDF 的对数似然函数为

$$L(v|\alpha, \beta) = n[\log \alpha + 2 \log \beta - \log(\beta + 1)] + \sum_{i=1}^n \log(1 + v_i) + (\alpha + 1) \sum_{i=1}^n \log \left( 1 - \frac{1 + \beta + \beta v}{1 + \beta} e^{-\beta v} \right) - \beta \sum_{i=1}^n v_i. \tag{2.10}$$

进一步，对 $\alpha$ 和 $\beta$ 对对数似然函数求导，可得

$$\frac{\partial L(v|\alpha, \beta)}{\partial \alpha} = \frac{n}{\alpha} + \sum_{i=1}^n \log \left( 1 - \frac{1 + \beta + \beta v}{1 + \beta} e^{-\beta v} \right). \tag{2.11}$$

$$\begin{aligned} \frac{\partial L(v|\alpha, \beta)}{\partial \beta} &= \frac{n}{\beta} - \sum_{i=1}^n v_i + (\alpha + 1) \sum_{i=1}^n \left[ \frac{1 - \frac{e^{-\beta v}}{(1+\beta)^2} + v e^{-\beta v}}{1 - \frac{1+\beta+\beta v}{1+\beta} e^{-\beta v}} \right] \\ &- (\alpha + 1) \sum_{i=1}^n \left[ \frac{\frac{e^{-\beta v}}{(1+\beta)^2} + v e^{-\beta v}}{1 - \frac{1+\beta+\beta v}{1+\beta} e^{-\beta v}} \right]. \tag{2.12} \end{aligned}$$

由于方程 (2.11) 和 (2.12) 包含非线性项，$\alpha$ 和 $\beta$ 的解可使用收敛速度快于牛顿法的准牛顿法等优化方法求得。估计量 $\hat{\alpha}$ 和 $\hat{\beta}$ 采用 PSO 算法确定。图 2.5 展示了实时风速数据的广义林德利拟合。

### 2.3.1.3 Stacy-Mihram 分布模型

威布尔分布模型的另一类是 Stacy–Mihram 模型，该模型通常能较好地描述风速分布。两参数模型为

$$f_{stm}(v) = \frac{\beta v^{\beta-1}}{\alpha^\beta} e^{-(\frac{v}{\alpha})^\beta}, \quad v > 0. \tag{2.13}$$

参数 $\alpha$ 和 $\beta$ 可使用 MLE 进行估计，其对数似然函数为

$$L(v|\alpha, \beta) = n \log \beta - n \beta \log \alpha + (\beta - 1) \sum_{i=1}^n \log(v_i) - \sum_{i=1}^n \left( \frac{v_i}{\alpha} \right)^\beta. \tag{2.14}$$

图 2.6 展示了风速时间序列的 Stacy–Mihram 拟合。

