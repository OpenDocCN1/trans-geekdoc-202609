

分类器学习问题是设计一个算法 `a`:ℰ→`y`，该算法基于学习样本，利用对象的属性描述来恢复对象的类别。

### 10.3.2 学习阶段

由于学习子集的存在，我们可以假设存在一个函数（某种决策规则）`F`:ℰ→**y**。学习问题在于选择近似函数 `F̂`(**a**) 的适当形式和参数。函数 `F̂`(**a**) 表示决策规则模型。

遵循熵分类概念，决策规则由随机化参数模型（RPM）描述，即具有随机化参数 **a** 的模型。它具有输入向量 {**e**^((1)),…,**e**^((*h*))} 和输出 $\hat{\mathbf{y}}(\mathbf{a})$，该输出取决于随机化参数 **a**。

作为此类模型选择单层感知器 [[63](#refbib.xhtml#r63)]，即

$$
\begin{array}{r} {{\hat{y}}^{(i)}(\mathbf{a}) = \text{sigm}\,\left( \left\langle \mathbf{e}^{(i)},\mathbf{a} \right\rangle \right),\text{\quad\quad}i = \overline{1,n},} \\ \end{array}
$$

(10.16)

其中

$$
\begin{aligned} {\text{sigm}(x_{i})} & {= \frac{1}{1 + \exp\lbrack - \alpha(x_{i} - \Delta)\rbrack},} \\ x_{i} & {= \left( \left\langle \mathbf{e}^{(i)},\mathbf{b} \right\rangle \right),} \\ \mathbf{a} & {= \left\{ \mathbf{b},\alpha,\Delta \right\}.} \\ \end{aligned}
$$

(10.17)

具有斜率 *α* 和阈值 Δ 参数的 Sigmoid 函数的图像显示在 [Fig. 10.1](#chapter10.xhtml#f10_1) 中。函数 sigm(*x*) 在区间 [1/2, 1] 内的值对应于第一类；在区间 [0, 1/2) 内对应于第二类。

![Figure 10.1: Structure of single-layer neural network.](images/fig10_1.jpg)

[Figure 10.1:](#chapter10.xhtml#f10_1b) Structure of single-layer neural network.

在随机化模型 (10.16, 10.17) 中，参数 **a** = {*a*[1],…,*a*[(*n* + 2)]} 为区间类型，其概率特性由集合 𝒜 上的联合概率密度函数 `P`(**a**) 刻画，即

$$
\begin{aligned} a_{k} & {\in \mathcal{A}_{k} = \lbrack a_{k}^{-},a_{k}^{+}\rbrack,\text{\quad\quad}k = \overline{1,n+2},} \\ \mathcal{A} & {= \otimes_{k = 1}^{n + 2}\mathcal{A}_{k}.} \\ \end{aligned}
$$

(10.18)

由于参数 **a** 具有随机性，对于每个对象 *e*[*i*] 存在随机数 *ŷ*^((*i*))(**a**) 的集合 ${\hat{\mathcal{Y}}}^{(i)}$，其来自区间 [0,1]。将其均值定义为

$$
\begin{array}{r} {\mathcal{M}\left\{ {\hat{y}}^{i}(\mathbf{a}) \right\} = {\int_{\mathcal{A}}P}(\mathbf{a})\text{sigm}\,\left( \left\langle \mathbf{e}^{(i)},\mathbf{a} \right\rangle \right)d\mathbf{a},\text{\quad\quad}i = \overline{1,h}.} \\ \end{array}
$$

(10.19)

因此，根据一般的 RML 过程 [[144](#refbib.xhtml#r144), [150](#refbib.xhtml#r150)]，分类问题可写为如下形式：

$$
\begin{array}{r} \left. \mathcal{H}\lbrack P(\mathbf{a})\rbrack = - {\int_{\mathcal{A}}P}(\mathbf{a})\,\ln P(\mathbf{a})d\mathbf{a}\Rightarrow\max \right. \\ \end{array}
$$

(10.20)

受约束于

* PDF 归一化条件

$$
\begin{array}{r} {{\int_{\mathcal{A}}P}(\mathbf{a})d\mathbf{a} = 1} \\ \end{array}
$$

(10.21)

和

* 输出平衡约束

$$
\begin{array}{r} {{\int_{\mathcal{A}}P}(\mathbf{a})\text{sigm}\,\left( \left\langle \mathbf{e}^{(i)},\mathbf{a} \right\rangle \right)d\mathbf{a} = y_{i},\text{\quad\quad}i = \overline{1,h},} \\ \end{array}
$$

(10.22)

其中 `P`(**a**) 属于所有连续可微函数类 ℂ¹。

方程 (10.20–10.22) 构成了一个函数熵-线性规划问题，其具有解析解——熵最优 PDF `P*`(**a** | *θ*)，由拉格朗日乘子 *θ* 参数化，即

$$
\begin{array}{r} \left. P^{\*}(\mathbf{a}\, \middle| \,\theta) = \frac{\exp\left\lbrack {- {\sum\limits_{i = 1}^{h}\theta_{i}}{\hat{y}}^{(i)}(\mathbf{a})} \right\rbrack}{\mathcal{P}(\theta)}, \right. \\ \end{array}
$$

(10.23)

其中 *ŷ*^((*i*))(**a**) 由 (10.2) 给出，且

$$
\begin{array}{r} {\mathcal{P}(\theta) = {\int_{\mathcal{A}}\exp}\left\lbrack {- {\sum\limits_{i = 1}^{h}\theta_{i}}{\hat{y}}^{(i)}(\mathbf{a})} \right\rbrack.} \\ \end{array}
$$

(10.24)

拉格朗日乘子由平衡约束 (10.22) 计算得出。这里一种可能的方法是采用 *L*²\-norm 最小化方程 (10.22) 的一般残差函数。

### 10.3.3 测试阶段

该阶段利用测试子集 𝒯，其对象由答案向量 **z** = {*z*[1],…,*z*[*r*]} 刻画，具有已知的分类（其属于第一类或第二类）。向量 **z** 将用于测试过程的质量评估。后者本身涉及子集 𝒯 以及学习阶段得到的决策规则模型。

需要根据公式 (10.23, 10.24) 测试具有模型参数熵最优 PDF 的随机化决策规则 (10.16, 10.17)。该过程执行大小为 *N* 的蒙特卡洛模拟序列，在每次模拟中生成一个服从熵最优 PDF `P*`(**a**) 的随机向量 **a**。

假设作为此类模拟的结果，测试子集中第一个对象被分配 *N*[1] 次到第一类和 *N* − *N*[1] 次到第二类，…，第 *k* 个对象被分配 *N*[*k*] 次到第一类和 *N* − *N*[*k*] 次到第二类，依此类推。在足够多的模拟次数下，定义经验概率

$$
\begin{aligned} p_{1}^{(1)} & {= \frac{N_{1}}{N},\ldots,p_{1}^{(k)} = \frac{N_{k}}{N},\ldots,...} \\ p_{2}^{(1)} & {= \frac{N - N_{1}}{N},\ldots,p_{2}^{(k)} = \frac{N - N_{k}}{N},\ldots,...} \\ \end{aligned}
$$

(10.25)

因此，对于测试样本中的每个对象 *i*，测试算法可以写成以下形式。

*Step 1-i.* 按照最优 PDF，生成熵最优决策规则模型 (10.23, 10.24) 的输出值集合，其中包含 *N* 个来自区间 {0,1} 的随机数。

*Step 2-i.* 对于模型的每一次实现（即对于大小为 *N* 的集合中的每个参数向量），使用公式 (10.16, 10.17) 计算决策规则值。如果所得值超过 1/2，则对象 `t`^((*i*)) 被分配到第一类；否则分配到第二类。

*Step 3-i.* 根据公式 (10.25) 求出属于这些类的经验概率。

通过此过程，每个对象可以以一定的概率被分配到两个类之一，这反映了可用数据以及近似决策规则模型的固有不确定性。

请注意，通常学习和测试子集的对象被视为独立的复制品。在此假设下，Step 1-i 可以组织为一个共同的预处理程序来生成一组随机变量，该变量将以相同的方式用于所有测试对象。

可以通过引入一个阈值概率来进行硬分类转换，当对象被分配到相应类时的概率超过该阈值。用于正确硬分类的对象数量取决于该阈值。如易证实，对于超过 0.5 的阈值，一些对象未被分类，但分类结果具有更高的可靠性。另一方面，对于小于 0.5 的阈值，所有对象都被分类（因为两个概率之和为 1），但结果可能类似于猜测，如果所属概率彼此接近。

