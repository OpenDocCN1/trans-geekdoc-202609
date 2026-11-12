
| Dextrocardia | Inverted P wave |
|---|---|
| Hyperkalemia | Tall T-wave without a P wave |
| Sudden cardiac death | Asymmetrical ECG |
| Sinoatrial block | Total interruption of a cardiac cycle |
| Myocardial ischemia | Inverted T wave |

## 10.2 LITERATURE REVIEW

DeepSleepNet is a deep learning model for automatic sleep stage rating based on raw single-channel EEG [17]. The majority of the currently used techniques rely on hand-engineered components, which necessitate prior sleep analysis expertise. Few of them incorporate within the retrieved features the temporal information necessary for determining the upcoming stages of sleep, such as transition rules. In this new model, convolutional neural networks extract time-invariant characteristics and bidirectional long short-term memory learns sleep-stage transition rules from EEG epochs.

In this study [18], a method for choosing mother wavelet basis functions is presented. It is used to denoise the ECG signal in the wavelet domain while preserving peak signal amplitudes that are close to their full values. The wavelet-based denoised ECG readings maintain the original diagnostic information [19].

Graph-based attention model uses an attention technique to describe a medical idea as a composite of its ontology ancestors based on the data volume and ontology structure. The classification of ECG beats using a mixed neural network model is demonstrated in this research [20]. ECG signals were dissected using discrete wavelet transform (DWT) and statistical characteristics were derived to describe distribution.

In Ref. [21], authors used both the original and noise-reduced sets of ECG signals from a public database for our experiment. The number of instances of each of the five kinds of heartbeats in this set was artificially increased, and high-frequency noise was removed by filtering. CNN was trained utilizing enhanced data and obtained 94.03% and 93.47% accuracy in diagnosing heartbeats in original and noise-free ECGs.

## 10.3 METHODS

### 10.3.1 ECG ANALYSIS

ECG signal analysis and identification has long been a fascinating subject, and there is still ongoing study in this area. For ECG analysis, several fast and short Fourier transform approaches have been developed [22].

#### 10.3.1.1 FAST FOURIER TRANSFORM

```
X_k = \sum_{n=0}^{N-1} x_n e^{-i 2\pi k n / N} \quad (10.1)
```

Various characteristics of ECG wave patterns are presented, as well as the condition associated with each type [22] (Table 10.2).

| Abnormality | Characteristics |
|---|---|
| Bradycardia | R–R interval is greater than 1 s |
| Tachycardia | R–R interval less than 0.6 s |
| Hypercalcemia | QRS interval less than 0.1 s |

where k is an integer between 0 and N – 1 where several methods are used to compress ECG signals.

One of the most important methods is FFT. The following steps make up the entire process:

- Obtaining an input signal or ECG sample.
- Before compression can be performed, the low-frequency components of the incoming signal are filtered out.
- Inverse FFT is used to recover the original signal.

However, the FFT has a limitation in that it cannot provide information about the precise timing of frequency components. This is a disadvantage of the FFT.

#### 10.3.1.2 SHORT-TIME FOURIER TRANSFORM (STFT)

The windowed-Fourier transform, commonly known as the short-time Fourier transform (STFT), was first introduced by Dennis Gabor in 1946 and thereafter referred to as the Gabor transform [28]. This was developed so that FFT could overcome this limitation. Time and frequency information is contained in STFT. It determines the signal's sinusoidal frequency and time-varying phase content. In comparison to other methods of time-frequency analysis, the STFT-based spectrogram is an easy and efficient process. It is a simple method for slicing the desired waveform into different short segments. Then, it uses the conventional Fourier transform to analyze each segment. A window function is used on a block of information to separate it from the rest of the waveform, and then the Fourier transform is used on that piece of data.

This can be represented with a spectrogram or the STFT. The definition of STFT for a signal x(t) can be found in Equation 10.2 as follows:

```
X(τ, f) = \int x(t) w(t-τ) e^{-i 2\pi f t} dt \quad (10.2)
```

