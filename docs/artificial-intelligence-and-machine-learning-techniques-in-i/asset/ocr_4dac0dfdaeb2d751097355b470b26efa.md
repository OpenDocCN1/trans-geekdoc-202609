+   • Finally, we discuss some quantitative results in terms of several peak signal-to-noise ratios (PSNR) and SSIM.

The remaining part of the chapter is organized as follows: Section 14.2 discusses some conventional and deep learning-based image SR methods. Sections 14.3 and 14.4 explain the different training and testing datasets involved in the deep CNN-based image SR and their quality matrix. In Section 14.5, we discuss some quantitative results in terms of PSNR, SSIM, and number k parameters. Finally, we present the conclusion with future suggestions.

# 14.2 CONVENTIONAL AND DEEP LEARNING-BASED IMAGE SUPERRESOLUTION METHODS

Single image SR has been reviewed by many studies, including conventional as well as deep learning-based approaches. Here initially, we discuss the basic concept of the conventional approach that involved the deep CNN for upscaling the LR image into an HR image.

# 14.2.1 INTERPOLATION-BASED UPSCALING APPROACH FOR IMAGE SUPERRESOLUTION

Image interpolation is a method that changes a LR image into a HR image. The design of interpolation-based methods is very simple, and implementation is very easy. The applications of interpolation in various areas include space imagery, military applications, medical image enhancement, and image decompression. The main categories of interpolation-based techniques are nearest neighbor, bilinear, and bicubic interpolation-based methods.

# 14.2.1.1 NEAREST-NEIGHBOR INTERPOLATION-BASED IMAGE SUPERRESOLUTION METHOD

The simple and basic method of interpolation is the nearest-neighbor interpolation-based method. In this method, rather than calculating an average value using weighting criteria or generating an intermediate value using complex methods, this method simply finds the “nearest” neighboring pixel and assumes its intensity value. The basic operation of nearest-neighbor interpolation is shown in Figure 14.2.