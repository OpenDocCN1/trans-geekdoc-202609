
## 19.2 Related Work

In the last decade, various approaches have been proposed to secure and protect patient’s confidential information using electrocardiogram (ECG) steganography. Transform domain steganography is a popular choice because of its robustness against steganography attacks (steganalysis) and substantial embedding capacity [6]. This section briefly reviews state-of-the-art ECG steganography approaches (It should be noted that the ECG watermarking techniques are not discussed here).

Special range numbers (2.1475×10⁹) of ECG signals are exploited for embedding and extraction of patient’s secret information with very low PRD (Percentage residual difference) of watermarked ECG [7]. The method was robust in terms of identifying locations of embedded bits. A wavelet-based ECG steganography approach was introduced in [4,8,9] by combining encryption and scrambling methods to protect patient’s confidential records. After five-level discrete wavelet transform (DWT) decomposition, the secret data is embedded using variable bit length least significant bits (LSB) insertion (1 to 5 LSB bits).

In transform domain ECG steganography, wavelet transform is widely used for information hiding. A DWT-SVD (singular value decomposition) based robust ECG steganography algorithm is presented using BCH (Bose–Chaudhuri–Hocquenghem) codes in [10]. Secret information is embedded in high frequency band of DWT, as this band is not significant during the diagnosis stage. Input 1-D ECG signal is converted into 2-D matrix before DWT decomposition. A similar approach is proposed without BCH codes for e-Healthcare applications [11]. Improved DWT-SVD based ECG steganography approach is demonstrated in [12] and compared to the method in [10]. After converting input ECG into 2-D matrix, DWT decomposition is applied. The secret data is embedded in a specified sub-band (HH-sub-band) by replacing the singular values of the 2-D ECG signal by the singular values of the secret information using dynamic location selection approach.

Use of a continuous ant colony optimization (CACO) is proposed [13] to enhance imperceptibility and robustness of DWT-SVD based steganography algorithm. To acquire multiple scaling factors (MSF), CACO based optimization problem is formulated and solved in order to reduce deterioration in the ECG stego signal. Reversible ECG steganography is presented using histogram shifting and thresholding approach [14]. Integer-to-integer DWT is applied over the ECG signal for reversibility and high capacity information hiding.

To provide high security to patient’s secret information, the input data is encrypted using Advanced Encryption Standards (AES) before embedding into LSB of DWT coefficients [15]. High peak signal to noise ratio (PSNR) is achieved using the proposed method. A low capacity reversible ECG steganography for secure transmission of patient’s data is proposed in [16]. The characteristics of the Hamming code and matrix coding are utilized for secret message insertion in the ECG signal. Same approach is extended for EMG (Electromyography) data embedding with minimum distortion using different hamming codes including (3,1),(7,4),(15,11),(31,26). Complete extraction of the embedded data at the receiver is presented using integer wavelet transform based ECG steganography [17–19]. Rest of the approach is similar to [4] including XOR ciphering and scrambling matrix embedding of data in wavelet coefficients. Curvelet transform based ECG steganography is proposed by choosing the curvelet coefficients around zero values for embedding [20,21]. Selection of these coefficients deteriorates the ECG signal least and ensures imperceptibility of the secret information. The method [20] has zero bit error rate and PSNR decreases as secret data size increases.

Discrete wavelet transform, discrete cosine transform (DCT) and discrete Fourier transform (DFT) are explored for ECG steganography using quantization based information hiding [6]. ECG signal is first decomposed using 7-level Haar DWT and secret data is embedded using coefficient quantization. Two methods, high-capacity but lossy and reversible ECG data hiding approaches are proposed [22] using the coefficient alignment. The first method is robust and capable of large information hiding capacity. Local linear predictor (LLP) based reversible ECG data hiding algorithm is presented in [23]. Input ECG signal is divided into three parts and three different predictors are used for each part. Higher payload is obtained and scrambling process incorporated to protect ECG signal and to enhance information security.

