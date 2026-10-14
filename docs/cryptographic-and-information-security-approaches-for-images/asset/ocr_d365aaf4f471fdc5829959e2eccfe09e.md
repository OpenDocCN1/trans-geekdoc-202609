rwe2 = ((inwr(1 : m/2, n/2 +1 : n)) - (inr(1 : m/2, n/2 +1 : n))). / α   (4.20)

rwe3 = ((inwr(m/2 +1 : m,1 : n/2)) - (inr(m/2 +1 : m,1 : n/2))). / α   (4.21)

rwe4 = ((inwr(m/2 +1 : m,n/2 +1 : n)) - (inr(m/2 +1 : m,n/2 +1 : n))). / α   (4.22)

The same process applies on both green and blue components of watermarked and cover images to extract four green (gwe1, gwe2, gwe3, and gwe4) and blue (bwe1, bwe2, bwe3, and bwe4) components.

+   3. Finally watermark (w1) can be obtained by combining (rwe1, gwe1, and bwe1) components, similarly watermark (w2) with (rwe2, gwe2, and bwe2) components, watermark (w3) with the combination of (rwe3, gwe3, and bwe3) components and watermark (w4) also with (rwe4, gwe4, and bwe4) components.

# 16.4.1.3 Experimental Results

This section deals with types of images, their features, software details and performance metric used for quality analysis. The work used in PET and MRI images. The input image dimensions of MRI and PET are 256×256 and 256 * 256 * 3 pixels respectively. The PET and MRI images are inregister. The medical scan images are collected from [19]. The input and output images of fusion rule is displayed in Figures 16.17 and 16.18 and performance results are tabulated in Table 16.1.

The fused color images were used as one of the watermark images. The other images are, Lena as patient photo, electrocardiogram (ECG) image (downloaded from net), and medical record (created by author). The host/cover image, watermark: embedding and extraction images are displayed in Figures 16.19 through 16.22.

![](bbox=[0.08, 0.75, 0.92, 0.9])

Figure 16.17 New mild Alzheimer’s disease images: (a) PET scan, (b) MRI scan, (c) ground truth image, and (d–l) output image of various algorithms listed in Table 16.1.