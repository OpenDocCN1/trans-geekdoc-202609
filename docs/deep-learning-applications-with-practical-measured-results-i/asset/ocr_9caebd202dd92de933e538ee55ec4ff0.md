![](bbox=[0.12, 0.12, 0.85, 0.55])

Figure 5. Comparison diagram of the results of our algorithm, PatchMatch [25] algorithm and Yu J [14] algorithm.

# Table 1. The results of image inpainting using three methods.

| Method | PSNR | SSIM | L1 Loss (%) |
|---|---|---|---|
| PatchMatch [25] | 17.36 | 0.5908 | 8.78 |
| Yu J [14] | 19.14 | 0.7090 | 5.06 |
| Our method | 19.78 | 0.7205 | 5.52 |

Our full model is implemented on TensorFlow v1.3, CUDNN v7.0, CUDA v9.0 and run on hardware of CPU Intel(R) Xeon(R) gold 5117 (2.00 GHz) and GPU GTX 1080 Ti. We introduced 16 residuals into the texture detail repair network. However, in the training, these 16 residual blocks consume a lot of memory and slow down the training speed. After trying to lessen 16 residual blocks to 5 residual blocks, we found that our full model run 0.2 s per frame on the GPU, with significant improvement in speed and no significant change in performance.

In addition, the proposed inpainting framework can also be applied to conditional image generation, image editing, and computational photography tasks, including image-based rendering, image super-resolution, boot editing, and so on

# 4.2. Mask Experiment

We also evaluated our proposed mask dataset on two dataset including VOC2017 and COCO dataset. In the previous section, our model is trained to handle fixed holes to make it easy to compare.