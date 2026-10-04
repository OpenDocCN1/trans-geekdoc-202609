# The use of ML algorithms in early detection of liver disease 273

dataset consists of various features, including age, gender, alkaline phosphatase, alanine aminotransferase, aspartate aminotransferase, total bilirubin, direct bilirubin, albumin, total proteins, and albumin and globulin ratio. These features are important for analyzing the patients' liver health. There are 1402 male patient records and 456 female patient records in the dataset. To maintain anonymity, any person who is older than 98 is labeled as 90. Before utilizing the dataset for this research, a thorough review will be conducted to ensure its reliability and accuracy, verifying the data sources and performing data quality checks. Figure 14.2 shows the overall description of the dataset, and Figure 14.3 shows the albumin and globulin ratio feature histogram.

# 14.4 DATA PREPROCESSING

The first step in the data preprocessing stage involves handling missing values in the dataset. In this case, we found null values in the feature named albumin and globulin ratio. The data in this is normally distributed but slightly right-skewed and has been shown in Figure 14.3; we decided to fill up the null values using the median method. We then proceeded to check two other features named total bilirubin and direct bilirubin and discovered the datasets contained huge outliers. Next, we performed label encoding on the dataset and looked for correlations between features. We observed that there was a high correlation between total bilirubin and direct bilirubin, as well as alanine aminotransferase and aspartate aminotransferase, and total proteins and albumin. To increase the transfer speed and accuracy of our model, we decided to eliminate one feature from each correlated pair. Therefore, we removed direct bilirubin, aspartate aminotransferase, and albumin from our model. Furthermore, we noticed that the dataset contained

![](bbox=[0.128, 0.606, 0.847, 0.856])

Figure 14.2 Overall description of the dataset.