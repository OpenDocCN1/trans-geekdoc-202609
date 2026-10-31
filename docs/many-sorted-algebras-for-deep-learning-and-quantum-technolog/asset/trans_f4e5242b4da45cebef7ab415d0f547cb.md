
$\\begin{array}{llllll} {|0} & { i|} & {|0} & {{- 1}|} & {|i} & {\\quad 0|} \\\\ {|i} & {0|} & {|1} & {\\mspace{20mu} 0|} & {|0} & {{- i}|} \\\\ \\end{array}$

![方程](Images/F000126si56.png)

换位子 `\[M1, M2\]=2 M3`、`\[M2, M3\]=2 M1`，最后，`\[M3, M1\]=2 M2`。`\[Mi, Mj\]=2 Eijk Mk`。这里，列维-奇维塔符号 `Eijk` 再次被使用。李代数 `sl(2,C)=su(2,C) + su(2,C) i`。该表达式将给出 `su(2,C)` 的复化。特殊线性代数 `sl(2,C)` 中最一般的元素是 `N=`

$\\begin{matrix} {|{x + {iy}}} & {{\\mspace{22mu} u + {iv}}|} \\\\ {|{r + {is}}} & {{- x - {iy}}|} \\\\ \\end{matrix}$

![方程](Images/F000126si57.png)

该矩阵具有复数值，且迹等于零。该李代数的一个基按 `N1`、`N2` 和 `N3` 的顺序如下给出：

$\\begin{array}{rrrrrr} {|1} & {0|} & {|0} & {1|} & {|0} & {0|} \\\\ {|0} & {{- 1}|} & {|0} & {0|} & {|1} & {0|} \\\\ \\end{array}$

![方程](Images/F000126si58.png)

回到 `su(2, C)` 并现在利用上述基可知 `su(2, C)` 中最一般的矩阵是 `M=ixN1−c\*N2 + cN3`，因为 `M` 由以下给出：

$\\begin{matrix} {|{ix}} & {{- c \\ast}|} \\\\ {|c} & {{ - {ix}}|} \\\\ \\end{matrix}$

![方程](Images/F000126si59.png)

这并不令人惊讶，因为 `su(2,C)` 是 `sl(n, C)` 的子李代数。目标是看到涉及 `su(2, C)` 复化的展开。现在考虑 `sl(2, C)` 中最一般的矩阵，它是 `N=−ixM3 + yM3−u/2 (M2 + i M1)−iv/2 (M2 + i M1) + r/2 (M2−iM1) + is/2 (M2−iM1)`。这表明两个李代数本质上是相同的。此外，注意描述 `N` 只需要 `su(2, C)` 的六个复化基元素。这六个矩阵是 `M1`、`M2`、`M3`、`iM1`、`iM2` 和 `iM3`。再次，这也是可以预期的，因为 `sl(2, C)` 在实数域上的维数是六。

## 参考文献

