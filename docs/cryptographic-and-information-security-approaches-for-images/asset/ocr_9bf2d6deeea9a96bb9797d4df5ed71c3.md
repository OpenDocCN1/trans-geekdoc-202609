# 18.4.3.4 Average Difference (AD)

AD is simply the average of difference between the reference signal and the test image and it is given by the equation

$$AD = \frac{1}{M \times N} \sum_{i=1}^{M} \sum_{j=1}^{N} (C(i,j) - S(i,j)).$$

# 18.4.3.5 Maximum Difference (MD)

MD is the maximum of the error signal (difference between the stego and cover image)

$$MD = Max\ |C(i,j) - S(i,j)|.$$

# 18.4.3.6 Peak Signal to Noise Ratio (PSNR)

The PSNR is evaluated in decibels and is inversely proportional the Mean Squared Error. It is given by the equation

$$MSE = 10\log_{10} \frac{255^2}{\sqrt{255}}.$$

# 18.4.3.7 Enhancement Error (EME)

A number of blind-reference metrics have been proposed during the last decade. EME (enhancement error) has been developed by Agaian et al. [17,18] give an absolute score to each image on the basis of image contrast processed with Fechner’s Law relating contrast to perceived brightness or the well-known entropy concept. The following equation gives us the EME formula

$$EME = \frac{1}{M \times N} \sum_{i=1}^{M} \sum_{j=1}^{N} 20\log_{2} \frac{\max(I(i,j)}{\min(I(i,j)}$$

where the image is divided into $M \times N$ blocks, max$(I(i,j)$, min$(I(i,j)$ are the maximum and minimum values of the pixels in each block of the enhanced image.