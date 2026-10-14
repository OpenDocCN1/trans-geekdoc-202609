
universal image quality index (UIQI), structural similarity index metric (SSIM) are included in human visual system (HVS)-based measures. The pixel difference-based, correlation-based and human visual system-based measures are defined as follows [16]:

## 18.4.3.1 Mean Squared Error (MSE)

The mean squared error (MSE) is the simplest, and the most widely used, full-reference image quality measurement. Similarity is determined by computing the error between the stego image and the reference cover image.

MSE = 1/(M × N) Σ_{i=1}^{M} Σ_{j=1}^{N} (C(i,j) − S(i,j))²

where M × N is the size of the image. The parameters C(i,j) and S(i,j) refer to the pixels located at the ith row and the jth column of original image and stego image due to the embedding of the secret information [19].

## 18.4.3.2 Root Mean Squared Error (RMSE)

To evaluate the proposed stegosystem, this method is tested on the color Lena image of 256 × 256 pixels as shown in Figure 18.7a. The stego image result is shown in Figure 18.7c. To find the accuracy of the results and the robustness of the steganographic system, a root mean square of error is calculated. These criteria provide the error between the cover image and stego image. The rms value can be described by the following relation [16]:

RMSE = √[ 1/(M × N) Σ_{i=1}^{M} Σ_{j=1}^{N} (C(i,j) − S(i,j))² ]

where the C(i,j) is the pixel intensity of the cover image, S(i,j) is the pixel intensity of the stego image. The row and column numbers of these two images are defined by M × N.

## 18.4.3.3 Mean Absolute Error (MAE)

MAE is the average of absolute difference between the reference signal and test image. It is given by the equation

MAE = 1/(M × N) Σ_{i=1}^{M} Σ_{j=1}^{N} |C(i,j) − S(i,j)|.

## 18.4.3.4 Average Difference (AD)

AD is simply the average of difference between the reference signal and the test image and it is given by the equation

$$AD = \frac{1}{M \times N} \sum_{i=1}^{M} \sum_{j=1}^{N} (C(i,j) - S(i,j)).$$

## 18.4.3.5 Maximum Difference (MD)

MD is the maximum of the error signal (difference between the stego and cover image)

$$MD = Max\ |C(i,j) - S(i,j)|.$$

## 18.4.3.6 Peak Signal to Noise Ratio (PSNR)

The PSNR is evaluated in decibels and is inversely proportional the Mean Squared Error. It is given by the equation

$$PSNR = 10\log_{10} \frac{255^2}{MSE}.$$

## 18.4.3.7 Enhancement Error (EME)

A number of blind-reference metrics have been proposed during the last decade. EME (enhancement error) has been developed by Agaian et al. [17,18] give an absolute score to each image on the basis of image contrast processed with Fechner’s Law relating contrast to perceived brightness or the well-known entropy concept. The following equation gives us the EME formula

$$EME = \frac{1}{M \times N} \sum_{i=1}^{M} \sum_{j=1}^{N} 20\log_{2} \frac{\max(I(i,j))}{\min(I(i,j))}$$

