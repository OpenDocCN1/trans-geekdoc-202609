# Deep Belief Networks for Intelligent Fault Diagnosis ■ 51

relationship between numbers of hidden units and classification performance of the net-work is also discussed in the next section.

In order to verify the effectiveness of the proposed approach in actual applications of fault diagnosis for induction motors, comparative experiments have been carried out, some of which are listed here:

+   1. Original vibration signals are used directly as input of soft-max function;

+   2. Original vibration signals are used directly as input of the backpropagation network with one hidden layer;

+   3. Original vibration signals are preprocessed to extract time domain features including mean value, root mean square (RMS) value, shape factor, skewness, kurtosis, impulse factor, and crest factor (Riera-Guasp, Antonino-Daviu, and Capolino 2015), then seven selected features are used as input of the BP network;

+   4. Four features including shape factor, impulse factor, crest factor, and kurtosis are used as input of the BP network,

+   5. Signals are preprocessed with 5-layer wavelet packet decomposition to get 63 sub-frequency bands, then the energy features at all sub-frequency bands are used as input of the BP network.

In addition, another comparative experiment is carried out where unprocessed raw vibration signal is used directly as the input data.

# Results and Discussion

# Results of Datasets

In this validation experiment

TABLE 3.2 Classification Rate with Different Methods

| Model | Classification Rate (%) |
| Soft-max | 17.88 |
| BP network | 80.67 |
| Seven-time domain features + BP | 85.61 |
| Four-time domain features +BP | 81.39 |
| Wavelet packet analysis + BP | 95.33 |
| DBN | 95.67 |
| FFT + DBN | 99.98 |