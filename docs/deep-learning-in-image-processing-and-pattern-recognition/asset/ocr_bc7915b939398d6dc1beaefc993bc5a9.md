and restores the shadow part well, but the overall image is not clear. CBDNet is better at processing low-noise images. While SRNN and WCNN performed well in terms of image sharpness and detail, there is still room for improvement. The algorithm proposed in this paper can recover image details more clearly and obtain a better visual effect. It still does not effectively remove all real noise, because the noise model does not perfectly represent real noise.

![](bbox=[0.14, 0.225, 0.87, 0.53])

**Figure 5.** Denoising results of the images on the Set12 dataset by different methods. (a) KPN [3]. (b) CDBNet [24]. (c) SRNet [14]. (d) WCNN [13]. (e) Ours.

Table 3 shows the average PSNR in Set12 data sets. Table 4 shows the average SSIM of different algorithms in Set12 data sets. The average PSNR of the algorithm in the paper is higher than the other algorithms. Except for low-noise images, the denoising effect of CBDNet is slightly better than that of the method in this paper. The performance of SRNet and WCNN is similar to that of the proposed algorithm. However, in terms of SSIM, our algorithm is superior to other algorithms. It shows that the proposed algorithm is superior to the previous algorithms in denoising performance. The average SSIM index of the restored image is close to that of the original image, indicating that the quality of the restored image is close to that of the original noiseless image.

**Table 3.** The average PSNR(DB) results of different methods on three datasets.

| Dataset   | Noise Level | KPN [3] | CBDNet [24] | SRNet [14] | WCNN [13] | Ours    |
|:----------|:------------|:--------|:------------|:-----------|:----------|:--------|
| McMaster  | σ1          | 32.69   | 34.34       | 33.76      | 33.65     | 34.31   |
|           | σ2          | 31.09   | 31.51       | 31.73      | 31.92     | 33.25   |
|           | σ3          | 29.76   | 29.84       | 30.42      | 30.78     | 31.03   |
| Set12     | σ1          | 30.96   | 33.53       | 33.11      | 32.91     | 33.50   |
|           | σ2          | 29.82   | 30.88       | 31.16      | 31.23     | 31.52   |
|           | σ3          | 28.59   | 28.79       | 29.28      | 29.57     | 29.95   |
| Kodak     | σ1          | 31.98   | 35.71       | 34.95      | 34.71     | 35.65   |
|           | σ2          | 30.57   | 31.86       | 32.44      | 32.93     | 33.63   |
|           | σ3          | 29.45   | 29.79       | 30.07      | 30.48     | 31.46   |