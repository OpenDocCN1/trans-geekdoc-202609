audio-tensor data into spectograms.
pipe = Pipeline([AudioTensor.create, crop1s, aud2spec]) If we go through some files, we see we get a different spectogram for each of them.

```
for fn in fnames[:3]:
audio = AudioTensor.create(fn)
audio.show()
pipe(fn).show()
```

Your browser does not support the audio element.

![](bbox=[0.11, 0.3, 0.71, 0.6])