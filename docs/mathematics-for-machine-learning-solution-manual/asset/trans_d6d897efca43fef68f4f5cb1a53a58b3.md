

E₁ 是 A 的唯一特征空间。

b. 对于 B，对应的特征空间（其中 λ_i ∈ ℂ）为

$$E_i = \begin{bmatrix}1\\i\end{bmatrix},\quad E_{-i}=\begin{bmatrix}1\\-i\end{bmatrix}.$$

## 4.4 计算以下矩阵的所有特征空间

$$A = \begin{bmatrix}0 & -1 & 1 & 1\\-1 & 1 & -2 & 3\\2 & -1 & 0 & 0\\1 & -1 & 1 & 0\end{bmatrix}.$$

(i) 特征多项式：

$$p(\lambda)=\begin{vmatrix}-\lambda & -1 & 1 & 1\\-1 & 1-\lambda & -2 & 3\\2 & -1 & -\lambda & 0\\1 & -1 & 1 & -\lambda\end{vmatrix}=\begin{vmatrix}-\lambda & -1 & 1 & 1\\0 & -\lambda & -1 & 3-\lambda\\0 & 1 & -2-\lambda & 2\lambda\\1 & -1 & 1 & -\lambda\end{vmatrix}$$

$$=\begin{vmatrix}-\lambda & -1-\lambda & 0 & 1\\0 & -\lambda & -1-\lambda & 3-\lambda\\0 & 1 & -1-\lambda & 2\lambda\\1 & 0 & 0 & -\lambda\end{vmatrix}$$

$$=(-\lambda)\begin{vmatrix}-\lambda & -1-\lambda & 3-\lambda\\1 & -1-\lambda & 2\lambda\\0 & 0 & -\lambda\end{vmatrix}-\begin{vmatrix}-1-\lambda & 0 & 1\\-\lambda & -1-\lambda & 3-\lambda\\1 & -1-\lambda & 2\lambda\end{vmatrix}$$

$$=(-\lambda)^2\begin{vmatrix}-\lambda & -1-\lambda\\1 & -1-\lambda\end{vmatrix}-\begin{vmatrix}-1-\lambda & 0 & 1\\-\lambda & -1-\lambda & 3-\lambda\\1 & -1-\lambda & 2\lambda\end{vmatrix}$$

$$=(1+\lambda)^2(\lambda^2-3\lambda+2)=(1+\lambda)^2(1-\lambda)(2-\lambda)$$

因此，A 的特征值为 λ₁ = -1，λ₂ = 1，λ₃ = 2。

(ii) 对应的特征空间是方程 (A - λ_i I)x = 0（i = 1,2,3）的解，由下式给出

$$E_{-1}=\text{span}\begin{bmatrix}0\\1\\1\\0\end{bmatrix},\quad E_{1}=\text{span}\begin{bmatrix}1\\1\\1\\1\end{bmatrix},\quad E_{2}=\text{span}\begin{bmatrix}1\\0\\1\\1\end{bmatrix}.$$

## 4.5 矩阵的可对角化性与可逆性无关。判断以下四个矩阵是否可对角化和/或可逆

$$\begin{bmatrix}1 & 0\\0 & 1\end{bmatrix},\quad \begin{bmatrix}1 & 0\\0 & 0\end{bmatrix},\quad \begin{bmatrix}1 & 1\\0 & 1\end{bmatrix},\quad \begin{bmatrix}0 & 1\\0 & 0\end{bmatrix}.$$

在上述四个矩阵中，第一个矩阵可对角化且可逆，第二个矩阵可对角化但不可逆，第三个矩阵可逆但不可对角化，最后，第四个矩阵既不可逆也不可对角化。

## 4.6 计算以下变换矩阵的特征空间。它们可对角化吗？
### a. 对于

$\boldsymbol{A}=\begin{bmatrix}2&3&0\\1&4&3\\0&0&1\end{bmatrix}$

(i) 计算特征多项式的根，得到特征值

