![](bbox=[0.2, 0.12, 0.32, 0.2])

![](bbox=[0.35, 0.12, 0.47, 0.2])

![](bbox=[0.51, 0.12, 0.63, 0.2])

![](bbox=[0.66, 0.12, 0.78, 0.2])

FIGURE 14.3 Color image denoising results of different methods on image "163085" from CBSD68 dataset with noise level 50. (a) Noisy (14.99 dB); (b) DnCNN (28.68 dB); (c) FFDNet (28.75 dB); (d) DRUNet (29.28 dB).

Such a discrepancy highlights the importance of reducing the image domain gap between training and testing for image denoising. The visual results of different methods on image "163085" from the CBSD68 dataset with noise level 50 are shown in Fig. 14.3, from which it can be seen that DRUNet can recover more fine details and textures than the competing methods.

TABLE 14.2 Average PSNR(dB) results of different methods for noise levels 15, 25 and 50 on CBSD68 (Martin et al., 2001; Roth and Black, 2009; Zhang et al., 2017a), Kodak24 and McMaster datasets. The best results are highlighted in bold.

| Datasets | Noise Level | CBM3D | DnCNN | IRCNN | FFDNet | DRUNet |
|---|---|---|---|---|---|---|
| CBSD68 | 15 | 33.52 | 33.90 | 33.86 | 33.87 | 34.30 |
|  | 25 | 30.71 | 31.24 | 31.16 | 31.21 | 31.69 |
|  | 50 | 27.38 | 27.95 | 27.86 | 27.96 | 28.51 |
| Kodak24 | 15 | 34.28 | 34.60 | 34.69 | 34.63 | 35.31 |
|  | 25 | 32.15 | 32.14 | 32.18 | 32.13 | 32.89 |
|  | 50 | 28.46 | 28.95 | 28.93 | 28.98 | 29.86 |
| McMaster | 15 | 34.06 | 33.45 | 34.58 | 34.66 | 35.40 |
|  | 25 | 31.66 | 31.52 | 32.18 | 32.35 | 33.14 |
|  | 50 | 28.51 | 28.62 | 28.91 | 29.18 | 30.08 |

# 14.3.4 HQS algorithm for plug-and-play IR

As mentioned previously, we adopt the HQS as the variable splitting algorithm for its simplicity and fast convergence. Meanwhile, there is no doubt that parameter setting is always a nontrivial issue (Romano et al., 2017). In other words, careful parameter setting is needed to obtain a good performance. To have a better understanding on the HQS-based plug-and-play IR, we will discuss the general methodology for parameter setting after providing a short review of the HQS algorithm. We then propose a periodical geometric self-ensemble strategy to potentially improve the performance.