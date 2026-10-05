# Generalization

parameters, and the hyperparameters all need to be decided at this point. The test set is then useful for giving an independent assessment of how the model might perform on new data.

The test set is critical as the model performance on the training set will overestimate its ability. Stated differently, we can expect that the performance on the test set will be better than the performance on the training set, and it will be more realistic. If the performance is measured on the test set, and then changes are made to the model, another test set will be needed for a true measure of performance. For this reason, multiple test sets are sometimes formed, leading to the training/validation/test1/test2 schema.

The process of breaking the data into pieces is data splitting, and it is an essential step in the machine learning process. This should take place after the data is cleaned and processed, before modeling. The separate pieces should be saved into separate files named such train.csv, validation.csv, test.csv.

Care needs when splitting the data. Since the pieces of data need to be independent from one another, we will need to think about each row represents. For example, suppose each row represents a patient measurement at a snapshot in time. This allows for the possibility that one or more patients can have multiple records in the dataset. If we split the data by randomly selecting rows, we encounter an issue called data leakage where one or more patients can have portions of their data in both the training and test set. This is a problem because the model will learn on the training data. Overstated performance can result from data leakage.

The issue can be circumvented by using the unique list of patient identifiers and randomly assigning fractions of them to each data subset. As an example, we might decide to allocate 60% of the data to the training set, 20% to the validation set, and 20% to the test set. Operationally, we would build the list of unique patient identifiers (a one-liner of Python code), randomly assign patient identifiers to the three sets in proportions, and move them with their associated data to create the datasets. In this way, each patient's record belongs fully to either the training set, validation set, or test set without risk of leakage.

Finally, let us return to the point that even if a model is trained on the training set and performs well on an independent test set, it can under later. This is a case where model generalized to unseen data at first, but its performance degraded later. Data scientists should expect this to happen, actually. The value of data decreases over time, and thus, the value of models will decrease over time. Patterns will change for many reasons, including:

+   * Pandemic

> It is common to use a majority of the data for training and 60% or 70% are common values, but not the final word.