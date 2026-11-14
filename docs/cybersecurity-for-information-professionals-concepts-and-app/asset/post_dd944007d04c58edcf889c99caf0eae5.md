
![](img/74778e0ca6379f5d5e4de83ac1ff23da_264_0.png)

Figure 11.2 Human brain regions.

Humphreys, 2004; Bajada et al., 2016; Chayer & Freedman, 2001; Fogassi et al., 2005; Stuss & Knight, 2002). Each lobe controls specific functions, for example, the frontal lobe constitutes two-thirds of the human brain and controls functions associated with problem solving, behavior, some emotion as well as muscle movement and physical reactions. The parietal lobe functions are associated with orientation, recognition, perception, and appreciation of form through touch (stereognosis). The occipital lobe is responsible for vision and reading functions, and the temporal lobe correlates with visual memories, speech and language, and some perception and recognition functions. As insider threats involve different behaviors and activities associated with the insider’s brain, we deeply investigate our results and identify if there is a correlation between the detection accuracy we achieve and the brain regions. We first investigate each channel’s location to find out which area of the brain the best channels belong to. Then, we calculate the average accuracy for each region using the results from each channel in that area.

To do that, we label our 256 channels to five brain regions based on the sensor’s location on the skull: Frontal, parietal, temporal, and occipital lobe regions, we add to that the central region which is shared between the frontal and parietal lobes and we call it the “Frontal-Parietal Lobe” region.

We run our classifiers using the data of each channel separately for the entire participant’s group and sort the average detection accuracy from each channel. Table 11.7 presents the top-ten channels, which show the best average detection accuracy. The first column shows the channels number based on the Geodesic Sensor Net used in our recording. As shown, we can reach up to 82% average accuracy using only one channel (single sensor). However, all the ten best channels are located in the frontal and parietal lobes, as both lobes are associated

Table 11.7 The top-ten channels and their associated brain regions

| Channel No. | Accuracy | Brain Location |
|---|---|---|
| 132 | 82.39 | Frontal-Parietal Lobe |
| 89 | 80.75 | Parietal Lobe |
| 185 | 80.51 | Frontal-Parietal Lobe |
| 81 | 80.48 | Frontal-Parietal Lobe |
| 79 | 79.67 | Frontal-Parietal Lobe |
| 17 | 79.62 | Frontal-Parietal Lobe |
| 198 | 79.38 | Frontal Lobe |
| 45 | 79.38 | Frontal-Parietal Lobe |
| 53 | 79.28 | Frontal-Parietal Lobe |
| 186 | 79.15 | Frontal-Parietal Lobe |

with functionality that can be correlated to insider practices and behavior, such as the fluctuation of behavior, emotional state, and attention.

Furthermore, we investigate each channel and each region’s performance in detecting the malicious insider. However, the accuracy when using a single channel is much lower than using the entire group of channels (256 channels); using 256 channels in real-life scenarios seems unrealistic, as this number of channels only available with medical devices and most of the consumer-grade brain computer interface devices have only a small number of channels (1 to 16 channels).

Therefore, it is better to find the right trade-off between the detection accuracy and the applicability of the approach. To find a smaller group of channels that can provide acceptable detection accuracy, we use the best performing channels and generate a combination of a small number of channels. We start by using one channel (best channel) then combine the channel with other channels and measure the performance. We use four groups of channels: two channels, three channels, four channels, and five channels. Table 11.8 presents the average results using the different groups of channels start with one channel to five channels group. As we can see, the average accuracy improves by increasing the number of channels for all the classifiers.

By only using a group of five channels, we can reach an average detection accuracy of 95.64% using the Random Forest classifier. These results indicate that we can reduce the number of channels to five channels and still achieve an excellent detection accuracy.

Table 11.8 Average results for detecting malicious activities using small groups of channels (EEG data)