$p(\lambda)=\det(\boldsymbol{A}-\lambda\boldsymbol{I})=\begin{vmatrix}2-\lambda&3&0\\1&4-\lambda&3\\0&0&1-\lambda\end{vmatrix}=(1-\lambda)\begin{vmatrix}2-\lambda&3\\1&4-\lambda\end{vmatrix}$
$= (1-\lambda)((2-\lambda)(4-\lambda)-3)=(1-\lambda)(8-2\lambda-4\lambda+\lambda^2-3)$
$= (1-\lambda)(\lambda^2-6\lambda+5)=(1-\lambda)(\lambda-1)(\lambda-5)=-(1-\lambda)^2(\lambda-5).$

因此，我们得到特征值 1 和 5。

(ii) 为了计算特征空间，我们需要求解 $(\boldsymbol{A}-\lambda_i\boldsymbol{I})\boldsymbol{x}=\boldsymbol{0}$，其中 $\lambda_1=1,\lambda_2=5$：

$E_1:\begin{bmatrix}1&3&0\\1&3&3\\0&0&0\end{bmatrix}\sim\begin{bmatrix}1&3&0\\0&0&1\\0&0&0\end{bmatrix}$

其中，我们用第二行减去第一行，然后将第二行除以 3，得到简化行阶梯形。由此可以看出

$E_1=\operatorname{span}\begin{bmatrix}3\\-1\\0\end{bmatrix}$

现在，我们通过求解 $(\boldsymbol{A}-5\boldsymbol{I})\boldsymbol{x}=\boldsymbol{0}$ 来计算 $E_5$：

$\begin{bmatrix}-3&3&0\\1&-1&3\\0&0&-4\end{bmatrix}\xrightarrow{\cdot(-\tfrac13),\tfrac13R_1+\tfrac43R_3\atop\cdot(-\tfrac14),\text{与 }R_2\text{ 交换}}\begin{bmatrix}1&-1&0\\0&0&1\\0&0&0\end{bmatrix}$

于是，$E_5=\operatorname{span}\begin{bmatrix}1\\1\\0\end{bmatrix}$

(iii) 该自同态不能被对角化，因为 $\dim(E_1)+\dim(E_5)\neq3$。

其他论证：

- $\dim(E_1)$ 不等于特征多项式中特征值 $\lambda=1$ 的代数重数
- $\operatorname{rk}(\boldsymbol{A}-\boldsymbol{I})\neq3-2$

### b. 对于

$\boldsymbol{A}=\begin{bmatrix}1&1&0&0\\0&0&0&0\\0&0&0&0\\0&0&0&0\end{bmatrix}$

(i) 计算特征多项式的根，得到特征值

$p(\lambda)=\det(\boldsymbol{A}-\lambda\boldsymbol{I})=(1-\lambda)\lambda^{3}$
$=\begin{vmatrix}1-\lambda&1&0&0\\0&-\lambda&0&0\\0&0&-\lambda&0\\0&0&0&-\lambda\end{vmatrix}=-(1-\lambda)\lambda^{3}$.

由此可知，特征值为 0 和 1，代数重数分别为 3 和 1。

(ii) 我们计算特征空间 $E_{0}$ 和 $E_{1}$，这需要我们确定零空间 $\boldsymbol{A}-\lambda_{i}\boldsymbol{I}$，其中 $\lambda_{i}\in\{0,1\}$。

(iii) 我们计算特征空间 $E_{0}$ 和 $E_{1}$，这需要我们确定零空间 $\boldsymbol{A}-\lambda_{i}\boldsymbol{I}$，其中 $\lambda_{i}\in\{0,1\}$。对于 $E_{0}$，我们计算 $\boldsymbol{A}$ 的零空间，得到

$E_{0}=\operatorname{span}\left[\begin{bmatrix}1\\-1\\0\\0\end{bmatrix},\begin{bmatrix}0\\0\\1\\0\end{bmatrix},\begin{bmatrix}0\\0\\0\\1\end{bmatrix}\right]$

为了确定 $E_{1}$，我们需要求解 $(\boldsymbol{A}-\boldsymbol{I})\boldsymbol{x}=\boldsymbol{0}$

