# 9.3.1 Data description

The selected dataset contains three voice recording replications of the continued (sustained). The number of instances in the whole dataset is 756 and available numbers of attributes are 21. All the dataset depends upon replication consideration. The examination of dataset depends upon matching a combination of classical concepts of some subject voice recordings. It is a critical problem to identify more similar features from different subjects (table 9.1).

In most of the studies, we find Parkinson's disease identifies by many symptoms.

In this chapter we select and predict speech based dataset categories as:

+   1. Contain the repetition of one term;
+   2. Consist of different spoken terms.

Dataset is accessible from the UCI machine learning repository. We select a Parkinson's speech dataset with multiple types of sound recording for prediction.

# Table 9.1. Parkinson's dataset features and description.

| Feature name | Description |
|---|---|
| ID | Subjects are required for identification |
| Recording | How many times recording is available |
| Status | 0 = Healthy, 1 = Parkinson's disease |
| Gender | 0 = Man, 1 = Woman |
| RPDE | Recurrence period density entropy in measurement |
| DFA | Signal fractal scaling exponent of detrended fluctuation analysis in measurement |
| PPE | Pitch (area of play) period entropy in measurement |
| GNE | Glottal-to-noise excitation ratio in measurement |
| Feature name | Group | Measure |
| Jitter | ‘Local, Absolute, Rap, PPQ5 and DDP’ | Frequency |
| Pulses | ‘Number of pulses, Period: Number, Mean and Standard Derivation’ | Pitch Local Perturbation |
| Shimmer | ‘Local (Shim_loc),
dB (Shim_dB),
3-point (Shim_APQ3),
5-point (Shim_APQ5),
11-point (Shim_APQ11)’. | Amplitude perturbation quotient |
| Harmonic-to-noise ratio | 0–500 Hz (HNR05)
0–1500 Hz (HNR15)
0–2500 Hz (HNR25)
0–3500 Hz (HNR35)
0–3800 Hz (HNR38). | Frequency band |
| Mel frequency cepstral coefficient | 0–12 (MFCC0, MFCC1,..., MFCC12)
and (Delta0, Delta1,..., Delta12). | MFCC-based spectral and their derivatives |