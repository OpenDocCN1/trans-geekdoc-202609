
![](img/6554116edbb19a8210b75a29243fd6ec_192_0.png)

FIGURE 10.1 Sensor data after sub-activity-related abnormal behavior is generated.

activity, the sensor $M_{26}$ is repeated more than usual, which can be used to emulate the usage of a computer. A snapshot for sub-activity-related abnormal behavior synthesis is depicted in Figure 10.1, where ONabn shows the inserted sensor activations.

Moreover, an addleror set of WSU dataset is used because it reflects the confusion and forgetting anomaly types such as forgetting to turn water tap off.

```
Algorithm 10.2: Simulation of Sub-Activity-Related Abnormal Behavior

**Input:** Sequence of $S$ of sensor activations of an activity $A$ such as $S = <a_1, a_2, ..., a_n>$. A sensor type $M$ that is involved in activity $A$. $A$ and $M$ are carefully chosen to reflect a dementia-related abnormal behavior (e.g. sensor $M_6$ in activity *working*). 
**Output:** $S = <a_1, M, a_2, M, a_3, ..., M, a_n>$
while true do
    Choose a random position $p$ in $S$
    Insert $M$ into $S$ at position $p$
end
```

## 10.5 SPATIO-TEMPORAL ACTIVITY RECOGNITION AND ABNORMAL BEHAVIOR DETECTION

RNNs have shown promising results in some sequence modeling problems such as speech recognition [61], machine translation [62,63], handwriting recognition and generation or translation, language modeling and protein secondary structure prediction [64]. Daily life activities can be modelled as sequences where sensor activations form time-series data. Thus, modeling activity recognition as a sequence labelling problem makes RNNs an appealing approach. In the present study, we exploit RNNs to model activities using their temporal information and then detect abnormal behavior deviating from normal patterns. Also, CNNs are good at encoding spatial information into account and extracting their own features. Thus, in this research, CNNs are used to encode the neighbourhood information of the sensors to recognise daily life activities and then detect abnormal behavior.

The following steps are applied:
- (1) A sliding-window approach inspired by Ref. [20] is applied to segment daily life sequences into time-slice chunks.
- (2) Time-slices are mapped onto features as described in Ref. [20].
- (3) Then, three variations of RNNs, namely Vanilla, GRU and LSTM and CNNs are used to model and classify activities.
- (4) Lastly, these classifiers are used to flag abnormal behavior based on the classification confusion probability.

The order of sensor readings is important to take the spatial information into account. We use a sliding window approach to segment data into activity instances. We applied the same sliding window approach as in Ref. [20] to extract the sensor reading chunks, which are used as input to RNNs and CNNs. The window size is based on time rather than the number of sensor events (one sensor reading tuple is named as the sensor event). Different time windows can be used such as 1-minute slices, 60-second slices and so on. If 1-minute windows are used, all sensor readings which are in that minute are extracted in a window. These windows are mapped into specific representations as described in the following.

### 10.5.1 Sensor Data Representation

Raw sensor readings are mapped to the following three representations using a sliding window.

- **Binary**: In this feature, sensors activated in a time-window are assigned to 1, while the ones not activated are assigned to 0.
- **Change-point**: In this feature, in a time-window, if a sensor changes from ON to OFF, or from OFF to ON, it is assigned to 1, while it is assigned to 0 if its state remains the same.
- **Last-fired**: In this feature, only one sensor is assigned to 1, indicating the last sensor which is fired last in a time-window.

### 10.5.2 Abnormal Behavior Detection

Abnormal behavior is detected as follows: The RNNs and CNNs are trained using the train set and then test instances are fed into these models to be classified. The classification confidence scores are used to decide if the test instances are normal or abnormal activities. For this purpose, a threshold, which is the mean of the confidence scores of training instances for each class, is used to decide the abnormality.

In the next section, the Kasteren dataset will be used to evaluate RNNs and Aruba dataset will be used to test the ability of CNNs as well as their combination with LSTM RNNs.

### 10.5.3 Experiments

In this study, RNN and CNN implementations from Theano [66] and Keras libraries [65] are used. The train and test instances with a batch size of 20 are used and an Adam optimiser is chosen. RNNs and CNNs are compared with the traditional machine learning methods such as SVM (WEKA implementation with default parameters), NB, HMM, HSMM and CRF (implementations of Ref. [20]).

The evaluation metrics, precision, recall, F-measure and accuracy (see Eqs. 10.1–10.4) are chosen to test the success of the proposed methods on activity recognition. Here, the following abbreviations are used: TP: True Positive, TT: Total True labels, TI: Inferred Labels, N: the number classes in the dataset and Total: total number of instances in the dataset.