$\begin{bmatrix}0&1&0&0\\0&-1&0&0\\0&0&-1&0\\0&0&0&-1\end{bmatrix}\xrightarrow{+R_{1}|\text{移到 }R_{4}\atop\cdot(-1)\atop\cdot(-1)}\begin{bmatrix}0&1&0&0\\0&0&1&0\\0&0&0&1\\0&0&0&0\end{bmatrix}$

由此我们看出 $E_{1}=\operatorname{span}\left[\begin{bmatrix}1\\0\\0\\0\end{bmatrix}\right]$。

(iv) 由于 $\dim(E_{0})+\dim(E_{1})=4=\dim(\mathbb{R}^{4})$，因此存在对角形。

## 4.7 以下矩阵是否可对角化？如果是，确定它们的对角形以及一组基，使得变换矩阵在该基下为对角矩阵。如果不是，说明它们不可对角化的原因。
### a.

$\boldsymbol{A}=\begin{bmatrix}0&1\\-8&4\end{bmatrix}$

我们计算特征多项式为

$$p(\lambda)=\det(\boldsymbol{A}-\lambda\boldsymbol{I})=-\lambda(4-\lambda)+8=\lambda^2-4\lambda+8.$$

特征多项式在 $\mathbb{R}$ 上不能分解为线性因式，因为 $p(\lambda)$ 的根是复数，且为 $\lambda_{1,2}=2\pm\sqrt{-4}$。由于特征多项式不能分解为线性因式，$\boldsymbol{A}$ 不可对角化（在 $\mathbb{R}$ 上）。

### b.

$$\boldsymbol{A}=\begin{bmatrix}1&1&1\\1&1&1\\1&1&1\end{bmatrix}$$

(i) 特征多项式为 $p(\lambda)=\det(\boldsymbol{A}-\lambda\boldsymbol{I})$。

$$p(\lambda)=\begin{vmatrix}1-\lambda&1&1\\1&1-\lambda&1\\1&1&1-\lambda\end{vmatrix}\xrightarrow{\text{从 }R_2,R_3\text{ 中减去 }R_1}\begin{vmatrix}1-\lambda&1&1\\\lambda&-\lambda&0\\\lambda&0&-\lambda\end{vmatrix}\xrightarrow{\text{按最后一行展开}}\lambda\begin{vmatrix}1&1\\-\lambda&0\end{vmatrix}-\lambda\begin{vmatrix}1-\lambda&1\\\lambda&-\lambda\end{vmatrix}=\lambda^2+\lambda(\lambda(1-\lambda)+\lambda)=\lambda(-\lambda^2+3\lambda)=\lambda^2(\lambda-3).$$

因此，$p(\lambda)$ 的根为 0 和 3，代数重数分别为 2 和 1。

(ii) 为了判断 $\boldsymbol{A}$ 是否可对角化，我们需要证明 $E_0$ 的维数为 2（因为 $E_3$ 的维数必然为 1：根据定义，特征空间至少为 1 维，且其维数不能超过其关联特征值的代数重数）。

我们来研究 $E_0=\ker(\boldsymbol{A}-0\boldsymbol{I})$：

$$\boldsymbol{A}-0\boldsymbol{I}=\begin{bmatrix}1&1&1\\1&1&1\\1&1&1\end{bmatrix}\sim\begin{bmatrix}1&1&1\\0&0&0\\0&0&0\end{bmatrix}.$$

这里，$\dim E_0=2$，与特征多项式中特征值 0 的代数重数相同。因此 $A$ 可对角化。此外，从简化行阶梯形中可以看出

$$E_0=\operatorname{span}\left[\begin{bmatrix}1\\-1\\0\end{bmatrix},\begin{bmatrix}1\\0\\-1\end{bmatrix}\right].$$

(iii) 对于 $E_3$，我们得到

$$\boldsymbol{A}-3\boldsymbol{I}=\begin{bmatrix}-2&1&1\\1&-2&1\\1&1&-2\end{bmatrix}\sim\begin{bmatrix}1&0&-1\\0&1&-1\\0&0&0\end{bmatrix},$$

其秩为 2，因此（利用秩-零度定理），

