
其中 f(i, j) 是尺寸为 U × U 的原始图像，而 f̂(i, j) 是解密后的图像。

图 8.2 和 8.3 分别展示了在频率选择性信道中，采用混沌和混沌输出反馈（OFB）加密算法的 FFT-OFDM、DCT-OFDM 和 DWT-OFDM 系统的 PSNR 性能随 E_b/N_0 的变化情况。

在没有 CFO 补偿且采用导频符号估计（PSE）的情况下，研究表明 CFO 扰乱了所有 OFDM 系统的 PSNR 性能；采用 CFO 补偿后，所有系统的 PSNR 性能均优于未补偿的情况。

这些图还显示，与 DCT-OFDM 和 DWT-OFDM 系统相比，采用 FFT-OFDM 系统的所有加密算法的 PSNR 性能最佳。

图 8.4 给出了在 N = 128 且 G = 32 时，FFT-OFDM 系统在 AWGN 信道上传输原始 Cameraman 图像的输出。

图 8.5 给出了在 N = 128 且 G = 32 时，FFT-OFDM 系统在衰落信道上传输原始 Cameraman 图像的输出。

![](img/47f81eeb5093bf67426e3b948e0d8952_127_0.png)

图 8.2 混沌加密图像在瑞利信道上通过 OFDM 系统传输时的 PSNR 与 E_b/N_0 关系。

![](img/47f81eeb5093bf67426e3b948e0d8952_128_0.png)

图 8.3 混沌-OFB 加密图像在瑞利衰落信道上通过 OFDM 系统传输时的 PSNR 与 E_b/N_0 关系。

![](img/47f81eeb5093bf67426e3b948e0d8952_128_1.png)

(a) E_b/N_0 = 0 dB
PSNR = 14.6993

(b) E_b/N_0 = 5 dB
PSNR = 23.7838

(c) E_b/N_0 = 10 dB
PSNR = 48.0593

(d) E_b/N_0 = 15 dB
PSNR > 60

图 8.4 AWGN 信道上 FFT-OFDM 的原始图像。

![](img/47f81eeb5093bf67426e3b948e0d8952_129_0.png)

图 8.5 衰落信道上 FFT-OFDM 的原始图像。

图 8.6 给出了在 *N* = 128 且 *G* = 32 时，FFT-OFDM 系统在 AWGN 信道上传输混沌加密图像的输出。

图 8.7 给出了在 *N* = 128 且 *G* = 32 时，FFT-OFDM 系统在衰落信道上传输混沌加密图像的输出。

图 8.8 给出了在 *N* = 128 且 *G* = 32 时，DCT-OFDM 系统在 AWGN 信道上传输原始 Cameraman 图像的输出。

图 8.9 给出了在 *N* = 128 且 *G* = 32 时，DCT-OFDM 系统在衰落信道上传输原始 Cameraman 图像的输出。

![](img/47f81eeb5093bf67426e3b948e0d8952_130_0.png)

图 8.6 AWGN 信道上 FFT-OFDM 的混沌加密图像。

图 8.10 给出了在 $N = 128$ 且 $G = 32$ 时，DCT-OFDM 系统在 AWGN 信道上传输混沌加密图像的输出。

图 8.11 给出了在 $N = 128$ 且 $G = 32$ 时，DCT-OFDM 系统在衰落信道上传输混沌加密图像的输出。

图 8.12 给出了在 $N = 128$ 且 $G = 32$ 时，DWT-OFDM 系统在 AWGN 信道上传输原始 Cameraman 图像的输出。

图 8.13 给出了在 $N = 128$ 且 $G = 32$ 时，DWT-OFDM 系统在衰落信道上传输原始 Cameraman 图像的输出。

![](img/47f81eeb5093bf67426e3b948e0d8952_131_0.png)

图 8.7 衰落信道上 FFT-OFDM 的混沌加密图像。

图 8.14 给出了在 *N* = 128 且 *G* = 32 时，DWT-OFDM 系统在 AWGN 信道上传输混沌加密图像的输出。

图 8.15 给出了在 *N* = 128 且 *G* = 32 时，DWT-OFDM 系统在衰落信道上传输混沌加密图像的输出。

表 8.2 总结了这些结果。

## 8.8 PAPR 的影响

OFDM 的主要限制之一是较高的 PAPR。通过子载波的建设性叠加可以得到具有大峰值的信号。PAPR 与子载波数量呈线性关系，并以 PAPR 来评估。

![](img/47f81eeb5093bf67426e3b948e0d8952_133_0.png)

图 8.9 衰落信道上 DCT-OFDM 的原始图像。

发送的 OFDM 信号的 PAPR 定义为

$$\mathrm{PAPR}=\frac{P_{peak}}{P_{avg}}=\frac{\max\left(|\bar{x}_m|^2\right)}{\frac{1}{N}\sum_{m=0}^{N-1}|\bar{x}_m|^2},\quad m=0,1,\ldots,N-1 \tag{8.20}$$

在式 (8.20) 中，分子表示最大包络功率，分母表示平均功率。

PAPR 的累积分布函数（CDF）是在应用 PAPR 降低技术前后最常用的 PAPR 性能指标之一。在文献中，通常使用互补累积分布函数（CCDF）代替

