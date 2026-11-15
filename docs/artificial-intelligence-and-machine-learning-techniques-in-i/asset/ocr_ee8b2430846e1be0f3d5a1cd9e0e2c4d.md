deep CNN model. These training datasets include DIV2K,²³ ImageNet,²⁴ General 200, Yang91,²⁵ and Flickr²⁶ image datasets. For testing purposes, the research community of image SR evaluates the performance on Set5,²⁷ Set14,²⁸ BSDS100,²⁹ Urban100,³⁰ and Manga109³¹ test datasets.

![](bbox=[0.13, 0.245, 0.88, 0.455])

FIGURE 14.21 The basic architecture of CNF for CNN-based image superresolution.

# 14.3.1 EVALUATIONS QUALITY METRICS

The main benchmark quality metrics to evaluate the performance of image SR are the peak signal-to-noise ratio (PSNR) and the structural similarity index measures (SSIM).³² The PSNR results of state-of-the-art methods are presented in Tables 14.2–14.5 for 2x, 3x, 4x, and 8x enlargement factors, respectively. Furthermore, Tables 14.6–14.9 present the SSIM of all enlargement scale factors as 2x, 3x, 4x, and 8x. Finally, Table 14.10 presents information about the number, parameters, types of input and output, network depths, and types of loss function. All quantitative results used are from the latest research work in Refs. [33, 34].

# 14.4 CONCLUSIONS AND FUTURE WORK

Recently, deep convolutional neural network-based image SR solutions have achieved remarkable improvements over the previous methods. Furthermore, image SR plays a vital role in real-time applications such as medical images, security surveillance images, satellite images, and astronomical imaging. Earlier methods of image SR depended on