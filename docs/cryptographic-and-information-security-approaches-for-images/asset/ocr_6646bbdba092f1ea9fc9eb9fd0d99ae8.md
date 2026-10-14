it should be less. For this reason, C should be considered the largest value of the image [12].

MSE and PSNR are inconvenient to express Human Visual System (HVS). In literature, UQI, and SSIM are proposed to measure the quality of stegano graphy process according to HVS [57–58]. SSIM is a perceptual metric using image quality degradation as perceived in structural information. In SSIM, structural information which indicates the structure of patterns in the scene of image, is not related to the average luminance and contrast that can be vary across in scene. The similarity between two image signals can be measured by the comparisons of luminance (l(x,y)), contrast (c(x,y)), and structure (s(x,y)). First, the luminance and contrast measurements of each signals are calculated by using the mean intensity (μx, μy) and the standard deviation (σx, σy). Second, the comparisons of the luminance, contrast and structure are obtained by these measurements values. Luminance comparison is given in Equation 22.27 [58].

$I(x,y)=\frac{(2\mu_x\mu_y + c_1)}{\mu_x^2\mu_y^2 + c_1}$ (22.27)

Where $c_1=(k_1 L)^2$ is the constant to ensure stability when $\mu_x^2 + \mu_y^2$ is very close to zero. L is dynamic range of pixel values that is 255 for 8-bit gray scale images and $k_1 \ll 1$ is a small constant [58].

The contrast comparison is shown in Equation 22.28.

$c(x,y)=\frac{(2\alpha_{xy}+c_2)}{\alpha_x^2+\alpha_y^2+c_2}$ (22.28)

Where $c_2=(k_2 L)^2$ and $k_2 \ll 1$ are constant [58].

The structure comparison that is correlated with luminance subtraction and variance normalization, is given in Equation 22.29.

$s(x,y)=\frac{(\alpha_{xy}+c_3)}{(\alpha_x\alpha_y + c_3)}$ (22.29)

SSIM combines the luminance, contrast, and structure comparisons with respect to Equation 22.30.

$SSIM(x,y)=[I(x,y)c(x,y)s(x,y)]=\frac{(2\mu_x\mu_y + c_1)(2\alpha_{xy}+c_2)}{(\mu_x^2+\mu_y^2 + c_1)(\alpha_x^2+\alpha_y^2 + c_2)}$ (22.30)

UQI index is derived from the equation of SSIM where assume as $c_1 = c_2 = 0$. UQI evaluates the luminance and contrast degradation in the image scenes [57–58]. The formulation of UQI index is shown in Equation 22.31.