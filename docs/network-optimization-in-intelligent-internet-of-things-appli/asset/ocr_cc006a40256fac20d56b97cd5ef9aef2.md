# 238 Network Optimization in Intelligent IoT Applications

It was observed within the CIDDS (2017) dataset, that features – “type of service” and “flows” – solely contain values of 0.0 and 1.0. Similarly, the “number of outbound commands” feature in the NSL-KDD dataset exclusively consists of 0.0 values. Consequently, it was decided to remove instances associated with these specific parameters.

# 13.4.3 OSAW Performance Over CIDDS (2017) and NSL-KDD Datasets

Table 12 covers diverse supervised ML techniques performance using the separate CIDDS (2017) and NSL-KDD datasets. K-Means clustering was employed to label the unlabelled data. The resultant clusters were then utilized to train the classifier. Across both datasets, there was an observable reduction in accuracy values. Table 13.3 shows the accuracy of our proposed method for detecting network anomalies based on concept drift on two separate datasets. Throughout the two datasets,

# TABLE 13.2
Performance of Machine Learning Techniques before Drift Handling

| Method | CIDDS (2017) [39] | | | | NSL-KDD [40] | | | |
|---|---|---|---|---|---|---|---|{}|
| | Acc (%) | Precision (%) | Recall (%) | F1-Score (%) | Accuracy (%) | Precision (%) | Recall (%) | F1-Score (%) |
| KNN | 82 | 79 | 75 | 77 | 77 | 83 | 77 | 77 |
| LR | 81 | 80 | 77 | 78 | 70 | 76 | 70 | 70 |
| RF | 86 | 89 | 88 | 88 | 77 | 83 | 77 | 76 |
| SVM | 88 | 86 | 84 | 85 | 81 | 85 | 81 | 81 |

# TABLE 13.3
Effectiveness of Machine Learning Approaches Following Drift Handling

| Method | CIDDS (2017) [39] | | | | NSL-KDD [40] | | | |
|---|---|---|---|---|---|---|---|{}|
| | Acc (%) | Precision (%) | Recall (%) | F1-Score (%) | Accuracy (%) | Precision (%) | Recall (%) | F1-Score (%) |
| Proposed OSAW & KNN | 91.2 | 90.8 | 92.3 | 92.7 | 81.6 | 85.7 | 81.7 | 81.5 |
| Proposed OSAW & LR | 94.4 | 92.4 | 93.6 | 93.1 | 85.4 | 76.4 | 70.7 | 70.8 |
| Proposed OSAW & RF | 96.2 | 93.5 | 92.1 | 91.7 | 88.5 | 85.2 | 88.4 | 87.2 |
| Proposed OSAW & SVM | 99.8 | 99.1 | 99.2 | 99.1 | 91.3 | 88.3 | 91.7 | 89.8 |