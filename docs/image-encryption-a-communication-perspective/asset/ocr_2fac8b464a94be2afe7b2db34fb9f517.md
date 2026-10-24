![](bbox=[0.18, 0.07, 0.9, 0.55])

Figure 7.1 Frequency response of the subcarriers in a seven-tone OFDM signal.

The closer the subcarriers are spaced, the more susceptible the OFDM signal is to Doppler spread, so the different transmission modes in digital audio broadcasting (DAB) and HDTV allow a trade-off between the amount of multipath protection (length of the guard period) and the Doppler spread tolerance [113].

The OFDM signal has the spectrum shown in Figure 7.1. In the frequency domain, each OFDM subcarrier has several sinc-shaped frequency responses. The sinc shape has a narrow main lobe with many side lobes that decay slowly with the magnitude of the frequency shift away from the center. Each carrier has a peak at the center frequency and nulls evenly spaced with a frequency gap equal to the carrier spacing [114,115].

# 7.2 Basic Principles of OFDM

All wireless communication systems use a modulation scheme to map the information signal to a form that can be effectively transmitted over the communication channel. A wide range of modulation schemes has been developed, with the most suitable one depending on whether the information signal is an analog waveform or a digital signal.