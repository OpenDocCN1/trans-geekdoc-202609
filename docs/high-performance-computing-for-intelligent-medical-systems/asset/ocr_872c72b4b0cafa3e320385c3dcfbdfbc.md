![](bbox=[0.156, 0.113, 0.844, 0.295])

Figure 1.1. Flowchart of the proposed methodology.

# 1.2.1 Dataset

The ECG dataset downloaded from smart health for assessing the risk of events from the physionet website (https://physionet.org/content/shareedb/1.0.0/). It contains nominal 24-h ECG holter recording of 139 subjects, and available length of ECG recording of each subject is approximately 2 h 10 min: 12 s. ECG signal of each subject is recorded from three channels III, V3, and V5, and sampled at a sampling frequency of 128 Hz, with 8-bit resolution. It contains 49 females of average age 55 ± 5 years and 90 males having average age 72 ± 7 years, respectively. Out of 139 subjects, 17 were identified as high-risk HPT and 122 were identified as normal [9]. In this chapter, ECG recordings are segmented into 2-min epochs. Figure 1.2 represents the three lead ECG recordings of normal and HPT subject.

# 1.2.2 Flexible analytic wavelet transform

The nature of ECG signal is nonlinear and nonstationary due to which many difficulties are faced in the time-frequency analysis of a signal. Hence this study considered FAWT to decompose the ECG signal into sub-bands. FAWT is the well-structured technique for decomposition of non-stationary and non-linear signal. FAWT contains Hilbert transform pairs of atoms for analyzing positive and negative structure, therefore, it is most suitable for nonstationary signal processing. It uses a bank of filters to decompose a signal into sub bands. An iterative filter bank is used for signal decomposition. It is a combination of two high pass filters and one low pass filter. FAWT low pass and high pass channels are allowed arbitrary sampling rate. In FAWT dilation factor, quality factor and the redundancy can be easily specified by the user, due to this flexibility it allows fast implementation with perfect reconstruction of a finite length signal [44].

The following variables are used in FAWT: low pass up-sampling ($s_1$), low pass down-sampling ($s_2$), high pass up-sampling ($s_3$), high pass down-sampling ($s_4$), controlling parameter $\beta$, quality factor and redundancy rate ($R$).