
![](img/47f81eeb5093bf67426e3b948e0d8952_102_0.png)

Figure 6.13 Medical image.

![](img/47f81eeb5093bf67426e3b948e0d8952_102_1.png)

Figure 6.14 Logo image.

![](img/47f81eeb5093bf67426e3b948e0d8952_102_2.png)

Figure 6.15 The medical image encrypted with (a) the RC6 algorithm in the ECB mode, (b) the AES in the ECB mode, (c) the RC6 algorithm in the ECB mode with preprocessing, (d) the AES in the ECB mode with preprocessing.

and 6.16, respectively. The histograms of these images are shown in Figures 6.17 and 6.18, respectively. From the obtained results, we notice that the encryption in the ECB mode fails with these images. We notice also that the preprocessing network enhances dramatically the encryption quality of these encrypted images with the ECB mode.

![](img/47f81eeb5093bf67426e3b948e0d8952_103_0.png)

**Figure 6.16** The logo image encrypted with (a) the RC6 algorithm in the ECB mode, (b) the AES in the ECB mode, (c) the RC6 algorithm in the ECB mode with preprocessing, (d) the AES in the ECB mode with preprocessing.

![](img/47f81eeb5093bf67426e3b948e0d8952_104_0.png)

![](img/47f81eeb5093bf67426e3b948e0d8952_104_1.png)

![](img/47f81eeb5093bf67426e3b948e0d8952_104_2.png)

![](img/47f81eeb5093bf67426e3b948e0d8952_104_3.png)

![](img/47f81eeb5093bf67426e3b948e0d8952_104_4.png)

Figure 6.17 The histograms of the medical image: (a) original, (b) encrypted with the RC6 algorithm, (c) encrypted with the AES, (d) encrypted with the RC6 algorithm in the ECB mode with preprocessing, (e) encrypted with AES in the ECB mode with preprocessing.

![](img/47f81eeb5093bf67426e3b948e0d8952_105_0.png)

Figure 6.18 The histograms of the logo image: (a) original, (b) encrypted with the RC6 algorithm, (c) encrypted with the AES, (d) encrypted with the RC6 algorithm in the ECB mode with preprocessing, (e) encrypted with AES in the ECB mode with preprocessing.

### 6.5 Summary

In this chapter, an efficient approach has been presented to solve the problems associated with encryption in the ECB mode. A preprocessing network processes the data before encryption to diffuse the data bytes together prior to the application of the encryption algorithm in the ECB mode. The test results have shown that any encryption algorithm implemented in the ECB mode with the preprocessing network achieves good diffusion characteristics and high encryption quality without losing the parallel processing advantage.

## ORTHOGONAL FREQUENCY DIVISION MULTIPLEXING

### 7.1 Introduction

The main objective of this book is to study image encryption from a communication perspective. So, we need to determine if an encryption algorithm fits the communication requirements. It is time now to switch to wireless communication to understand the communication process and its limitations and hence to study the performance of the decryption algorithms after the communication process. We consider multicarrier modulation (MCM), especially orthogonal frequency division multiplexing (OFDM), in our study because it is the new trend in wireless communication systems. MCM is used not only in the physical layer of several wireless network standards such as Institute of Electrical and Electronics Engineers (IEEE) 802.11a, IEEE 802.16a, and HIPERLAN2 (High-Performance Radio Local Area Network Type 2), but also in HDTV (high-definition television) applications that include image communication [111,112]. OFDM overcomes the effects of multipath fading by breaking the signal into several narrow-bandwidth carriers. This results in a low symbol rate reducing the amount of ISI (intersymbol interference). The high tolerance to multipath fading makes OFDM more suited to transmissions with a high data rate in terrestrial environments compared to single-carrier transmissions.

The transmission frequency, receiver velocity, and required multipath tolerance all determine the most suitable transmission mode to use. Doppler spread is caused by rapid changes in the channel response due to movement of the receiver through a multipath environment. It results in random frequency modulation of the OFDM subcarriers, leading to signal degradation. The amount of Doppler spread is proportional to the transmission frequency and the velocity of movement.

![](img/47f81eeb5093bf67426e3b948e0d8952_107_0.png)

Figure 7.1 Frequency response of the subcarriers in a seven-tone OFDM signal.

The closer the subcarriers are spaced, the more susceptible the OFDM signal is to Doppler spread, so the different transmission modes in digital audio broadcasting (DAB) and HDTV allow a trade-off between the amount of multipath protection (length of the guard period) and the Doppler spread tolerance [113].

The OFDM signal has the spectrum shown in Figure 7.1. In the frequency domain, each OFDM subcarrier has several sinc-shaped frequency responses. The sinc shape has a narrow main lobe with many side lobes that decay slowly with the magnitude of the frequency shift away from the center. Each carrier has a peak at the center frequency and nulls evenly spaced with a frequency gap equal to the carrier spacing [114,115].

### 7.2 Basic Principles of OFDM

All wireless communication systems use a modulation scheme to map the information signal to a form that can be effectively transmitted over the communication channel. A wide range of modulation schemes has been developed, with the most suitable one depending on whether the information signal is an analog waveform or a digital signal.

Common analog modulation schemes include frequency modulation (FM), amplitude modulation (AM), and phase modulation (PM). Common single-carrier modulation schemes for digital communications include amplitude shift keying (ASK), frequency shift keying (FSK), phase shift keying (PSK), and quadrature amplitude modulation (QAM) [115].

OFDM is different from frequency division multiplexing (FDM) in several ways. In conventional broadcasting, each radio station transmits on a different frequency, effectively using FDM to maintain a separation between the stations. There is, however, no coordination or synchronization between each of these stations. With an OFDM transmission system such as DAB or digital video broadcasting (DVB), the information signals from multiple stations are combined into a single multiplexed stream of data. These data are then transmitted using an OFDM ensemble that is made from dense packing of several subcarriers. All the subcarriers within the OFDM signal are time and frequency synchronized to each other, allowing the interference between subcarriers to be carefully controlled. These multiple subcarriers overlap in the frequency domain but cause small effects of intercarrier interference (ICI) due to the orthogonal nature of the modulation. Typically, with FDM the transmission signals need to have a large frequency guard band between channels to prevent interference. This lowers the overall spectral efficiency. However, with OFDM, the orthogonal packing of the subcarriers greatly reduces this guard band, improving the spectral efficiency [116–122].

Each of the carriers in an FDM transmission system can use an analog or digital modulation scheme. There is no synchronization between the transmissions, so one station could transmit using FM and another in a digital form using FSK. In a single OFDM transmission system, all the subcarriers are synchronized to each other, restricting the transmission to digital modulation schemes. OFDM is symbol based and can be thought of as a large number of low-bit-rate carriers transmitted in parallel. All these carriers transmit using synchronized time and frequency, forming a single block of spectrum to ensure that the orthogonal nature of the structure is maintained. Because these multiple carriers form a single OFDM transmission, they are commonly referred to as subcarriers, with the term carrier reserved for describing the radio-frequency (RF) carrier mixing the
