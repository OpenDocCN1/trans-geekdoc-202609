# 10 Featured Examples

![](bbox=[0.218, 0.146, 0.781, 0.483])

# ### Create Time-Frequency Representations

After making the folders, create time-frequency representations of the ECG signals. These representations are called scalograms. A scalogram is the absolute value of the CWT coefficients of a signal.

To create the scalograms, precompute a CWT filter bank. Precomputing the CWT filter bank is the preferred method when using the CWT of many signals using the same parameters.

Before generating the scalograms, examine one of them. Create a CWT filter bank using cfilterbank for a signal with 1000 samples. Use the filter bank to take the CWT of the first 1000 samples of the signal and obtain the scalogram from the coefficients.

```
Fs = 120;
fb = cfilterbank('Signallength',1000,...
    'SamplingFrequency',Fs,...
    'VoicesPerOctave',12);
sig = ECGData.Data(1:1000);
[cfs,frq] = wt(fb,sig);
t = (0:999)/Fs;figure;pcolor(t,frq,abs(cfs))
set(gca,'yscale','log');shading,interp;axis tight
title('Scalogram');xlabel('Time (s)');ylabel('Frequency (Hz)')
```

10-158