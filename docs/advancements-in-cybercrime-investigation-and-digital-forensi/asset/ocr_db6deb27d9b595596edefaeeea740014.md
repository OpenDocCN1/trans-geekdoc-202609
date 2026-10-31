we need a financial dataset, but due to the privacy policies, there is a lack of datasets. Here, a synthetic dataset has been created through a simulator named PaySim. It used a sample of real transactions of an African country total of a month transactions to create a synthetic dataset that looks similar to the normal transactions. The synthetic data is 1/4 of the original data.

The dataset contains 11 features. The variables are as follows step one unit of time, types of transactions, amount of transactions, nameOrig origin of the transaction, oldbalanceOrg old balance of origin of the transaction, newbalanceOrig new balance of origin, nameDest recipient customer, oldbalanceDest old balance of the recipient, newbalanceDest new balance of the recipient, isFraud this is target variable 0 means non-fraud 1 means fraud. PaySim is the simulator which produced the synthetic dataset then preprocessing is done, after processing the dataset, it is given as input to all algorithms to get their results which are then ensembled to get our final predictive model.

Figure 12.1 is the flow diagram of the process of building our model for fraud detection. PaySim2 is the simulator that gave us a synthetic dataset, this data was further preprocessed, and feature engineering was done. After that, this dataset was fed to all three tree-based algorithms to get their results, and then they were ensembled to get a combined result and all four results were then compared.

![](bbox=[0.12, 0.57, 0.9, 0.86])

FIGURE 12.1 Flow diagram.