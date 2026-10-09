where $L(x,y)$ is the luminance maximum for each pixel RGB channel, which is used to normalize the RGB colors. Then, calculate the color components for each channel, as shown in Equation (15).

$$r(x,y)=\frac{R(x,y)}{L(x,y)}, g(x,y)=\frac{G(x,y)}{L(x,y)}, b(x,y)=\frac{B(x,y)}{L(x,y)}$$
$\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad(15)$

Based on the estimation of illumination obtained above, the detail layer of the image is obtained, as shown in the following equation

$$L^{*}(x,y)=\log(L(x,y)-\log(L_{i}^{*}))$$
$\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad(16)$

where $L^{*}(x,y)$ is the image detail layer.

# 3.4.2. Image Fusion and Color Retention

The detail layer and the illumination layer after dynamic range compression are fused to obtain the result, as shown in the following equation:

$$L_{d}(x,y)=\beta L_{d}(x,y)+\gamma e^{L^{*}(x,y)}$$
$\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad(17)$

where $L_{d}(x,y)$ is the brightness value after fusion, $\beta$ and $\gamma$ are the reconstruction coefficients of the image fusion process, and the reconstruction coefficients take different values because the image illumination layer and the detail layer contain different information. The illumination layer contains the dynamic range of the image, which generally needs to be compressed, and the choice for $\beta$ is generally less than 1. However, if the value is too small, it will cause problems such as a low overall brightness value and low contrast, which will affect the image quality. The detail layer contains the image detail information, which generally needs to be enhanced, and the choice for $\gamma$ is generally greater than 1. However, it should not be set too large because it can cause excessive detail enhancement while creating problems such as halo artifacts and unnatural overall image effects. Based on that, we set $\beta$ and $\gamma$, respectively, to 0.8 and 1.2.

After the above processing, the color information needs to be recovered, as shown in the following equation.

$$\begin{array}{c} \{ R^{*}(x,y)=L_{d}(x,y) \times [r(x,y)]^{s} \\<br> G^{*}(x,y)=L_{d}(x,y) \times [g(x,y)]^{s} \\<br> B^{*}(x,y)=L_{d}(x,y) \times [b(x,y)]^{s} \end{array}$$
$\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad\quad(18)$

where $R^{*}(x,y), G^{*}(x,y), B^{*}(x,y)$ are the three-channel information after color recovery, and $s$ is the gamma correction factor that determines the color saturation of the recovered image. In most cases, we can achieve close-to-ideal colors mostly by using a monitor with a gamma value of 2.2. Most LCD monitors are designed based on a gamma value of 2.2. So, we set $s = 1/2.2$, i.e., $s = 0.45$, in our method.

# 4. Experimental Results and Analysis

An experimental platform with an Intel i5-6300HQ processor, 8 GB memory capacity, 64-bit Windows 10 operating system, and Matlab 2016b simulation software was used to verify the feasibility of the proposed method. The LDR images were displayed on a Samsung LCD monitor model S32AM700PC. HDR images from the TMQI database [14] were selected for experimental comparison and analysis, and all images in the TMQI database are shown in Figure 4. The dataset contains some high-dynamic range scenes from the world, such as landscape photos, architecture photos, etc. A total of 15 selected HDR images from the database were used to analyze and evaluate the LDR images tonemapped by TVI-TMO [3], the method of Li et al. [7], the method of Aziz et al. [1], the method of Gu et al. [15], the method of Shibata et al. [16], and the proposed method. Tone-mapped images were evaluated by subjective and objective assessment.