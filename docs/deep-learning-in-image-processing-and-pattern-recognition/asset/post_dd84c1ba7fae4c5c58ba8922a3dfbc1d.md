
between the number of parameters, FLOPs, and performance of each model in Figure 8. We can see from the figure that our RNET achieves a good balance between computational complexity and performance.

## Table 2. The results of model efficiency and computational cost.

| Method | Parameters | Activations | FLOPs | Runtime | Memory |
|---|---|---|---|---|---|
| VDSR [3] | 86 K | 2.38 G | 612.6 G | 0.037 s | 340 MB |
| LapSRN [31] | 83 K | 0.58 G | 149.4 G | 0.020 s | 360 MB |
| DRRN [30] | 298 K | 24.89 G | 6796.9 G | 0.556 s | 827 MB |
| IMDN [22] | 715 K | 0.15 G | 40.9 G | 0.015 s | 228 MB |
| RLFN-5 [50] | 470 K | 0.12 G | 25.6 G | 0.018 s | 170 MB |
| RNET (Ours) | 401 K | 0.17 G | 20.4 G | 0.022 s | 230 MB |

![](img/e4200cc4308edaf8913e513b0f96dbb6_86_0.png)

## Figure 8. A comparison of performance and model complexity on Set5 dataset; the upscale factor is ×4.

### 4.2.5. Comparison with Other Transformer-Based Methods

Currently, there are two mainstream approaches to solve the problem of high computation brought by vision transformers: one is to use a sliding window, also known as a swin transformer, such as SwinIR [11]; the other approach is to improve the self-attention part—for example, ESRGAN [53] uses the splitting factor approach to reduce the computational burden brought by the self-attention. The RNET proposed in this paper uses cross-channel self-attention to achieve the same purpose. We provide a detailed comparison of these three approaches in Table 3. It can be seen that our RNET has better performance than ESRGAN on the Set5 dataset and achieves similar performance to SwinIR while having the least number of parameters and FLOPs.

## Table 3. Detailed comparison with other transformer-based methods.

| Method | Parameters | FLOPs | Set5 PSNR/SSIM | Set4 PSNR/SSIM |
|---|---|---|---|---|
| SwinIR [11] | 897 K | 49.6 G | 32.44/0.8976 | 28.77/0.7858 |
| ESRGAN [53] | 751 K | 67.7 G | 32.19/0.8947 | 28.69/0.7833 |
| RNET (Ours) | 401 K | 20.4 G | 32.39/0.8976 | 28.68/0.7837 |

## 4.3. Ablation Study

In this subsection, we design a series of ablation experiments to analyze the effectiveness of our proposed network. We first investigate the effects of different network depths and widths on the experimental results. Then, we demonstrate the effectiveness of the ET module and explore the placement of the module. We also compare different activation functions.

### 4.3.1. The Depth and Width of the Network

The experimental results are shown in Table 4, where depth indicates the number of HFEBs used and width indicates the number of feature channels. From the experimental results, it can be seen that increasing both depth and width can enhance the model ability. And experiments show that network width influences results more than depth. When d increased from 6 to 8, the indicator of Urban100 increased by 0.21 db, but when d increased from 8 to 10, the indicator only increased by 0.05 db, while at the same time, the parameters increased to 479 K. And when w increased from 32 to 48, the indicator on Urban100 increased by 0.43 db, but from 48 to 56, the indicator only showed a slight increase or even a decrease. But the parameters reach 513 K. From Table 4, when d = 10 and w = 56, the PSNR on all five benchmark test sets are improved, but the parameters of the network reach 638 K. In order to better balance the performance of the network with the parameters, we finally set the depth and width of the network to 8 and 48, respectively.

## Table 4. Ablation studies of different depths and widths of the network, where d indicates the number of HFEBs used, and w indicates the number of feature channels.

