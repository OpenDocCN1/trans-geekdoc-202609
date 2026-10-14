![](bbox=[0.12, 0.1, 0.78, 0.35])

Figure 22.8 (a) selection the center of image, (b) selection pixels with 3 × 3 window (k = 3), (c) selection pixels with 5 × 5 window (k = 5). (From Raul, R.-C. et al., Electronics, Communications and Computers, CONIELECOMP '07, 17th International Conference on, 32–37, 2007.)

Statistical values such as mean, standard deviance, or variance can be used to select the pixels to embed message. For instance, the variance values of pixel are calculated in the block with k × k size of the pixels starting from the center of image, and then the possible pixels are determined according to a threshold value defined by user, as shown in Figure 22.8. The variance formula is given in Equation 22.8 [16].

σ² = 1/k² Σₓ₌₀ᵏ⁻¹ Σᵧ₌₀ᵏ⁻¹ (f(x,y) − μ)²
μ = 1/k² Σₓ₌₀ᵏ⁻¹ Σᵧ₌₀ᵏ⁻¹ f(x,y) (22.8)

In the second method, RGB (R: Red, G: Green, B: Blue) values of medical image can be converted into YCbCr (Y: Luminance, Cb: Chrominance Blue, Cr: Chrominance Red) color space with Equation 22.9. The bits of the message are replaced with the pixel LSBs of Cb and Cr components. After embedding the message, YCbCr color components of medical image are converted into RGB space to generate the stego-medical image. It secures the message against steg-attacks such as image compression, motion blur, erosion, multiplicative, averaged, dilated, salt and pepper noise, and Gaussian noise, as shown in Figure 22.9 [37].

[ Y ]   [ 0.299    0.587    0.114   ] [ R ]
[ Cb ] = [ -0.168636 0.232932 -0.064296 ] [ G ] (22.9)
[ Cr ]   [ 0.499813 -0.418531 -0.081282 ] [ B ]