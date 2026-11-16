

当我们对 \(\alpha |0\rangle + \beta |1\rangle\) 应用 H 门时，我们有

\(H (\alpha |0\rangle + \beta |1\rangle) = \alpha (H |0\rangle) + \beta (H |1\rangle) = \frac{\alpha + \beta}{\sqrt{2}} |0\rangle + \frac{\alpha - \beta}{\sqrt{2}} |1\rangle\)

因为 \(H |0\rangle = \frac{1}{\sqrt{2}} |0\rangle + \frac{1}{\sqrt{2}} |1\rangle\) 和 \(H |1\rangle = \frac{1}{\sqrt{2}} |0\rangle - \frac{1}{\sqrt{2}} |1\rangle\)，可以通过矩阵乘法验证。请注意 \(|\frac{\alpha+\beta}{\sqrt{2}}|^2 + |\frac{\alpha-\beta}{\sqrt{2}}|^2 = 1\)，因为 \(|\alpha|^2 + |\beta|^2 = 1\)。

我们将在书中需要时后面介绍其他门，例如我们称作 R 门和 P 门。

一般来说，单个量子比特量子门 \(U\) 通常表示为一个 \(2 \times 2\) 矩阵，其元素为复数，并且是 *幺正* 的，也就是说，它的逆与其共轭转置相同：\(U^{-1} = U^\dagger\) 或 \(UU^{-1} = U^\dagger U = I\)，其中 \(U^\dagger\) 表示 \(U\) 的 *共轭转置*（或 *厄米特转置*），它是通过转置 \(U\) 并取其所有元素的复共轭形成的，即 \(U^\dagger = \overline{U^T}\)。对于幺正 \(U\)，我们有 \(UU^\dagger = U^\dagger U = I\)，其中 \(I\) 表示单位矩阵。

此外，如果一个平方矩阵等于其自身的共轭转置，则它是 *厄米特* 的，即 \(U = U^\dagger\)。请注意，我们已经见过的门 \(X\)、\(Z\)、\(Y\) 和 \(H\) 都是厄米特且幺正的，即 \(XX = ZZ = YY = HH = I\)，并且它们都是自身的逆。

还应当注意，对于幺正矩阵，其对状态向量 \(\mathbf{s} = \alpha |0\rangle + \beta |1\rangle = \binom{\alpha}{\beta}\) 的作用保持范数，即 \(||U\mathbf{s}|| = ||\mathbf{s}||\)，其中 \(||.||\) 表示向量的范数，也就是说，对于向量 \(\mathbf{x}\)，\(||\mathbf{x}|| = \sqrt{\langle \mathbf{x}, \mathbf{x} \rangle} = \sqrt{\mathbf{x}^\dagger \mathbf{x}}\)，其中 \(\langle ., . \rangle\) 表示内积。

因此，幺正算子有助于保持概率幅平方和为一的性质：假设 \(U\) 和 \(\mathbf{s}\) 满足 \(||\mathbf{s}||^2 = \binom{\alpha}{\beta}^\dagger \binom{\alpha}{\beta} = \alpha \overline{\alpha} + \beta \overline{\beta} = |\alpha|^2 + |\beta|^2 = 1\)，\(||U\mathbf{s}|| = ||\mathbf{s}||\) 且 \(U\mathbf{s} = \binom{\alpha'}{\beta'}\)，那么 \(||U\mathbf{s}|| = |\alpha'|^2 + |\beta'|^2 = ||\mathbf{s}|| = 1\)。

因此，将一个有效量子态映射到另一个有效量子态的量子门需要是幺正算子，这是合理的。

量子门的一个直观解释是对状态向量 \(|\psi\rangle = \alpha |0\rangle + \beta |1\rangle\) 在某个状态空间或某个坐标系中的操纵，正如我们所见。

但请考虑 *Bloch 球面*，它是量子比特状态空间的几何表示，球面的两个极对应于两个基向量 \(|0\rangle\) 和 \(|1\rangle\)，然后 Bloch 球面上的一个箭头（从球面中心开始）表示量子比特的一个状态。

许多书籍已经解释了 Bloch 球面，因此我们这里不再重复，而是将读者引荐至 Hughes et al. [2021b]。

有了这样的几何表示，量子门操作可以被视为箭头围绕穿过球面中心的三个正交轴（x、y 和 z）的旋转。14

![](img/fb3eb7e935470a2da12b03f528f097ee_40_0.png)

图 2.3 单个量子比特门 H、X、Y 和 Z 的符号和矩阵。

在图示中，量子门 H、X、Y 和 Z 的符号如图 2.3 所示。

