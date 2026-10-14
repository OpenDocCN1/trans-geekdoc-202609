
- 2. The Red (inr), Green (ing), and Blue (inb) components of cover image are divided into four equal parts. Each part size is 128*128.

- 3. The embedding process is given below:

The red components of four watermark images embedding into red component of cover image with scaling factor α to obtain new red component (fr). Where α = 0.005.

rr1 = inr(1 : m/2,1 : n/2) + (α * rw1) (4.11)
rr2 = inr(1 : m/2, n/2 +1 : n) + (α * rw2) (4.12)
rr3 = inr(m/2 +1 : m,1 : n/2) + (α * rw3) (4.13)
rr4 = inr(m/2 +1 : m,n/2 +1 : n) + (α * rw4) (4.14)
fr(1 : m/2,1 : n/2) = rr1 (4.15)
fr(1 : m/2,n/2 +1 : n) = rr2 (4.16)
fr(m/2 +1 : m,1 : n/2) = rr3 (4.17)
fr(m/2 +1 : m,n/2 +1 : n) = rr4 (4.18)

The same procedure is applicable for green and blue components to obtain a new green component (fg) and a new blue component (fb).

- 4. Finally a watermarked image (wd) can be obtained by combining the above three new (red, green and blue) components.

The whole process of embedding is shown in Figure 16.15.

### 16.4.1.2.2.2 Watermark Extraction Process

- 1. Consider watermarked image (wd). The watermarked image having three components (red, green, and blue). The red (inwr), green (inwg), and blue (inwb) components are divided into four equal parts. Each part having same size.

- 2. The extraction of watermark image is given below:

To extract the red components of four watermark images (rwe1, rwe2, rwe3, and rwe4) by following equations.

rwe1 = ((inwr(1 : m/2,1 : n/2)) - (inr(1 : m/2,1 : n/2))). / α (4.19)
rwe2 = ((inwr(1 : m/2, n/2 +1 : n)) - (inr(1 : m/2, n/2 +1 : n))). / α (4.20)
rwe3 = ((inwr(m/2 +1 : m,1 : n/2)) - (inr(m/2 +1 : m,1 : n/2))). / α (4.21)
rwe4 = ((inwr(m/2 +1 : m,n/2 +1 : n)) - (inr(m/2 +1 : m,n/2 +1 : n))). / α (4.22)

The same process applies to both green and blue components of watermarked and cover images to extract four green (gwe1, gwe2, gwe3, and gwe4) and blue (bwe1, bwe2, bwe3, and bwe4) components.

- 3. Finally watermark (w1) can be obtained by combining (rwe1, gwe1, and bwe1) components, similarly watermark (w2) with (rwe2, gwe2, and bwe2) components, watermark (w3) with the combination of (rwe3, gwe3, and bwe3) components and watermark (w4) also with (rwe4, gwe4, and bwe4) components.

## 16.4.1.3 Experimental Results

This section deals with types of images, their features, software details and performance metric used for quality analysis. The work used in PET and MRI images. The input image dimensions of MRI and PET are 256×256 and 256 * 256 * 3 pixels respectively. The PET and MRI images are in register. The medical scan images are collected from [19]. The input and output images of fusion rule are displayed in Figures 16.17 and 16.18 and performance results are tabulated in Table 16.1.

The fused color images were used as one of the watermark images. The other images are, Lena as patient photo, electrocardiogram (ECG) image (downloaded from net), and medical record (created by author). The host/cover image, watermark: embedding and extraction images are displayed in Figures 16.19 through 16.22.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_484_0.png)

Figure 16.17 New mild Alzheimer’s disease images: (a) PET scan, (b) MRI scan, (c) ground truth image, and (d–l) output image of various algorithms listed in Table 16.1.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_485_0.png)

Figure 16.18 New mild Alzheimer’s disease images: (a) PET scan, (b) MRI scan, (c) ground truth image, (d–l) output image of various algorithms listed in Table 16.1.

**Table 16.1 Performance Metric Values of Fusion Methods with PSNR (Peak Signal to Noise Ratio) and MSE (Mean Squared Error)**

