
## 5.3. Selected Features

In order to complete the study, we will show which features and measurements are the most frequently selected and the percentage of selection. Table 3 shows the average number of features by the GAs from each measurement and signal, considering a maximum number of selected features Nmax=40, for the different combination of signals. As we can see, the most selected measurement from the ECG is the RR. Considering the TEB, the RF and the BRV measurements present high ratios in the case of considering all signals in the combination. And the most selected measurement from the EDA is the processed measurement taken in hand.

Table 3. Average number of features selected from the measurements of different signals, with Nmax=40 features.

| Signal Measurement | ECG Arm | TEB Arm | EDA Arm | ECG EDA | TEB EDA | EDA EDA |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| ECG | 6.5 | | | | 1.5 | 3.5 | 3.8 |
| RR | 13.1 | | | | 4.9 | 8.3 | 6.0 |
| RA | 6.7 | | | | 2.4 | 3.5 | 2.1 |
| HR | 6.5 | | | | 1.5 | 2.9 | 1.1 |
| HRV | 2.8 | | | | 2.4 | 2.4 | 2.2 |
| PSD | 0.6 | | | | 0.4 | 0.7 | 0.3 |
| PSD-VLF | 0.5 | | | | 0.3 | 0.4 | 0.7 |
| PSD-LF | | | | | 0.4 | 0.5 | 0.8 |
| PSD-HF0 | 0.9 | | | | 0.4 | 0.6 | 0.9 |
| PSD-VHF | 0.6 | | | | 0.3 | 0.4 | 0.7 |
| TEB | | 8.4 | | | | | 1.6 |
| LF | | 8.9 | | | 1.4 | 3.8 | 1.5 |
| RF | | 10.1 | | | 2.0 | 1.2 | 3.3 |
| BRV | | 5.0 | | | 2.5 | 3.6 | - |
| PSD | | 1.9 | | | 0.3 | 0.6 | 0.2 |
| PSD-VLF | | 0.9 | | | 0.6 | 0.5 | 0.7 |
| PSD-LF | | 0.8 | | | 1.0 | 1.0 | 1.1 |
| PSD-HF | | 2.3 | | | 1.0 | 0.9 | - |
| PSD-VLF | | 0.8 | | 0.6 | 0.6 | 0.6 |
| EDA-Original | | | 5.6 | | 1.6 | 1.3 | 2.6 |
| EDA-Process | | | 9.8 | | 1.4 | 2.5 | 3.5 |
| EDA-LF | | | 8.9 | | 1.5 | 1.3 | 4.0 |
| EDA-HF | | | 0.7 | | 0.6 | 0.8 | 3.8 |
| EDA-PSD | | | 3.2 | | 0.5 | 0.9 | 1.4 |
| EDA-PSD-LF | | | 1.9 | | 0.4 | 0.7 | 0.5 |
| EDA-PSD-HF | | | | | 0.8 | 0.6 | 1.3 |
| EDA-Original | | | 2.8 | | 1.7 | 2.1 | 2.3 |
| EDA-processed | | | 11.6 | 3.9 | 6.0 | 6.9 | 9.2 |
| EDA-LF | | | 6.1 | 1.5 | 1.9 | 2.7 |
| EDA-HF | | | 6.6 | 1.4 | 1.7 | 2.0 | 2.2 |
| EDA-PSD | | | 1.3 | 0.2 | 0.4 | 0.7 | 0.8 |
| EDA-PSD-LF | | | 0.7 | 0.2 | 0.6 | 2.4 | 3.1 |
| EDA-PSD-HF | | | 4.6 | 0.2 | | 1.2 | 1.6 |

To go deeper into the analysis, Table 4 shows the top-40 selected features, in the case of selecting a maximum of Nmax=40 features. In this case, we show the percentage of occurrence in the three best combinations of signals: the TEB, the EDA and the ECG, and the case of using all biosignal. We can see that, in general, the mean baseline is one of the most frequent parameters.

- The most selected features from each signal: the generic mean of the HRV, the mean baseline of the RR, the length of the SD of the RR, and the DFA1 of the HR.
- From the TEB signal: the average BR of the RF, the mean baseline of the BRV, and the minimum of the BRV.
- From the EDA measured in the hand: the mean baseline of the original measurement, and the mean baseline of the processed measurement.

There are no features from the EDA measured in the hand which is used more than 40% of cases in the case of considering all possible biosignal in the GA. The most one from this signal is the skewness of the processed measurement.

Table 4. Top-40 selected features from the different signal, and percentage of occurrence with N_{max} = 40 features.