请注意，当量子态通过密度算符表示，形式为 \(\rho = \sum_i p_i |\psi_i\rangle\langle\psi_i|\) 的 \(\rho\) 时，其中 \(\sum_i p_i = 1\)，则由于幺正算符 \(U\) 导致的量子系统演化到新态由以下给出

\(U \rho U^\dagger = U \left( \sum_i p_i |\psi_i\rangle\langle\psi_i| \right) U^\dagger = \sum_i p_i U |\psi_i\rangle\langle\psi_i| U^\dagger\)

## 2.2.2 测量算符

我们之前见过测量的概念，它有效地将状态 \(|\psi\rangle = \alpha|0\rangle + \beta|1\rangle\) “转换”为以概率 \(|\alpha|^2\) 得到 \(|0\rangle\) 或以概率 \(|\beta|^2\) 得到 \(|1\rangle\)。

令 \(\langle 0| = |0\rangle^\dagger\) 和 \(\langle 1| = |1\rangle^\dagger\)，可以用常以以下形式表示的算符来表示测量：

\(|0\rangle\langle0| = \begin{bmatrix} 1 \\ 0 \end{bmatrix} [1 \quad 0] = \begin{bmatrix} 1 & 0 \\ 0 & 0 \end{bmatrix}\) and \(|1\rangle\langle1| = \begin{bmatrix} 0 \\ 1 \end{bmatrix} [0 \quad 1] = \begin{bmatrix} 0 & 0 \\ 0 & 1 \end{bmatrix}\)

请注意 \(|0\rangle\langle0| + |1\rangle\langle1| = I\)。那么，由于 \((|0\rangle\langle0|)(\alpha|0\rangle + \beta|1\rangle) = \alpha|0\rangle\langle0|0\rangle + \beta|0\rangle\langle0|1\rangle = \alpha|0\rangle\) 以及

\((|0\rangle\langle0|(\alpha|0\rangle + \beta|1\rangle))^\dagger = (\alpha|0\rangle + \beta|1\rangle)^\dagger(|0\rangle\langle0|)^\dagger = (\alpha|0\rangle + \beta|1\rangle)^\dagger(|0\rangle^\dagger|0\rangle)^\dagger = (\bar{\alpha}\langle0| + \bar{\beta}\langle1|)|0\rangle\langle0| = \bar{\alpha}\langle0|0\rangle\langle0| + \bar{\beta}\langle1|0\rangle\langle0| = \bar{\alpha}\langle0|\)

得到 \(|0\rangle\) 结果的概率可以写成

prob(|0⟩) = \(|\alpha|^2 = \bar{\alpha}\alpha = \bar{\alpha}\alpha \langle0|0\rangle = \bar{\alpha} \langle0|\alpha|0\rangle = (\alpha\langle0| + \beta\langle1|)^\dagger(|0\rangle\langle0|)^\dagger(|0\rangle\langle0|)(\alpha|0\rangle + \beta|1\rangle) = \langle\psi| M_0^\dagger M_0 |\psi\rangle\)

最后一行是通过设置 \(M_0 = |0\rangle\langle0|\) 得到的。同样，令 \(M_1 = |1\rangle\langle1|\)，类似计算将得到：prob(|1⟩) = \(\langle\psi| M_1^\dagger M_1 |\psi\rangle\)。

### 2.2.2.1 测量公设（一般测量）

更一般来说，量子理论中的一个公设是，量子测量可以由一组测量算符 \(\{M_m\}\) 表示，每个算符作用于被测量子系统的状态，索引 \(m\) 指的是相对于算符 \(M_m\) 可能发生的测量结果，且结果 \(m\) 的概率由以下给出

p(m) = \(\langle\psi| M_m^\dagger M_m |\psi\rangle\)

且测量后的状态由以下给出

\(\frac{M_m |\psi\rangle}{\sqrt{\langle \psi | M_m^\dagger M_m | \psi \rangle}} = \frac{M_m |\psi\rangle}{\sqrt{p(m)}}\)

且算符满足以下完备性条件：\(\sum_m M_m^\dagger M_m = I\)。

回到我们的示例，在 \(M_0\) 之后，我们有状态：

\(\frac{M_0 |\psi\rangle}{\sqrt{\langle \psi | M_0^\dagger M_0 | \psi \rangle}} = \frac{M_0(\alpha |0\rangle + \beta |1\rangle)}{\sqrt{|\alpha|^2}} = \frac{\alpha |0\rangle}{|\alpha|}\)

而在 \(M_1\) 之后，我们将有状态：\(\frac{\beta|1\rangle}{|\beta|}\)。由于 \(|\frac{\alpha}{|\alpha|}| = |\frac{\beta}{|\beta|}| = 1\)，我们可以忽略乘数，从而得到状态 \(|0\rangle\) 或 \(|1\rangle\)，正如我们之前所见。

