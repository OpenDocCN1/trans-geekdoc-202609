
SNR to get a complete evaluation of image quality, such as the SSIM and PSNR, which are more robust and take into account both luminance and structural information. The formula for SNR is:

$$SNR = 10 \times \log_{10}\left(\frac{\text{Peak signal power}}{\text{Mean square error}}\right)$$  (9.4)

- 2. **PSNR** measures the quality of a reconstructed image compared to a reference image. It is defined as the ratio of the peak signal power to the power of the noise in the reconstructed image. This metric is mathematically expressed as:

$$PSNR = 10 \times \log_{10}\left(\frac{MAX^2}{MSE}\right)$$  (9.5)

where MAX is the maximum possible pixel value of the image, and MSE is the mean squared error between the conditioned and original volume.

- 3. **SSIM** is a measure of the similarity between two images. It considers the luminance, contrast, structure, mean, standard deviation and cross-covariance of the image pixels and gives an understanding of the structural similarity between two images. SSIM is mathematically written as:

$$SSIM(x,y) = \frac{(2 \times \mu_x \times \mu_y + C1) \times (2 \times \Sigma_{xy} + C2)}{(\mu_x^2 \times \mu_y^2 + C1) \times (\Sigma_x^2 + \Sigma_y^2 + C2)}$$  (9.6)

where μₓ and μᵧ are the pixel values’ means of images x and y, respectively, and Σₓ and Σᵧ are the pixel values’ standard deviations of images x and y, respectively, Σₓᵧ is the pixel values’ covariance of images x and y and C₁ and C₂ are constants.

## 4. Results and Discussion

### 4.1 Conditioned Seismic Volume

In Figs. 9.4, 9.5, and 9.6, you will note the high level of improvement in the conditioned image resolution volumes for inlines, crosslines, and depth, respectively. In this study, we employed two CNN models, named the mean resolution volume and super-resolution volume based on their performance, to increase the quality of seismic images. The results showed massive improvements visually, especially in the deeper parts with low quality. Specifically, the super-resolution volume model achieved visually better results. While the use of deep learning in seismic image processing has demonstrated significant improvements in image quality, it is important to note that the models are not without limitations. One of the key limitations is the presence of false geological structures, which can be introduced during the

![](img/80b94770dd572ad559c67fa9921bb887_211_0.png)

![](img/80b94770dd572ad559c67fa9921bb887_211_1.png)

![](img/80b94770dd572ad559c67fa9921bb887_211_2.png)

Fig. 9.4. Inline 2000 comparison of (a) original, (b) mean resolution conditioned, and (c) super-resolution conditioned volumes.

![](img/80b94770dd572ad559c67fa9921bb887_212_0.png)

![](img/80b94770dd572ad559c67fa9921bb887_212_1.png)

![](img/80b94770dd572ad559c67fa9921bb887_212_2.png)

Fig. 9.5. Xline 3000 comparison of (a) original, (b) mean resolution conditioned, and (c) super-resolution conditioned volumes.

important to understand that these metrics each provide a different perspective on the quality of the enhanced or denoised image.

PSNR is a simple metric that measures the ratio of the maximum possible power of a signal to the power of the noise that corrupts the signal. It is generally used to compare the original image to the processed image in order to assess the quality of image enhancement and denoising methods. A higher PSNR value indicates a higher quality image with less noise. From the results in Fig. 9.7, the mean resolution model achieved the highest PSNR compared to the super-resolution model. This metric is easy to understand and compute. However, it cannot give a comprehensive evaluation of an image’s quality as it only considers the values and does not take into account the visual perception.

