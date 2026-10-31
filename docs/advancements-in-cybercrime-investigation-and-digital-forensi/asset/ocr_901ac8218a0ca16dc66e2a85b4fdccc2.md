# 12.4.2 PREPROCESSING

Pre-processing is the process of preparing the raw data for model training. It consists of finding missing values and removing or imputing them (Ravisankar, 2011). There were no missing values in the dataset, and all the values with 0 only were replaced with −1. One hot encoding was used for categorical variables. Min-max scaler is used for scaling the features. Furthermore, the features which are not contributing to model results were removed. Some insights into the dataset are discussed in subsections.

# 12.4.2.1 TRANSACTIONS BY HOURS OF THE DAY

As an added insight, Figure 12.2 shows activity based on hours, the observations from this were substantial and can affect the project flow in any significant manner. The fraud transactions were continuous along with the 24 hours duration, whereas valid transactions were significantly less at night.

![](bbox=[0.14, 0.5, 0.86, 0.8])

FIGURE 12.2 Fraudulent and valid transactions over hours of the day.

# 12.4.2.2 AMOUNT OF TRANSACTIONS

Certain trends were seen in the fraudulent activity based on the amount of the transaction as shown in Figure 12.3. The fraud transactions never crossed the 10-lakh line, whereas valid transactions were high up to 1 crore.