### 2.2.2.2 POVM

请注意，如果我们定义一组正算符 \(\{E_m\}\)，例如 \(E_m = M_m^\dagger M_m\)，则这些算符称为 POVM（正算符值测度）元素，\(\{E_m\}\) 被称为一个 POVM。

### 2.2.2.3 投影测量

假设我们有一组测量算符 \(\{P_m\}\)，其中有一个厄米特矩阵 \(M\)（表示可观测量，即物理学中可测量的物理量）如下：

\(M = \sum_m m P_m\)

这表明了这一组测量算符 \(\{P_m\}\) 如何相关，且结果 \(m\) 的概率由 \(p(m) = \langle \psi | P_m | \psi \rangle\) 给出，测量后的状态由 \(\frac{P_m | \psi \rangle}{\sqrt{p(m)}}\) 给出，那么 \(M\) 描述了一种具有测量算符 \(\{P_m\}\) 的投影测量，这些算符是投影到 \(M\) 的特征值为 \(m\) 的特征空间上的投影算符（例如，将 \(M\) 的相应特征向量表示为 \(|m\rangle\)，即 \(M | m \rangle = m | m \rangle\)，那么我们可以将 \(P_m\) 写为 \(|m\rangle \langle m|\)）。

另外，假设根据上述公设我们有一组测量算符 \(\{M_m\}\)，且这些算符是正交投影算符，即 \(M_m M_{m'} = \delta_{m,m'} M_m\)，其中若 \(m = m'\) 则 \(\delta_{m,m'} = 1\)，若 \(m \neq m'\) 则 \(\delta_{m,m'} = 0\)。

然后，请注意 \(p(m) = \langle \psi | M_m^\dagger M_m | \psi \rangle = \langle \psi | M_m | \psi \rangle\)，因为 \(M_m^\dagger M_m = M_m M_m = M_m\)（注意 \(M_m^\dagger = M_m\)，因为 \(M_m\) 是厄米特的）。

因此，投影测量构成了一类特殊的测量。

投影测量的一个示例是使用测量算符 \(\{M_0 = |0\rangle \langle 0|, M_1 = |1\rangle \langle 1|\}\) 在计算基下的测量，或相对于可观测量 \(Z = |0\rangle \langle 0| - |1\rangle \langle 1| = M_0 - M_1\) 的测量，其中对 \(\alpha | 0 \rangle + \beta | 1 \rangle\) 作用时，我们观察到得到对应于特征值 1 的结果的概率为 \(p(1) = \bar{\alpha}\alpha = |\alpha|^2\)，结果状态为 \(|0\rangle\)，而得到对应于特征值 -1 的结果的概率为 \(p(-1) = |\beta|^2\)，结果状态为 \(|1\rangle\)。)

另一个示例是在 Hadamard 基下的测量，即相对于测量算符 \(\{|+\rangle \langle +|, |-\rangle \langle -|\}\)，其中 \(|+\rangle = (|0\rangle + |1\rangle)/\sqrt{2}\) 且 \(|-\rangle = (|0\rangle - |1\rangle)/\sqrt{2}\)。可观测量是矩阵 \(X = |+\rangle \langle +| - |-\rangle \langle -|\)。如果我们测量处于状态 \(\alpha | 0 \rangle + \beta | 1 \rangle\) 的一个量子比特，结果的概率是多少？

我们可以将状态重写如下：\(\alpha | 0 \rangle + \beta | 1 \rangle = \frac{\alpha+\beta}{\sqrt{2}} |+\rangle + \frac{\alpha-\beta}{\sqrt{2}} |-\rangle\)，并且我们观察到得到对应于特征值 1 的结果的概率为 \(p(1) = |\frac{\alpha+\beta}{\sqrt{2}}|^2\)，结果状态为 \(|+\rangle\)，而得到对应于特征值 -1 的结果的概率为 \(p(-1) = |\frac{\alpha-\beta}{\sqrt{2}}|^2\)，结果状态为 \(|-\rangle\)。

请注意，假设我们的仪器只能在计算基下进行测量，那么可以做的是首先对状态施加（Hadamard）\(H\) 算符，如下所示：

\(H(\alpha | 0 \rangle + \beta | 1 \rangle) = \alpha H | 0 \rangle + \beta H | 1 \rangle = \alpha |+\rangle + \beta |-\rangle = \frac{\alpha+\beta}{\sqrt{2}} |0\rangle + \frac{\alpha-\beta}{\sqrt{2}} |1\rangle\)

然后，相对于计算基进行测量。请注意，现在得到对应于特征值 1 的结果的概率为

