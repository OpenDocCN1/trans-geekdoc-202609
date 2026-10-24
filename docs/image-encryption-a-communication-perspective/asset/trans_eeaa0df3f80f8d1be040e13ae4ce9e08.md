
![](img/47f81eeb5093bf67426e3b948e0d8952_184_0.png)

![](img/47f81eeb5093bf67426e3b948e0d8952_184_1.png)

![](img/47f81eeb5093bf67426e3b948e0d8952_184_2.png)

![](img/47f81eeb5093bf67426e3b948e0d8952_184_3.png)

图 9.53 在 AWGN 信道中采用 DCT-OFDM 的混沌加密图像。

图 9.84 给出了在 $N=128$ 且 $G=32$ 时，混沌加密图像在衰落信道中传输的 DWT-OFDM 系统输出。

图 9.85 给出了在 $N=128$ 且 $G=32$ 时，DES 加密图像在 AWGN 信道中传输的 DWT-OFDM 系统输出。

图 9.86 给出了在 $N=128$ 且 $G=32$ 时，DES 加密图像在衰落信道中传输的 DWT-OFDM 系统输出。

图 9.87 给出了在 $N=128$ 且 $G=32$ 时，AES 加密图像在 AWGN 信道中传输的 DWT-OFDM 系统输出。

![](img/47f81eeb5093bf67426e3b948e0d8952_185_0.png)

![](img/47f81eeb5093bf67426e3b948e0d8952_185_1.png)

![](img/47f81eeb5093bf67426e3b948e0d8952_185_2.png)

![](img/47f81eeb5093bf67426e3b948e0d8952_185_3.png)

图 9.54 在衰落信道中采用 DCT-OFDM 的混沌加密图像。

图 9.88 给出了在 N = 128 且 G = 32 时，AES 加密图像在衰落信道中传输的 DWT-OFDM 系统输出。

图 9.89 给出了在 N = 128 且 G = 32 时，RC6 加密图像在 AWGN 信道中传输的 DWT-OFDM 系统输出。

图 9.90 给出了在 N = 128 且 G = 32 时，RC6 加密图像在衰落信道中传输的 DWT-OFDM 系统输出。

表 9.2 总结了这些结果。

![](img/47f81eeb5093bf67426e3b948e0d8952_186_0.png)

(a) E_b/N_0 = 0 dB
PSNR = 8.3762

![](img/47f81eeb5093bf67426e3b948e0d8952_186_1.png)

(b) E_b/N_0 = 5 dB
PSNR = 11.1133

![](img/47f81eeb5093bf67426e3b948e0d8952_186_2.png)

(c) E_b/N_0 = 10 dB
PSNR = 34.4818

![](img/47f81eeb5093bf67426e3b948e0d8952_186_3.png)

(d) E_b/N_0 = 15 dB
PSNR >60

图 9.55 在 AWGN 信道中采用 DCT-OFDM 的 DES 加密图像。

## 9.2 存在 CFO 时的仿真实验

图 9.91 展示了 FFT-OFDM、DCT-OFDM 和 DWT-OFDM 系统在不同加密算法下 PSNR 随 E_b/N_0 的变化。假设符号速率为 250,000 symbols per second，ε = 0.1，N = 128，且信道为 AWGN。该图显示，由于 CFO 的存在，所有系统在不同加密算法下的 PSNR 性能均下降，因为 CFO 破坏了子载波之间的正交性并产生载波间干扰 (ICI)，从而导致性能下降。该图还显示，CFO 补偿过程可以避免 CFO 的影响并产生高质量的解密图像。另一方面，在没有 CFO 补偿的情况下，CFO 明显会降低所有 OFDM 系统中 DES、AES 和 RC6 的 PSNR 性能。

![](img/47f81eeb5093bf67426e3b948e0d8952_187_0.png)

**图 9.56** 在衰落信道中采用 DCT-OFDM 的 DES 加密图像。

图 9.92 至 9.97 展示了在频率选择性信道中，FFT-OFDM、DCT-OFDM 和 DWT-OFDM 系统在不同加密算法下 PSNR 随 E_b/N_0 的变化。在没有 CFO 补偿的情况下，CFO 会破坏所有 OFDM 系统的 PSNR 性能，而与加密算法无关。然而，有 CFO 补偿时，所有系统的 PSNR 性能均优于无 CFO 补偿的情况。这些图还显示，与 DCT-OFDM 和 DWT-OFDM 系统相比，FFT-OFDM 系统下所有加密算法的 PSNR 性能最佳。

与混沌算法相比，DES、AES 和 RC6 在所有 OFDM 系统中提供了较低的 PSNR 性能，因为这些算法具有扩散机制，从而降低了抗噪性。另一方面，混沌算法对噪声更鲁棒。

## 9.3 增强算法的仿真实验

