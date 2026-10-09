

称为线性映射 $f$ 的核。$\operatorname{Im} f=\{f(X)|X \in V\}$ 称为线性映射 $f$ 的像。

容易证明 $\operatorname{Ker} f$ 和 $\operatorname{Im} f$ 分别是 $V$ 和 $W$ 的子空间。当 $\operatorname{Ker} f=0$ 时，称 $f$ 为单射。当 $\operatorname{Im} f=W$ 时，称 $f$ 为满射。当线性映射既是满射又是单射时，称 $f$ 为同构映射。若向量空间 $V$ 和 $W$ 之间存在同构映射 $f$，则也称 $W$ 与 $V$ 同构。考虑映射
$\begin{aligned} & a: V 1 \times V 2 \times \cdots \times V r \rightarrow R \\ & \forall X 1, \ldots, X r \in V, a(X 1, \ldots, X r) \in R \end{aligned}$ 使得 $\begin{aligned} & a\left(X 1, \ldots, X i+X i, \ldots, X r\right)=a\left(X 1, \ldots, X i, \ldots, X r\right)+a\left(X 1, \ldots, Y i, \ldots, X r\right) \\ , & a\left(X 1, \ldots, a X i, \ldots, X r\right)=a a\left(X 1, \ldots, X i, \ldots, X r\right) \\ , & a\left(X 1, \ldots, X i, \ldots, X j, \ldots, X r\right)=-a\left(X 1, \ldots, X j, \ldots, X i, \ldots, X r\right) \end{aligned}$ $(\forall i, j=1, \ldots, r, a \in R)$。

我们将 $a$ 称为向量空间 $V$ 上的 $r$ 元逆线性函数或 $V$ 上的 $r$ 形式。

**定义 17.12.** 设 $u$ 和 $v$ 是 $2 n$ 维空间中的向量，其中
$$
\begin{aligned} & u=\left[X_{1}, \ldots, X_{n}, \xi_{1}, \ldots, \xi_{n}\right]^{T} \\ & v=\left[Y_{1}, \ldots, Y_{n}, \eta_{1}, \ldots, \eta_{n}\right]^{T} . \end{aligned}
$$

则内积定义为 $\omega(u, v)=\sum_{i=1}^{n}\left(x_{i} \eta_{i}-y_{i} \xi_{i}\right)=u^{T} J v^{T}$ 且 $\omega(S u, S v)=\omega(u, v)$，其中 $J=\left[\begin{array}{cc} 0 & I_{n} \\ -I_{n} & 0 \end{array}\right]$，具有性质 $J^{-1}=J^{T}=-J$，$I_{n}$ 是 $n$ 阶单位矩阵。内积的内在性质如下：

- (1) 双线性：$\omega\left(\lambda_{1} u_{1}+\lambda_{2} u_{2}, v\right)=\lambda_{1} \omega\left(u_{1}, v\right)+\lambda_{2} \omega\left(u_{2}, v\right)$；
- (2) 反对称性：$\omega(u, v) = -\omega(v, u)$；
- (3) 非退化性：对于每个 $v \in R^{2 n}$，若对所有 $u$ 都有 $\omega(u, v)=0$，则 $v=0$；

**定义 17.13.** 满足上述条件的辛积 $\omega$ 的实向量空间 $(R^{2 n}, \omega)$ 称为辛空间。

**定义 17.14.** 若辛空间 $(R^{2 n}, \omega)$ 中的线性变换 $S$ 满足 $S: R^{2 n} \rightarrow R^{2 n}$，且对所有 $u$，$v \in R^{2 n}$ 都有 $\omega(S u, S v)=\omega(u, v)$，则线性变换 $S$ 称为辛变换或正则变换，且辛变换保持辛积不变。

### 定理 17.6
辛空间 $S$ 的线性变换为辛变换的充要条件是
$$S^{T} J S=J .$$

