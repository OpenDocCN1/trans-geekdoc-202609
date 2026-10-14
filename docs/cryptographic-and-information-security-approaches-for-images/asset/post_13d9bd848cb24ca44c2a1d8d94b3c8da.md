
probability value for the various levels of significance (e.g., 5%, 1% etc.) and the hypothesis. If the estimated values lie below the critical values, then it justifies that the encrypted histogram has uniform pixel distribution.

### 11.5.1.8 Histogram Deviation

It measures the variation in the pixels between the original and encrypted image histogram. It can be estimated using

$$ H_D = \left( \frac{ \frac{i_0 + i_{255}}{2} + \sum_{j=1}^{254} i_j }{ a \times b } \right) $$

where $i_j$ represents the amplitude of the difference at a pixel value $j$, $a \times b$ represents the row and the column of the encrypted image. The higher the estimated value, the better will be the encryption algorithm.

### 11.5.1.9 Irregular Deviation

It estimates the difference between the original and the encrypted image by estimating the mean difference in the histograms. It can be calculated as

$$ I_D = \left( \frac{ \sum_{j=0}^{255} \text{MH}(j) }{ a \times b } \right) $$

where MH(j) represents the histogram deviation and is given as the difference between the Mean Histogram value from Histogram deviation. $a \times b$ represents the image size. Lower the estimated value; better will be the encryption algorithm.

### 11.5.1.10 Deviation from Ideality

It is a measure, which helps in reducing the deviation of the encrypted image from the ideal case. It can be estimated using

$$ \text{HI}_E = \begin{cases} \frac{a \times b}{256} & 0 \le E_i \le 255 \\ 0 & \text{otherwise} \end{cases} $$

$$ I = \frac{ \sum_{c=0}^{255} | \text{HI}(E) - H(E) | }{ a \times b } $$

where HI(E) and H(E) represent the histograms of the ideal and actual encrypted image. The lower the computed value, the better will be the encryption algorithm.

## 11.5.2 Differential Attack Analysis

Differential attack analysis determines the difference in the pixel values of the encrypted images by making a one-bit change in the image pixel of the original image.

### 11.5.2.1 NPCR and UACI

Number of Pixel Changing Rate (NPCR) and Unified Average Changing Intensity (UACI) are the most commonly used measures in Differential attack analysis. It can be done by analysing the two encrypted images: one from the original input plain image and the second from the plain image after making a single bit change. They are calculated using the following equations:

$$ \mathrm{NPCR} = \frac{ \sum_{o,p} E(o,p) }{ a \times b } \times 100\% $$

$$ \mathrm{UACI} = \frac{1}{a \times b} \left[ \sum_{o,p} \frac{ | E1(o,p) - E2(o,p) | }{ 255 } \right] \times 100\% $$

where \(E(o,p)\) is of the same image size as \(E1(o,p)\) and \(E2(o,p)\):

$$ E(o,p) = \begin{cases} 0 & \text{if } E1(o,p) = E2(o,p) \\ 1 & \text{if } E1(o,p) \neq E2(o,p) \end{cases} $$

The estimated UACI should lie between the lower and the upper significance levels and the NPCR value should lie above the critical value to resist the differential attacks as in Tables 11.3 and 11.4.

**Table 11.3 Theoretical UACI Critical Value for Various Significance Levels**

| Significance level | Theoretical UACI critical value |
|---|---|
| \(U^-_{0.05}\) | 33.2824% |
| \(U^-_{0.01}\) | 33.2255% |
| \(U^-_{0.001}\) | 33.1594% |
| \(U^+_{0.05}\) | 33.6447% |
| \(U^+_{0.01}\) | 33.7016% |
| \(U^+_{0.001}\) | 33.7677% |

**Table 11.4 Theoretical NPCR Critical Value for Various Significance Levels**

| Significance level | Theoretical NPCR critical value |
|---|---|
| \(N^*_{0.05}\) | 99.5693% |
| \(N^*_{0.01}\) | 99.5527% |
| \(N^*_{0.001}\) | 99.5341% |

## 11.5.3 Attack Analysis

To validate and to prove the robustness and the strength of the encryption algorithm, various attack analysis have to be carried out. This section discusses three types of attacks namely cropping attack, noise attack and chosen plain text attack.

### 11.5.3.1 Cropping Attack

In cropping attack, some random blocks or uniform blocks of the encrypted images are cropped intentionally (1%, 5% etc.) and it is given as input to the decryption algorithm. At the receiver end, the decrypted image recovery determines the resistant against various attacks purposely caused by the intruders over a public medium which validates the strength and immune power of the proposed encryption algorithm. Real time example includes CCTV image transmission through internet gateway when hacked by an intruder, the security algorithm at the receiver end should estimate the input image to some extent.

### 11.5.3.2 Noise Attack Analysis

In real time scenario, during diagnosis of the medical records, the encrypted medical image will be passed through a communication channel to exchange data between peers. This section discusses various communication channels like AWGN (Additive White Gaussian Noise), Rayleigh and Rician.

**Color Noises:** Color noises arise due to the power spectrum of noise signals. Each color noise has its property. With the Power Spectral Density (PSD) of noise, various noises can be generated.

