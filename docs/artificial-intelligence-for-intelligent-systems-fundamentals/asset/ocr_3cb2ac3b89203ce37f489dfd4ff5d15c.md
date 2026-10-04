# Artificial intelligence for intelligent systems

# Correlation Matrix Heat Map

| | Age | Sex | AST | ALP | ALT | AST | BIL | CHE | CHOL | CREA | GGT | PROT |
|---|---|---|---|---|---|---|---|---|---|---|---||
| Age | 0.038 | -0.072 | -0.081 | -0.089 | 0.62 | 0.4 | -0.237 | 0.14 | 0.44 | 0.084 |
| Sex | 0.038 | 0.025 | -0.017 | -0.066 | 0.089 | 0.032 | -0.075 | 0.125 | -0.022 | 0.15 | -0.15 |
| AST | -0.072 | 0.015 | -0.016 | -0.16 | -0.17 | -0.11 | 0.016 | -0.013 | -0.091 |
| ALP | -0.018 | -0.01 | -0.064 | 0.0026 | -0.19 | -0.22 | 0.38 | 0.13 | -0.0016 | 0.16 | 0.55 |
| ALT | -0.063 | 0.012 | -0.01 | 0.17 | 0.062 | 0.049 | 0.033 | 0.12 | -0.064 | 0.09 |
| AST | -0.089 | -0.016 | 0.016 | 0.27 | 0.23 | 0.015 | -0.068 | 0.06 |  0.09 |
| BIL | 0.62 | -0.089 | -0.019 | -0.062 | 0.27 | 0.31 | -0.21 | -0.0021 | 0.49 | 0.04 |
| CHE | 0.04 | 0.032 | -0.112 | -0.049 | -0.036 | 0.31 | -0.33 | -0.16 | -0.041 | 0.42 |
| CHOL | -0.075 | -0.017 | 0.038 | -0.013 | -0.21 | -0.33 | 0.42 | -0.011 | -0.041 | 0.29 |
| CREA | -0.027 | 0.03 | 0.02 | -0.068 | -0.081 | -0.016 | 0.42 | -0.041 | -0.0068 | 0.11 | 0.12 |
| GGT | 0.14 | -0.022 | 0.014 | -0.0015 | -0.014 | 0.031 | -0.031 | -0.048 | 0.11 | -0.012 |
| PROT | 0.44 | -0.15 | -0.16 | -0.44 | 0.25 | 0.49 | -0.22 | 0.29 | 0.21 | -0.0668 | 0.12 | -0.12 |
| | 0.014 | -0.015 | -0.051 | -0.054 | 0.094 | 0.04 | -0.041 | -0.041 | -0.032 | |

Figure 12.9 Correlation between columns.

After completing each of the previous procedures, we move on to implement a total of 12 machine learning models. The dataset was split in an 80:20 ratio for training and testing. As shown in Figure 12.3, it is clear that our dataset has an imbalance. To achieve a balanced dataset, the undersampling technique is employed. Undampling is a method that reduces the number of samples in the major class in line with the number of samples in the minority class [39]. This process aims to create a more equal distribution of data for training machine learning models. This approach minimizes bias towards the dominant class and improves the overall accuracy of classification. Next, we execute a comparative analysis of the results obtained from the machine learning models by evaluating the accuracy, recall, and precision metrics for before balancing and after balancing datasets.

# 12.4 EXPERIMENTAL RESULTS

The tables in this research show the results of the machine learning algorithms used to detect hepatitis C.