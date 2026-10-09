
luminance of all the pixels in group two, according to Equation (6). After Stage 2, Stage 3 computes the luminance of all the pixels in group three, according to Equation (7). All pixels of the three groups are collected to generate the tone mapped image.

![](img/e4200cc4308edaf8913e513b0f96dbb6_497_0.png)

Figure 4. The flowchart of the three-stage algorithm.

### 3.3. Color Image

We separate lightness and color features by converting RGB images into HSV space. Figure 5 shows the data flow diagram for dealing with a color image.

![](img/e4200cc4308edaf8913e513b0f96dbb6_497_1.png)

Figure 5. Data flow diagram for dealing with a color image.

Three channels are separated into H, S, and V channels, where the V channel is only used to compress dynamic range, and the H and S channels are constant. The last part is Gamma correction, which is used for overcoming the non-linear response of the display device.

## 4. Results

Our method is simulated by Matlab 2016a on a desktop computer with an Intel i5-7400 CPU and Kingston 2400 MHz 8G-DDR4 internal storage. Tone-mapped images are shown on a Dell S2721DG digital display whose gamma parameter approximates 2.2. The test radiance maps contain three famous scenes and the TMQI database [19] with a very high dynamic range.

### 4.1. Subjective Performance Evaluation

In this part, we use three famous radiance maps to make a comparison among several tone mapping algorithms. The compared tone mapping algorithms include DeepTMO [16], Thai [22], TMO-Net [17], L1-L0 [23], and Khan [12]. The three test radiance maps are shown directly in Figure 6. Figures 7–9 demonstrate a comparison of tone-mapped images.

![](img/e4200cc4308edaf8913e513b0f96dbb6_498_0.png)

**Figure 6.** The picture shows the test radiance maps rendering on standard LCD. The left image, called “memorial church”, is an HDR image from TMQI database [19]. The middle image, called “moto”, and the right image, called “apartment”, are reprinted with permission from Ref. [24]. 2022 Elsevier B.V. (Reprinted from Signal Processing: Image Communication, Vol (29). Authors (Narwaria, M., Da Silva, M.P., Le Callet, P. and Pépion, R.). Title of article (Tone mapping based HDR compression: Does it affect visual experience?), Pages (257–273), Copyright (2013), with permission from Elsevier.)

The images derived by our algorithm show visually pleasing results due to the clear details and distinguishable information both in dark areas and bright areas. The compared tone mapping algorithms suffer from some reduction in image quality. TMO-Net provides a good, clear result in the darker areas, while the contrast in the brighter area is decreased which leads to a problem of overexposure. DeepTMO improves the global contrast of the original real-world image. The content of the dark area is revealed and the brightness becomes more apparent. However, the reproduced image was blurred while the details are reduced both in low-light and bright areas. Both Thai and Khan have the problem of contrast loss in the low-light area, which leads to over-compression of some intensity levels. There, some image quality is lost, particularly in darker areas. The visibility of the dark area is improved by L1-L0 and the tone-mapped images make a good balance between detail enhancement and visual naturalness for both indoor and outdoor scenes. However, the LDR image obtained by L1-L0 has problems with halo artifacts and the contrast is over-enhanced. Meanwhile, the tone-mapped images show a little brightness distortion.

Another experiment was conducted to test the validity of the tone mapping algorithm. We selected the TMQI database [19] that contains 15 radiance maps to compute the mean opinion score (MOS). TMQI database is shown in Figure 10. It can be seen that the TMQI database includes six indoor scenes and nine outdoor scenes. Due to the unequal resolution, we resize the images without aspect ratio preservation to favor the demonstration. The image displayed in Figure 10 leads to unsatisfactory visibility which is caused by extremely high contrast. The algorithms compared and the algorithm proposed were adopted to convert every radiance map of the TMQI database to a displayed image. Thus, we obtained 90 LDR images. Figure 11 shows four groups of LDR images. It can be seen from Figure 11 that the visibility of our method is improved with better performance than the other competitive tone mapping methods. The subjective visual quality of each tone-mapping image share quality consistent with the reproduced image shown in Figures 7–9.

![](img/e4200cc4308edaf8913e513b0f96dbb6_499_0.png)

**Figure 7.** A comparison of tone mapping algorithms on the memorial church image. **(a)** Result by TMO-Net. **(b)** Result by DeepTMO. **(c)** Result by Thai. **(d)** Result by L1-L0. **(e)** Result by Khan. **(f)** Result by our algorithm.

![](img/e4200cc4308edaf8913e513b0f96dbb6_499_1.png)

**Figure 8.** A comparison of tone mapping algorithms on the moto image. **(a)** Result by TMO-Net. **(b)** Result by DeepTMO. **(c)** Result by Thai. **(d)** Result by L1-L0. **(e)** Result by Khan. **(f)** Result by our algorithm.

![](img/e4200cc4308edaf8913e513b0f96dbb6_500_0.png)

**Figure 9.** A comparison of tone mapping algorithms on the apartment image. **(a)** Result by TMO-Net. **(b)** Result by DeepTMO. **(c)** Result by Thai. **(d)** Result by L1-L0. **(e)** Result by Khan. **(f)** Result by our algorithm.

![](img/e4200cc4308edaf8913e513b0f96dbb6_500_1.png)

**Figure 10.** The 15 radiance maps from the TMQI database.

Then, the tone-mapped images of the TMQI database were shown on an S2721DGF Display. To determine MOS, 31 volunteers, including 16 females and 15 males aged between 23 and 34, were invited to give the score for each image shown on the display produced by the above tone mapping algorithms. The score range is from 1 to 10, where 1 means the worst visual quality and 10 means the best visual quality. The mean and std of MOS values are shown in Figure 12.

It can be seen that our method has a higher score (8.9) than other compared methods. Meanwhile, the lowest std value (0.175) means the performance of our algorithm is widely recognized among these volunteers. The mean score and standard deviation for other tone mapping methods are DeepTMO (7.9, 0.3), Thai (5.8, 0.6), Khan (5.1, 1.1), TMO-Net (7.2, 0.25), and L1-L0 (7.7, 0.4). According to the mean scores, our method achieves about 12% higher than the closest tone mapping method (DeepTMO).

![](img/e4200cc4308edaf8913e513b0f96dbb6_501_0.png)

**Figure 11.** Four groups of tone-mapped images were obtained by our algorithm and the compared algorithms. The order of sub-photographs keeps in line with Figure 7.

![](img/e4200cc4308edaf8913e513b0f96dbb6_501_1.png)

**Figure 12.** Mean and std of subjective rankings of the six tone mapping algorithms.

### 4.2. Objective Performance Evaluation

Besides subjective performance evaluation, we employed a tone-mapped image quality index (TMQI [19]) and natural image quality evaluator (NIQE [25]) as objective evaluations to further evaluate the performance of related tone mapping algorithms. The TMQI score ranges from 0 (worst quality) to 1 (best quality), and a smaller NIQE indicates a higher image quality. Tables 1 and 2 show the TMQI and NIQE scores for related tone mapping algorithms. According to Tables 1 and 2, our algorithm results in a higher score than the compared tone mapping algorithms. The mean TMQI score for our tone mapping method is higher by about $9\%$, $30\%$, $12\%$, $8\%$, and $41\%$ as compared to DeepTMO, Thai, TMO-Net, L1-L0, and Khan tone mapping methods. The mean NIQE score for our tone mapping method is lower than the competitive tone mapping methods. The highest TMQI and lowest NIQE scores indicate the tone-mapped image obtained by our algorithm provides better structural fidelity and less statistical naturalness than the other methods.
