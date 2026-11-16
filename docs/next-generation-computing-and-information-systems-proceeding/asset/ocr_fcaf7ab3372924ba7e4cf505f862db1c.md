In this study, we used deep learning classifiers for the classification of emotions based on the EEG signals. Arousal, Valence, Liking and Dominance are the emotions that will be used in our study. Convolutional Neural Network model is developed using the programming language Python, the Keras API, and the framework called TensorFlow.

# 3 MATERIALS AND SUGGESTED APPROACH

This section will include our suggested method of recognizing the emotions as well as the dataset that was used in the study.

# 3.1 Overview of the dataset

A cutting-edge dataset, DEAP [Koelstra et al. 2012], is discussed in this paper, which includes EEG signals that were captured on the scalp using 32 electrodes. The electrical activity of the brain is measured with the help of EEG, which provides information about emotional reactions. Physiological signals including conductance of the skin, respiration, and heart rate, temperature are also included in the dataset. Additional details regarding the participant's emotions may be revealed by these signals. A collection of 40 video clips intended to illicit different emotions, such as fear, anger, sadness, and happiness, were shown to the participants. Following a screening of every movie, the participants self-reportedly rated their emotional experiences. For tasks involving emotion classification and regression, these ratings serve as the ground truth. In the domains of affective computation, recognizing emotions, and brain-computer interfaces, the DEAP dataset is extensively used. A snapshot of the DEAP dataset is given in Figure 1.

![](bbox=[0.21, 0.46, 0.8, 0.71])

Figure 1. Synopsis of DEAP dataset.

The DEAP dataset's EEG data is 40 x 40 x 8064 in shape as shown in Figure 2. The breakdown of this is as follows:

+   - 40: This is generally the total number of individuals or participants in the research.
+   - 40: This indicates the total number of electrodes or channels that were utilized to record each participant's EEG signals.
+   - 8064: This is the total amount of points of data in the EEG signal for each channel, and it relates to how long the EEG data was captured.