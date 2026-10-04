

在光 OFDM-IM 接收机中，在移除 CP 并实现 FFT 操作之后，紧接着进行信道估计操作。为了能够在频域中均衡接收信号，估计信道频率响应非常重要。*X̂ [g]* (*i*) 是 FFT 操作后第 *g^(th)* 个 OFDM 子块的接收向量，其由下式给出

(10)

*X̂*[*g*](*i*) = *H*[*g*](*i*)*X*[*g*](*i*) + *W*[*g*](*i*), *i* = 1, …, *n*

其中 *H[g]*(*i*) 和 *W[g]*(*i*) 分别表示第 *g^(th)* 个 OFDM 子块的第 *i^(th)* 个子载波上的信道频率响应和零均值复加性高斯白噪声 (AWGN)，其方差为 *N*[0]。用于信道估计的 PN 序列块适用于慢变的光纤光学信道，其由下式给出

(11)

$${\\hat{H}}\_{g}(i) = \\frac{{\\hat{X}}\_{g}^{PN}(i)}{X\_{g}^{PN}(i)},i = 1,\\ldots,n$$

其中 *X*̂ *[g]^(PN)* (*i*) a d n *X[g]^(PN)* (*i*) 分别是接收端和发送端第 *g^(th)* 个 OFDM 子块的第 *i^(th)* 个子载波上的 PN 序列信号。

