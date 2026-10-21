first fixed and then the high-value customers are filtered. Then the exploratory data analysis is performed, which helps in extracting the useful insights. Using the extracted information feature, data manipulation is performed whereby the features are reduced by means. This process is followed by model generation, which includes scaling, train/test split, feature reduction, and the model is then trained using various algorithms such as logistic regression, decision tree. The I-GBDT algorithm is chosen by applying a cross-validation algorithm and its estimated using valuation metrics likely to find accuracy, to find precision, to estimate recall. The optimal results are derived from the I-GBDT model. Window OS, the Python – Flask micro web framework, the XGBoost Open Source Library, and the Pickle –Python Object Structure are all employed to implement the proposed system (Singh et al., 2021). The data set contains the customer details. Likely information includes the Login and service history, Account information, and Demographic information (Bhambri et al., 2021).

# 12.3.1 ALGORITHM OF I-GBDT

+   1. Data preparation
+      a. Prepare the data set for the customer (customer id and total charges) based on numerical and categorical values.
+   2. Exploratory data analysis
+      a. Remove the duplicates and to perform univariate and bivariate analysis
+      b. Generate the bar plot which shows the percentage of observations (Yes/No).
+      c. Generate the histogram to evaluate the influence of each independent variable.
+   3. Feature Engineering
+      a. Extracting the features of the data into the .my-GBDT model.
+      b. Measures the mutual dependency between two variables based on entropy.
+      c. Higher degree of dependency shows to predict the target of the independent variable.
+      d. Transformations made by Pandas & alternative implementation by Scikit-Learn.
+      e. Label encoding – to convert categorical to numerical values.
+      f. One-hot Encoding – to create a column will set the level of categorical value.
+   4. Model Generation
+      a. Using the Scikit-Learn preprocessing package.
+      b. Normalize the data within the range then speed up the calculations.
+      c. Build a model based on the training set and testing sets to evaluate the performance.
+      d. In this model, create X to store the independent attributes of the data set, Y to store the target variable churn.
+      e. Churn rate = (Users at the beginning of the period – Users at end of period) / Users at beginning of period.