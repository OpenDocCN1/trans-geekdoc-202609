+   - Using the generated chaotic sequences, perform pixel and block scrambling on the secret QR
+   - Read the input DICOM
+   - Perform shuffling, permutation and diffusion operation based on the sequence generated from the individual maps
+   - To the diffused image, embed the QR watermarking as in Figure 11.5, to produce the final encrypted image.

# Method 2: QR based watermarking in RGB DICOM

+   - Watermarking will be implemented for authentication and embedding for data integrity.
+   - Quick response (QR) codes are widely used in various products for ownership identification.
+   - In the proposed scheme, QR code-based visible watermarking will be done on the encrypted NROI image
+   - The NROI section of DICOM image will carry the 25 × 25 QR code as a watermark, the size of which can be decided based on medical image payload.
+   - LSB substitution has been adopted as simple data embedding on the spatial domain for greater imperceptibility.

In the encrypted NROI, the pixel bits which were present before the insertion of 25 × 25 QR code image coefficients will be embedded in the LSBs of the other sections of the DICOM image to avoid data loss. Here QR code is generated using patient and doctor's name which will be watermarked as in Figure 11.6a. The sample results are shown in Figure 11.6 (b–h).

![](bbox=[0.12, 0.78, 0.9, 0.92])

Figure 11.5 QR based secret sharing in DICOM.