As described above, all the ECG data hiding algorithms are classified into two categories. First type includes transform based techniques (DWT, DCT and DFT) which are widely studied with high embedding capacity. Second category involve methods that embed the secret information directly in the ECG signal. These methods are less robust and have low embedding capacity. Also, very few approaches are concerned with data security and the corresponding encryption technique as described in [4,16,17,20,23].

Robustness is another critical and significant characteristic of the steganography technique, as it is important to recover the patient’s information at the receiver side with zero bit error rate. Different methods including [16,20,23] recovers the secret data with zero bit error rate at the receiver. Reconstruction of the ECG signal without any loss (reversible approach) is proposed in [14,16,22,23]. Fractional Fourier transform is a generalization of the classical Fourier transform and used in various signal and image processing applications. This chapter presents fractional Fourier transform based secure and robust ECG data hiding techniques with zero bit error rate. Secret information of the patient is encrypted using XOR encryption to increase the security. Additionally, Hamming code is applied to enhance the robustness of the proposed approach and lowering the bit error rate at the receiver (extraction side). Table 19.1 summarizes different ECG steganography techniques.

## Table 19.1 Various ECG Steganographic Techniques

| Method | Transform | Security Analysis | Capacity | PRD (%) | Comments |
|---|---|---|---|---|---|
| [4] | Wavelet | Yes | 2.4 kB | 0.32 | 59 ECG samples including normal, VF and VT samples used for analysis |
| [7] | LSB of ECG signal | Yes | 2.5 kB | 0.0678 | Simple and efficient method |
| [10] | DWT-SVD | No | — | 0.000059 | Use of BCH error-correcting codes to improve robustness |
| [12] | DWT-SVD | No | 3500 bits | 0.0031 | Dynamic location selection approach with error rates less than 0.6% |
| [13] | DWT-SVD | No | 3.07 kB | 0.06 | Continuous ant colony optimization (CACO) is employed to improve robustness |
| [14] | IWT | No | 324.3 kB for 30 min | 0.2241 | Use of IWT for reversible operation |
| [16] | Hamming code | Yes | 66.67 kB | 0.1286 | Reversible approach |
| [17] | IWT | Yes | 2.4 kB | 0.2934 | Faster and low loss of information |
| [20] | FDCT | Yes | 512 Bytes | 0.0132 | Zero bit error rate |
| [6] | DWT, DCT & DFT | No | 32 bits | – | DWT is better compared DCT and DFT in terms of SNR and RMSE |
| [22] | ECG coefficients | No | 40 kB | 0.4388 | Robust and reversible technique |
| [23] | LLP | Yes | 7.9 BPS | 2.1179e+03 | High capacity reversible approach |

## 19.3 Fractional Fourier Transform Based ECG Steganography

ECG steganography hides the information in cover ECG sample. Proposed fractional Fourier transform based ECG steganography architecture consists of two major steps: (a) embedding algorithm and (b) extraction algorithm. Embedding algorithm is used to ensure secure information insertion and to hide the data with minimum degradation in the cover ECG.

The electrocardiogram sample is subjected to a fractional Fourier transform resulting in transform coefficients. The embedding step hides the patient’s secret information into these coefficients. In order to reconstruct the stego ECG signal, inverse fractional Fourier transform is applied. At the receiver side, the patient’s data is retrieved using the stego ECG. This data can be extracted only by authorized person using the encryption key. Sample data consisting of patient personal data and medical records is depicted in Figure 19.2.

To secure secret information and to not allow unauthorized access, shared key based encryption algorithm is employed. XOR ciphering technique is employed with ASCII shared key, which acts as a security key. XOR encryption is simple to implement and has low complexity. Additionally, to reduce bit error rate and in turn to enhance robustness of the approach, Hamming block coding is used. Hamming encoder and decoder with the codeword length n and the message length k is used.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_572_0.png)

Figure 19.2 Patient’s personal and medical data to be embedded.
