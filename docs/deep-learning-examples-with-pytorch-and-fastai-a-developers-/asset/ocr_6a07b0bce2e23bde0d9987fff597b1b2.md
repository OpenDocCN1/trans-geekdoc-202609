![](bbox=[0.13, 0.09, 0.71, 0.38])

# 20.3 Preparing the Dataset

With fastai2audio we can do different configurations. Currently it has:

+   - BasicMelSpectrogram
+   - BasicMFCC
+   - BasicSpectrogram
+   - Voice

We’ll be using the Voice module today as this dataset just contains human voices. With a configuration we can e.g. set a frequency range.

```
cfg = AudioConfig.Voice()
cfg.f_max, cfg.sample_rate
(8000.0, 16000)
aud2spec = AudioToSpec.from_cfg(cfg)
```

We can now use this configuration to build a spectogram from the audio data.

Now we crop out the original audio file to 1000ms because all of our training data should be the same size.

```
crop1s = CropSignal(1000)
```

We can now build a pipeline. The first thing to do is aud2spec to convert the