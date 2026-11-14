ECG signals as explained, and the non-signal psychophysiological behavioral module which utilizes the eye-tracking data combined with the computer-based behaviors data (the mouse movements and keystrokes data). Then, we consolidate all measures in one framework by calculating the decisions fusion for each classifier.

For our signal module, we use the synchronized EEG and ECG extracted features from participants’ data. After extracting the features for each of the signals separately, we use our canonical correlation analysis method to fuse the pair of synchronized feature vectors and generate a new feature vector that represents the correlated features. Then, we run the classifiers for each user individually and calculate the average results. Table 11.14 presents our signal features fusion results.

As shown, the fused feature set shows a detection accuracy of up to 95.16% using the SVM classifier; this result is about 2% higher than using the EEG signal alone and about 6% higher than using the ECG data individually.

The Random Forest classifier shows an average detection accuracy of up to 95.93% which is also higher than the detection accuracy achieved by the feature set of each signal separately.

We also investigate the detection accuracy improvement on combining the features extracted from our eye-tracking data with the features derived from the mouse movement and keystroke data. For each participant, we consider both eye-tracking and mouse movement and keystroke features in building our non-signal module.

Table 11.15 shows the results of using the non-signal psychophysiological behaviors. The top part of the table shows the results for all participants. As shown, the best detection accuracy is achieved using the Random Forest classifier with up to 94.37% average detection accuracy, 0.94 true-positive rate, and 0.08 false-positive rate. The middle part of the table presents the results for participants with eyeglasses where the best average detection accuracy is about 90.81% using the Random Forest classifier. This is about 4% lower than the average detection accuracy for all participants as eyeglasses may reflect the light and impact the recording accuracy of the eye-tracking device.

# Table 11.14 Average results for detecting malicious activities using the EEG and ECG fused features set and the individual signal features set

| Classifier | EEG Accuracy | EEG TP Rate | EEG FP Rate | ECG Accuracy | ECG TP Rate | ECG FP Rate | Fused Accuracy | Fused TP Rate | Fused FP Rate |
|------------|--------------|-------------|-------------|--------------|-------------|-------------|----------------|---------------|---------------|
| SVM | 93.27 | 0.93 | 0.09 | 88.97 | 0.89 | 0.14 | 95.16 | 0.95 | 0.05 |
| Random F | 94.75 | 0.95 | 0.05 | 92.10 | 0.92 | 0.1 | 95.93 | 0.95 | 0.07 |
| k-NN | 93.16 | 0.93 | 0.09 | 91.19 | 0.92 | 0.10 | 91.57 | 0.94 | 0.07 |