```
Precision = 1/N(∑_{i=1}^{N} Tpi/ Tti) (10.1)

Recall = 1/N(∑_{i=1}^{N} Tpi/ Tti) (10.2)

F-measure = 2 × Precision × Recall/ (Precision + Recall) (10.3)

Accuracy = ∑_{i=1}^{N} Tpi/ Total (10.4)
```

Sensitivity (True Positive Rate) and Specificity (True Negative Rate) metrics (Eqs. 10.5 and 10.6) are used to evaluate the proposed method's success in abnormal behavior detection. A True Positive Rate (TPR) reflects the ability to detect true abnormal behavior, while a True Negative Rate (TNR) measures the ability to identify normal behavior.

```
Sensitivity = TP/(TP + FN) (10.5)

Specificity = TN/(TN + FP) (10.6)
```

### 10.5.4 Results with Recurrent Neural Networks

For the RNN experiments, Kasteren datasets are divided into train and test sets following a cross-validation approach on a daily basis so that one day data are used for testing while the remaining days are used for training and validation (10% of them are used for validation). The success rate is reported by averaging over the days. Train data are fed into the classifier using batches of 10 in 500 epochs. The RNN network has two layers of 30 and 50 hidden neurons and each time, 25 time-slices are given as an instance. These parameters are set empirically. The results are compared with HMM, HSMM, CRF and NB results of Ref. [20] as depicted in Tables 10.2–10.4.

TABLE 10.2 Activity Recognition Results for Household A of the Van Kasteren Dataset

| Model | Feature | Precision | Recall | F-Measure | Accuracy |
|---|---|---|---|---|---|
| NB | Binary | 48.3 ± 17.7 | 42.6 ± 16.6 | 45.1 ± 16.9 | 77.1 ± 20.8 |
| | Change-point | 52.7 ± 17.5 | 43.2 ± 18.0 | 47.1 ± 17.2 | 55.9 ± 18.8 |
| | Last-fired | 67.3 ± 17.2 | 64.8 ± 14.6 | 65.8 ± 15.5 | 95.3 ± 2.8 |
| HMM | Binary | 37.9 ± 19.8 | 45.5 ± 19.5 | 41.0 ± 19.5 | 59.1 ± 28.7 |
| | Change-point | 70.3 ± 16.0 | 74.3 ± 13.3 | 72.0 ± 14.2 | 92.3 ± 5.8 |
| | Last-fired | 54.6 ± 17.0 | 69.5 ± 12.7 | 60.8 ± 14.9 | 89.5 ± 8.4 |
| HSMM | Binary | 39.5 ± 18.9 | 48.5 ± 19.5 | 43.2 ± 19.1 | 59.5 ± 29.0 |
| | Change-point | 70.5 ± 16.0 | 75.0 ± 12.1 | 72.4 ± 13.7 | 91.8 ± 5.9 |
| | Last-fired | 60.2 ± 15.4 | 73.8 ± 12.5 | 66.0 ± 13.7 | 91.0 ± 7.2 |
| CRF | Binary | 59.2 ± 18.3 | 56.1 ± 17.3 | 57.2 ± 17.5 | 89.8 ± 8.5 |
| | Change-point | 73.5 ± 16.6 | 68.0 ± 16.0 | 70.4 ± 15.9 | 91.4 ± 5.6 |
| | Last-fired | 66.2 ± 15.8 | 65.8 ± 14.0 | 65.9 ± 14.6 | 96.4 ± 2.4 |
| Vanilla | Binary | 46.5 ± 17.7 | 64.8 ± 16.2 | 53.5 ± 16.3 | 86.8 ± 10.6 |
| | Change-point | 46.3 ± 19.5 | 63.8 ± 16.4 | 53.2 ± 17.9 | 61.4 ± 16.4 |
| | Last-fired | 61.9 ± 19.1 | 74.3 ± 12.8 | 67.2 ± 16.4 | 95.5 ± 3.4 |
| LSTM | Binary | 50.8 ± 18.4 | 63.9 ± 16.5 | 56.2 ± 17.1 | 86.7 ± 10.5 |
| | Change-point | 46.8 ± 18.7 | 63.6 ± 14 | 53.5 ± 16.7 | 61.4 ± 16.4 |
| | Last-fired | 63.7 ± 19.9 | 73.9 ± 16.8 | 68.1 ± 18.2 | 96.7 ± 2.6 |
| GRU | Binary | 47.3 ± 18.7 | 69.1 ± 14.9 | 55.4 ± 16.5 | 86.6 ± 10.7 |
| | Change-point | 42.9 ± 19 | 65.0 ± 15.3 | 51.0 ± 17.1 | 61.4 ± 16.4 |
| | Last-fired | 61.8 ± 16.3 | 80.6 ± 11.5 | 69.5 ± 14.0 | 96.1 ± 2.5 |
| SVM | Binary | 45.6 ± 17.9 | 69.1 ± 15.9 | 54.2 ± 15.9 | 85.4 ± 10.4 |
| | Change-point | 40.3 ± 19.1 | 63.4 ± 14.6 | 48.6 ± 17.0 | 55.9 ± 18.7 |
| | Last-fired | 58.6 ± 16.2 | 77.2 ± 14.0 | 66.3 ± 14.9 | 96.1 ± 2.4 |

