# TABLE 5.2 (Continued)
Performance Comparison of the Mean-Shift MULTI-SEGM Regarding Other
Studied Schemes Using the Berkley Dataset [60]

| | Metric | PSO [30] | CS [38] | SFS [37] | FCM [8] | MULTI-SEGM |
|---|---|---|---|---|---|---|
| $I_9$ | AD | 68.3427 | 40.4627 | 60.2085 | 89.2966 | 9.6449 |
| | FSIM | 0.4029 | 0.6488 | 0.2856 | 0.2517 | 0.9284 |
| | MD | 149.2432 | 94.8812 | 160.3654 | 249.4975 | 35.6534 |
| | MSE | 6098.1390 | 2528.9509 | 4949.8706 | 9348.8253 | 196.0710 |
| | NAE | 0.7205 | 0.4266 | 0.6347 | 0.9889 | 0.1016 |
| | NK | 0.3004 | 0.5990 | 0.3183 | 0.0094 | 0.9213 |
| | SC | 28.8975 | 54.1237 | 8.6147 | 9528.4186 | 1.1605 |
| | SSIM | 0.2647 | 0.5886 | 0.3723 | 0.0405 | 0.93211 |
| | PSNR | 10.5873 | 15.1627 | 60.2085 | 8.4232 | 25.2066 |
| | Time (s) | 7.0067 | 15.0412 | 17.1686 | 16.4132 | 10.8274 |
| $I_{10}$ | AD | 36.1076 | 26.4838 | 42.8133 | 55.7475 | 11.6531 |
| | FSIM | 0.6268 | 0.7557 | 0.7952 | 0.2464 | 0.9508 |
| | MD | 105.82 | 81.04 | 166.38 | 251.00 | 34 |
| | MSE | 2573.3881 | 1411.6807 | 4503.5444 | 6144.8574 | 210.6904 |
| | NAE | 0.6633 | 0.4865 | 0.7865 | 0.9823 | 0.2140 |
| | NK | 0.4615 | 0.6018 | 0.1123 | 0.0090 | 0.9033 |
| | SC | 5.6639 | 115.6884 | 22.8523 | 6257.5956 | 1.1846 |
| | SSIM | 0.4405 | 0.6285 | 0.4103 | 0.2443 | 0.8145 |
| | PSNR | 14.4542 | 17.2941 | 11.5977 | 10.2456 | 24.8943 |
| | Time (s) | 20.0068 | 40.0404 | 42.1896 | 50.4229 | 30.8358 |

According to both tables, although the PSO maintains a small computational overload, its performance in terms of AD, FSIM, MD, NK, MSE, NAE, SC, SSIM, and PSNR indexes is the worst. Under such conditions, it can be said that the MS method provides the best balance with regard to quality and velocity. Besides the quantitative evaluation, a qualitative analysis is an important part of producing consistent conclusions when evaluating the performance of segmentation schemes. The objective of the qualitative analysis is to evaluate the visual quality and the presence of annoying distortions or other artifacts in the results attributed to a deficient operation of the used algorithms. Analyzing Figure 5.8, in general, the MS scheme is able to efficiently segment the images even in case of noise or texturized objects.

The remarkable results of the MS method are attributed to three important elements. One of them is the use of a small data set for its operation instead of the complete dataset. This mechanism allows for reducing the segmentation process without decreasing its resultant quality. As a consequence, it is possible to obtain excellent segmentation quality by investing a small amount of time (which would be required to compute the complete dataset). The second factor is the use of the MS algorithm and the Epanechnikov kernel function. With these incorporations, it is possible to obtain consistent clustering