SSIM takes into account the mean, standard deviation, and cross-covariance of the image pixels and gives an understanding of the structural similarity between two images. Based on the data it takes into account when computing, SSIM is a more reliable metric for evaluating image quality than PSNR, but it requires more computation than PSNR. This metric is based on the idea that the human visual system is highly adapted to recognise small changes in structural information, such as edges and textures, rather than small changes in pixel intensities. It is typically used as a measure of image quality in signal processing applications. However, it cannot give a comprehensive evaluation of an image’s quality as it only considers the values and does not take into account the visual perception. As such, it is imperative to combine it with other metrics like the PSNR. A higher SSIM value indicates a higher quality image with less noise. As such, the mean resolution model achieved the highest SSIM compared to the super-resolution model, which is shown in Fig. 9.8. The SSIM is usually measured between 0 and 1. However, for this study, the original seismic volume was used as a standard for comparison. As such, the initial SSIM was 1, while the improvements gained by the models were estimated between 0 and 1 to capture the increased SSIM. The mean resolution model achieved an improved SSIM of 0.4, while the super-resolution resulted in an SSIM of 0.31. This result shows that not all high resolution images should be classified as the best model. Some enhancements may result in the loss of important geological structures through false improvements, as typified by the SSIM results.

When evaluating image enhancement or denoising methods, PSNR, SSIM, and SNR can be used together to provide a more comprehensive image quality evaluation. For example, a method that provides a high PSNR value and a high SSIM value is likely to produce an image that is both visually vivid and accurate in terms of preserving the original information. Additionally, a high SNR value means that the signal is stronger than the noise, and it indicates that the denoising method performed well in removing the noise. It is also important to note that even though the PSNR and SSIM values may

Super-Vertical-Resolution Reconstruction of Seismic Volume 199

Fig. 9.7. Comparison of the models PSNR improvements.

![](img/80b94770dd572ad559c67fa9921bb887_215_0.png)

Fig. 9.8. Comparison of the models' SSIM improvements.

![](img/80b94770dd572ad559c67fa9921bb887_215_1.png)

be high, the visual perception of the image can be different. That is why it is good practice to use multiple metrics to get a more comprehensive evaluation and to consider the specific application for which the image will be used. Hence, when there is the need to make an image resolution very high, the super-resolution model performs better, especially in the shallower part of the seismic volume. However, when the model is needed to enhance the seismic volume for interpretation, the mean resolution model is the better of the 2 due to the fact that more geological structures and features were preserved while exhibiting fewer falsely enhanced areas or less confident resolution in the deeper parts of the subsurface.

Figure 9.9 presents the spectral analysis results performed on the original, mean, and super-resolution volumes along inline 2000. Our findings indicate that the original volumes had an SNR of 70.9, which was significantly improved upon by the mean resolution volume achieving an SNR of 212.5. Interestingly, despite the improvement in spatial resolution, the

![](img/80b94770dd572ad559c67fa9921bb887_216_0.png)

**Fig. 9.9.** Comparison of spectral analysis for (a) original seismic, (b) super-resolution volume, and (c) mean resolution volume.

Inline - 2700

![](img/80b94770dd572ad559c67fa9921bb887_217_0.png)

Depth - 2040

![](img/80b94770dd572ad559c67fa9921bb887_217_1.png)

Xline - 5500

![](img/80b94770dd572ad559c67fa9921bb887_217_2.png)

Fig. 9.10. Super-resolution conditioned volume showing Inline 2700, crossline 5500, and depth 2040.

super-resolution volume only recorded an SNR of 83.6, suggesting that while super-resolution techniques can improve the resolution of seismic data, they may not always result in better SNR. Based on the spectral analysis results, the mean volume outperformed the super-resolution volume due to its ability to preserve low-frequency information, leading to a better SNR. Additionally, the super-resolution volume amplifies the noise in the data, resulting in a lower SNR. This is shown in Figs. 9.10 and 9.11 representing the pictorial depiction of the Super-resolution conditioned volume and the Mean resolution conditioned volume respectively.

Our study highlights the potential of using the mean resolution (GAN) techniques to enhance the seismic data quality and emphasises the importance of evaluating the effectiveness of super-resolution (CNN) techniques on a case-by-case basis. Overall, our findings provide valuable insights for the seismic imaging community in their efforts to enhance the quality of subsurface images for accurate interpretation and analysis.
