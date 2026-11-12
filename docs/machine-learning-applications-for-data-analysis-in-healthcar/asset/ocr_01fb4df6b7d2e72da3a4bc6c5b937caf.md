# TABLE 1.1 (Continued)

| Index | Features | Data Type | Non-null Values | Missing Values | Null Percentage |
|---|---|---|---|---|---|
| 33. | Lymphocyte | float64 | 1032 | 145 | 12.32 |
| 34. | PT | float64 | 1157 | 20 | 1.70 |
| 35. | INR | float64 | 1157 | 20 | 1.70 |
| 36. | NT-proBNP | float64 | 1177 | 0 | 0 |
| 37. | Creatine kinase | float64 | 1012 | 165 | 14.02 |
| 38. | Creatinine | float64 | 1177 | 0 | 0 |
| 39. | Urea nitrogen | float64 | 1177 | 0 | 0 |
| 40. | Glucose | float64 | 1159 | 18 | 1.53 |
| 41. | Blood potassium | float64 | 1177 | 0 | 0 |
| 42. | Blood sodium | float64 | 1177 | 0 | 0 |
| 43. | Blood calcium | float64 | 1176 | 1 | 0.08 |
| 44. | Chloride | float64 | 1177 | 0 | 0 |
| 45. | Anion gap | float64 | 1177 | 0 | 0 |
| 46. | Magnesium ion | float64 | 1177 | 0 | 0 |
| 47. | pH | float64 | 885 | 292 | 24.81 |
| 48. | Bicarbonate | float64 | 1177 | 0 | 0 |
| 49. | Lactic acid | float64 | 948 | 229 | 19.46 |
| 50. | PCO₂ | float64 | 883 | 294 | 24.98 |
| 51. | EF | int64 | 1177 | 0 | 0 |

# 1.4.2.1 HANDLING MISSING VALUES

We saw in Table 1.1 that a lot of features had null values. The number of missing values in any of the columns did not exceed 25%. So, they were to be filled in order to avoid any decay in accuracy or any biased behavior. So, keeping this in mind, the data were divided into two parts based on its outcome “alive” or “dead” which were denoted by “0” and “1,” respectively, in the outcome or the target column. Then all the missing feature values of each separated outcome data were handled using Simple Imputer having its strategy attributefixed to “mean” which means “mean” of their respective feature columns. After handling all the missing values, the datasets were concatenated and finally the outcome or target column was separated from the dataset.