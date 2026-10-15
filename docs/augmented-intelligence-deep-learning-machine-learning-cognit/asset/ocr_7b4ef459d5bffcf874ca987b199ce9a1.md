# Table 5. Performances of Bankruptcy Prediction Model using G-mean.

| Feature selection methods | Classifiers | 1st year | 2nd year | 3rd year | 4th year | 5th year |
|---|---|---:|---:|---:|---:|---:|
| SBS | SBSAda-Rip | **92.9** | **88.1** | **89.1** | **87.2** | **81.4** |
| SBS | AdaBoost+ C4.5 | 78.5 | 73.6 | 72.2 | 63 | 76.2 |
| SBS | AdaBoost+OneR | 77.9 | 63.9 | 57.4 | 64.7 | 75.4 |
| SBS | AdaBoost+PART | 90.2 | 76.6 | 83.7 | 64.1 | 64.2 |
| SBS | AdaBoost+CART | 85 | 90.6 | 65.8 | 57.6 | 91 |
| SBS | AdaBoost+RF | 79.6 | 75.3 | 80.2 | 54.6 | 78.6 |
| SFS | AdaBoost+JRip | 87 | 78.1 | 80.3 | 78.6 | 81.8 |
| SFS | AdaBoost+ C4.5 | 78.7 | 66.2 | 70.8 | 49.5 | 74.1 |
| SFS | AdaBoost+OneR | 79.6 | 47.5 | 53.5 | 61.4 | 73.3 |
| SFS | AdaBoost+PART | 94.5 | 74.7 | 81.3 | 66.7 | 75.1 |
| SFS | AdaBoost+CART | 91.5 | 76.2 | 67.7 | 79.5 | 91 |
| SFS | AdaBoost+RF | 83.7 | 63.9 | 69.4 | 41 | 79.4 |
| PSO | AdaBoost+JRip | 89.1 | 85.5 | 82 | 84.6 | 79.4 |
| PSO | AdaBoost+ C4.5 | 82.2 | 85.2 | 65.2 | 63.2 | 71.3 |
| PSO | AdaBoost+OneR | 74.2 | 40.1 | 63.3 | 57.5 | 77.4 |
| PSO | AdaBoost+PART | 72.3 | 73.6 | 62.1 | 65.1 | 78.7 |
| PSO | AdaBoost+CART | 86.5 | 74.3 | 65.5 | 77.5 | 91 |
| PSO | AdaBoost+RF | 69.4 | 61.5 | 54.8 | 56 | 76.6 |
| RSFS | AdaBoost+JRip | 92.2 | 87.3 | 73.6 | 76.8 | 87.4 |
| RSFS | AdaBoost+ C4.5 | 78.4 | 82 | 72.4 | 67 | 72.4 |
| RSFS | AdaBoost+OneR | 71.2 | 41.5 | 60.1 | 66 | 77.6 |
| RSFS | AdaBoost+PART | 72.3 | 67 | 61.3 | 63.6 | 76.7 |
| RSFS | AdaBoost+CART | 86.5 | 72.5 | 68.1 | 79 | 81.6 |
| RSFS | AdaBoost+RF | 69.4 | 55.7 | 54.3 | 43.7 | 72.8 |

Table 6 demonstrates the performance in the F-measure of all the used algorithms in this study. This table shows that, much like table 5, some instances of other algorithms perform slightly better than our proposed approach. Nevertheless, when compared to the performance of our technique, which ranges between 94.3% and 97.1%, it is evident that on average, it performs better than the others as it maintains stable results on all the datasets. It leads us to validate the performance of SBSAda-Rip for corporate bankruptcy prediction