The MMN results show that in-ear EEG correlates with T7 and T8 EEG signals. Furthermore, similar signal response to the theory in [39] shows that in-ear EEG could be accurately used in a standard ERP test. The validity of in-ear EEG was substantiated.

# 4.2. DEAP Data Analysis

The emotion classification using T7 and T8 signals from DEAP dataset by SVM, as described in Section 2.4, was performed. From 32 subjects consisting of 40 trials per subject each were used for the classification. Ten-fold cross-validation was applied to suppress biases. In each classification, 36 trials were used as the training set and the other four were used for the test set. Ten different sets were trained and tested for each subject.

The accuracy achieved was approximately 69.85 percent for valence classification and 76.7 percent for arousal classification. The overall accuracy for classification was approximately 58.12 percent.

Furthermore, the analysis of emotion classification using T7 or T8 channel was compared. The accuracy was approximately 71.30% for valence, 76.67% for arousal, and 57.56% for four emotions (valence and arousal combined); and the accuracy from emotion classification using T8 were approximately 70.93% for valence, 72.20% for arousal, and 57.34% for 4 emotions (valence and arousal).

The T-test result from SPSS (IBM Corp., New York, USA) indicated that there was no statistically significant difference in classification emotions between T7 and T8. The accuracy of T7 was approximately 75.56 ± 15.19 the p-value was 0.955 on both tails, less than 0.955, indicating that there was no significance difference between emotion classification using T7 and T8.

The results show that T7 and T8 could be used as a single channel for valence, arousal, and the simple emotion classification, as the classification accuracy is comparable to the multichannel classification model in [7].

# 4.3. In-Ear EEG Emotion Classification

Out of twenty-three subjects, for 10 decided to put an in-ear EEG on the left. The measurement of raw EEG data showed no statistically significant difference between EEG collected from left and right ear (p-value = 0.95).

In-ear EEG signals were recorded while subjects were watching pictures during experiment, described in Section 3.5. The EEG signal was filtered using a 4th order Butterworth filter to out out noise at 50 Hz. The signal was separated into four frequency bands that theta (4-8 Hz), beta (12-32 Hz), and Butterworth bandpass filters. Statistical parameters by Picard et al. [48] were used for signal feature extraction

Ten-fold cross-validation was used for classifying each subject's data. The SVM model described in Section 3.4 was used for classification. The signal processing and classification was performed using Matlab (The MathWorks, Inc., Natick, MA)

Binary classification was done by SVM on valence (positive or negative) and arousal (high or low). The four emotion classification was performed using the valence and arousal classification results, mapped onto the simplified valence-arousal emotional model in Figure 5. For example, positive valence and high arousal was classified as happy. Hence the simplified emotions could be classified into four groups: positive valence/high arousal, positive valence/low arousal, negative valence/high arousal, negative valence/low arousal. Classification accuracy was calculated by comparing SVM classifications with subjects' attentions. The accuracy of in-ear EEG is shown in Table 1.