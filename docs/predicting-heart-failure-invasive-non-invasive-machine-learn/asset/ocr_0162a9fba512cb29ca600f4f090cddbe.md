# Table 7.3 Statistical description of Statlog data set.

| | age | trestbps | chol | thalach | oldpeak | ca |
|---|---|---|---|---|---|---|
| mean | 54.44 | 131.34 | 249.66 | 149.68 | 1.05 | 0.67 |
| std | 9.10 | 17.86 | 51.69 | 23.17 | 1.15 | 0.94 |
| min | 30.00 | 94.00 | 126.00 | 71.00 | 0.00 | 0.00 |
| 0.25 | 48.00 | 120.00 | 213.00 | 133.00 | 0.00 | 0.00 |
| 0.50 | 55.00 | 130.00 | 245.00 | 153.50 | 0.80 | 0.00 |
| 0.75 | 61.00 | 140.00 | 280.00 | 166.00 | 1.60 | 1.00 |
| max | 77.00 | 200.00 | 564.00 | 202.00 | 6.20 | 3.00 |

![](bbox=[0.16, 0.34, 0.89, 0.52])

Figure 7.4 Bar plot for the relationship between target and sex.

Figure 7.5 shows the average age for males and females distributed based on the target label. We can notice that the average age for male patients is slightly smaller than females for both target labels in both data sets, which means that men are likely to have heart disease earlier than females during their lives. This finding is also confirmed in Figure 7.6, which shows that males’ age distribution is much more normal than the distribution of females’ age in both data sets. Most females are likely to have heart problems in the late stage of their lives.

Figure 7.7 demonstrates the distribution of resting blood pressure for heart and normal patients, classified based on sex variables. We can notice that both data sets have relatively the same distribution. The main observation is that there is no significant difference between heart patients and normal patients for males, but there is a significant difference between the two distributions for females.

# 7.4.2 Data Preprocessing

The data sets were preprocessed to handle noise, inconsistency, and missing values. The noises and inconsistencies were corrected manually. However, the missing values had to be treated before being used as they could have led to failure in classification or