| Method | Parameters | Set5 PSNR/SSIM | Set14 PSNR/SSIM | BSD100 PSNR/SSIM | Urban100 PSNR/SSIM | Manga109 PSNR/SSIM |
|:---|:---|:---|:---|:---|:---|:---|
| d = 6 w = 32 | 139 K | 37.94 / 0.9607 | 33.44 / 0.9168 | 32.10 / 0.8994 | 31.72 / 0.9239 | 38.47 / 0.9767 |
| d = 6 w = 48 | 291 K | 38.04 / 0.9610 | 33.60 / 0.9184 | 32.18 / 0.9005 | 32.10 / 0.9270 | 38.78 / 0.9775 |
| d = 6 w = 56 | 387 K | 38.07 / 0.9611 | 33.63 / 0.9187 | 32.21 / 0.9008 | 32.20 / 0.9280 | 38.93 / 0.9777 |
| d = 8 w = 32 | 183 K | 37.92 / 0.9607 | 33.50 / 0.9172 | 32.13 / 0.8997 | 31.88 / 0.9251 | 38.65 / 0.9771 |
| d = 8 w = 48 | 385 K | 38.10 / 0.9612 | 33.69 / 0.9190 | 32.23 / 0.9009 | 32.31 / 0.9289 | 39.01 / 0.9778 |
| d = 8 w = 56 | 513 K | 38.11 / 0.9612 | 33.65 / 0.9187 | 32.23 / 0.9009 | 32.30 / 0.9293 | 38.99 / 0.9778 |
| d = 10 w = 32 | 228 K | 38.01 / 0.9609 | 33.51 / 0.9173 | 32.16 / 0.9001 | 32.03 / 0.9265 | 38.73 / 0.9773 |
| d = 10 w = 48 | 479 K | 38.10 / 0.9612 | 33.70 / 0.9188 | 32.24 / 0.9011 | 32.36 / 0.9295 | 39.00 / 0.9779 |
| d = 10 w = 56 | 638 K | 38.12 / 0.9613 | 33.74 / 0.9195 | 32.25 / 0.9014 | 32.47 / 0.9305 | 39.12 / 0.9779 |

### 4.3.2. Ablation Study of Efficient Transformer (ET) Block

We performed ablation experiments to separately verify the impact of different convolutions in our proposed ET module and the effectiveness of the ET module. Within the two key components of the ET module, MBTA and GBFN, we replaced BSCConv with traditional Depth-Wise Convolution (DWConv). The experimental results are shown in Table 5. Using BSCConv in the ET module introduces an insignificant increase in parameters, but it improves the model’s performance on all five benchmark test sets. Therefore, we employed BSCConv for channel feature extraction in the final ET module.

Subsequently, to verify the effectiveness of the ET module, we placed the ET module at Position 1 (P1 in Figure 9) or Position 2 (P2 in Figure 9) or removed the ET module altogether. The experimental results are shown in Table 5. After removing the ET module, the network’s performance significantly decreased on all five benchmark datasets. When the ET module was placed at Position 2, there was a slight decline in the results on these datasets. These results demonstrate that the ET module at Position 1 can effectively enhance the capacity of the HFEF model. Consequently, in the final model, we positioned the ET module at Position 1.

![](img/e4200cc4308edaf8913e513b0f96dbb6_87_0.png)

## Table 5. Quantitative comparison of the position of ET block and different convolutions used in ET.

| Ablation | Variant | Parameters | Set5 PSNR/SSIM | Set14 PSNR/SSIM | BSD100 PSNR/SSIM | Urban100 PSNR/SSIM | Manga109 PSNR/SSIM |
|---|---|---|---|---|---|---|---|
| HFEB | ET in P1 | 385 K | 38.10/0.9612 | 33.69/0.9190 | 32.23/0.9009 | 32.31/0.9289 | 39.01/0.9778 |
| HFEB | ET in P2 | 380 K | 38.06/0.9612 | 32.66/0.9187 | 32.22/0.9008 | 32.29/0.9289 | 38.96/0.9778 |
| HFEB | without ET | 135 K | 38.09/0.9612 | 33.20/0.9152 | 32.01/0.8983 | 31.39/0.9289 | 38.01/0.9756 |
| ET | BSCConv | 385 K | 38.10/0.9612 | 33.69/0.9190 | 32.23/0.9009 | 32.31/0.9289 | 39.01/0.9778 |
| ET | DWConv | 384 K | 38.06/0.9601 | 33.63/0.9189 | 32.22/0.9003 | 32.23/0.9273 | 38.86/0.9766 |