证明。在辛空间 $(R^{2n}, \omega)$ 中，存在辛基 $\{e_1, e_2, \ldots, e_n, e_{n+1}, \ldots, e_{2n}\}$ 上的辛变换 $S$ 的矩阵，记为 $S$。则对于 $X = \sum x^i e_i$ 和 $Y = \sum y^j e_j$。

由 $\omega(S X, S Y)=\omega(X, Y)$，
$$\left(x^{1}, \ldots, x^{2 n}\right) S^{T} J S\left(\begin{array}{c} y^{1} \\ \vdots \\ y^{2 n} \end{array}\right)=\left(x^{1}, \ldots, x^{2 n}\right) J\left(\begin{array}{c} y^{1} \\ \vdots \\ y^{2 n} \end{array}\right)$$
其中 $J=\left(\begin{array}{cc} 0 & I \\ -I & 0 \end{array}\right)$ 是辛形式 $\omega$ 在 $\{e_1, e_2, \ldots, e_n, e_{n+1}, \ldots, e_{2n}\}$ 下的矩阵表示，$T$ 表示矩阵的转置。因此，
$$S^{T} J S=J$$
是辛变换的充要条件。

```
Algorithm 17.6: Judgment of symplectic transformation algorithm
Input: r and s.
Output: {1, -1}.
Procedure check_Symplectic_transform(r,s)
If u = [x_1, ..., x_n, \xi_1, ..., \xi_n]^T \in r and v = [y_1, ..., y_n, \eta_1, ..., \eta_n]^T \in r
\omega(u, v) = \sum_{i=1}^{n} (x_i\eta_i - y_i\xi_i) = u^T J v^T.
Then, r is the symplectic space.
\omega(\lambda_1 u_1 + \lambda_2 u_2, v) = \lambda_1 \omega(u_1, v) + \lambda_2 \omega(u_2, v);
\omega(u, v) = -\omega(v, u);
If \omega is a symplectic space,
If S^T JS = J
then s is a symplectic transformation.
return 1.
else
return -1
end if.
End if.
end check_Symplectic_transform.
```

### 定义 17.15
若 $2n$ 阶矩阵 $B$ 满足
$$B^{T}JB = J$$
则称 $B$ 为辛矩阵。

### 定义 17.16
若 $2n$ 阶矩阵 $B$ 满足
$$JB + B^{T}J = 0$$
则称 $B$ 为无穷小辛变换矩阵。

### 推论 17.1
矩阵
$$\left[\begin{array}{cc} I & B \\ 0 & I \end{array}\right], \quad \left[\begin{array}{cc} I & 0 \\ D & I \end{array}\right]$$
为无穷小辛变换矩阵当且仅当 $B^{T} = B$，$D^{T} = D$。

### 定义 17.17
设 $(V, \omega)$ 是一个 $2n$ 维辛空间。若 $(V, \omega)$ 的一组向量 $e_{1}, e_{2}, \ldots e_{2n}$ 满足 $\delta(e_i, e_j) = \delta_{ij}$ 且对于 $i \neq j$ 有 $\omega(e_{i}, e_{j}) = \omega(e_{n+i}, e_{n+j}) = 0$，以及 $\omega(e_i, e_{n+i}) = 1$，则称其为 $(V, \omega)$ 的辛基（或辛标架）。

### 定义 17.18
设 $(V, \omega)$ 是一个辛空间。$(V, \omega)$ 的自同构是 $(V, \omega)$ 到其自身的同构映射。因此，$(V, \omega)$ 是 $V$ 的线性变换群 $\mathrm{Gl}(V)$ 的元素，若记为 $s$，则它满足
$$\omega(\mathrm{s}x, \mathrm{s}y) = \omega(x, y), \forall x, y \in V$$

容易知道，$(V, \omega)$ 的自同构构成的群是 $\mathrm{Gl}(V, R)$ 的子群，我们记作 $\mathrm{Sp}(V, \omega)$。特别是，标准辛空间 $(k^{2n}, \omega)$ 的自同构记作 $\mathrm{Sp}(2n, k)$，若 $k = R$，则 $\mathrm{Sp}(2n, k)$ 简记为 $\mathrm{Sp}(2n)$，称为 $2n$ 维辛群。

