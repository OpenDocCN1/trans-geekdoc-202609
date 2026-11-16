

FA通过最大化熵、能量和对比度的组合作为目标函数，优于基于Lévy飞行算法的FA、PSO和GA。Benala et al.提出了基于人工蜂群（ABC）算法的边缘图像增强模型，且ABC在此领域优于GA（Benala, T. R. et al. (2009)）。基于混沌序列的ABC算法也已应用于保持亮度的图像增强领域（Dhal, K. G., Das, S. (2015)）。所提ABC通过考虑所用目标函数的效率，优于传统的ABC和PSO。基于Lévy飞行和混沌序列的CS算法已应用于图像增强领域（Dhal, K. G., Quraishi, I. M., Das, S. (2017), Dhal, K. G., Sen, M., Das, S. (2017), Dhal, K. G., Das, S. (2017), Bhandaria, A. K. (2014)）。作者提出了一种混沌版本的蝙蝠算法（Dhal, K. G., Quraishi, I. M., Das, S. (2015), Dhal, K. G., Quraishi, I. M., Das, S. (2015)），该算法在图像增强领域优于混沌CS算法和混沌版本的FA。下一节将介绍所提图像增强方法。

## 所提双直方图模糊对比度拉伸（BHFCS）方法

本文展示了一种用于图像增强的新参数化双直方图模糊对比度拉伸模型（BHFCS），如下所述：

- 1. 查找相应图像的直方图。
- 2. 基于阈值\(X_T\)划分直方图，该阈值使输入和输出图像之间的亮度误差最小（Chen, S. D., Ramli, A. R. (2004), Chen, S. D., Ramli, A. R. (2003)）。已证明该阈值有助于保持图像的原始亮度（Dhal, K. G., Sen, S., Sarkar, K., Das, S. (2016), Dhal, K. G., Das, S. (2017a)）。
- 3. 如果任意像素，即\(X_i \le X_T\)，则\(X_i \in C_1\)；如果\(X_i \ge X_T\)，则\(X_i \in C_2\)，其中\(C_1\)和\(C_2\)分别对应背景和前景类。因此，类\(C_1\)和\(C_2\)对应像素的隶属度计算如下：

\(\mu_{c1}(X_i) = 1 - \frac{X_T - X_i}{X_T}, \mu_{c2}(X_i) = 1 - \frac{E - X_i}{E - X_T}\) (1)

其中，E ≤ 255，并通过优化设置。\(\mu_{c1}\)和\(\mu_{c2}\)分别是类\(C_1\)和\(C_2\)的隶属度，隶属度值介于

$$0 \le \begin{cases} \mu_{c1}(X_i) \\ \mu_{c2}(X_i) \end{cases} \le 1$$

- 4. 类\(C_1\)（即\(X_{ie}^{c1}\)）和类\(C_2\)（即\(X_{ie}^{c2}\)）的增强像素值计算如下：
  - \(X_{ie}^{c1} = X_i + \mu_{c1}(X_i) \cdot K_1,\)
  - \(X_{ie}^{c2} = X_i \cdot \mu_{c2}(X_i) + (E - \mu_{c2}(X_i) \cdot K_2)\) (2)
  - 如果（\(X_{ie}^{c1}\)或\(X_{ie}^{c2} > 255\)），则执行归一化。
  - 这里，\(X_{ie}^{c1}\)和\(X_{ie}^{c2}\)是增强像素值，它们极大地依赖于属于[0, 255]且由修改DE算法优化的参数\(K_1\)和\(K_2\)。

- 5. 合并\(X_{ie}^{c1}\)和\(X_{ie}^{c2}\)两个分量，得到增强图像。

因此，所提增强方法清楚地表明，适当的增强在很大程度上取决于三个相关参数，即E、\(K_1\)和\(K_2\)，它们具有不同的范围。这些参数的最优值通过采用一种修改的DE算法计算得出，以FD和QILV的组合作为目标函数，这将在下一节中讨论。

## 目标函数

本文还致力于寻找一个适当的目标函数以保存图像的原始亮度。本研究中提出了一种新颖的目标函数来满足这一需求。所提目标函数是分形维数（FD）（Al-Kadi, O., S., Watson, D. (2008)）和基于局部方差的质量指数（QILV）（Aja-Fern´andez, S. (2006)）的组合。

## 分形维数（FD）

分形基于自相似性，而分形维数是图像固有维度的定量表达式（Al-Kadi, O., S., Watson, D. (2008)）。推导分形维数的基本方法是箱计数法。箱计数是通过计算确定框或网格内的点数来构建整个维度。在数学上，FD使用以下公式计算：

\( D = \frac{\log N_r}{\log \left( \frac{1}{r} \right)} \)

其中，D是分形维数。通过求出每个框（2×2）的最大和最小强度并求和其差，得到N和 r，如下所示：

\( r = \frac{s}{M} \text{ Where, } M= min (R, C) \)