**Communication Channels:** AWGN channel is the one which adds white Gaussian noise to it. Rayleigh channel makes the fading of the input signal amplitude which is based on the Rayleigh distribution parameter. Rician channel provides multipath to the applied input signal and in that one of the signal path will be shortened or extended based on Rician distribution. The channel output can be estimated using Signal to Noise Ratio (SNR), Bit Energy to PSD of Noise (Eb/N0) and Signal Energy to PSD of noise (ES/N0).

**System Noises:** Gaussian noise model is a statistical model, whose Probability Density Function (PDF) is equal to the Gaussian distribution function. Poisson noise is a noise, an electronic noise created by Poisson distribution function. Salt and pepper noise is an impulse noise created due to the sudden disturbances in the image input. Colored noises and system noises can be added to the encrypted medical images and passed over the communication channels. At the receiver end, the image recovery decides the withstanding capacity of the encryption algorithm.

### 11.5.3.3 Chosen Plaintext Attack

Any encryption algorithm which can withstand chosen plaintext attack should naturally withstand plain and cipher text attack also. The equation to estimate the attack is done by the bit XOR operation of two cipher images obtained from two everyday images equals to the bit XOR operation between the two plain images

$$ (\text{Cipher image}_1 (M \times N) \text{ XOR } \text{Cipher image}_2 (M \times N)) = (\text{Plain image}_1 (M \times N) \text{ XOR } \text{Plain image}_2 (M \times N)) $$

The cipher image output depends on the number of rounds involved in each stage of the encryption algorithm. If the equation is satisfied by the proposed algorithm, then it is prone to chosen plaintext attack by the intruder, else it will resist against this attack.

## 11.6 Encryption Techniques in DICOM

Electronic Patient Record (EPR) has been implemented in many developing countries which refer to the systematic collection and storage of health information about patients in digital format. It includes medical history, personal details and billing information of the patients. Attacks like an interruption, interception, modification, and fabrication of health records have been identified as the root cause for the failure of telemedicine projects.

Maintaining EPR is the fundamental role for the successful implementation of Telemedicine application in urban areas to improve the health care quality. Confidentiality, Integrity, Authentication (CIA), reliability, availability and privacy are the key features of any telemedicine diagnosis. Department of Health Services, New Delhi, elaborated the various ethical issues while maintaining and sharing EPR in real time scenario [8].

Department of Community Medicine, New Delhi, differentiates EMR and EHR and also elaborates on the challenges in customising the EMR as it provides efficient use of digitised data, which provides the chance for doctors to efficiently diagnose the diseases in due course of treatment.

In this regard, Bhattacharya et al. [9] Indian Institute of Information Technology & Management, Gwalior, provides the security solutions in accessing EPR by employing RSA and DES algorithms. Sugandh [26], co-founder of Iam wire, a digital tech incubator, recommended a secured cloud-based storage of digitised EPR to enhance life-saving in emergency situations. Pradeep Kumar et al. [12], Erode, Tamil Nadu addressed the DCT and DWT based watermarking schemes on medical records to provide identity and privacy to EPR. Lavanya et al. [11] MIT, Chennai, proposed a joint encryption and watermarking scheme to provide integrity to patients medical record by considering the NROI of the EPR. Saroj Kanta Mishra et al. [13], Sanjay Gandhi Postgraduate Institute of Medical Sciences (SGPGIMS), Lucknow, and Rajesh [14], Indian Institute of Management, Ahmedabad, provide the challenges, solutions, merits and demerits of telemedicine in India.

To overcome the challenges faced by EPR access, a secured cloud-based structure for sharing EPR among peers using Attribute-Based Encryption (ABE) was carried out by Sangeetha et al. [15], where the details of the patients were encrypted and stored on semi-trusted cloud servers. In their work, the cloud-based security has been divided into Personal Domains (PSDs) to provide privacy to patients to authenticate the users in hospitals and related healthcare providers.

When the EPR is loaded on the cloud servers, flexible access, security, and privacy have to be provided by the servers. To curtail these issues, improved Shamir secret sharing encryption was proposed by Sangeetha et al. [16] to enhance the integrity and the authenticity of the secured cloud environment.

To establish a secure communication between authenticated stakeholders in e-health care, the conventional methods employed are steganography, cryptography and watermarking. The traditional security algorithms employed in the current medical applications are Advanced Encryption Standard (AES) and Data Encryption Standard (DES) by Norcen et al. [27]. However, the same algorithms cannot be used for accessing EPR due to its large capacity and size.

To provide integrity to EPR data, watermarking integrated with steganography was proposed by Zaz et al. [28] and Coatrieux et al. [29]. To minimize the computational complexity and the time involved in executing the algorithms on EPR, many researchers are attracted to develop selective image encryption schemes without compromising the security aspects [30].

Secured medical data sharing and handling is a primary objective in IoT platform for various medical applications. Ibrahim Mashal et al. [18] and Debasis Bandyopadhyay et al. [19] proposed the end-to-end communication using IoT architecture and the related security issues in interconnecting the smart devices and the protocols used to provide confidentiality and authentication of the stakeholders involved in communication.