*   [Bargmann, 1947](#Ch011_191-216_B9780443136979000126.xhtml#BIB_1) Bargmann V. 洛伦兹群的不可约酉表示。*Ann Math.* 1947;48n.
*   [Benkart, 1977](#Ch011_191-216_B9780443136979000126.xhtml#BIB_2) Benkart G. 关于李代数的内理想和 ad-幂零元。*Trans Am Math Soc.* 1977;.
*   [Berry, 2006](#Ch011_191-216_B9780443136979000126.xhtml#BIB_3) Berry, D., 2006. 用于模拟稀疏哈密顿量的高效量子算法，arXiv:quant-ph/0508139.
*   [Draper and Meulewaeter, 2022](#Ch011_191-216_B9780443136979000126.xhtml#BIB_4) Draper C, Meulewaeter J. 实单李代数的内理想。*Bull Malaysian Math Sci Soc.* 2022;45.
*   [Giardina, 1973](#Ch011_191-216_B9780443136979000126.xhtml#BIB_5) Giardina, C., 1973. 使用 Cayley 变换和四元数的 strapdown 导航，Singer Kearfott，报告。
*   Gilmore, 1974 Gilmore R. *李群、李代数及其某些应用* J Wiley & Sons 1974;.
*   Hall, 2013 Hall B. *数学家的量子理论*. 978-1461471158  *GTM*. Vol. 267 Springer 2013;.
*   Hall, 2015 Hall B. 978-3319134666  *李群、李代数与表示*. Vol. 222 second ed. Springer 2015;.
*   [Hatcher, 2002](#Ch011_191-216_B9780443136979000126.xhtml#BIB_9) Hatcher A. 0-521-79540-0 *代数拓扑* Cambridge U. Press 2002;.
*   [Humphreys, 1997](#Ch011_191-216_B9780443136979000126.xhtml#BIB_10) Humphreys J. 978-3540900535  *李代数与表示论导论*. Vol. 9 second ed. Springer 1997;.
*   Jacobson, 1979 Jacobson N. 9978-0486-63832-4 *李代数* Dover 1979;.
*   [Johnson, 1976](#Ch011_191-216_B9780443136979000126.xhtml#BIB_12) Johnson R. 紧群在拓扑向量空间上的表示：一些注记。*Proc Am Math Soc.* 1976;61.
*   [Palais et al., 2008](#Ch011_191-216_B9780443136979000126.xhtml#BIB_13) Palais B, et al. 对欧拉旋转轴定理的一种令人困惑的审视。*Am Math Monthly*. 2008;116(10):200.

# 第13章
## 算子的谱

### 摘要

展示谱存在性的判据已得到回顾。Lumer-Phillips 定理在 Banach 空间中对伴随算子和对偶算子的谱应用已给出。对点谱、连续谱以及 Banach 空间和 Hilbert 空间中的剩余谱给出了描述和示例。Hellinger-Toeplitz 定理针对无界算子陈述并举例说明，包括动量算子和距离算子。数值域相对于谱值以及耗散算子和增生算子进行了描述。给出了对称算子为自伴算子的条件。近似特征值概念连同其在紧算子上的应用被描述。Cauchy 积分定理被用于确定预解集。本章以谱测度和谱理论的介绍结束。此外，在最后一节中，举例说明了 Stieltjes 积分。并且，投影值测度相对于谱定理进行了描述。

#### 关键词

Lumer-Phillips 定理; Hellinger-Toeplitz 定理; 一参数半群; 耗散算子; 增生算子; Stieltjes 积分; 剩余谱; 近似谱; saltus

## 13.1 有界算子的谱分类

本节是 [第 8.5 节](#Ch008_145-164_B9780443136979000059.xhtml#s0030) 和 [第 8.6 节](#Ch008_145-164_B9780443136979000059.xhtml#s0035) 的延续。本章主要早期部分的主要参考文献是 [Halmos (1957)](#Ch013_231-253_B9780443136979000138.xhtml#bib20) 和 [He’lein (2014)](#Ch013_231-253_B9780443136979000138.xhtml#bib21)。在 [第 8 章](#Ch008_145-164_B9780443136979000059.xhtml#Ch008_145-164_B9780443136979000059) 中，源自第一参考文献的判据 [Halmos, 1957](#Ch013_231-253_B9780443136979000138.xhtml#bib20) 已给出用于说明谱的存在，具体为 Hilbert 空间 `H` 中的谱 `spT`。必要充分条件在此重复。对于算子 `T`，在 `B(H,H)` 中，`spT={c, such that c in C, and (c I−T) is not invertible iff both 1) and 2) hold}`：

1. 1) `T` 的像在 `H` 中稠密，且
2. 2) 存在标量 `a> 0` 使得对所有 `v` 在 `H` 中 `‖Tv‖>a‖v‖`。

在前面给出的第二参考文献中，判据 (1) 被称为弱满射，而第二判据 (2) 被暗示为强单射。

对于 `T`，在 `B(H,H)` 中，`T` 的谱已被证明非空并在 `C` 中形成紧集。此外，预解集 `RsT` 是 `C` 中的开集。该集合 `RsT` = {`λ`![方程](Images/F000138si3.png)，其中 `λ`![方程](Images/F000138si4.png) 在 `C` 中，且使得 (`T−λI`) 是单射且满射，(`T−λI`) ^(−1)![方程](Images/F000138si5.png) 有界}。逆的有界性也由有界逆定理得出。该定理可在附录 A.6 中找到。此外，`spT` 的一个划分由三个不相交集合 `sppT`、`spcT` 和 `sprT` 提供。简要地，谱将对 `T` 进行描述，`T` 是不同于 `{0}` 的复 Banach 空间 `X` 上的有界算子。内积对于此发展不是必要的；因此使用 Banach 空间。提供了众多示例，并在无界情形下以形式方式给出。不考虑定义域问题。

1. 1) 点谱 `sppT={λ in C such that (T−λI) is not one to one on X}`。
2. 2) 连续谱 `spcT={λ in C such that (T−λI) is one to one on X, but it is not onto X; however, it has ran (T−λI) dense in X}`。
3. 3) 剩余谱 `sprt={λ in C such that (T−λI) is one to one and not onto, but with ran (T−λI) not dense in X}`。

