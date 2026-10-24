
![](img/47f81eeb5093bf67426e3b948e0d8952_169_0.png)

(a) E_b/N_0 = 0 dB
PSNR = 8.6932

![](img/47f81eeb5093bf67426e3b948e0d8952_169_1.png)

(b) E_b/N_0 = 5 dB
PSNR = 14.1673

![](img/47f81eeb5093bf67426e3b948e0d8952_169_2.png)

(c) E_b/N_0 = 10 dB
PSNR = 36.8018

![](img/47f81eeb5093bf67426e3b948e0d8952_169_3.png)

(d) E_b/N_0 = 15 dB
PSNR >60

Figure 9.28 AES-encrypted image with FFT-OFDM over a fading channel.

Figure 9.58 gives the output of the DCT-OFDM system for the transmission of the AES-encrypted image over a fading channel at N = 128 and G = 32.

Figure 9.59 gives the output of the DCT-OFDM system for the transmission of the RC6-encrypted image over an AWGN channel at N = 128 and G = 32.

Figure 9.60 gives the output of the DCT-OFDM system for the transmission of the RC6-encrypted image over a fading channel at N = 128 and G = 32.

Figures 9.61 to 9.63 illustrate the variation of the PSNR of a decrypted image with the SNR in the channel (E_b/N_0) for the DWT-OFDM system with different encryption algorithms in an AWGN channel for different numbers of subcarriers. These figures show that as the number of subcarriers is increased, the quality of the decrypted images is improved.

![](img/47f81eeb5093bf67426e3b948e0d8952_170_0.png)

(a) E_b/N_0 = 0 dB
PSNR = 8.3916

![](img/47f81eeb5093bf67426e3b948e0d8952_170_1.png)

(b) E_b/N_0 = 5 dB
PSNR = 9.4165

![](img/47f81eeb5093bf67426e3b948e0d8952_170_2.png)

(c) E_b/N_0 = 10 dB
PSNR = 30.9051

![](img/47f81eeb5093bf67426e3b948e0d8952_170_3.png)

(d) E_b/N_0 = 15 dB
PSNR >60

Figure 9.29 RC6-encrypted image with FFT-OFDM over an AWGN channel.

Each encryption algorithm was studied for a different number of subchannels as shown in Figures 9.64 to 9.66 without equalization and Figures 9.67 to 9.69 with ZF equalization. From these figures, it is clear, as obtained in the previous results, that equalization enhanced system performance. The best-obtained results from an encryption algorithm were for the chaotic encryption algorithm because it is a permutation-based ciphering algorithm. The DES, the AES, and the RC6 encryption algorithms provide worse PSNR performance for the DWT-OFDM system compared with the chaotic algorithm because these algorithms have a diffusion mechanism that reduces the noise immunity. On the other hand, the chaotic algorithm is more robust to noise.

![](img/47f81eeb5093bf67426e3b948e0d8952_171_0.png)

The effect of the guard interval length on the system was studied; Figures 9.70 to 9.72 illustrate the PSNR performance versus the $E_b/N_0$ for the DWT-OFDM systems with different encryption algorithms in an AWGN channel. The guard intervals utilized ranged from 0 to 32 samples. From these figures, it is clear that the PSNR performances of all encryption algorithms with the DWT-OFDM system at $G=0$ were the best compared with those with $G=16$ and 32. The chaotic encryption gives the best PSNR values.

Figures 9.73 to 9.75 illustrate the variation of the PSNR with the $E_b/N_0$ for the DWT-OFDM with $G=[0,16,32]$, with different encryption algorithms in a frequency-selective channel.

Figure 9.30 RC6-encrypted image with FFT-OFDM over a fading channel.

![](img/47f81eeb5093bf67426e3b948e0d8952_172_0.png)

**Figure 9.31** PSNR versus $E_b/N_0$ in the DCT-OFDM system for an AWGN channel with $N = 64$.

![](img/47f81eeb5093bf67426e3b948e0d8952_172_1.png)

**Figure 9.32** PSNR versus $E_b/N_0$ in the DCT-OFDM system for an AWGN channel with $N = 512$.

![](img/47f81eeb5093bf67426e3b948e0d8952_173_0.png)

Figure 9.33 PSNR versus E_b/N_0 in the DCT-OFDM system for an AWGN channel with N = 1024.

![](img/47f81eeb5093bf67426e3b948e0d8952_173_1.png)

Figure 9.34 PSNR versus E_b/N_0 in the DCT-OFDM system for a Rayleigh channel with N = 64 without PSE and equalization.

![](img/47f81eeb5093bf67426e3b948e0d8952_174_0.png)

**Figure 9.35** PSNR versus $E_b/N_0$ in the DCT-OFDM system for a Rayleigh channel with $N = 512$ without PSE and equalization.

![](img/47f81eeb5093bf67426e3b948e0d8952_174_1.png)

**Figure 9.36** PSNR versus $E_b/N_0$ in the DCT-OFDM system for a Rayleigh channel with $N = 1024$ without PSE and equalization.