[Table 27.1](#ch27.xhtml#tab27_1) 总结了 *p*[1] 位序列与 *J* 个活动子载波索引之间的映射关系，对于 *n* = 4, *k* = 2 和 *p*[1] = 2。

它需要检测活动子载波的索引以及相应的附加信息位。索引检测器用于从每个 OFDM 子块中检测活动子载波的索引。光 OFDM-IM 系统的最大似然 (ML) 检测器搜索所有子载波索引和星座点的组合，以便对每个 OFDM 子块的活动子载波索引和传输符号进行联合判决。每个比特的 ML 检测的搜索空间由 *O*(*C*(*n*, k) + *M^k*) 的阶给出。由于复杂度随着 *k* 值增加而呈指数增长，最优 ML 检测器具有较高的复杂度。为了实现接近最优的性能，提出了低复杂度的后验概率检测 (PPD) 方法 \[[8](#ch27.xhtml#ref27_8)\]。

光 OFDM-IM 的 PPD 检测器通过考虑值是零或非零的情况，给出了频域信号后验概率的对数比 \[[9](#ch27.xhtml#ref27_9)\]。对于第 *g^(th)* 个 OFDM 子块，PPD 检测器给出对应索引 *i* 为活动状态的概率，其中 *i* = 1, 2, ..., *n*，由下式给出；

(12)

$$\\lambda\_{g}(i) = \\ln\\frac{{\\sum\_{m = 1}^{M}P}\\left( {X\_{g}(i) = Q\_{m} \\mid {\\hat{X}}\_{g}(i)} \\right)}{P\\left( {X\_{g}(i) = 0 \\mid {\\hat{X}}\_{g}(i)} \\right)},$$

其中 *Q[j]* 是 *M*\-ary 信号星座的一个元素。λ[*g*] (*i*) 的值越大，对应 *i* 为活动子载波的概率越高。利用贝叶斯公式，式 (12) 可表示为

(13)

$$\\lambda\_{g}(i) = \\ln(k) - \\ln(n - k) + \\frac{\\left| {{\\hat{X}}\_{g}(i)} \\right|^{2}}{\\sigma\_{k}^{2}} + \\ln\\left( {{\\sum\\limits\_{m = 1}^{M}\\exp}\\left( {- \\frac{1}{\\sigma\_{k}^{2}}\\left| {{\\hat{X}}\_{g}(i) - H\_{g}(i)Q\_{m}} \\right|^{2}} \\right)} \\right)$$

在根据式 (13) 得到所有后验概率后，对于每个 OFDM 子块，接收机决定具有最大后验概率的 *k* 个活动索引 (*Ĵ*)。确定 *k* 个活动索引后，附加信息位和数据符号可以很容易地确定。

它从索引检测器获取活动索引序列，并对每个 OFDM 子块执行 *k*—组合系数的求和 (Algorithm-2)。计算出十进制数 *Ẑ* 后，可通过十进制到二进制转换器确定附加信息位。*k* 个活动子载波上 *M* —ary 信号星座 (*Q*) 集合的传输符号估计为

(14)

*P̂*[*g*](*i*)|[*i* = 1]^(*k*) = arg min[(*Q*[*m*] ∈ *Q*)]|*X̂*[*g*](*i*)−*Ĥ*[*g*](*i*)*Q*[*m*]|²

## 3. 性能分析

### 3.1 光谱效率

光谱效率 (SE) 是 OFDM 系统中的一个重要性能参数。它定义为单位带宽 B 内可以实现的比特率。对于传统的光 OFDM 系统，SE 可以由下式给出

(15)

$$\\text{~Spectral~Efficiency~}\_{\\text{O-OFDM~}} = \\frac{N\_{u}\\log\_{2}M}{\\left( {T\_{FFT} + T\_{CP}} \\right)B}\\text{,~}$$

其中 *N[u]* 是光 OFDM 系统中用于数据传输的活动子载波数，且

(16)

$$\\text{SE}\_{\\text{O} - \\text{OFDM} - \\text{IM}} = \\frac{G\\left( {k\\log\_{2}M + \\log\_{2}(C(n,k))} \\right)}{\\left( {T\_{FFT} + T\_{CP}} \\right)B}$$

| **Algorithm 2**: Obtain Decimal Number Ẑ from the Indices Sequence Ĵ |
| --- |
| 
1. **Input:** The indices sequence Ĵ = {Ĵk, , … Ĵ1}, the number of subcarriers n, the number of active subcarriers *k*
2. Ẑ ← 0
3. **for** *i* = 1: k **do**
4. ComCoef ← C (Ĵ[*i*], *i*)
5. Ẑ ← Ẑ + ComCoef
6. : **end for**
7. : **return Z**̂
 |

考虑 *N[u]* = *N[FFT]* = 256 和 *N[CP]* = 16，光 OFDM 系统可实现 0.9412 bits/s/Hz 的光谱效率值，采用 2-PSK 调制方案。然而，光 OFDM with IM 系统可实现 *n* = 4, *k* = 2 时 0.9412 bits/s/Hz 的光谱效率值，以及 *n* = 4, *k* = 3 时 1.1765 bits/s/Hz 的光谱效率值，均采用 2-PSK 调制方案。

因此，在光 OFDM with IM 系统的情况下，对于所选的 *n* 和 *k* 值，光谱效率值可以高于光 OFDM 系统。因此，适当选择 *n* 和 *k* 值有助于增强光谱效率性能。在 [Figure 27.2](#ch27.xhtml#fig27_2) 中，光谱效率作为活动子载波 *k* 的函数，在各种 OFDM 子块水平下，对于 *M* = 2, *N[FFT]* = 256, *N[CP]* = 16 以及 2-PSK 调制方案。从 [Figure 27.2](#ch27.xhtml#fig27_2) 可以观察到，当选择适当的活动子载波数时，光 OFDM with IM 系统可以提高光谱效率，优于简单的光 OFDM 系统。

![Figure 27.2 SE of optical-OFDM with IM system.](images/fig27_2_C.jpg)

[Figure 27.2 SE of optical-OFDM with IM system.](#ch27.xhtml#R_fig27_2)

[Figure 27.3](#ch27.xhtml#fig27_3) 说明了光 OFDM with IM 可以在 2-PSK、4-PSK 和 16-QAM 调制方案下实现比光 OFDM 更好的 SE 性能。然而，对于更高阶调制方案，光 OFDM-IM 的 SE 无法与简单的光 OFDM 竞争。

![Figure 27.3 SE in the Optical-OFDM system with IM for different OFDM sub-block configurations.](images/fig27_3_C.jpg)

[Figure 27.3 SE in the Optical-OFDM system with IM for different OFDM sub-block configurations.](#ch27.xhtml#R_fig27_3)

光谱效率的最大化几乎等同于最大化每符号的比特数。二项式系数序列 *C*(*n*, *k*) 是一个对数凹序列。因此，可以在分析上检测使 *p* 比特最大化的活动子载波的最优值 \[[19](#ch27.xhtml#ref27_19)\]。于是，

(17)

*p* = *k*log[2]*M* + log[2](*C*(*n*, *k*))

考虑在式 (17) 中去掉 floor 函数，然后对 *p* 关于 *k* 求导可表示为

(18)

$$\\frac{dp}{dk} = \\log\_{2}M + \\log\_{2}\\left( {\\Gamma\_{n - k} - \\Gamma\_{k}} \\right)$$

(19)

$$\\Gamma\_{k} = {\\sum\\limits\_{i = 1}^{k}\\frac{1}{j}} = \\frac{1}{1} + \\frac{1}{2} + \\frac{1}{3} + \\ldots + \\frac{1}{k}.$$

其中 *k^(th)* 调和数 Г[*k*] 是前 k 个正整数倒数之和。由于极限 (Г[*k*] - log *k*) → γ 为欧拉-马歇罗尼常数，Г[*k*] 的近似值可表示为

(20)

