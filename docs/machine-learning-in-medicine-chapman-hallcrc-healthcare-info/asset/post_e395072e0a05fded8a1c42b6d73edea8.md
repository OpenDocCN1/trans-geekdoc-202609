
## TABLE 10.7 Activity Recognition Results on the Aruba Dataset

| Model | Precision (%) | Recall (%) | F-Measure (%) | Accuracy (%) |
| :--- | :--- | :--- | :--- | :--- |
| NB | 42.87 | 61.04 | 50.36 | 84.37 |
| HMM | 43.66 | 72.03 | 54.36 | 77.90 |
| HSMM | 43.97 | 71.56 | 54.47 | 77.98 |
| CRF | 50.24 | 52.83 | 51.50 | 88.58 |
| LSTM | 38.65 | 41.29 | 39.92 | 89.00 |
| CNN-1D | 31.42 | 36.78 | 33.89 | 87.50 |
| CNN-2D | 46.84 | 41.68 | 44.11 | 89.67 |
| CNN-2D + LSTM | 51.20 | 50.55 | 50.87 | 89.72 |

results (77.90% and 77.98% respectively). NB gives a better accuracy result (84.37%) than HMM and HSMM but it results in lower precision (42.87%) and recall (61.04%) rates. Although HMM and HSMM give the best recall rates (72.03% and 71.56%), they fail in giving good precision rates (43.66% and 43.97% respectively). We see that the CNN-1D network has an accuracy of 87.50% while it fails in high precision (31.42%) and recall (36.78%) values. CNN-1D extracts features on temporal dimension, it takes temporal information within a time-slice chunk into account but on the other hand, it ignores the relationship between sensors since it doesn't do convolution on the feature dimension. Thus, it doesn't learn class-specific feature maps to differentiate between different classes resulting in high accuracy (87.50%) but low precision and recall. When 2D convolution is used, both temporal information and spatial information are considered and the networks learn more informative features. Thus, it gains the ability to learn class-specific features, which results in higher precision and recall values (46.84% and 41.68%) and high accuracy results (89.67%). CNNs cannot remember the previous and the next inputs, but feeding the feature maps into an LSTM layer helps us process the temporal dimension further. As a result, CNN-2D + LSTM networks achieve a precision rate of 51.20%, a recall rate of 50.55% and an accuracy of 89.72%.

The learnt feature patterns are depicted in Figure 10.3. As the features are going to the next layers, it is seen that noise is reduced and features become clearer. The feature dimension is shown on the $x$-axis and the time axis is depicted on the $y$-axis while the white pixels show the activations.

Results on the Aruba dataset show that classifiers most successfully detect the instances of leave home and enter home activities since they are the only activities involving door sensors, thus they are not confused with any other activities. Moreover, meal preparation activity is confused with

![](img/6554116edbb19a8210b75a29243fd6ec_202_0.png)
![](img/6554116edbb19a8210b75a29243fd6ec_202_1.png)
![](img/6554116edbb19a8210b75a29243fd6ec_202_2.png)
FIGURE 10.3 a) First layer activations b) Second layer activations c) Flatten layer activations.

wash dishes activity most of the time since they involve the same kind of sensors and they both take place in the kitchen. Also, housekeeping activity is generally confused with work activity since they may take place in the same room and may involve the same sensors.

## TABLE 10.8

| Model | Aruba Modified Sensitivity (%) | Aruba Modified Specificity (%) | WSU Sensitivity (%) | WSU Specificity (%) |
| :--- | :--- | :--- | :--- | :--- |
| NB | 99.33 | 33.89 | 46.17 | 98.42 |
| HMM | 45.54 | 27.71 | 100 | 50.55 |
| HSMM | 100 | 35.61 | 100 | 42.89 |
| CRF | 100 | 66.03 | 47.87 | 72.17 |
| LSTM | 98.67 | 75.48 | 86.50 | 77.89 |
| CNN-2D | 85.33 | 33.89 | 88.70 | 67.46 |