```
**Algorithm 17.7: Judgment symplectic algorithm**
Input: S is the group to be judged, T is the transformation.
Output: {-1, 1}.
Procedure check_symplectic_group(R,S,T)
// R is the symplectic space, T is the symplectic transformation, and S is the group to be judged
If $(V, \omega) \in R$ and $Sp(2n) \in T$. 
If $S \in T$ and $Sp(2n) \in Gl(V, \omega)$.
then return 1.
else return -1.
End if.
End if.
End check_symplectic_group.
```

设 $A_{0}$ 是 $R^{2n}$ 上的反对称 2-形式。满足对于子空间中任意 $x, x'$ 都有 $\omega(x, x') = 0$ 的所有子空间的集合称为 $\omega$ 的核，记为 $\mathrm{Ker}(\omega)$。
$$\mathrm{Ker}(\omega) = \{x | \omega(x, y) = 0, \forall y \in R^{2n}\}$$

当 $\mathrm{Ker}(\omega)=\{0\}$ 时，该形式称为非退化的；否则称为退化的。我们可以得到
$$\operatorname{rank} \omega = \operatorname{dim} R^{2 n}-\operatorname{dim} \mathrm{Ker}\left(\omega\right)\tag{17.1}$$

### 定理 17.7
辛空间 $(R^{2 n}, \omega)$ 必须是偶数维的。

*证明.* 事实上，由于辛形式 $\omega$ 是非退化的，$\mathrm{Ker}(\omega)=\{0\}$。根据 (17.1)，$\operatorname{dim} R^{2 n}=\operatorname{rank} \omega$。由于反对称矩阵的秩总是偶数，因此辛空间必须是偶数维的。$\square$

### 定义 17.19
若 $G$-空间 $M$ 具有辛结构 $\omega$，且在 $G$ 的作用下保持 $\omega$ 不变，即 $\forall g \in G$，$\Phi_g: M \rightarrow M$ 是辛微分同构，即 $\Phi_g^*\omega = \omega$，则称 $\omega$ 为 $M$ 上的辛结构，$(M, \omega)$ 称为辛流形。

我们将 $2l$ 维辛空间的基按以下顺序排列
$$a=1, \overline{1}, 2, \overline{2}, \ldots, l, \bar{l}\tag{17.2}$$

引入 $2l$ 维反对称矩阵 $J$
$$J=I_{l} \otimes\left(i \sigma_{2}\right)=-J^{-1}=-J^{T}, \quad \operatorname{det} J=1 .\tag{17.3}$$

所有满足下列条件的 $2l$ 维伪正交矩阵 $R$ 的集合在矩阵乘法下构成实群 $\operatorname{Sp}(2l, R)$：
$$R^{\dagger}=R^{-1}, \quad R^{T} J R=J$$
$\operatorname{Sp}(2l, R)$ 群是一个非紧李群。所有满足下列条件的 $2l$ 维酉矩阵 $u$ 的集合构成酉辛群 $\mathrm{USp}(2l)$：
$$u^{\dagger}=u^{-1}, \quad u^{T} J u=J$$
$\mathrm{USp}(2l)$ 群是一个紧李群。容易证明根据定义有 $R J R^{T}=J$ 且 $u J u^{T}=J$。

辛群和酉辛群的群空间都是连通的；它们是半单李群；其维数为 $l \cdot(2 l+1)$。通过相应的变换，我们可以将紧李群 $\mathrm{USp}(2l)$ 与非紧李群 $\operatorname{Sp}(2l, R)$ 联系起来。如果允许辛群的参数取复数值，则酉辛群和辛群的不可约表示是相关的，但参数的实部不同。这是计算非紧李群不可约表示的标准方法。

由于辛群和酉辛群的不可约表示相互对应，它们的生成元也相互对应，只是参数的实项不同。我们仅讨论这些群的张量表示。