where characteristics of high frequency are represented by T. Contrary to STFT, continuous wavelet transform (CWT) is not restricted to sinusoidal analytical functions. It is possible to select localized waveforms that adhere to mathematical standards [29].

Signal x(t) CWT is provided by Equation 10.3. The STFT, where w(t) is a window with duration T and is centered at time point t, is the Fourier transform of the windowed signal x(t)w(t - \tau) [16].

```
W(a, b) = \frac{1}{\sqrt{a}} \int x(t) h(\frac{t-b}{a}) dt \quad (10.3)
```

STFT's time-frequency accuracy is not ideal. To overcome this, a better technique is used.

#### 10.3.1.3 WAVELET TRANSFORM

The y-axis scaling parameter a, and the x-axis shift parameter b are all related to the mother wavelet, h(t). To explain what the DWT is:

```
W(j, k) = \Sigma \Sigma k x(k) e(n - k) (10.4)
```

does not give information about the signal at different resolutions.

Wavelet transform, on the other hand, has a feature called “multiresolution,” which gives information about both time and frequency by letting the window size change [30].

French geophysicist Jean Morlet introduced the Wavelet in 1982.

The term “Wavelet” refers to a little wave, and research into the wavelet transform is a new method for analyzing seismic signals.

Alex Grossmann theoreticians studied the wavelet transform inverse formula [28].

An analytical tool for transitory, nonstationary, or time-varying signals, a wavelet is a tiny wave with energy concentrated in time [31].

- Wavelets have a confined frequency and temporal domain.
- Nonstationary signals like ECG exhibit frequent level changes and uneven characteristics.
- Wavelets split signals into multiresolution components.

A time-scale representation known as the wavelet transform has proven useful in several applications, most notably signal compression. The signal is divided into several scales related to frequency components, and each scale is subjected to a linear process that examines it with a specific resolution [32]. Another benefit of the wavelet technique is the availability of a variety of wavelet functions, which allows choosing the optimal function for analyzing the signal as opposed to Fourier analysis, which is limited to one feature morphology, the sinusoid.

#### 10.3.1.4 TEAGER ENERGY OPERATOR (TEO)

Independent RR interval analysis does not capture nonlinear RR interval inconsistency. Teager energy operator (TEO) represented the nonlinear behavior of the energy-tracking RR interval. The signal-generating device’s energy, amplitude envelope, and frequency are all measured. The amount of ECG energy required to produce signals with various frequencies and the same energy and amplitude might change. High-frequency signals use more energy. TEO responds to source energy, showing conduction channel instabilities and Teager energy impulses.

#### 10.3.1.5 RR INTERVAL FEATURES

RR intervals R is the ECG waveform’s peak, and RR is the interval between QRS complexes. Nonlinear ECG components vary more than linear equivalents during arrhythmia. RR intervals are easy to calculate and noise resistant. To define the heartbeat’s dynamic qualities, previous RR, average RR, post-RR, and local-RR intervals were retrieved from the RR sequence.

#### 10.3.1.6 EXTREME LEARNING MACHINE (ELM)

Extreme learning machine (ELM) is a feedforward neural network with one hidden layer and three layers: input, hidden, and output. Figure 10.3 shows ELM’s structure. ELM uses different parameters than blood pressure. The parameters for the hidden layer are produced at random, whereas the parameters for the output layer are computed analytically by applying least-squares regression. ELM approximates across the board. A network with hidden layer parameters that are generated at random has the ability to approximate any restricted noncontact piecewise continuous activation function with an error that can be arbitrarily small.

#### 10.3.1.7 DATASET

This study uses data from the PhysioNet MIT-BIH Arrhythmia and PTB Diagnostic ECG Databases [33]. We also demonstrate how data from the first database may be successfully moved to the second to train inference models. In all of our tests, the input was ECG lead II resampled to a sampling frequency of 125 Hz. The ECG recordings from 47 different individuals
