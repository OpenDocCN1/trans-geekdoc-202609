
群 $C_q(K)$ 是基于 $[s_i^q | 1 \leq i \leq r_q]$ 的自由阿贝尔群，且边际同态 $\partial: C_q(K) \to C_{q-1}(K)$ 基于关联矩阵 $([s_i^q : s_j^{q-1}]$。对于正则胞腔复形，这一点显而易见。

### 命题 14.3.
若 $s_i^q > s_j^{q-1}$，则 $[s_i^q : s_j^{q-1}] = \pm1$；否则 $[s_i^q : s_j^{q-1}] = 0$。

细分映射 Sd: K → SdK 是一个胞腔映射。由其确定的胞腔链映射被称为细分链映射 Sd#: $C_*(K) \to C_*(SdK)$。

### 命题 14.4.
K 的每个胞腔均已定向。设 $s^q$ 为 K 的 q 维定向胞腔。则 $Sd#s^q = \Sigma_{[t^{-1},...,t^0][s^q: t^{q-1}]}...[t^1: t^0]s^qt^{q-1}...\tilde{t}^0$。

此公式是对所有胞腔序列 $t^{q-1}$, ..., $\tilde{t}^0$ 进行求和。实际上，它仅得出满足条件 $s^q > t^{q-1} > ... t^0$ 的胞腔序列 $t^{q-1} > ... t^0$ 之和。否则，关联系数之积 $[s^q : t^{q-1}...]...[t^1: t^0] = 0$。当 q = 0 时，该公式应理解为 $Sd#s^0 = \tilde{s}^0$。

### 定义 14.13.
K 的每个胞腔均已定向。设 $s^q$ 和 $s^{p+q}$ 为 K 上的两个胞腔。定义 SdK 上的交系链：

$I(s^{q*}, s^{p+q}) = \Sigma_{t^{p+q+1},...,t^{q+1}}[s^{p+q} : t^{p+q-1}]...[t^{q+1}: s^q]$.$\tilde{s}^{p+q}\tilde{t}^{p+q-1}...,\tilde{t}^{q-1}\tilde{s}q$。

求和是在 K 的所有处进行的，且满足所有胞腔序列 $\tilde{t}^{p+q-1} > ... t^{q-1}$ 符合 $s^{p+q} > t^{p+q-1} > ..., t^{q+1} > s^q$ 的条件。

我们现在引入交系链的边界。

### 推论 14.1.
交系链的边界 $\partial I(s^{q*}, s^{p+q}) = (-1)^p I(\partial s^{q*}, s^{p+q}) + I(s^{q*}, \partial s^{p+q})$。因此，双线性对应 I: $C^q(K) \times C_{p+q}(K) \to C_p(SdK)$ 确定了一个双线性对应 I: $H^q(K) \times H_{p+q}(K) \to H_p(SdK)$。可以证明，该边界公式是该命题和积（Cup product）边界公式的直接推论。根据上述理论，我们得到算法 14.9，即正则胞腔同调边界算法：

**算法 14.9: 正则胞腔同调边界**
过程 正则胞腔同调边界
//输入: 定向胞腔 $s^{q*}$//
//输出: {0,1}//

输入满足条件 $\langle s^{q*}, t^q \rangle = \begin{cases} 1, if \ t^q = s^q \\ 0, if \ t^q \neq s^q \end{cases}$ 的余链（cocochain）；

计算余环（cocycle） $Z^q(SdK)$；
计算余边界（coboundary）链 $B^q(SdK)$；
计算上同调（cohomology） $H^q(SdK)$；
结束过程 正则胞腔同调边界

## 14.3 同调边界学习算法的设计与分析

本节主要讨论同调边界细分算法的设计与分析。

同调边界细分算法（HBDA）[11]。
算法描述：

**算法 14.10**: 过程 同调边界细分

**输入**: 变量数量；$\theta$: 边界阈值；

**输出**: 数据的边界；

初始化：
- for $i=0,1\ldots q$
    - $\sum \lambda_{i} = 1$；
        (14.9)
- for $i=0,1\ldots q$
    - 我们选择一组可以构成另一个集合的 $a^{i}$；
        - 例如，$e^{1}=a^{1}-a^{0}, e^{2}=a^{2}-a^{0}, \ldots, e^{q}=a^{q}-a^{0}$。(14.10)
- 一组 $e^{i}$ 必须是线性无关的；
- 开始
    - $x_{q}=g_{1}s_{1}^{q}+g_{2}s_{2}^{q}+\cdots g_{aq}s_{aq}^{q}$; $y_{q}=h_{1}s_{1}^{q}+h_{2}s_{2}^{q}+\ldots h_{aq}s_{aq}^{q}$；
    - $Y=\lambda_{0}e^{0}+\lambda_{1}e^{1}+\ldots \lambda_{q}e^{q}$；在此表达式中，$y$ 必须满足 (14.1) 和 (14.10) 的条件；
- 然后
    - $\partial s^{q}=\sum_{i=0}^{q}(-1)a^{0} \ldots a^{i} \ldots a^{q}$ (14.11)
    - $f(y)=f(\sum_{i=0}^{q} \lambda_{i} e^{i})=\sum_{i=0}^{q} \lambda_{i} f(e^{i})=\sum_{i=0}^{q} \lambda_{i} \nu(e^{i})=\sum_{i=0}^{q} \lambda_{i} a^{i}=x$ (14.12)
- 该表达式定义了线性扩展。
- 它可以保持重心的不变性
- 结束过程 HBDA

由上述算法，我们得到以下结果。

**定理 14.2**。HBDA 算法所需的时空复杂度为 O(n³)，而时间复杂度为 O(n²)。

证明。假设在欧几里得空间中选取了一组满足算法要求的点。设 $g^{q}=\left(a^{0}, a^{1}, \ldots a^{q}\right)$ 和 $\mathbb{I}^{q}=\left(b^{0}, b^{1}, \ldots b^{q}\right)$ 为欧几里得空间 $E^{m}$ 和 $E^{n}$ 中的二维单形，满足 $v: a^{i} \rightarrow b^{i}, i=0,1, \ldots q$ 是它们顶点的自然一一映射。

根据 (14.10)，初始化的第一步时间复杂度为 O(n)，空间复杂度为 O(n)。

根据初始化的第二步，我们可以确定时间复杂度为 O(n)，空间复杂度为 O(n)。

根据程序主体，由 (14.11) 和 (14.12) 可知，时间复杂度为 O(N²)，空间复杂度为 O(N³)。

根据命题：在欧几里得空间中，任何 q 维单形 $s^{q}$ 和欧几里得空间 $E^{n}$ 中的自然 q 维单形 $t^{q}$ 在保持重心坐标的拓扑映射下是同胚的。因此，在任何保持重心坐标的拓扑映射下，任何二维单形都是同胚的。

$f(y)=f\left(\sum_{i=0}^{a} \lambda_{i} e^{i}\right)=\sum_{i=0}^{q} \lambda_{i} f\left(e^{i}\right)=\sum_{i=0}^{q} \lambda_{i} \nu\left(e^{i}\right)=\sum_{i=0}^{q} \lambda_{i} a^{i}=x \ .$ (14.13)

由 (14.13) 可知，拓扑映射保持重心坐标。因为点 $y$ 的重心是 $\lambda_{0}, \lambda_{1}, \ldots, \lambda_{q}$，所以在坐标 $t^{q}$ 中情况相同，如在直角坐标 $E^{q+1}$ 中一样。因此，点 $x=f(y)$ 是点 $y$ 上的连续函数，即 $f$ 是映射。最后，$t^{q}$ 是列紧集，且 $f$ 是拓扑映射。此映射称为仿射映射或保持重心坐标的拓扑映射。这就证明了它们是同胚的。

此外，我们假设 $s_{1}^{q}=\left(a_{0}^{i}, a_{1}^{i}, \ldots, a_{q}^{i}\right) t_{1}^{r}=\left(b_{0}^{i}, b_{1}^{i}, \ldots, b_{r}^{i}\right)$，满足 $r \leq q$。那么，我们可以得到 $v_{1}$，它是 $v$ 在顶点集 $s_{1}^{q}$ 上的限制，$f\left(\lambda_{0} a_{0}+\lambda_{1} a_{1}+\cdots+\lambda_{q} a_{q}\right)=\lambda_{0} b_{0}+\lambda_{1} b_{1}+\cdots+\lambda_{q} b_{q}$，$f: s^{q} \rightarrow t^{q}$ 是保持重心坐标的拓扑映射。因此，$v_{1}$ 上的线性扩展 $f_{1}$ 是 $v$ 上的线性扩展 $f$ 在顶点集 $s_{1}^{q}$ 上的限制。

HBDA 算法的空间复杂度为 O(N³)，时间复杂度为 O(N²)，其中 $t^{q}$ 和 $s^{q}$ 是同胚的。

## 14.4 总结

同调代数，特别是同调和同伦知识，已应用于计算机科学。同调理论是一种边界划分方法。因此，我们介绍了同调边界，并提出了同调边界划分模型以及胞腔同调边界划分模型。

## 参考文献

- [1] Fabio A, Alessandro S. A re-weighting strategy for improving margins. Artificial Intelligence, 2002, 137, 197–216.
- [2] Zhang C, Zhang H. Application of Canny algorithm for edge detection of grain shape. Grain and Feed Industry, 2008, 6, 3–4.
- [3] Chen CK, Yang JY. Regularized Large Margin Classifier. Third international Conference on Natural Computation, 2007.
- [4] Wang T, Xing XL, Zhuang XH. A new edge detection algorithm. Electronic journal, 1992, 20(1), 74–77.
- [5] Wang SP, Li RQ, Fu DS. Fuzzy edge detection algorithm based on qualification function. Computer Engineering, 2005, 31(23), 167–168.
- [6] Jiang ZH. An introduction to topological Science. Shanghai: Shanghai science and Technology Press, 1978.
- [7] Jiang BJ. Homology. Beijing: Peking University press, 2006.
- [8] Liao ST, Liu WJ. The basis of homotopy theory. Beijing: Peking University press, 1980.
- [9] Chen ZH. The theory of layer and its cohomology. Shanghai: Tongji University press, 1997.
- [10] Huang BJ. Homology and homotopy principle. Hefei: University of Science and Technology China press, 2005.
- [11] Xian M, Li FZ. A homology edge learning algorithm. Computer Engineering and Application, 2008, 44(21), 192–194.

