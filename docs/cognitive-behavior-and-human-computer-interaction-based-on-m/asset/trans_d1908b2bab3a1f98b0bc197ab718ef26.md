

该估计器需要事先了解噪声方差 ![img](images/img005.jpg)和每个系数的边缘方差（`σ*²*`）`σ²`。可以使用区域 `N(k)` 中的邻近系数进行估计。它是所有位于 `k^(th)` 系数中心的正方形窗口内的系数 ![img](images/img006.jpg)它可以使用稳健中位数估计器从噪声系数中估计。

(4.28)![img](images/eq4_28.jpg)

### 4.3.3 性能评估参数

了解任何方法的效率是可取的。为此，需要计算 PSNR、MSE 和 SSIM 等各种参数。PSNR 表示定量性能，而 SSIM 表示定性性能。下面是每个参数的解释。

#### 4.3.3.1 均方误差

设两个不同的灰度图像为 `I[1](i, j)` 和 `I[2](i, j)`，大小均为 `M × N`，则两幅图像之间的 MSE 如下所示：

(4.29)![img](images/eq4_29.jpg)

#### 4.3.3.2 峰值信噪比

数学上，它如下所示：

(4.30)![img](images/eq4_30.jpg)

如果两幅图像相同，则 MSE 为零，PSNR 为无穷大 \[2\]。

#### 4.3.3.3 结构相似性指数矩阵

它测量任何技术获得的图像质量，并测量两幅图像之间的相似性。其值范围从 0 到 1。如果为 1，则两幅图像在各方面都相同。它是在两个具有标准尺寸的图像之间计算的。数学上，它如下所示：

(4.31)![img](images/eq4_31.jpg)

![images](images/inline03.jpg)图像一和图像的均值。

![images](images/inline04.jpg)图像一和图像二的方差，分别为。

![eq](images/inf001.jpg)

![images](images/inline05.jpg)用于稳定弱分母 `L` 除法的两个变量是两幅图像的协方差和像素值的动态范围。值 `K[1] K[2]` 分别为 0.01 和 0.03。

## 4.4 方法论

