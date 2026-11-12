# Quality-Preserving Extreme Image Compression: Using Interpretable Conditioning Inputs with Diffusion Models

Shayan Ali Hassan(⊗), Danish Humair, Ihsan Ayyub Qazi, and Zafar Ayyub Qazi

Department of Computer Science, Lahore University of Management Sciences, Lahore, Pakistan.
{25100165,25100183,ihsan.qazi,zafar.qazi}@lums.edu.pk

**Abstract.** Diffusion models have revolutionized image synthesis, but their potential for image compression remains underexplored. We introduce PLIC (Pseudo-Lossy Image Compression), a compression framework leveraging diffusion models and conditioning inputs to achieve high compression ratios while maintaining strong perceptual similarity and superior image quality. Unlike traditional neural compressors using abstract latent representations, our approach uses interpretable conditioning inputs (text prompts, canny edges, color palettes) to guide diffusion-based image reconstruction. Grounded in rate-distortion-perception theory, PLIC prioritizes minimizing bitrate and distortions over pixel-perfect reconstruction, allowing diffusion models to fill in plausible details during decompression which still results in high perceptual similarity. Evaluating on 490 real-world images, we demonstrate superior compression ratios (0.004 bits per pixel and 0.197 bits per pixel on average) while maintaining excellent image quality (mean BRISQUE=23.36, mean CPBD=0.60) and high perceptual similarity. Our approach scales effectively with increasing image resolution, with compression advantages growing at the most common image resolutions. We analyze practical implications including benefits for internet affordability, archival storage, and deployment considerations. Our project code can be found at: https://github.com/PseudoLossy/PLIC.

**Keywords:** Image Compression · Diffusion Models · Conditioning Inputs

# 1 Introduction

Image compression is widely used for reducing the data footprint of images while maintaining acceptable visual quality. Without image compression, many