
Sharma et al. [20] provide the methodology to protect EPR by employing ROI and NROI based watermarking and embedding schemes. Further, the identity of the patient has also been verified using MD5 Hash and Rivest-Shamir-Adleman (RSA) algorithms to enhance the robustness of the system. Also, Hamming error correction code has been applied to the encrypted medical data to resist the channel noise.

## Method 1: 2D Chaotic based gray scale DICOM image encryption

- Read DICOM image.
- Using the key, permute the DICOM sequence.
- Using two different initial seed values, generate chaotic sequences 1 and 2.
- Bit-XOR the sequences with two different key values.
- Concatenate the bit-XOR sequence outputs.
- Use this sequence for diffusing the image pixel values in the diffused image to produce the final encrypted output as in Figure 11.3.

## Method 2: 3D Chaotic based RGB DICOM image encryption

- Read RGB DICOM image.
- Divide into R, G and B planes as in Figure 11.4.
- Generate a 3D chaotic map using initial seed generator.
- Using the generated sequences, positions of the pixels in the individual planes are scrambled.
- Concatenate the planes and apply transformation.
- Concatenated image is then divided into blocks and sorting is done based on the scrambled pixel values.
- Then scrambling of the blocks is carried out using the chaotic sequences to generate the final encrypted image.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_334_0.png)

Figure 11.3 Chaotic key diffusion sequence based image encryption.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_335_0.png)

Figure 11.4 Pixel and block based chaotic image encryption.

## 11.6.1 Watermarking and Embedding Techniques in DICOM

The impact of design and methodology selection with improved assurance in medical records optimised communication, and clear medical terminologies have been analysed by Soderstrom et al. [31]. A cloud-based EPR using Fuzzy has been implemented by Liu and Weng et al. [22] and Chen et al. [32]. Here, binary tree and attribute-based encryption schemes have been developed to encrypt the medical records of the patients before storing it in the cloud environment. This helps in securing the EPR and maintains its privacy.

A reversible encrypted data hiding scheme by employing ROI and NROI of DICOM image has been carried out by Liu et al. [23] and Cyganek et al. [24]. In this scheme encryption followed by substitution-based data hiding has been employed to protect the EPR and to measure its tolerance against tamper.

Hazzaa et al. [33] introduced a Discrete Wavelet Transform based digital watermarking technique. In this technique, patient details are embedded as a watermark in the original image to restrict any unauthorised access of the EPR when transmitted. Tieu et al. [34] provided a review on protection of EPR and its related security issues. Solutions to protect it from unauthorised access and alterations have been carried out by Mancy et al. [35] to improve the data protection level in EPR sharing.

### Method 1: QR based secret sharing in DICOM

- Get the secret input.
- Apply QR (Quick Response) to it.
- Initial seed is used to generate chaotic maps and then concatenate to form multiple chaotic maps.
- Using the generated chaotic sequences, perform pixel and block scrambling on the secret QR.
- Read the input DICOM.
- Perform shuffling, permutation and diffusion operation based on the sequence generated from the individual maps.
- To the diffused image, embed the QR watermarking as in Figure 11.5, to produce the final encrypted image.

### Method 2: QR based watermarking in RGB DICOM

- Watermarking will be implemented for authentication and embedding for data integrity.
- Quick Response (QR) codes are widely used in various products for ownership identification.
- In the proposed scheme, QR code-based visible watermarking will be done on the encrypted NROI image.
- The NROI section of DICOM image will carry the 25 × 25 QR code as a watermark, the size of which can be decided based on medical image payload.
- LSB substitution has been adopted as simple data embedding on the spatial domain for greater imperceptibility.

In the encrypted NROI, the pixel bits which were present before the insertion of 25 × 25 QR code image coefficients will be embedded in the LSBs of the other sections of the DICOM image to avoid data loss. Here QR code is generated using patient and doctor's name which will be watermarked as in Figure 11.6a. The sample results are shown in Figure 11.6 (b–h).

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_336_0.png)

Figure 11.5 QR based secret sharing in DICOM.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_337_0.png)

Figure 11.6 (a) QR based watermarking in RGB DICOM (b) original DICOM, (c) NROI, (d) ROI, (e) encrypted NROI, (f) encrypted ROI, (g) encrypted output DICOM, and (h) QR watermark in NROI.

## 11.6.2 Cryptographic Techniques in DICOM