### 4.3.3. Different Activation Function in HFEB

We designed an ablation experiment to explore the effectiveness of the activation function in HFEB. The results in Table 6 show that different activation functions significantly affect the performance of the model. Among these activation functions, LeakyReLU obtains a significant performance gain, especially on the Urban100 and Manga109 datasets. Therefore, we chose LeakyReLU as the activation function in our model.

## Table 6. Ablation study using different activation functions in HFEB.

| Activation Function | Parameters | Set5 PSNR/SSIM | Set14 PSNR/SSIM | BSD100 PSNR/SSIM | Urban100 PSNR/SSIM | Manga109 PSNR/SSIM |
|---|---|---|---|---|---|---|
| GELU | 385 K | 38.08/0.9611 | 33.66/0.9184 | 32.21/0.9008 | 32.24/0.9287 | 38.94/0.9777 |
| ReLU | 385 K | 38.08/0.9612 | 33.69/0.9189 | 32.21/0.9008 | 32.23/0.9285 | 38.90/0.9777 |
| LeakyReLU | 385 K | 38.10/0.9612 | 33.69/0.9190 | 32.23/0.9009 | 32.31/0.9289 | 39.01/0.9778 |

### 4.3.4. Effectiveness of ESA and CCA Blocks

In order to verify the effectiveness of the ESA and CCA modules, we sequentially removed these two modules from the HFEB network proposed in this paper, re-trained the ×4 scale model, and tested the network on each of the five benchmark datasets. And the experimental results are shown in Table 7. The experiments show that after removing the two attention modules, the performance of our network on all the five benchmark datasets shows some degradation. At the same time, we find that both the ESA and CCA modules hardly increase the complexity of the whole model—only increasing the number of parameters by about 2%—and result in a PSNR gain of about 0.1 db on each dataset. Thus, the ESA with CCA module used in this paper is able to give the model a performance boost at a small cost.

## Table 7. Ablation studies of the effectiveness of ESA and CCA blocks, where √ indicates the block is used, and ✗ indicates the block is not used.

| ESA | CCA | Parameters | Set5 PSNR/SSIM | Set14 PSNR/SSIM | BSD100 PSNR/SSIM | Urban100 PSNR/SSIM | Manga109 PSNR/SSIM |
|---|---|---|---|---|---|---|---|
| ✗ | ✗ | 393 K | 32.29/0.8964 | 28.61/0.7823 | 27.59/0.7388 | 26.14/0.7863 | 30.47/0.9081 |
| ✗ | √ | 397 K | 32.31/0.8967 | 28.62/0.7823 | 27.60/0.7388 | 26.16/0.7863 | 30.58/0.9094 |
| √ | ✗ | 397 K | 32.32/0.8970 | 28.65/0.7829 | 27.61/0.7393 | 26.18/0.7873 | 30.64/0.9099 |
| √ | √ | 401 K | 32.39/0.8976 | 28.68/0.7837 | 27.65/0.7403 | 26.24/0.7894 | 30.67/0.9102 |

## 5. Conclusions

In this paper, we propose a novel Residual Network with Efficient Transformer (RNET) for lightweight single-image super-resolution. RNET achieves a good balance between performance and model parameters. Specifically, we adopt a local residual connection structure as the backbone network for deep feature extraction modules. Compared to the widely used knowledge distillation structure, this structure significantly enhances inference speed. Concurrently, we utilize BSCConv to replace traditional convolutional operations, which greatly reduces the number of required parameters. To fully exploit global information while avoiding excessive computational redundancy, we introduce an
