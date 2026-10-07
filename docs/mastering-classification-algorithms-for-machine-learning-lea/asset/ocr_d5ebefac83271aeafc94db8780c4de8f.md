# Mastering Classification Algorithms for Machine Learning

Now we will compute the Chroma features.

In Western music, chroma feature or chroma gram closely relates to the twelve pitch classes. Chroma-based features, also called “pitch class profiles”, are a powerful tool for analyzing music whose can be meaningfully categorized (often into twelve categories) and whose tuning approximates the equal-tempered scale. One main property of chroma features is that they capture harmonic and melodic characteristics of music while being robust to changes in timbre and instrumentation.

We can extract chroma from speeches to gather information about the pitch.

The parameter n_fft is the length of the FFT window.

The parameter hop_length is the number of samples between successive frames. Chroma features are the features that can be used in our model:

```
chroma = np.mean(librosa.feature.chroma_stft(S = stft, sr = samplingRate,
n_fft = 2048, hop_length = 1024).T, axis = 0
```

```
print('Chroma Features\n', chroma)
```

```
print('\nShape of Chroma Features:', chroma.shape)
```

Chroma Features

```
[0.51026803 0.4963213 0.49816346 0.51692945 0.5742091 0.6114398 0.64996433 0.7051374 0.75990446 0.73575807 0.574072 ]
```

Shape of Chroma Features: (12,)

Let us plot the Spectrograms of the chroma features:

```
plt.specgram(chroma, Fs = samplingRate)
```

```
plt.xlabel('Time')
```

```
plt.ylabel('Frequency')
```

```
plt.show()
```