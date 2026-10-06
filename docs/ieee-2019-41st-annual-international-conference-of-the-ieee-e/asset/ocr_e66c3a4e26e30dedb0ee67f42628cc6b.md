# IEEE Access

**TABLE 7. Correct classification for Appliance Database.**

| | ElectSense | CLM+SVM | LC-KSVD | Proposed |
|---|---|---|---||
| | [72] | [77] | | |
| Fold 1 | 25.0 | 62.5 | 55.0 | 85.0 |
| Fold 2 | 30.0 | 60.0 | 55.0 | |
| Fold 3 | 32.5 | 67.5 | 62.5 | 90.0 |
| Fold 4 | 32.5 | 67.5 | 62.5 | 87.5 |
| Fold 5 | 30.0 | 60.0 | 60.0 | 87.5 |
| **Aggregate** | **30.0** | **63.5** | **68.0** |

not able to surpass the results with random assignment, and the classification accuracy is pegged at 1/number of appliances). The technique for classifying appliances with EMI signatures is [78]; therefore we compared our technique using ElectSense[78] and features extracted using Conditional Likelihood Maximization (CLM) by SVM classification. The marks, are also compared using LC-KSVD and the results are shown for 5-fold validation. For the proposed method, two levels of classification are identified, in the first level the number of atoms is 500 and in the second level 100. The second level generates sparse features. Table 7 shows that the proposed algorithm outperforms all others. ElectSense yields around 30% correct classification accuracy and CLM yields around 60–67%, whereas the proposed dictionary learning yields more 85% for all others. This also suggests that the proposed algorithm can be extended to other interesting where deep learning techniques may not provide an acceptable level of performance.

from different EMI; but EMI harmonics have an inherent overlap. The power signal and its harmonics analysis based on such signatures is not regrettable [76]. In a technical report [77], it has been shown that, using rudimentary heuristics one can achieve results from CM EMI based classification. The details regarding the development of the CM EMI sensor, sensor acquisition and data are given in [77]:

![](bbox=[0.062, 0.403, 0.487, 0.513])

**FIGURE 10. Block view of EMI sensor.** The data is collected for collection.

Fig. 10 shows the setup for five devices—CPU, CPU, Laptop, Charger and Background Noise (when nothing is in). There are five instances of each appliance. 1500 traces are collected for each instance of each appliance. Each trace is of 1-millisecond duration and constitutes a vector of length 16,384. The training set consists of samples from 1 instance for each appliance while forming 4 instances of each appliance constitutes the test set. For every problem, the training data for each class has 100 traces and the test data is 4 × 1500 = 6000.

The protocol has been described in [77]. For testing, all 1500 traces should be considered as a single task; the task is to identify the appliance from traces. Therefore the classified label of the 1500 samples used majority voting to a single appliance. Cepstrum features [78] are used as the feature set for classification; some examples of cepstrum features are shown in Fig. 11. It can be seen that the cepstrum features for the same appliance look similar and those from different appliances look different.

On the other, stacked autoencoders and deep belief networks, even before pre-processing and normalization, are

Deep learning methods are for classification problems. A recent study [80] GraphEncoder, which uses a stacked feature learning with K-means clustering. In this research, we compare the results of the proposed algorithm with GraphEncoder on datasets (we only use those datasets with ground-truth) we follow the same experimental protocol. We extract features using deep learning and use K-means clustering on the learned features. The datasets for this experiment are described below:

# E. CLUSTERING

1 WINE [81]
The dataset is derived from the UCI Machine Learning Repository, consisting of 178 instances with 13 attributes. Every instance corresponds to a wine with its chemical analysis as the attributes. All instances are labeled with three categories. We use a cosine similarity graph using these instances and the labels as the truth.

2 NO-NEWGROUP [69]
The dataset has been discussed before. Our discovery as a vector of tf-idf (term frequency - inverse document) frequencies of scores; the cosine similarity graph was built on the tf-idf scores. To detect the robustness of our algorithms with different cluster numbers, we constructed three graphs from 3, 6, and 9 different groups respectively. The new groups respects respectively. Each instance in each graph is listed as the following, where the abbreviation NG used in graph is for Newgroup.

+   * 3-NG:corp.graph.ics, rec.sport.basketball, talk.politics, guns.

S. Tiyal et al.: Deep Dictionary Learning

VOLUME 4, 2016

10105