# Z. Sun et al.

# Biomedical Signal Processing and Control 112 (2026) 106528

![](bbox=[0.105, 0.068, 0.495, 0.283])

Fig. 3. Location of electrode distribution and experimental configuration. Fz (central frontal), F3 (left frontal), F4 (right frontal), F7 (left posterior frontal), F8 (right posterior frontal), Cz (central parietal), C3 (left parietal), C4 (right parietal), T3 (left temporal), T4 (right temporal), Pz (posterior parietal), P3 (left posterior temporal), T5 (left posterior temporal), and T6 (right posterior temporal).

subject, that the model subject is trained and tested on the participant’s data from different subjects. Data expansion is applied using the overlapping window method described in Section 2.4 to enhance the dataset while preserving the temporal characteristics of EEG signals.

# 2.4. Data expansion

EEG acquisition is a time-consuming task, from initial preparation to data collection. Prolonged monitoring task may also lead to fatigue. In this study’s EEG data, experiment generates 150 sets of training data. Deep learning techniques typically require large datasets and are limited in scale due to the high cost and difficulty in recruiting a sufficient number of subjects for EEG-based studies. As a result, the available data in this study is relatively small.

To address the restricted size inherent in EEG datasets, we applied an overlapping window segmentation approach that preserves temporal dependencies. Each trial lasts for 4 s, at a sampling rate of 125 Hz, yields 501 samples (the extra is obtained by including the starting point). To augment the dataset, a sliding window of 2 s with a sample size of 50 samples. Consequently, each 4-second trial is segmented into 6 overlapping segments, as calculated by: $N = rac{501}{50} + 1 = 6$. Despite this, each segment retains the same label as the original, and the timeline-graph of data expansion is shown in Fig. 4. The resultingfold resulted in increase in training samples (dataset-size amplification) without introducing artificial features or altering spectral characteristics, complying with the data integrity principles.

# 2.5. Mathematical method

# 2.5.1. Convolutional neural networks

Convolutional Neural Networks (CNNs) have emerged as a powerful tool for EEG signal analysis due to their ability to capture and learn resemble patterns in artificial neural networks and are deep learning models that widely used for visual image analysis [32]. The multi-channel, continuous, and spatial nature of EEG makes CNNs particularly suitable for extracting relevant features from this data type. A typical CNN consists of five layers: (1) input, (2) convolutional, (3)

# Data Augmentation

![](bbox=[0.145, 0.733, 0.855, 0.913])

Fig. 4. The timeline-graph of data expansion.

4