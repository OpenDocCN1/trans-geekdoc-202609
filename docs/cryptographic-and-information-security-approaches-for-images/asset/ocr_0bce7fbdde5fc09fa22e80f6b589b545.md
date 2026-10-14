+   2. Apply one level DWT on MRI (ip1) and intensity component (i) of PET color image to attain one low frequency co-efficient and three high frequency coefficients.
+   
+   1 – DDWT (ip 1) ∈ (LL, LH, HL, HH) (4.8)
+   
+   1 – DDWT (i) ∈ (LL1, LH1, HL1, HH1) (4.9)
+   
+   3. Apply DCT on wavelet co-efficient of MRI (LL, LH, HL, and HH) and intensity component of PET image (LL1, LH1, HL1, and HH1).
+   
+   4. Apply the following fusion rule:
+   Compute spatial frequency of two image DCT coefficients. Apply the following functional conditions to get fused coefficients [8].
+   
+   F_LL1 = { f_LL(x,y)   SF_DCT(LL) > SF_DCT(LL1) + TH ; f_LL1(X,Y)   SF_DCT(LL) < SF_DCT(LL1) + TH ; (f_LL + f_LL1)/2   otherwise } (4.10)
+   
+   Apply the same rule for F_LH1, F_HL1 & F_HH1 also.
+   
+   5. Apply Inverse DCT on fused F_LL1, F_LH1, F_HL1 & F_HH1 coefficients respectively.
+   
+   6. Apply Inverse DWT on output of step 5 to get new intensity component image.
+   
+   7. Finally the fused color image is a combination of new intensity component of PET image and unchanged components of hue and saturation.

# 16.4.1.2.2 Image Watermarking

The second part of proposed algorithm is image watermarking. This can effectively reduce the total information size by embedding multiple reports into a single cover image. The cover image inhabits the multiple patient reports and transfers to the destination for further processing. At the receiver end all the images are extracted effectively with lossless. The whole procedure is split into the embedding process and extraction process, one is at the transmission side and the other one is at the receiver end. The following sections discuss the watermarking embedding and extraction process.

# 16.4.1.2.2.1 Watermark Embedding Process

+   1. Read the color cover image (IN) (256*256*3) and four color watermark images (W1, W2, W3, and W4) (128*128*3). Out of four one is fused scan image and other three are clinical reports of patient (like patient photo, medical record, ECG report).