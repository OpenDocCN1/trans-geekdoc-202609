# Table 17.5 (Continued) Summary of Recent State-of-the-Art Watermarking Techniques for Tele-Health Applications

| Ref No. | Proposed Objectives | Techniques to Achieve Objectives | Type of Watermarking Technique | Performance Evaluations | Size of the Cover/Watermark Image(s) | Other Important Considerations |
|---|---|---|---|---|---|---|
| [49] | Secure watermarking using encrypted image. | Identified the regions
Image encryption
LSB substitution | Reversible | PSNR = 131.02, SSIM = 0.9999 (Max—recovered image) PSNR = 113.55 SSIM = 0.9999 (Max—decrypted image) embedding rate = 0.05 | 512 × 512/size of ROI = 144/16 payload bits. | – Using image database of CIP. |
| [54] | Secure medical data hiding using cryptography. | Identified the regions, LSB
AES | Reversible | PSNR = 107.1503 dB
MSE = 0.0828
computational complexity = O(x*n)
For images of size 512 × 512, insertion rate = 0.25 bpp, mean execution time for embedding and extraction is 697.4 and 403.4 milliseconds, respectively. | 512 × 512/insertion of 0.25 bits per pixel. | – Using AES with a key size = 128 bits. |