where the image is divided into $M \times N$ blocks, max$(I(i,j)$, min$(I(i,j)$ are the maximum and minimum values of the pixels in each block of the enhanced image.

## 18.4.3.8 Structure Content (SC)

It is one of the correlation based measures. It means the closeness between two digital images which can be quantified in terms of correlation function. This metrics measures the similarity between two images. The structural content metric is based on the following equation:

SC = sum_{i=1}^{M} sum_{j=1}^{N} (C(i, j))^2 / sum_{i=1}^{M} sum_{j=1}^{N} (S(i, j))^2 ,

where C(i, j) is the (i, j)th pixel value of cover image, S(i, j) is the pixel value of stego image.

## 18.4.3.9 Normalized Cross Correlation (NCC)

The Normalized Cross Correlation (NCC) metric is used to show the amount of deflection in the stego image with respect to the cover image after insertion of the message. NCC is applied to evaluate the performance of various existing methods which is given by the following equation

NCC = sum_{i=1}^{M} sum_{j=1}^{N} C(i, j) × S(i, j) / sum_{i=1}^{M} sum_{j=1}^{N} (C(i, j))^2 .

This measure measures the similarity between two images, hence in this sense it’s complementary to the difference-based measures.

## 18.4.3.10 Human Visual System (HVS) Based Measures

A noteworthy accentuation in late research has been given to a more profound investigation of the Human Visual System (HVS) highlights. Specialists expect that fusing information of the HVS and human recognition into target quality appraisal algorithms could expand their precision. This HVS-based FR worldview has been the prevailing worldview throughout the previous three decades. The fundamental idea is that humans don’t see pictures as signs in a high-dimensional space, yet are occupied with different properties of those pictures, for example, brightness, contrast, shape and texture of objects, orientations, smoothness, etc. Since the affectability of the HVS is distinctive for various parts of pictures, it bodes well to represent these sensitivities while influencing an examination between the test and the reference to flag.

There are a great deal of HVS attributes that may impact the human visual recognition on picture quality. In spite of the fact that HVS is excessively mind boggling, making it impossible to completely comprehend with show psychophysiology implies, the joining of even an improved model into target measures purportedly prompts a superior relationship with the reaction of the human spectators. Human Visual System (HVS) has been broadly presented to the common visual condition, and an assortment of confirmation has demonstrated that the HVS is exceptionally adjusted to extricate helpful data from normal scenes. Two HVS based picture quality measures are given beneath [19]:

## Universal Image Quality Index (UIQI)

Let x = {x_i, i = 1,2,........,N} and y = {y_i, i = 1,2,.........,N} be the cover and stego images. The proposed quality index is defined as:

Q = 4σ_xy x̄ ȳ / ((σ_x² + σ_y²)(x̄² + ȳ²))

where
x̄ = 1/N Σ_{i=1}^{N} x_i, ȳ = 1/N Σ_{i=1}^{N} y_i, σ_x² = 1/(N-1) Σ_{i=1}^{N} (x_i - x̄)², σ_y² = 1/(N-1) Σ_{i=1}^{N} (y_i - ȳ)²,
σ_xy = 1/(N-1) Σ_{i=1}^{N} (x_i - x̄)(y_i - ȳ).

The dynamic range of Q is [0,1]. The best value Q = 1, is achieved when x_i = y_i, i = 1,2,...,n. The UIQI can also be defined as the product of three components:

Q = Q1 × Q2 × Q3

where
Q1 = σ_xy / (σ_x σ_y)
Q2 = 2 x̄ ȳ / (x̄² + ȳ²)
Q3 = 2 σ_x σ_y / (σ_x² + σ_y²)

where first term defines the degree of correlation between x and y with dynamic range between [−1,1], second term measures how close the luminance is between x and y range is [0,1] and third term measures how similar the contrasts of the image x and y are.

## 18.4.3.11 Structural Similarity Index Metric (SSIM)

The structural similarity index metric (SSIM) is a technique for measuring the similarity between two pictures. The SSIM index is a full reference metric; as such, the measuring of picture quality focused around an introductory uncompressed or without distortion picture as reference. The SSIM metric is figured on different windows of a picture. The measure between original and marked images of size is given below [19]:

$$SSIM(X,Y)=\frac{(2\mu_x\mu_y + c_1)(\sigma_{xy} + c_2)}{(\mu_x^2 + \mu_y^2 + c_1)(\sigma_x^2 + \sigma_y^2 + c_2)}.$$

The error comparison between a cover image and stego image are shown in the Tables 18.13 through 18.15. These results indicate the presence of secret information in the stego image. These tables additionally concludes that the stego image is of better quality if MAE, MSE, RMSE, AD, NAE and EME values are less while the high value of PSNR means that the stego image is most similar to the original image. It is hard

## Table 18.13 Simple Statistics Errors for Cover and Stego Images for Steganographic System-I

|  | Red | Green | Blue |
|---|---|---|---|
| MSE | 14.6721 | 13.0356 | 13.6659 |
| RMSE | 3.83042 | 3.61049 | 3.69674 |
| PSNR | 36.4659 | 36.9795 | 36.7744 |
| MAE | 3.00061 | 2.84267 | 2.87642 |
| AD | 0.554657 | 0.561356 | 0.409073 |
| MD | 19 | 15 | 20 |
| NAE | 0.0166466 | 0.028655 | 0.0272485 |
| EME (Cover image) | 7.87436 | 19.4497 | 11.7173 |
| EME (Stego image) | 8.34606 | 20.9805 | 12.7009 |
