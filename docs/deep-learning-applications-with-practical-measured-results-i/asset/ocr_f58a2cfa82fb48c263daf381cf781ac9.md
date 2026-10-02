where X(k) is the time series.

More detailed calculations include:

```
X(kf1) = DFT [x(nTs)] = \sum_{n=0}^{N-1} X(nTs) e^{-j(2\pi/N)nk},  (17)

f1 = 1/T1',  (18)

Ts = T1/N',  (19)
```

where T1 is signal time, f1 is the frequency interval, N is the number of signal sampling, and Ts is the signal sampling interval time.

The amplitude spectrum analysis of these datasets is performed, so as to check the existence of repetitive patterns in the datasets. The hourly PM2.5 and ISO-NE data of test set and predictions are plotted in the frequency domain as shown in Figures 10 and 11 separately, where Freq is the frequency with a unit of 1/Hour and Am is the amplitude in dB. Sampling frequency is set to 8760 (the same as test set time variable length). Sampling frequency is set to 8760 (the same as the time variable length set by the test), which ensures that the frequency and time correspond to each other numerically. Both figures show that frequency domain is irregular continuous waveform indicating a non-periodic of PM2.5 and ISO-NE datasets. As can be clearly seen, PM2.5 data have no periodicity, which brings great errors to accurate prediction. Since the ISO-NE data change regularly from 1 to 1000 h, the prediction effect is the best.

![](bbox=[0.18, 0.52, 0.8, 0.66])

![](bbox=[0.18, 0.68, 0.8, 0.8])

Figure 10. Amplitude Spectrum of Beijing PM2.5 Dataset. Freq: the hourly data in frequency domain (1/Hour); Am: the amplitude of data in both datasets.