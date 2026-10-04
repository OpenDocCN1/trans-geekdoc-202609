
`sRNN` consists of 128 single hidden layers. The same preprocessing method for `KNN` is applied to divide the datasets with equal length. For hyperparameters, the `sRNN` is initialized in the same way as the proposed `LCED`. Besides, the K- Average operation is utilized to estimate the accuracy of the `LCED` performance.

### 6.Evaluation

The section mainly analyzes and estimates the performance of WiFi-based human activity recognition using the proposed `LCED` model in terms of different individuals, different distances between one transmitter and one receiver, and different heights between wireless devices and the floor. The details of these analyses are as follows.

#### 6.1 Performance of individuals

The research goal is to analyze the impact of individuals’ differences on the accuracy of human activity recognition. We use the proposed `LCED` model to evaluate the performance of individuals in human activity recognition using WiFi CSI. More-over, we also leverage three methods: `KNN`, `SVM`, `sRNN` as contrast methods to compare with the proposed `LCED`. [Table 3](#chap5.xhtml#tab3) shows the performance of 16 activities of `Volunteer` 2 using `KNN`. We take `Antenna_A` as an example and analyze recognition performance of 16 activities in terms of `Precision`, `Recall` and `F1-score`. `Precision` is the number of the right samples from all samples which are predicted an activity. `Recall` denotes the number of right samples from 30 samples of an activity. The precision of `Activity` 1 is 1.00 and `Recall` is 0.83. The above two metrics show that several samples of `Activity` 1 are misidentified as another activity. `Activity` 3, `Activity` 4, `Activity` 12, `Activity` 13 and `Activity` 15 achieve recognition accuracy of 100%. However, only `Activity` 4, `Activity` 13 and `Activity` 15 achieve recognition accuracy of 100% for the same volunteer using `Antenna_B`’s activity data. By combining with results of the two antennas on human activity recognition, average accuracy of 16 activities using `KNN` achieves 80% except for `Activity` 5 and `Activity` 8 due to low-quality data. In summary, `KNN` can roughly detect and recognize daily activity using WiFi signals in a simple indoor environment.

**Table 3:** `KNN` performance for one individual with two antennae.

![figure](images/p126-1.jpg)

Differences of individuals find expression in recognition accuracy of each activity in the same indoor environment using the same classification algorithm. We select confusion matrix of activity recognition accuracy to analyze relationship of each activity. [Figure 8](#chap5.xhtml#fig8) shows the confusion matrix of two volunteers for human activity recognition using `SVM` algorithm. For `Volunteers` 2’s confusion matrix, the `Antenna_A`’s performance is superior to the `Antenna_B` and the `Antenna_C` as the confusion matrix of `Antenna_B` occurs with few misjudgement samples. Moreover, there are some same activities with low accuracy in three antennae like `Activity` 5 because other activities are mistaken for `Activity` 5, `Activity` 2, `Activity` 12, `Activity` 13, `Activity` 15, `Activity` 16 of the 16 activities achieve good performance for `Volunteer` 2 and `Activity` 1, `Activity` 2, `Activity` 12 and `Activity` 13 also achieve better performance for `Volunteer3`. The similar activities keep similar performance for `KNN` and `SVM` such as `Activity` 12 and `Activity` 13. According to the above analysis, we know that recognition algorithms depend on extracted features to recognize human activity, which leads to huge difference in accuracy of recognition of the same activity for the same volunteer.

![figure](images/p127-1.jpg)

**Figure 8:** Two volunteers and three antennae: the accuracy of 16 activities using `SVM`.

![figure](images/p128-1.jpg)

**Figure 9:** Performance analysis of four algorithms. `VIA` is the accuracy of `Volunteer` 1’s activity data on `Antenna_A`. `V1M` denotes the average accuracy of `Volunteer` 1’s activity data on three antennas (`Antenna_A`, `Antenna_B`, `Antenna_C`). `V1STD` is the standard deviation of `Volunteer` 1 ‘s activity data on three antennas.

We randomly select activity data of three volunteers as analysis objects to estimate the influence of three antennas on activity performance using four recognition algorithms. The experimental results are shown in [Figure 9](#chap5.xhtml#fig9). According to the comparison of three volunteers regarding recognition accuracy using `KNN`, `Volunteer` 2 achieves an average accuracy of 90% and `Volunteer` 3 shows high 80% recognition accuracy. The worst accuracy is `Volunteer` 1 with average 77%. `Antenna_A` of `Volunteer` 1 and `Volunteer` 2 on activity recognition accuracy achieve 5% higher than other antennas. The stability of `Volunteer` 3 on recognition accuracy using `KNN` is superior to `Volunteer` 1 and `Volunteer` 3. Although the accuracy of `Volunteer` 1 is still lower than the other two individuals using `SVM`, `RNN`, the average stability of recognition accuracy on three antennas is higher than the other two individuals. Compared with `KNN`, `SVM` and `RNN`, the accuracy of activity recognition increases 10% on average using the proposed `LCED` model. Moreover, the average stability of three volunteers on the accuracy of human activity recognition is superior to the other three algorithms. In summary, the important performance achieved by the proposed `LCED` not only reduces the difference of recognition accuracy on three antennas but also enhances the robustness of activity recognition on individuals.

We focus on the average difference of each antenna on human activity recognition for individuals using WiFi signals. [Figure 10](#chap5.xhtml#fig10) shows performance difference of each antenna for seven volunteers under the four recognition algorithms. We take `Antenna_As` of seven individuals as an example to analyze their performance. The average accuracy of seven volunteers on `Volunteer_A` is superior to `Antenna_B` and `Antenna_C` except for `LCED`’s result. However, the stability of `Antenna_A` is lower than the other two antennas according to the `VASTD`. In other words, the difference of recognition accuracy of the seven volunteers on `Antenna_A` is huge. The three antennas have stability accuracy with a high of 80% average accuracy, respectively, and up to 95% accuracy by using `LCED` model. The standard deviation of the three antennas is less than 0.1 for `KNN`, `SVM` and `RNN`. Compared with the above, the standard deviation of the `Antenna_B` and `Antenna_C` using `LCED` model is less than 0.01.

![figure](images/p129-1.jpg)

**Figure 10:** Performance analysis of three antennas under four algorithms. `VAM` is the average accuracy of all `Antenna_A`s; `VASTD` is the standard deviation of all `Antenna_A`s.

We discuss difference of three antennas of individuals under the prosed `LCED`. [Figure 11](#chap5.xhtml#fig11) lists recognition accuracy of three antennas of seven individuals using `LCED` model. The average accuracy of three antennas regarding activity recognition is higher than 93% and the standard deviation is less than 0.02 except for the performance of `Volunteer` 3. Compared with the above-mentioned three recognition algorithms, accuracy of `Volunteer` 3’s three antennas is superior.

![figure](images/p130-1.jpg)

**Figure 11:** Performance analysis of individuals. `VA` is the accuracy of a `Antenna_A`; `VM` is the average accuracy of three antennas; `VSTD` is the standard deviation of three antennas.

#### 6.2 Performance of different distances