Diagnostic medical equipment such as Magnetic Resonance Imaging Scanner (MRI) and Computed Tomography Scanner (CT) play a crucial role in recording the clinical status of a patient diagnosed or suspected with organ abnormality due to chronic diseases. For the treatment of malignant or benign tumours on the brain or other significant parts of human body, MRI images have a noticeable role in assisting the medical practitioners during diagnosis.

The Electronic Patient Record (EPR) in various modalities is a collection of the status report obtained through these MRI or CT scanners. Security of such patient records requires a critical attention as the number of patients reported with abnormalities is, unfortunately, rapidly increasing every day. Presently such patient records are being stored in a compact disk (CD) storage medium and handed over to the concerned patients in most of the scanning centres attached to hospitals. Hence, chances for the unauthorised access to medical records are on the higher side.

For enhanced EPR security, the digitised legal patient record which carries the sensitive health information of patient must be encrypted with a stringent procedure. Digital Imaging and Communications in Medicine (DICOM) is one of the predominantly used formats for representing the medical information all over the world [1]. The proposed system secures the acquired DICOM images of patients from MRI/CT scanner and embeds the patient details. Firstly, the medical image is divided into ROI and NROI based on the diagnosis. The NROI of the EPR will be watermarked with patient and hospital details (visible/non-visible) to yield a high level of authentication.

### Method 1: LSIC – Rubik’s – DNA Triple layered HASH based cryptographic technique

In this regard, the provision of security elements such as CIA to EPR storage will be carried out.

A simple but efficient encryption algorithm integrating Latin Square Image Cipher (LSIC) and Rubik’s algorithm to achieve high throughput considering the massive arrival of medical images.

MD5 Hash is a favorite Hash function used to generate Hash values to verify the integrity of a data unit. In the proposed scheme, hash value will be generated using the following equations.

F(B, C, D) = (B & C) | (~B & D)    (1)
G(B, C, D) = (B & D) | (C & ~D)    (2)
H(B, C, D) = B ^ C ^ D    (3)
I(B, C, D) = C ^ (B | ~D)    (4)

where &, ~, ^ and | represent the AND, NOT, XOR and OR operations, respectively.

Further, ROI will be divided into bit blocks, and bit XOR operation will be performed between the ROI and the hash value.

Concatenate ROI and NROI to form the final encrypted image as in Figure 11.7.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_338_0.png)

Figure 11.7 Triple layered HASH based cryptographic technique.

### Method 2: DNA and Chaos-based encryption in DICOM

- Read the DICOM image from the storage unit.
- Divide the image into two blocks of equal size and perform DNA addition and subtractions using Tables 11.5 and 11.6.
- Compute the discrete logistic sequence by the following equation $X_{n+1}=r X_n(1-X_n)$.
- Select the DNA rules using the chaotic sequence to perform DNA encoding and decoding.

Perform Discrete Gould Transform (DGT) using the matrix given below:

$g_{r,m,o}=(-1)^{m+o}\left(\frac{r!}{(m-o)!(r-m+o)!}\right)$

where $m, o = 0, 1, ..., K-1$ and $r$ is a positive integer. Compute DGT matrix for the required order and perform XOR operation between the DGT output and encoded result to produce the final encrypted image as in Figure 11.8.

**Table 11.5 DNA Operations**

| + | T | C | G | A |
|---|---|---|---|---|
| T | T | C | G | A |
| C | A | T | C | G |
| G | G | A | T | C |
| A | C | G | A | T |

| - | T | C | G | A |
|---|---|---|---|---|
| T | G | C | T | A |
| C | C | T | A | G |
| G | T | A | G | C |
| A | A | G | C | T |

Source: Rehman, A.U. et al., Multimed. Tools Appl., 74, 4655–4677, 2015.

**Table 11.6 DNA Encoding and Decoding Using Chaotic Sequences Derived from Rehman et al.**

| S. No | Interval of Chaotic sequence | Encoding | Decoding |
|---|---|---|---|
| 1 | 0.10–0.15, 0.20–0.25, 0.35–0.40, 0.80–0.85, 0.55–0.60 | GATC | CTAG |
| 2 | 0.01–0.05, 0.50–0.55, 0.60–0.65, 0.85–0.90, 0.95–0.99 | AGCT | GTAC |
| 3 | 0.15–0.20, 0.25–0.30, 0.40–0.45, 0.65–0.70, 0.75–0.80 | CATG | TCGA |
| 4 | 0.05–0.10, 0.30–0.35, 0.45–0.50, 0.70–0.75, 0.90–0.95 | ACGT | TGCA |

Source: Rehman, A.U. et al., Multimed. Tools Appl., 74, 4655–4677, 2015.