In the third experiment, abnormal activity detection is performed firstly on a modified Aruba set. As a representative of CNN networks, we present the result only with the CNN-2D network in order to see the effect of CNNs individually. After training the models with normal behavior, a test set that included abnormal behavior is introduced to the classifier and activity instances that are assigned a label with low confidence values are flagged as abnormal. In Table 10.8, we see that the highest specificity is achieved by LSTM networks giving an accuracy of 75.48% (and a sensitivity rate of 98.67%). Although NB, HMM and HSMM models give higher sensitivity rates (99.33%, 100% and 100% respectively), the specificity rates are smaller (33.89%, 27.71% and 35.61% respectively). HMM gives the worst results (a sensitivity rate of 45.54% and a specificity rate of 27.72%). CNN-2D gives a sensitivity rate of 85.33% and a specificity of 33.89%. This shows that LSTMs are more suitable to detect repetition and order-related abnormal activities since they can relate current input with the upcoming ones what CNN cannot do.

The second part of anomaly detection experiments is performed on the WSU testbed. We extracted 30-second time-slice chunks from sensor readings from WSU. This dataset is not collected in a daily life scenario; thus, sensor readings are not in a sequential order. The sensor readings are available only for activities labelled in the dataset. The adnormal set is used as a training set and the adderror set is used as a test dataset. The aim here is to measure how successful the classifiers are to detect the anomalies given the normal dataset. The results in Table 10.8 indicate that the highest sensitivity rate is given by HMM and HSMM (both 100%), while HMM gives a specificity rate of 50.55% and HSMM achieves a specificity of 42.89%. The highest sensitivity rate is achieved by the CNN-2D classifier (86.70%), but LSTM gives a very close sensitivity rate (86.50%) and a higher specificity rate (77.89%) where CNN-2D achieves a specificity rate of 67.47% only. In Ref. [17], the authors present their results as follows. The number of

correctly detected activities are 95 for adlnormal and 76 for adlerro, both out of 100 activity instances. We perform experiments on activity slices, on the other hand, they take the whole activity and extract features from that activity and then try to decide if it is normal or abnormal. The problem here is that in a real-life scenario, we cannot know, where an activity starts and ends. Thus, using slice-based detection is more meaningful.

While repetition-related abnormal behavior is detected better by LSTM, abnormal activities stemming from confusion is recognised better by CNN because of its ability to detect variances in feature patterns. The activation order and the relationship between the sensors form steps of activities. When we think about the activity of going to the toilet, it is observed that a person first goes out of bed, walks through the bedroom and then goes to the toilet. As CNN exploits the spatial neighbourhood of the features, it can model this kind of patterns.

The combination of RNNs and CNNs performs the best results since they encode both temporal and spatial information coming from the sensors. However, they fail to understand the intrinsic structure of activities. Thus, we need hierarchical models to understand the sub-activities and their relationships in a given activity and relate them to cognitive decline related to abnormal behavior.

## 10.6 CONCLUSIONS AND FUTURE WORK

### 10.6.1 Conclusion

The main goal of this study was to detect abnormal behavior of ageing persons with dementia in the daily routines. Elderly people suffering from dementia tend to confuse things or repeat and skip certain activities in their daily life patterns. Firstly, a method was proposed to synthesise abnormal behavior stemming from dementia. For this purpose, two types of abnormal behavior were generated, which are activity- and sub-activity-related anomalies. Secondly, deep learning methods such as RNNs and CNNs were exploited to detect abnormal behavior. Thirdly, we compared these methods with the traditional machine learning methods such as HMMs, CRFs, Support Vector Machines and Naive Bayes methods. The results show that the proposed methods are competitive with the state-of-the-art machine learning methods.

First of all, given the scarcity of real-world data available, we proposed a method to manually synthesise abnormal activities to mimic the activity routines of ageing persons. We modified some instances of datasets already available in the literature. The modification was done through
