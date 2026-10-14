![](bbox=[0.11, 0.12, 0.89, 0.28])

Figure 17.6 Important watermark attacks. (From Mohanty, S.P., Digital watermarking: A tutorial review. http://www.csee.usf.edu/smohanty/research/Reports/WMSurvey1999Mohanty.pdf, 1999.)

# 17.8 Recent State-of-the-Art Watermarking Techniques for Tele-Health Applications

In [18], Ustubioglu and Ulutas proposed a secure medical image watermarking technique using fusion of modified difference expansion and least significant bit (LSB). Initially, the medical cover image is divided into different blocks and the watermark information is embedded only in the border pixels of the cover image. Further, the method can detect tampered regions with finer precision and it does not depend on the size of the region of interest (ROI) portion of the cover. Experimental results demonstrated that the performance in terms of PSNR and (true positive rate) TPR is found superior than other similar existing methods [19–24].

Parah et al. developed a blind watermarking technique using intermediate significant bit (ISB) for e-healthcare applications [25]. Two different watermarks are embedded into the same cover media for content authentication at receiver end. Further, security of the watermark data is enhanced by using non-linear dynamics of chaos. The imperceptibility, robustness, localization analysis and tamper detection and of the work is found to be suitable for e-medical applications.

Sharifara and Ghaderi proposed a robust and secure watermarking technique in DWT (discrete wavelet transform) domain [26]. In this method, the cover image is divided into region of interest (ROI) and region of non-interest (RONI). Both ROI and RONI portions are transformed using DWT. However, the encrypted watermark(s) (using public key) information is embedded into the RONI portion of the cover. The performance of the method is determined by PSNR and SSIM.

Further, region-based blind watermarking is proposed by Shih et al. [27]. This method embeds the watermark information in RONI portion of the cover image using particle swarm optimization (PSO). First, the RONI portion of the cover is transformed by DWT and the singular vector of the selected DWT sub-band is determined by singular wave decomposition (SVD). Finally, the singular vector is further transformed by DCT and the middle frequency DCT component is