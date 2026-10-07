MFCCs are features that can be used for our model:

# # Compute MFCCs

```
mfccs = np.mean(librosa.feature.mfcc(y = emphasizedSignal, sr =\nsamplingRate, n_mfcc = 20).T,axis=0)
```

```
print('\MFCCs\n', mfccs)
```

```
print('\nShape of MFCCs:', mfccs.shape)
```

MFCCs

| -689.4513 | 13.136131 | -38.444023 | 28.491467 | -36.779255 |
| 9.32245 | -34.116608 | -1.4327488 | -19.810574 | 4.656265 |
| -11.9879 | -10.639531 | 4.917104 | -14.493996 | 1.9685544 |
| -12.012225 | 3.0940394 | -10.074612 | -1.8482265 | -6.0479755 |

Shape of MFCCs: (20,)

Let us plot the Spectrogram of the MFCCs:

```
plt.spectrogram(mfccs, Fs = samplingRate)
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

![](bbox=[0.267, 0.683, 0.732, 0.917])

Figure 6.9: Spectrogram of the MFCCs