其中，s表示缩放因子，R和C分别表示网格尺寸加倍时的行数和列数，R和C减为原值的一半，上述过程迭代重复，直到max(R, C)大于2。线性回归模型用于拟合log(N)与log(1/r)图中的直线，斜率给出FD，如下所示：

\( log N_r = D log \left( \frac{1}{r} \right) \)

## 基于局部方差的质量指数（QILV）

QILV用于测量图像的结构信息（Aja-Fern´andez, S. (2006)）。图像大量结构信息编码在其局部方差分布中。图像的局部方差特征有助于正确比较两幅图像。图像I的局部方差定义为\( Var \left( I_{i,j} \right) = E \left( \left( I_{i,j} - \overline{I_{i,j}} \right)^2 \right) \)，其中\(\overline{I_{i,j}} = E \left( I_{i,j} \right)\)为图像的局部均值。可使用待分析像素的加权邻域\(\eta_{i,j}\)及其相应权重\(\omega_p\)来估计，如下所示：

\( Var \left( I_{i,j} \right) = \frac{ \sum_{p \in \eta_{i,j}} \omega_p \left( I_{i,j} - \overline{I_{i,j}} \right)^2 }{ \sum_{p \in \eta_{i,j}} \omega_p } ; \overline{I_{i,j}} = \frac{ \sum_{p \in \eta_{i,j}} \omega_p I_p }{ \sum_{p \in \eta_{i,j}} \omega_p } \quad (6)\)

估计的图像局部方差将用作两幅图像之间结构相似性的质量度量。局部方差的均值\(\mu_{V_I}\)估计如下：

\(\mu_{V_I} = \frac{1}{MN} \sum_{i=1}^M \sum_{j=1}^N Var \left( I_{i,j} \right) \quad (7)\)

局部方差的（全局）标准差定义为：

\(\sigma_{V_I} = \left( \frac{1}{MN-1} \sum_{i=1}^M \sum_{j=1}^N \left( Var \left( I_{i,j} \right) - \mu_{V_I} \right)^2 \right)^{\frac{1}{2}} \quad (8)\)

最后，两幅图像\(I\)和\(J\)的方差之间的协方差定义为：

\(\sigma_{V_I V_J} = \frac{1}{MN-1} \sum_{i=1}^M \sum_{j=1}^N \left( Var \left( I_{i,j} \right) - \mu_{V_I} \right) \left( Var \left( J_{i,j} \right) - \mu_{V_J} \right) \quad (9)\)

两幅图像\(I\)和\(J\)之间的基于局部方差的质量指数（QILV）如下：

\( QILV \left( I, J \right) = \frac{ 2 \mu_{V_I} \mu_{V_J} }{ \mu_{V_I}^2 + \mu_{V_J}^2 } \cdot \frac{ 2 \sigma_{V_I} \sigma_{V_J} }{ \sigma_{V_I}^2 + \sigma_{V_J}^2 } \cdot \frac{ \sigma_{V_I V_J} }{ \sigma_{V_I} \sigma_{V_J} } \quad (10)\)

其中，\( 0 < QILV \le 1 \)

QILV方程的第一项比较两幅图像的局部方差分布的均值。第二项比较局部方差的标准差。第三项用于引入空间连贯性。为了避免小值引起的某些计算问题，方程中的每一项可以添加一些常数。

分形维数（FD）测量图像的粗糙度。有报道指出，局部方差分布提供了关于图像结构的信息（Dhal, K. G., Sen, M., Das, S. (2017)）。如果QILV增加，则增强图像的结构信息得到保存。因此，为了进行适当的增强，FD和QILV的组合被作为目标函数。

目标函数定义为：

$$Fit\left(E,K_{1}, K_{2}\right)=\left\{\exp\left(FD\right)+\exp\left(QILV\right)\right\}$$

其中，Fit(.)是目标函数。FD和QILV分别表示相应图像的分形维数和基于局部方差的质量指数。exp是指数运算符。因此，从目标函数的定义可以轻易验证，如果所提目标函数被最大化，则相应图像的FD和QILV被最大化，即图像的结构信息和原始亮度得到保存。

因此，优化问题定义如下：

$$\{E_{0}, K_{10}, K_{20}\} = arg[max_{E, K_{1}, K_{2}} \{ Fit\left(E, K_{1}, K_{2}\right) \}]$$

该最大化问题已通过采用修改的混沌DE算法求解，该算法将在下一节中讨论。

## 混沌差分进化（CDE）

本研究采用了一种新的步长来控制差分进化的变异因子。该步长背后的方法如下讨论：

$$Step Size (SS_{i}^{t}) = \left| \frac{Fit\left(X_{gbest}^{t}\right) - Fit^{t}\left(X_{i}\right)}{max\left(Fit\left(X_{gbest}^{t}\right), Fit^{t}\left(X_{i}\right)\right)} \right|$$

其中，Fit\left(X_{gbest}^{t}\right)是截至第t代的全局最佳解的适应度值。Fit^{t}\left(X_{i}\right)是第t代第i个个体的适应度值。很容易理解（0 <= SS <= 1）。还很明显，SS执行主要的