本部分涉及应用于去噪受 AWGN 影响的数字灰度图像的方法论。去噪是在小波域中进行的。我们可以使用常规 `DWT` 进行分解，使用 `IDWT` 重建图像，但由于常规 `DWT` 存在上述问题，因此使用了 `DTCWT` 以获得更好的结果。由于它需要的时间较少，因此冗余度较低。与 `UDWT` 相比，其计算成本较低 \[28\]。[Figure 4.11](#c04.xhtml#fig4-11) 显示了基于 `DTCWT` 的图像去噪技术的框图表示。它只需要三个简单的步骤：

![Figure 4.11 Image denoising using DTCWT-based thresholding technique.](images/fig4_11.jpg)

**[Figure 4.11](#c04.xhtml#fig4-11)** 基于 DTCWT 的阈值技术图像去噪。

![Figure 4.12 Flow chart for the wavelet-based thresholding technique.](images/fig4_12.jpg)

**[Figure 4.12](#c04.xhtml#fig4-12)** 基于小波的阈值技术流程图。

1. (i) 计算 `DTCWT` 以分解噪声图像。

2. (ii) 使用任何阈值规则修改噪声小波系数。

3. (iii) 计算 `IDTCWT` 以重建去噪图像。

在第一步中，对噪声图像进行小波变换并获得小波系数。其中一些系数是噪声系数，因此需要被删除或替换。

为此，使用阈值技术，它可以删除或抑制这些噪声系数。需要重建，这是通过逆小波变换 \[45–47\] 完成的，以获得去噪图像。

希望计算一些性能评估参数，*即*，PSNR、MSE 和 SSIM。[Figure 4.12](#c04.xhtml#fig4-12) 显示了流程图，它指示了解应用的阈值方法的逐步过程。

## 4.5 结果与讨论

在本部分中，使用上述技术的去噪结果已在去噪图像和从不同阈值技术获得的性能评估参数中显示。这些技术已应用于大小为 512 × 512 的标准灰度图像。这些标准图像是 Lena、barbara、cameraman 和 pepper，并在 [Figure 4.13](#c04.xhtml#fig4-13) 中显示。

从数据库中获取一张标准图像。现在，使用 MATLAB 编程将该图像损坏为 AWGN。结果，得到一张噪声图像。现在，需要对这张噪声图像应用各种阈值技术，如 [Section 4.4](#c04.xhtml#sec4-4) 中讨论的那样。现在，需要增加噪声量并重复该过程。同样，同样的过程也应用于其他图像。通过应用阈值技术，得到了不同的去噪图像，[Figure 4.14](#c04.xhtml#fig4-14) 显示了噪声图像。从上述图像可以得出结论，基于小波的阈值技术提供了良好的结果。然而，通过计算性能评估参数，其去噪能力可能更加精确。为了验证各种技术的性能，已针对不同噪声水平计算了 PSNR 和 SSIM。

[Table 4.1](#c04.xhtml#tab4-1) 显示 PSNR（以 dB 为单位），[Table 4.2](#c04.xhtml#tab4-2) 显示不同图像在各种噪声条件下以及从各种阈值技术获得的去噪图像的 SSIM 值。从表格的观察可以清楚地看出，SURE shrink 优于 Neigh shrink 和 Bayes shrink 这两种方法。然而，其性能并不优于 block k shrink 和双变量阈值技术。双变量阈值技术对包含较少噪声的图像给出了更好的响应，但如果图像中存在的噪声增加，那么大多数情况下块阈值技术优于双变量阈值技术。[Figures 4.15](#c04.xhtml#fig4-15) 和 [4.16](#c04.xhtml#fig4-16) 是针对 Lena 图像中存在的不同噪声值绘制的噪声和去噪 PSNR 及 SSIM 值的柱状图。

![Figure 4.13 Standard gray images (512 × 512): (a) lena image; (b) barbara image; (c) cameraman image; (d) pepper image.](images/fig4_13.jpg)

**[Figure 4.13](#c04.xhtml#fig4-13)** 标准灰度图像 (512 × 512)：(a) lena 图像；(b) barbara 图像；(c) cameraman 图像；(d) pepper 图像。

![Figure 4.14 (a) Noisy image (noise level = 10); (b) Denoise image (SURE shrink); (c) Denoise image (Neigh shrink); (d) Denoise image (Bayes Shrink); (e) Denoise image (Block shrink); (f) Denoise image (Bivariate shrink).](images/fig4_14.jpg)

**[Figure 4.14](#c04.xhtml#fig4-14)** (a) 噪声图像（噪声级别 = 10）；(b) 去噪图像（SURE shrink）；(c) 去噪图像（Neigh shrink）；(d) 去噪图像（Bayes Shrink）；(e) 去噪图像（Block shrink）；(f) 去噪图像（Bivariate shrink）。

**[Table 4.1](#c04.xhtml#tab4_1)** 不同 AWGN 值的灰度图像 (512×512) 的 PSNR 值。

| **测试图像**  || **噪声级别--->** || **5** || **10** || **15** || **20** || **25** || **30** |

| --- | --- | --- | --- | --- | --- | --- | --- |

| Lena || 噪声 || 36.323 || 34.321 || 28.375 || 24.389 || 18.662 || 14.332 |

| --- | --- | --- | --- | --- | --- | --- | --- |

| 去噪 (SURE shrink) || 38.463 || 36.883 || 32.743 || 27.757 || 24.854 || 20.021 |

| 去噪 (Neigh shrink) || 38.123 || 36.385 || 32.376 || 28.324 || 24.334 || 19.732 |

| 去噪 (Bayes shrink) || 38.276 || 36.455 || 32.443 || 27.545 || 24.002 || 19.438 |

| 去噪 (Block shrink) || 39.456 || 38.481 || 35.787 || 32.764 || 26.654 || 24.761 |

| 去噪 (Bivariate shrink) || 40.543 || 39.667 || 37.721 || 32.435 || 26.098 || 24.405 |

| Barbara || 噪声 || 35.984 || 34.562 || 29.122 || 24.427 || 18.549 || 15.022 |

| 去噪 (SURE shrink) || 37.492 || 36.587 || 32.142 || 27.259 || 24.455 || 19.023 |

| 去噪 (Neigh shrink) || 38.326 || 36.405 || 32.381 || 28.305 || 24.327 || 19.722 |

| 去噪 (Bayes shrink) || 38.255 || 36.432 || 32.419 || 27.537 || 23.082 || 19.419 |

