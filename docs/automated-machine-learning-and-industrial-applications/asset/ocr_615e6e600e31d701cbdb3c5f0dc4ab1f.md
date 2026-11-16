| PROBLEM FORMULATION AND DATA PREPARATION | CLEAR GOALS | DATA UNDERSTANDING | DATA WRANGLING |
| --- | --- | --- | --- |
| TOOL SELECTION | AUTOMATED ML LIBRARIES | PROBLEM SUITABILITY | INTEGRATION |
| TRAINING AND EVALUATION | CROSS-VALIDATION | BEYOND ACCURACY | DOMAIN EXPERT FEEDBACK |
| EXPLAINABILITY AND INTERPRETABILITY | EXPLAINABILITY TOOLS | CLINICAL TRANSLATION | |
| DEPLOYMENT AND MONITORING | INTEGRATION MODE | RE-TRAINING | AUDITING |

# Figure 3.3 Practical implementation: from concept to application.

+   - Data Understanding: Assess the available data (sources, formats, volumes). Identify inconsistencies, missing values, and potential biases. Close collaboration with healthcare professionals is vital.
+   - Data Wrangling: Data cleaning, imputation methods, feature engineering, and normalization enhance data quality and compatibility with AutoML tools.

```
import pandas as pd
# Load EHR Data
data = pd.read_csv('sepsis_ehr_data.csv')
# Data Cleaning and Preprocessing
data.dropna(subset=['temperature', 'heart_rate'], inplace=True)
# Drop missing vital signs
data['lab_abnormal'] = data['lab_results'].apply
(lambda x: detect_abnormalities(x))
# Custom function
```

# 3.7.2 Tool Selection

+   - AutoML Libraries: Consider the trade-offs between ease-of-use and customization offered by frameworks like TPOT, H2O AutoML, Auto-sklearn, etc. [9].