对 (FFT/DCT/DWT)-OFDM 系统中混沌算法及其模式 (ECB、CFB、CBC 和 OFB) 的性能进行了比较。在 AWGN 信道下，N = 128 且 G = 32 时，所有 OFDM 系统中混沌-ECB、混沌-CFB、混沌-CBC 和混沌-OFB 算法的 PSNR 性能在中等至高的 E_b/N_0 值时开始上升。在图 9.98 中，与 FFT-OFDM 下所有其他加密算法模式相比，混沌-ECB 算法的 PSNR 也是最佳的。从图 9.99 可知，与 DCT-OFDM 下所有其他加密算法模式相比，混沌-(OFB 和 ECB) 算法的 PSNR 也是最佳的。从图 9.100 可知，与 DWT-OFDM 下所有其他加密算法模式相比，混沌-OFB 算法的 PSNR 是最佳的。

![](img/47f81eeb5093bf67426e3b948e0d8952_189_0.png)

(a) E_b/N_0 = 0 dB
PSNR = 8.5829

![](img/47f81eeb5093bf67426e3b948e0d8952_189_1.png)

(b) E_b/N_0 = 5 dB
PSNR = 10.2435

![](img/47f81eeb5093bf67426e3b948e0d8952_189_2.png)

(c) E_b/N_0 = 10 dB
PSNR = 14.1012

![](img/47f81eeb5093bf67426e3b948e0d8952_189_3.png)

(d) E_b/N_0 = 15 dB
PSNR = 16.2472

图 9.58 在衰落信道中采用 DCT-OFDM 的 AES 加密图像。

对 (FFT/DCT/DWT)-OFDM 系统中混沌算法及其模式 (ECB、CFB、CBC 和 OFB) 的性能进行了比较。在衰落信道下，N = 128 且 G = 32 时，所有 OFDM 系统中混沌-ECB、混沌-CFB、混沌-CBC 和混沌-OFB 算法的 PSNR 性能在中等至高的 E_b/N_0 值时开始上升。在图 9.101 至 9.103 中，在无 CFO 的情况下，与 FFT/DCT/DWT-OFDM 下所有其他加密模式相比，混沌-CBC 算法的 PSNR 是最佳的。从图 9.104 至 9.106 可知，在存在 CFO 的 FFT-OFDM 系统中，与所有其他加密算法模式相比，混沌-CBC 算法的 PSNR 也是最佳的。

在无 PSE 的频率选择性信道中，CP-OFDM 系统与 ZP-OFDM 系统在不同混沌加密模式下的比较研究如图

![](img/47f81eeb5093bf67426e3b948e0d8952_190_0.png)

**图 9.59** 在 AWGN 信道中采用 DCT-OFDM 的 RC6 加密图像。

![](img/47f81eeb5093bf67426e3b948e0d8952_191_0.png)

(a) E_b/N_0 = 0 dB
PSNR = 8.5691

![](img/47f81eeb5093bf67426e3b948e0d8952_191_1.png)

(b) E_b/N_0 = 5 dB
PSNR = 10.2276

![](img/47f81eeb5093bf67426e3b948e0d8952_191_2.png)

(c) E_b/N_0 = 10 dB
PSNR = 14.1490

![](img/47f81eeb5093bf67426e3b948e0d8952_191_3.png)

(d) E_b/N_0 = 15 dB
PSNR = 16.1107

图 9.60 在衰落信道中采用 DCT-OFDM 的 RC6 加密图像。

![](img/47f81eeb5093bf67426e3b948e0d8952_191_4.png)

图 9.61 在 N = 64 的 AWGN 信道中，DWT-OFDM 系统的 PSNR 随 E_b/N_0 的变化。

![](img/47f81eeb5093bf67426e3b948e0d8952_192_0.png)

图 9.62 在 N = 512 的 AWGN 信道中，DWT-OFDM 系统的 PSNR 随 E_b/N_0 的变化。

![](img/47f81eeb5093bf67426e3b948e0d8952_192_1.png)

图 9.63 在 N = 1024 的 AWGN 信道中，DWT-OFDM 系统的 PSNR 随 E_b/N_0 的变化。

![](img/47f81eeb5093bf67426e3b948e0d8952_194_0.png)

图 9.66 在无 PSE 且无均衡的 N = 1024 瑞利信道中，DWT-OFDM 系统的 PSNR 随 E_b/N_0 的变化。

![](img/47f81eeb5093bf67426e3b948e0d8952_194_1.png)

图 9.67 在具有 PSE 和均衡的 N = 64 瑞利信道中，DWT-OFDM 系统的 PSNR 随 E_b/N_0 的变化。

![](img/47f81eeb5093bf67426e3b948e0d8952_195_0.png)

**图 9.68** 在具有 PSE 和均衡的 N = 512 瑞利信道中，DWT-OFDM 系统的 PSNR 随 E_b/N_0 的变化。

![](img/47f81eeb5093bf67426e3b948e0d8952_195_1.png)

**图 9.69** 在具有 PSE 和均衡的 N = 1024 瑞利信道中，DWT-OFDM 系统的 PSNR 随 E_b/N_0 的变化。