| | | Combination of Signals | | |
| --- | --- | --- | --- | --- | --- |
| | Measure | Parameter | TEB | ECG | ECG EDA |
| TEB | | Average BR | 100% | 0% | 0% |
| TEB | BRV | Mean baseline | 100% | 0% | 0% |
| EDA-hand | Original | Mean baseline | 0% | 100% | 100% |
| EDA-hand | Processed | Mean baseline | 0% | 0% | 100% |
| ECG | HRV | Geom. mean | 0% | 0% | 100% |
| ECG | RR | log(SD) | 0% | 0% | 99% |
| ECG | RR | DFA1 | 0% | 0% | 98% |
| TEB | BRV | Minimum | 0% | 0% | 94% |
| ECG | HR | Mean baseline | 0% | 0% | 93% |
| ECG | RA | Mean baseline | 0% | 0% | 68% |
| EDA-hand | LF | | 0% | 43% | 56% |
| TEB | PSD-VLF | Mean baseline | 66% | 0% | 50% |
| TEB | | | 97% | 0% | 50% |
| EDA-hand | Processed | Number | 0% | 100% | 49% |
| EDA-hand | HF | Mean baseline | 0% | 72% | 48% |
| TEB | PSD-LF | Mean baseline | 56% | 0% | 48% |
| ECG | Original | Skewness | 0% | 0% | 44% |
| ECG | RA | Mean abs. dev | 0% | 0% | 40% |
| EDA-arm | Processed | Skewness | 0% | 8% | 40% |
| TEB | PSD-HF | HF/LF | 78% | 0% | 39% |
| TEB | LF | Mean baseline | 100% | 0% | 37% |
| ECG | Original | Mean baseline | 10% | 0% | 36% |
| ECG | RR | Tr. mean | 25% | 0% | 36% |
| TEB | PSD-LF | (LF+MF) | 25% | 0% | 35% |
| EDA-hand | Processed | PNS | 0% | 35% | 35% |
| EDA-hand | Processed | NZC | 0% | 41% | 34% |
| EDA-hand | Processed | PZC | 0% | 24% | 33% |
| TEB | PSD-MF | MF/HF | 5% | 0% | 33% |
| TEB | | Mean baseline | 100% | 0% | 33% |
| LF | Percentile 75% | 93% | 0% | 32% |
| EDA-hand | Processed | Maximum | 0% | 82% | 31% |
| ECG | RR | Median | 0% | 0% | 31% |
| EDA-hand | Processed | Minimum | 0% | 47% | 27% |
| EDA-hand | Processed | Median | 0% | 100% | 26% |
| ECG | RR | Geom. mean | 0% | 0% | 25% |
| TEB | Original | Percentile 75 | 16% | 0% | 23% |

## 6. Discussion and Conclusion

Nowadays, activity recognition based on physiological signals is a relevant research field with a promising future. This paper presents an evaluation of the classification performance of different sensing modes ECG, EEG and EDA for detection of 4 different activities. The evaluation includes typical characterization features for the measured signal within each sensing mode. The characterization features included in the evaluation have been selected from a review of literature. The evaluation has been done from several perspectives, the sensing mode perspective, the type of activity targeted and other parameters related to the feature extraction and classifier. Continuous meaningful conclusion can be derived from this work:

- In most of the cases, the best results are obtained with a window length of 40 s. For the used database, the classifier that render the best results is the simplest ones, the LSCs.
- When evaluating the classification of physiological signals is better to detect the type of activity, an LSLC with the feature set obtained when applying a GA considering all signals (TEB+EEG+EDA) has the lowest classification error probability (22.2%). In the case of the system with features selected from the ECG+TEB signal, the results are quite similar (24.5%), and there is no need to detect the EDA signal, making this choice convenient for those in which we need to pay attention to the simplicity of the acquisition system. It, for the comfort of the user when there is no need to wear any gear or armband is, the performance of the activity detection system is near the same.
- In addition, for each activity separately the feature set that provides the best results significantly on the activity. While for neutral activity and mental activity, the best result is obtained with ECG+TEB+EDA feature set, for emotional activity, the best result is obtained with TEB+EDA. Finally, best result for physical activity is provided by the EDA feature-set. This may be because physical activity causes the activation of the sweat glands in a meaningful way than the rest of the activities studied. In general, the signals working independently obtain that in the case of physical activity the results are very similar using one or several signals. However, this does not happen in other cases in which the error is reduced in a remarkable way when signals are used in the training of the classifier. For other type of activities, combining sensing modes provide similar or better performance than using only one type of sensing mode.
- The GAs seems to be very useful in order to select the most relevant features, improving the results in both complexity after training and error rate. From a total of 533 features, only 40 were necessary to achieve the minimum observed error. TEB signal seems to contain some useful information than the other signals.
- The results clearly show that the activity most identifiable is physical activity. The neutral, the emotional and finally the mental activity. Due to the presence of misclassification between emotional and mental activities, can be naturally expected.
- As a possible limitation of the study, we should consider that these conclusions might be different with other electronic devices. For instance, improvement on the textile sensors or the use of gel-based classical sensors might improve the quality of the acquired signals, changing the usefulness of the measured features. Furthermore, the use of a more extensive database might overcome the generalization problems, allowing to obtain better results with more complex classifiers. In this sense, this does not try to propose a close solution by a methodology, and the comparison of the features and signals carried out might be conditioned to the actual textile technology.

As a final conclusion, we have demonstrated the suitability of the GAs to select the best features among a wide dataset, containing most of the features identified as useful in the literature. The present study allows to extract significant conclusions concerning the information in each measurement, and
