# Super-Vertical-Resolution Reconstruction of Seismic Volume 199

# Fig. 9.7. Comparison of the models PSNR improvements.

![](bbox=[0.05, 0.22, 0.95, 0.55])

# Fig. 9.8. Comparison of the models' SSIM improvements.

![](bbox=[0.05, 0.68, 0.95, 0.92])

be high, the visual perception of the image can be different. That is why it is good practice to use multiple metrics to get a more comprehensive evaluation and to consider the specific application for which the image will be used. Hence, when there is the need to make an image resolution very high, the super-resolution model performs better, especially in the shallower part of the seismic volume. However, when the model is needed to enhance the seismic volume for interpretation, the mean resolution model is the better of the 2 due to the fact that more geological structures and features were preserved while exhibiting fewer falsely enhanced areas or less confident resolution in the deeper parts of the subsurface.

Figure 9.9 presents the spectral analysis results performed on the original, mean, and super-resolution volumes along inline 2000. Our findings indicate that the original volumes had an SNR of 70.9, which was significantly improved upon by the mean resolution volume achieving an SNR of 212.5. Interestingly, despite the improvement in spatial resolution, the