| Figures | Parameters | PSNR (dB) | MSE |
|---|---|---|---|
| New Mild Alzheimer's disease images (Figure 16.17) | DWT and SF | 43.4645 | 0.4599 |
| New Mild Alzheimer's disease images (Figure 16.17) | DSWT | 43.4864 | 0.4241 |
| New Mild Alzheimer's disease images (Figure 16.17) | PCA | 47.6211 | 0.4012 |
| New Mild Alzheimer's disease images (Figure 16.17) | Brovey | 52.8826 | 0.3348 |
| New Mild Alzheimer's disease images (Figure 16.17) | IHS and PCA | 53.0583 | 0.3215 |
| New Mild Alzheimer's disease images (Figure 16.17) | DWT and PCA | 55.3214 | 0.2334 |
| New Mild Alzheimer's disease images (Figure 16.17) | DWT and PCA with SF | 59.2578 | 0.1589 |
| New Mild Alzheimer's disease images (Figure 16.17) | Ref. [20] | 64.7244 | 0.0748 |
| New Mild Alzheimer's disease images (Figure 16.17) | Proposed method | 67.5575 | 0.0114 |
| New Mild Alzheimer's disease images (Figure 16.18) | DWT and SF | 46.4746 | 0.0260 |
| New Mild Alzheimer's disease images (Figure 16.18) | DSWT | 56.7172 | 0.0692 |
| New Mild Alzheimer's disease images (Figure 16.18) | PCA | 58.1331 | 0.0500 |
| New Mild Alzheimer's disease images (Figure 16.18) | Brovey | 62.2149 | 0.0174 |
| New Mild Alzheimer's disease images (Figure 16.18) | IHS and PCA | 62.5289 | 0.0182 |
| New Mild Alzheimer's disease images (Figure 16.18) | DWT and PCA | 62.7243 | 0.0174 |
| New Mild Alzheimer's disease images (Figure 16.18) | DWT and PCA with SF | 63.3078 | 0.0152 |
| New Mild Alzheimer's disease images (Figure 16.18) | Ref. [20] | 63.4051 | 0.0148 |
| New Mild Alzheimer's disease images (Figure 16.18) | Proposed method | 63.9120 | 0.0115 |

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_486_0.png)

Figure 16.19 Watermark embedding process: (a) Color cover image, (b–e) color watermark images: Patient photo, medical record, and fused scan image, ECG record respectively.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_486_1.png)

Figure 16.20 Watermark extraction process: (a) Color Watermarked image, (b–e) Extracted watermark images: Patient photo, medical record, and fused scan image, ECG record respectively.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_486_2.png)

Figure 16.21 Watermark embedding process: (a) Color cover image, (b–e) color watermark images: Patient photo, medical record, and fused scan image, ECG record respectively.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_486_3.png)

Figure 16.22 Watermark extraction process: (a) Color watermarked image, (b–e) Extracted watermark images: Patient photo, medical record, and fused scan image, ECG record respectively.

The experimental results are verified with PSNR (Peak Signal to Noise Ratio) [3, 6] and MSE (Mean Squared Error) [7]. These values prove the strength of the proposed work. The highest PSNR value means the host image and watermarked image both are identically same for human perception.

### 16.4.1.3.1 Fusion Results

The following figure and table address the results of proposed fusion process and the results are compared with existing techniques. The existing methods results are collected from [34] reference.

The performance of the fusion process is compared with various standard algorithms and existing techniques. The details are tabulated in Table 16.1.

### 16.4.1.3.2 Watermark Results

The following figures and Table 16.2 address the proposed watermarking process on various patient databases. Figures 16.19 and 16.21 are embedding process results and Figures 16.20 and 16.22 are extraction process results. The database includes the patient photo, patient disease record, fused scan report and ECG report. The ECG signals are downloaded from [35].

### 16.4.1.3.3 Watermark Results with Noise

The following Figures 16.23 and 16.24 are showing the extracted watermark images in the presence of salt and pepper noise with various densities like 0.1, 0.001 etc.

**Table 16.2 The Image Watermarking Performance Results in Terms of PSNR and MSE**

| Parameters | PSNR (dB) | MSE |
|---|---|---|
| Ref. [9] | 45.0833 | 2.0172 |
| Proposed method (Figures 16.19 and 16.20) | 49.7155 | 0.6943 |
| Proposed method (Figures 16.21 and 16.22) | 50.6625 | 0.5583 |

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_487_0.png)

Figure 16.23 Salt and pepper noise (density = 0.1) (a) watermarked images, (b–e) extracted watermark images.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_488_0.png)

Figure 16.24 Salt and pepper noise (density = 0.001) (a) watermarked images, (b–e) extracted watermark images.

**Table 16.3 The Measures Results in Terms of PSNR and MSE after Attacks**

| Figures | Noise | Density | PSNR (dB) | MSE |
|---|---|---|---|---|
| Figure 16.23 | Salt and pepper | 0.1 | 14.6763 | 2.2154e+003 |
| Figure 16.24 | Gaussian noise | 0.01 | 20.4297 | 588.9992 |

When the watermarked image is travelling through channels it is affected by various noises. Hence, the author proves the robustness of the proposed algorithm (Table 16.3).

## 16.5 Summary

This section summarised the novel approach in watermarking process by carrying various medical databases in a single image instead of various images. Thus, this chapter showed that multiple images can be embedded into a single image for an easy and short way of transmission. The effectiveness of the technique was also verified under various noises. Nearly five patient image databases were embedded and transmitted effectively. This can be extended by transmitting various other medical scan images, iris image, biometric image etc.

## References

- 1. N. Kausar, A. Majid, and S. G. Javed. A novel ensemble approach using individual features for multi-focus image fusion, *Computers and Electrical Engineering*, (2016), 1–13.
- 2. M. Haribabu, C.H. Bindu, and K.S. Prasad. Multimodal medical image fusion of MRI—PET using wavelet transform, *IEEE International Conference MANCAps*, (2012), 127–130.
- 3. A. Roček, K. Slaviček, O. Dostál, and M. Javorník. A new approach to fully-reversible watermarking in medical imaging with breakthrough visibility parameters, *Biomedical Signal Processing and Control*, 29 (2016), 44–52.
