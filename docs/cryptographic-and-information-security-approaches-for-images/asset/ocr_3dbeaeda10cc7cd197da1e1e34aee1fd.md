# Table 8.5 Quality Measures Value for CS Based Encryption Process and Decryption Process for Landsat Satellite Images

| Secret Key k (M×N×C) | Using DCT Basis Matrix [8] [52] |  | Using DFT Basis Matrix |  | Using DWT Basis Matrix |  | Compression Ratio (CR) |
| | PSNR (dB) | SSIM | PSNR (dB) | SSIM | PSNR (dB) | SSIM | |
| 216000 (180×400×3) | 34.34 | 0.7007 | 38.48 | 0.8201 | 31.82 | 0.2990 | 2.22 |
| 288000 (240×400×3) | 34.62 | 0.7506 | 39.18 | 0.8776 | 32.24 | 0.3591 | 1.66 |
| 360000 (300×400×3) | 34.79 | 0.7729 | 39.81 | 0.9147 | 32.66 | 0.4477 | 1.33 |
| 432000 (360×400×3) | 34.90 | 0.7864 | 40.42 | 0.9399 | 33.24 | 0.5373 | 1.11 |

# 8.4.5 Discussion

The test database [63,64] which contains 15 standard color images and 35 Landsat satellite images are used for analysis of a proposed encryption approach. It is observed that the results of DCT and DWT based approaches for Landsat satellite images are not good. This happens since images are acquired remotely by moving sensors from very large distances and have low resolution. It is also observed that the same image transforms effectively work on standard images.

Some researchers [73–75] showed the application of CS theory on Landsat satellite images and color videos. The results obtained using these techniques are not good for data acquired by moving sensor or moving data acquired by steady sensor. The reason behind this situation is that these data are acquired in real time and have real as well as imaginary components. While CS theory using DCT and DWT works effectively on real data, it is observed that there is less effect on imaginary data. On the other hand, the CS theory using DFT effectively works on real as well as imaginary data and hence is good for Landsat satellite images.

# 8.4.6 Comparison of Presented Process

The presented process using DFT and DWT basis matrices is compared with the Nagesh [8] and Singh [52] processes by various features listed in Table 8.6. While the Nagesh [8] and Singh [52] process used DCT basis matrix, the presented process used DFT and DWT basis matrices. The maximum PSNR value in the Nagesh [8] and Singh [52] processes is 37.75 dB, and in the presented processes it is 40.42 dB.