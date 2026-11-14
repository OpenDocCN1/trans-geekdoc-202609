
广义`Omega函数`[[维基百科](https://en.wikipedia.org/wiki/Prime_omega_function)]定义如下：若`q[k]`![Image](images/B9780443218576000217/si43.png)的质因数分解为`q[k] = p[1]^(a[1]) p[2]^(a[2]) ⋯ p[d]^(a[d])`![Image](images/B9780443218576000217/si67.png)，则`Ω(q[k]) = a[1]χ(p[1]) + ⋯ + a[d]χ(p[d])`![Image](images/B9780443218576000217/si68.png)。函数`(-1)^(Ω(q[k]))`![Image](images/B9780443218576000217/si69.png)记作`λ(q[k])`![Image](images/B9780443218576000217/si70.png)，称为广义`刘维尔函数`[[维基百科](https://en.wikipedia.org/wiki/Liouville_function)]。公式[(17.4)](#Chp017_329-360_B9780443218576000217.xhtml#deq5)中的级数称为`狄利克雷-L函数`[[维基百科](https://en.wikipedia.org/wiki/Dirichlet_L-function)]。函数`χ`可推广至所有严格正整数，如下所示：`χ(1) = 1`![Image](images/B9780443218576000217/si6.png)，若`p ∉ P`![Image](images/B9780443218576000217/si72.png)则`χ(p) = 0`![Image](images/B9780443218576000217/si71.png)，且`χ(ab) = χ(a)χ(b)`![Image](images/B9780443218576000217/si5.png)。于是`χ(q[k]) = λ(q[k])`![Image](images/B9780443218576000217/si73.png)是一个`完全乘法函数`[[维基百科](https://en.wikipedia.org/wiki/Multiplicative_function)]。

从现在起，所有记作`χ(⋅)`![Image](images/B9780443218576000217/si4.png)的函数均假定为完全乘法函数，因此由其在素数参数上取得的值唯一确定。现在，设`L_P(z, χ) = (1 - 2^(1 - z))^(-1) η_P(z, χ)`![Image](images/B9780443218576000217/si74.png)。则有：

$L\_{P}(z,\\chi) = \\sum\\limits\_{k = 1}^{\\infty}\\chi(k)k^{- z},\\quad\\eta\_{P}(z,\\chi) = (1 - 2^{1 - z})L\_{P}(z,\\chi) = \\sum\\limits\_{k = 1}^{\\infty}{( - 1)}^{k + 1}\\chi(k)k^{- z},$

![Image](images/B9780443218576000217/si75.png)(17.5) 

$L\_{P}(z,\\chi) = \\prod\\limits\_{p \\in P}\\frac{1}{1 - \\chi(p)p^{- z}},\\quad|L\_{P}(z,\\chi)| = \\prod\\limits\_{p \\in P}|1 - \\chi(p)p^{- z}|^{- 1} \\geqslant \\prod\\limits\_{p \\in P}\\frac{1}{1 + p^{- \\sigma}}.$

![Image](images/B9780443218576000217/si76.png)(17.6) 

若对固定整数`m > 1`![Image](images/B9780443218576000217/si77.png)，当`p, q ∈ P`![Image](images/B9780443218576000217/si79.png)为满足`p ≡ q mod m`![Image](images/B9780443218576000217/si80.png)的两个素数时有`χ(p) = χ(q)`![Image](images/B9780443218576000217/si78.png)，且若`p`整除`m`时额外有`χ(p) = 0`![Image](images/B9780443218576000217/si71.png)，则称`χ(⋅)`![Image](images/B9780443218576000217/si4.png)为模`m`的`狄利克雷特征`[[维基百科](https://en.wikipedia.org/wiki/Dirichlet_character)]。标准Omega函数和刘维尔函数对应`χ`为常数+1、且`P`为全体素数集合的情况。标准刘维尔函数还满足

$\\sum\\limits\_{k = 1}^{n}\\lambda(k)\\left\\lfloor \\frac{n}{k} \\right\\rfloor = \\lfloor\\sqrt{n}\\rfloor,\\quad L(n) = \\sum\\limits\_{k = 1}^{n}\\lambda(k) = \\sum\\limits\_{k = 1}^{n}\\mu(k)\\left\\lfloor \\sqrt{\\frac{n}{k}} \\right\\rfloor,$

![Image](images/B9780443218576000217/si81.png)

其中`μ(k)`![Image](images/B9780443218576000217/si82.png)是刘维尔的姐妹函数，称为`莫比乌斯函数`[[维基百科](https://en.wikipedia.org/wiki/M%C3%B6bius_function)]。详见[此处](https://mathoverflow.net/questions/393351/exact-formula-for-partial-sums-of-liouville-function-ln-oeis-sequence-a0028)。括号代表取整函数。刘维尔函数的部分和记作`L(n)`![Image](images/B9780443218576000217/si83.png)，而莫比乌斯函数的部分和称为`梅滕斯函数`[[维基百科](https://en.wikipedia.org/wiki/Mertens_function)]，记作`M(n)`![Image](images/B9780443218576000217/si84.png)。若`q = q[k] = p[1]^(a[1]) p[2]^(a[2]) ⋯ p[d]^(a[d])`![Image](images/B9780443218576000217/si85.png)，则`μ(q[k]) = (-1)^(w(q[k]))`![Image](images/B9780443218576000217/si86.png)，其中`ω(q[k]) = χ(p[1]) + ⋯ + χ(p[d])`![Image](images/B9780443218576000217/si87.png)。标准莫比乌斯函数对应`χ`为常数函数1、且`P`为全体素数集合的情况。

最后，公式[(17.3)](#Chp017_329-360_B9780443218576000217.xhtml#deq4)给出了原点到`η_P(z, χ)`![Image](images/B9780443218576000217/si88.png)轨道上任意点距离的下界，该公式仍然适用且保持不变。特别地，若`P`为全体素数集合（或足够大的无限子集），则因乘积发散，下界为零。若该下界确实被达到（即使仅渐近地），则找到比单点集更大的空洞的希望便会落空。

### 17.2.2 无限欧拉乘积

若`P`为全体素数集合，则公式[(17.1)](#Chp017_329-360_B9780443218576000217.xhtml#deq2)、[(17.3)](#Chp017_329-360_B9780443218576000217.xhtml#deq4)和[(17.4)](#Chp017_329-360_B9780443218576000217.xhtml#deq5)中的乘积变为无限乘积。结果，若`0.5 ≤ σ < 1`![Image](images/B9780443218576000217/si89.png)，[图17.1](#Chp017_329-360_B9780443218576000217.xhtml#f0010)中轨道内的空洞可能收缩为空集（`σ = 0.5`![Image](images/B9780443218576000217/si53.png)）或单点——即原点（若`0.5 < σ < 1`![Image](images/B9780443218576000217/si90.png)）。实际上，后一种情况下也可能是空集；无人知晓。但黎曼假设断言它应为单点。这是`χ`为常数函数1时的情况。此语境下该函数称为`主特征`。但若`χ`非常数会怎样？在后一种情况下，视`χ`而定，轨道可能永远不会过于接近原点。

考虑一个称为非平凡`模4狄利克雷特征`的`完全乘法`函数`χ`，记作`χ[4]`![Image](images/B9780443218576000217/si1.png)或`χ[4, 1]`![Image](images/B9780443218576000217/si91.png)。它由其在素数`p`上的取值唯一确定，如下：若`p mod 4 = 1`![Image](images/B9780443218576000217/si93.png)则`χ[4](p) = +1`![Image](images/B9780443218576000217/si92.png)；若`p mod 4 = 3`![Image](images/B9780443218576000217/si95.png)则`χ[4](p) = -1`![Image](images/B9780443218576000217/si94.png)；且`χ[4](2) = 0`![Image](images/B9780443218576000217/si96.png)。它对所有正整数满足`χ[4](k + 4) = χ(k)`![Image](images/B9780443218576000217/si97.png)。同样，`P`为全体素数集合。