![](img/47f81eeb5093bf67426e3b948e0d8952_134_0.png)

(a) E_b/N_0 = 0 dB
PSNR = 15.0481

![](img/47f81eeb5093bf67426e3b948e0d8952_134_1.png)

(b) E_b/N_0 = 5 dB
PSNR = 24.4613

![](img/47f81eeb5093bf67426e3b948e0d8952_134_2.png)

(c) E_b/N_0 = 10 dB
PSNR = 53.4971

![](img/47f81eeb5093bf67426e3b948e0d8952_134_3.png)

(d) E_b/N_0 = 15 dB
PSNR >60

图 8.10 AWGN 信道上 DCT-OFDM 的混沌加密图像。

CDF 本身。PAPR 的 CCDF 表示数据块的 PAPR 超过给定阈值的概率。在 [152] 中，推导出了多载波信号 PAPR 的 CCDF 的一个简单近似表达式；x(t) 的实部和虚部服从高斯分布。OFDM 信号样本幅度 z 的 CDF 由下式给出

F(z) = 1 - e^{-z}   (8.21)

我们需要推导 OFDM 数据块 PAPR 的 CDF。假设信号样本互不相关且不相关，OFDM 数据块的 PAPR 的 CDF 可以表示为

P(PAPR ≤ z) = F(z)^N = (1 - e^{-z})^N   (8.22)

![](img/47f81eeb5093bf67426e3b948e0d8952_135_0.png)

(a) E_b/N_0 = 0 dB
PSNR = 16.3858

![](img/47f81eeb5093bf67426e3b948e0d8952_135_1.png)

(b) E_b/N_0 = 5 dB
PSNR = 23.0375

![](img/47f81eeb5093bf67426e3b948e0d8952_135_2.png)

(c) E_b/N_0 = 10 dB
PSNR = 30.3995

![](img/47f81eeb5093bf67426e3b948e0d8952_135_3.png)

(d) E_b/N_0 = 15 dB
PSNR = 33.2591

图 8.11 衰落信道上 DCT-OFDM 的混沌加密图像。

当采用过采样时，信号样本互不相关且不相关的假设是不成立的。此外，对于少量子载波而言，该表达式也不准确，因为在这种情况下高斯假设不成立 [156–159]。研究表明，N 个子载波的过采样信号的 PAPR 可由无过采样的 αN 个子载波的分布近似，其中 α 大于 1 [160]。换句话说，过采样的效果可通过增加一定数量的额外信号样本来近似。

因此，过采样信号的 PAPR 的 CDF 由下式给出

$P(PAPR \le z) \approx (1 - e^{-z})^{\alpha N}$ (8.23)

![](img/47f81eeb5093bf67426e3b948e0d8952_136_0.png)

![](img/47f81eeb5093bf67426e3b948e0d8952_136_1.png)

![](img/47f81eeb5093bf67426e3b948e0d8952_136_2.png)

![](img/47f81eeb5093bf67426e3b948e0d8952_136_3.png)

图 8.12 AWGN 信道上 DWT-OFDM 的原始图像。

研究发现，对于四倍过采样的 OFDM 信号，α = 2.3 是一个很好的近似值 [161]。根据式 (8.23)，PAPR 超过 PAPR₀ 的概率由下式给出

CCDF = Pr[PAPR > PAPR₀] = 1 - (1 - e^{-PAPR₀})^{αN} (8.24)

## 8.9 PAPR 降低方法

文献中已提出了多种 OFDM 信号 PAPR 降低方法。在本书中，我们重点关注其中三种方法：削波、压缩和混合削波与压缩。这些都是三种简单的 PAPR 降低方法。我们的目标是展示 PAPR 降低方法对加密图像传输的影响。

![](img/47f81eeb5093bf67426e3b948e0d8952_137_0.png)

(a) E_b/N_0 = 0 dB
PSNR = 17.5731

![](img/47f81eeb5093bf67426e3b948e0d8952_137_1.png)

(b) E_b/N_0 = 5 dB
PSNR = 24.9482

![](img/47f81eeb5093bf67426e3b948e0d8952_137_2.png)

(c) E_b/N_0 = 10 dB
PSNR = 32.6435

![](img/47f81eeb5093bf67426e3b948e0d8952_137_3.png)

(d) E_b/N_0 = 15 dB
PSNR = 37.7109

图 8.13 衰落信道上 DWT-OFDM 的原始图像。

### 8.9.1 削波方法

削波是最简单的方法，可将信号幅度限制在期望的阈值。它是非线性过程，可能导致带内失真和带外辐射。这会导致 BER 性能下降 [162,163]。在削波方法中，当幅度超过某一阈值时，会进行硬削波，而相位被保留。也就是说，当我们假设基带 OFDM 信号 \bar{x}_m 的相位为 \phi_m 且阈值为 A 时，削波后的输出信号如下所示：

```
\bar{x}_m = \begin{cases} A e^{j\phi_m} & |\bar{x}_m| > A \\ \bar{x}_m & |\bar{x}_m| \le A \end{cases} \tag{8.25}
```