TABLE 10.3 Activity Recognition Results for Household B of the Van Kasteren Dataset

| Model | Feature | Precision | Recall | F-Measure | Accuracy |
|---|---|---|---|---|---|
| NB | Binary | 33.6 ± 10.9 | 32.5 ± 8.4 | 32.4 ± 8.9 | 80.4 ± 18.9 |
| | Change-point | 40.9 ± 7.2 | 38.9 ± 5.7 | 39.5 ± 5.9 | 67.8 ± 18.6 |
| | Last-fired | 43.7 ± 8.7 | 44.6 ± 7.2 | 43.3 ± 4.8 | 86.2 ± 13.8 |
| HMM | Binary | 38.8 ± 14.7 | 44.7 ± 13.4 | 40.7 ± 12.4 | 63.2 ± 24.7 |
| | Change-point | 48.2 ± 17.2 | 63.1 ± 14.1 | 53.6 ± 16.5 | 81.0 ± 14.2 |
| | Last-fired | 38.5 ± 15.8 | 66.6 ± 19.5 | 41.8 ± 17.1 | 48.4 ± 26.9 |
| HSMM | Binary | 37.4 ± 16.9 | 44.6 ± 14.3 | 39.9 ± 14.3 | 63.8 ± 24.2 |
| | Change-point | 49.8 ± 15.8 | 65.2 ± 13.4 | 55.7 ± 14.6 | 82.3 ± 13.5 |
| | Last-fired | 40.8 ± 11.6 | 53.3 ± 10.9 | 45.8 ± 11.2 | 67.1 ± 24.8 |
| CRF | Binary | 35.7 ± 15.2 | 40.6 ± 12.0 | 37.5 ± 13.7 | 78.0 ± 25.9 |
| | Change-point | 48.3 ± 8.3 | 51.5 ± 8.5 | 49.7 ± 7.9 | 92.9 ± 6.2 |
| | Last-fired | 46.9 ± 12.5 | 47.8 ± 12.1 | 46.6 ± 12.9 | 89.2 ± 13.9 |
| Vanilla | Binary | 26.7 ± 13.5 | 46.9 ± 24.8 | 32.5 ± 17.9 | 65.2 ± 34.7 |
| | Change-point | 39.6 ± 8 | 62.4 ± 15.3 | 48.3 ± 10.2 | 76.9 ± 13.9 |
| | Last-fired | 41.2 ± 12.3 | 64.4 ± 17.8 | 49.7 ± 13.6 | 87.9 ± 13.1 |
| LSTM | Binary | 29.1 ± 12.0 | 44.0 ± 22.0 | 33.9 ± 16.2 | 63.5 ± 32.7 |
| | Change-point | 40.0 ± 11.2 | 59.0 ± 16.4 | 47.5 ± 12.9 | 76.8 ± 14.2 |
| | Last-fired | 40.8 ± 10.7 | 60.1 ± 16.3 | 48.2 ± 12.3 | 87.2 ± 13.2 |
| GRU | Binary | 28.5 ± 15.9 | 36.3 ± 17.2 | 31.4 ± 16.2 | 64.5 ± 32.1 |
| | Change-point | 37.7 ± 7.6 | 53.5 ± 9.2 | 44.9 ± 7.1 | 76.4 ± 11.5 |
| | Last-fired | 41.7 ± 13.2 | 50.9 ± 17.9 | 47.5 ± 14.6 | 87.0 ± 12.9 |
| SVM | Binary | 39.6 ± 10.9 | 58.5 ± 17.4 | 46.7 ± 12.9 | 81.6 ± 18.5 |
| | Change-point | 32.3 ± 6.5 | 53.6 ± 7.5 | 40.0 ± 6.2 | 67.9 ± 28.5 |
| | Last-fired | 36.4 ± 5.4 | 54.0 ± 10.4 | 43.5 ± 6.6 | 86.2 ± 14.9 |
