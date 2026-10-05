# 4 Transforming Healthcare

# 1.2.1.1 Traditional ML auscultation algorithms

Traditional ML-based auscultation algorithms classify respiratory illnesses using audio recordings. The two stages' advances are described here before comparing stated performance on real-world repository data from the most recent relevant literature.

Respiratory acoustics evaluate jitter, shimmer, MFCCs, roll-off frequency, HNR, onset, tempo, pitch, CZR, and beat loudness [34,35]. The popular Python package Librosa can automatically extract these properties from raw data [36]. Auditory cues for respiratory disorders may be complex, subtle, and implicit, making the pretty criteria unsuitable for disease categorization. Many statistical functions extract high-order descriptors, including the mean, delta, peak, and percentiles of these features over all audio frames, excelling in related tasks [37]. Open-source feature extraction tools like SMILE [38], MIR Toolbox [39], and others may speed processing.

A decision tree, random forest, vector machine, or MLP classifier may be trained with feature representation for sound categorization and respiratory disease prediction [40]. The DT classifier classifies attributes using trees. Bootstrapping creates an RF ensemble of DTs for classifier error robustness [41]. SVM kernels cluster complex data into two in a representative, low-dimensional space. The most-cited sound classification method is SVM owing its consistent performance and flexible kernel selection. A MLP artificial neural network's activation functions and connection weights distribute properties between layers. The model properly captures input-attribute correlations with which weights are backpropagated.

Monaco et al. [42] used the public ICBHI data to perform RF, MLP, and SVM statistics on 33 acoustic characteristics. Other models showed 81%-85% accuracy, whereas MLP had 85%. Since the light model has few parameters to fit, hand-crafted feature-based classical ML classifiers may explain categorization in small audio datasets.

Pamono et al. [43] used the SVM classifier with MFCC, CZR, crest factor, energy level, and 11 features to distinguish ten patients from non-pertuss cases. Using ICBHI 2017 database data, SVM classifiers recognized COPD, pneumonia, and health patients with 99% accuracy [44].

In 2022, ML distinguished COPD patients from health controls in a private, properly verified voice dataset. Their investigation indicated that the open SMILE toolkit's 2016 feature set was more accurate [45].

# 1.2.1.2 Deep learning methods

DL and other ML methods have improved acoustic modeling by gathering more audio data [46]. Deep neural networks may sound better than