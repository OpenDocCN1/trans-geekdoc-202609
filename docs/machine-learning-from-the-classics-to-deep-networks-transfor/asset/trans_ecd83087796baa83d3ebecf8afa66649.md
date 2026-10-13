
$U_r := [\mathbf{u}_1, \dots, \mathbf{u}_r] \in \mathbb{R}^{m \times r},\quad V_r := [\mathbf{v}_1, \dots, \mathbf{v}_r] \in \mathbb{R}^{l \times r}$。

![Equation](images/B9780443292385000123/si84.png)(6.15)

公式 [(6.14)](#Chp006_249-291_B9780443292385000123.xhtml#deq40) 给出了用 $U_r$、$V_r$ 和 $D$ 表示的 $X$ 的矩阵分解。我们将在第 [20](#Chp020_1103-1179_B9780443292385000263.xhtml) 章处理降维技术时用到该分解。[图 6.2](#Chp006_249-291_B9780443292385000123.xhtml#f0015) 给出了公式 [(6.14)](#Chp006_249-291_B9780443292385000123.xhtml#deq40) 的示意图解。

![Figure 6.2 The m × l matrix X, of rank r ≤ min{m,l}, factorizes in terms of the matrices U\_{r} \\in \\mathbb{R}^{m \\times r}Equation, V\_{r} \\in \\mathbb{R}^{l \\times r}Equation and the r × r diagonal matrix D.](images/B9780443292385000123/gr002.jpg)

[图 6.2](#Chp006_249-291_B9780443292385000123.xhtml#cf0255) 秩为 $r \le \min\{m,l\}$ 的 $m \times l$ 矩阵 $X$，可分解为矩阵 $U_r \in \mathbb{R}^{m \times r}$、$V_r \in \mathbb{R}^{l \times r}$ 以及 $r \times r$ 对角矩阵 $D$。

结果表明，$\mathbf{u}_i \in \mathbb{R}^m,\ i = 1,2,\dots,r$（称为*左奇异向量*）是 $XX^T$ 的非零特征值对应的归一化特征向量，而 $\mathbf{v}_i \in \mathbb{R}^l,\ i = 1,2,\dots,r$ 是 $X^TX$ 的非零特征值对应的归一化特征向量，称为*右奇异向量*。注意 $XX^T$ 和 $X^TX$ 具有相同的特征值（问题 [6.3](#Chp006_249-291_B9780443292385000123.xhtml#o0020)）。

**证明**

根据各自的定义（附录 A），我们有

$XX^T\mathbf{u}_i = \lambda_i\mathbf{u}_i,\quad i = 1,2,\dots,r,$

![Equation](images/B9780443292385000123/si91.png)(6.16)

和