![](img/47f81eeb5093bf67426e3b948e0d8952_175_0.png)

**Figure 9.37** PSNR versus E_b/N_0 in the DCT-OFDM system for a Rayleigh channel with N = 64 with PSE and equalization.

![](img/47f81eeb5093bf67426e3b948e0d8952_175_1.png)

**Figure 9.38** PSNR versus E_b/N_0 in the DCT-OFDM system for a Rayleigh channel with N = 512 with PSE and equalization.

![](img/47f81eeb5093bf67426e3b948e0d8952_176_0.png)

**Figure 9.39** PSNR versus *E_b/N_0* in the DCT-OFDM system for a Rayleigh channel with *N* = 1024 with PSE and equalization.

![](img/47f81eeb5093bf67426e3b948e0d8952_176_1.png)

**Figure 9.40** PSNR versus *E_b/N_0* in the DCT-OFDM system for an AWGN channel with *G* = 0.

![](img/47f81eeb5093bf67426e3b948e0d8952_177_0.png)

**Figure 9.41** PSNR versus E_b/N_0 in the DCT-OFDM system for an AWGN channel with G = 16.

![](img/47f81eeb5093bf67426e3b948e0d8952_177_1.png)

**Figure 9.42** PSNR versus E_b/N_0 in the DCT-OFDM system for an AWGN channel with G = 32.

![](img/47f81eeb5093bf67426e3b948e0d8952_178_0.png)

**Figure 9.43** PSNR versus E_b/N_0 in the DCT-OFDM system for a Rayleigh channel with G = 0 without PSE and equalization.

![](img/47f81eeb5093bf67426e3b948e0d8952_178_1.png)

**Figure 9.44** PSNR versus E_b/N_0 in the DCT-OFDM system for a Rayleigh channel with G = 16 without PSE and equalization.

![](img/47f81eeb5093bf67426e3b948e0d8952_179_0.png)

**Figure 9.45** PSNR versus *E_b/N_0* in the DCT-OFDM system for a Rayleigh channel with *G* = 32 without PSE and equalization.

![](img/47f81eeb5093bf67426e3b948e0d8952_179_1.png)

**Figure 9.46** PSNR versus *E_b/N_0* in the DCT-OFDM system for a Rayleigh channel with *G* = 0 with PSE and equalization.

![](img/47f81eeb5093bf67426e3b948e0d8952_181_0.png)

**Figure 9.49** PSNR versus E_b/N_0 in the DCT-OFDM system with ZP and HGI for a Rayleigh channel with N = 128 and G = 32 without PSE and equalization.

![](img/47f81eeb5093bf67426e3b948e0d8952_181_1.png)

**Figure 9.50** PSNR versus E_b/N_0 in the DCT-OFDM system with ZP and HGI for a Rayleigh channel with N = 128 and G = 32 with PSE and equalization.

![](img/47f81eeb5093bf67426e3b948e0d8952_182_0.png)

**Figure 9.51** Original image with DCT-OFDM over an AWGN channel.

Without PSE and equalization, it is shown that fading disrupts the PSNR performance of the DWT-OFDM systems regardless of the encryption algorithm. However, Figures 9.76 to 9.78 show that, with PSE and equalization, the PSNR performances of all systems were better than those without PSE and equalization.

The DES, AES, and RC6 provide lower PSNR performance for the DWT-OFDM system than the chaotic algorithm because these algorithms have a diffusion mechanism that highly reduces the noise immunity. On the other hand, the chaotic algorithm was more robust to noise.

The different types of guard intervals were studied. A comparison study between the HGI and the ZP guard interval with the different encryption algorithms in a frequency-selective channel is illustrated in Figures 9.79 and 9.80. CFO compensation was performed. The PSNR performance of the ZP-OFDM systems was slightly better than that of the HGI-OFDM systems.

![](img/47f81eeb5093bf67426e3b948e0d8952_183_0.png)

(a) E_b/N_0 = 0 dB
PSNR = 16.7843

![](img/47f81eeb5093bf67426e3b948e0d8952_183_1.png)

(b) E_b/N_0 = 5 dB
PSNR = 23.2367

![](img/47f81eeb5093bf67426e3b948e0d8952_183_2.png)

(c) E_b/N_0 = 10 dB
PSNR = 27.9452

![](img/47f81eeb5093bf67426e3b948e0d8952_183_3.png)

(d) E_b/N_0 = 15 dB
PSNR = 29.3708

Figure 9.52 Original image with DCT-OFDM over a fading channel.

Figure 9.81 gives the output of the DWT-OFDM system for the transmission of the original Cameraman image over an AWGN channel at N = 128 and G = 32.

Figure 9.82 gives the output of the DWT-OFDM system for the transmission of the original Cameraman image over a fading channel at N = 128 and G = 32.

Figure 9.83 gives the output of the DWT-OFDM system for the transmission of the chaotic-encrypted image over an AWGN channel at N = 128 and G = 32.
