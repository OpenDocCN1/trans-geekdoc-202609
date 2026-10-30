![](bbox=[0.13, 0.14, 0.42, 0.31])

EW1-Extracted Watermark 1
(Cameraman)

![](bbox=[0.5, 0.14, 0.82, 0.3])

EW2-Extracted Watermark 2 (Details of patient)

Figure 5.9 Extracted watermark images.

# Table 5.1 Values of performance parameters (No attack)

| Input Images | PSNR (dB) | MSE | SSIM | NCC1 | NCC2 | KL distance | JS distance |
|---|---|---|---|---|---|---|---|
| P1 | 49.7073 | 1.2259e-05 | 0.9951 | 1.0000 | 0.9998 | 0.8639 | 0.2071 |
| P2 | 49.8335 | 1.2259e-05 | 0.9958 | 0.9999 | 0.9998 | 0.8389 | 0.1952 |
| P3 | 49.9574 | 1.2259e-05 | 0.9945 | 1.0000 | 0.9998 | 0.8346 | 0.1977 |

is 0.9999, and NCC2 values are 0.9998 in all cases. KL and JS distances are used to test imperceptibility. Lesser values of both distances imply that the imperceptibility is high. The best value for KL distance is for P3 and JS distance is for P2.

Table 5.2 shows the values of PSNR, NCC1, and NCC2 for P1 under various attacks. The value of PSNR is highest for JPEG 2000, i.e., 48.6785 (P1). The values of NCC1 and NCC2 are highest for JPEG 2000 (10), i.e., 0.9998 (P1) and 0.9995 (P1), respectively. The least value for PSNR is for histogram equalization (9.2285-P2). The lowest value of NCC1 and NCC2 is for Gaussian noise (0.1), i.e., 0.9738 (P1) and 0.9871 (P1), respectively. In almost all the cases, the NCC value is greater than 0.9. Table 5.3 and Table 5.4 show the values of performance parameters for P2 and P3, respectively. Figure 5.10 shows the embedding procedure, and Figure 5.11 shows the extraction and authentication process. Figure 5.12 shows the comparison of PSNR (dB), NCC, and KL and JS distances.

In Table 5.5, the timing analysis is mentioned for different input images. The embedding, extraction, and total time elapsed is shown separately in which embedding time is less for input image P2 and extraction time is less for P1. The total time elapsed is less for input image P2.