| Classifier | Number of Channels | Accuracy | TP Rate | FP Rate | F-Measure |
| :--- | :--- | :--- | :--- | :--- | :--- |
| SVM | 1 | 79.58 | 0.796 | 0.370 | 0.760 |
| Random Forests | 1 | 82.39 | 0.824 | 0.236 | 0.823 |
| k-NN | 1 | 80.53 | 0.805 | 0.240 | 0.808 |
| SVM | 2 | 85.88 | 0.858 | 0.194 | 0.848 |
| Random Forests | 2 | 89.31 | 0.893 | 0.136 | 0.893 |
| k-NN | 2 | 87.57 | 0.876 | 0.162 | 0.876 |
| SVM | 3 | 87.77 | 0.878 | 0.174 | 0.871 |
| Random Forests | 3 | 92.12 | 0.921 | 0.100 | 0.921 |
| k-NN | 3 | 90.82 | 0.908 | 0.124 | 0.908 |
| SVM | 4 | 89.99 | 0.900 | 0.138 | 0.899 |
| Random Forests | 4 | 93.51 | 0.935 | 0.086 | 0.935 |
| k-NN | 4 | 91.91 | 0.919 | 0.108 | 0.920 |
| SVM | 5 | 92.49 | 0.925 | 0.0899 | 0.925 |
| Random Forests | 5 | 95.64 | 0.956 | 0.060 | 0.956 |
| k-NN | 5 | 94.85 | 0.948 | 0.0721 | 0.949 |

## Distinguishing Malicious Activities from Benign Activities Performed Under Stress

One may argue that changes in neural activity might be due to emotional stress. To address this issue, we examined the capability of our approach in distinguishing between benign activities that are performed by users under emotional stress or high mental workload and the malicious activities of an insider. To do that, we use the second setup which contains four tasks: tasks 2 and 4 which are benign activities performed under stressful conditions, and tasks 5 and 6 which are the insider threat tasks. We evaluate the performance of the classifiers using the data with this setup. We choose to use the feature vectors extracted from five channels as using the entire group of channels will always show relatively better results. We want to make it slightly difficult for the classifiers by using less number of channels. Table 11.9 presents the results for each classifier. As shown, the three classifiers are able to distinguish between the malicious and the benign stressful activities with about 90% detection accuracy on average. However, the Random Forest classifiers show the best result with 91.92% detection accuracy on average. Using the ECG data, our approach reaches up to a 91% average detection accuracy in distinguishing between benign activities and malicious activities. Table 11.10 shows the results in more detail. As shown, the

Table 11.9 Average results for detecting malicious activities from benign activities performed under stress (EEG data)

| Classifier | Number of Channels | Accuracy | TP Rate | FP Rate | F-Measure |
|---|---|---|---|---|---|
| SVM | 5 | 89.53 | 0.90 | 0.10 | 0.89 |
| Random Forests | 5 | 91.92 | 0.92 | 0.08 | 0.92 |
| k-NN | 5 | 90.71 | 0.91 | 0.10 | 0.91 |

Table 11.10 Average results for detecting malicious activities from benign activities performed under stress (ECG data)

| Classifier | Number of Participants | Accuracy | TP Rate | FP Rate | F-Measure |
|---|---|---|---|---|---|
| SVM | 25 | 84.12 | 0.84 | 0.17 | 0.82 |
| Random Forests | 25 | 91.38 | 0.91 | 0.09 | 0.91 |
| k-NN | 25 | 91.09 | 0.91 | 0.10 | 0.91 |

Random Forest and the k-NN classifiers still show an average detection accuracy close to 91%. These results clearly show that our study does not look for stress or emotional symptoms but can differentiate between malicious and benign activities even when they involve emotion or stress.

## Analysis of Non-signal Psychophysiological Measure and Results

In this section, we analyzed the eye tracking and the mouse and keystroke dynamics data from our main experiment. The Tobii Pro eye-tracking device captures the eye gaze locations on the screen (x,y) coordinates, and produces raw data at a sampling rate of 60 times per second including the saccade, fixation locations (x,y), and pupil diameter. We analyze the raw samples to extract the features. We sample the eye-tracking raw data into 10-second time frames (epochs), each time frame representing one feature vector. We extract all possible features from the eye-tracking data: the movement features, which can be categorized as spatial and temporal features, as well as the pupil features.

We obtain a total of 38 movement features and 8 pupil features that include temporal features such as the saccade and fixation duration, the pairwise speed and acceleration, spatial features such as the pairwise distance, the distance from the
