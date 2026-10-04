# 204 T. P. Fowder, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoonon

Name-Value pair: In the case where the random forest technique is used, the two Name-Value pair given in Table 3.19 must be defined:

# Table 3.19. Random Forest – Name-Value pair

| Name | Value | Description |
| --- | --- | --- |
| Method' | 'Bag' | The ensemble aggregation method for random forest must be defined as Bag so that the function bagging with random predictor selectors at each branch node. |
| 'Learners' | templateTree | A template object with parameters of the decision trees must be created and input to the fittest function. |

A MATLAB simulation demonstrating the use of the fitensemble function is described below. The simulation involves using the random forest technique for the classification of iris from Fisher's iris dataset based on their petals' measurements.
First of all, Fisher's iris dataset is loaded in the MATLAB workspace using the codes given in Listing 3.54:

# Listing 3.54. Random Forest– Load dataset

```
rng(1); % For reproducibility
load fisheriris
```

In Listing 3.55, the partition function is used to create a random partition in the data so that 80% of the data is used for training the model and 20% is used for testing it. The training dataset is then compiled in a table tblTr. Each row in the table consists of one iris and each column represents a measurement. The iris species names which can be considered as the class names are placed in the last column.

# Listing 3.55. Random Forest– Divide dataset

```
load fisheriris
N = size(meas,1);
cvp = partition(N,'Holdout',0.2); % Partition data in training and test sets
idxTrn = training(cvp); % Training set indices
idxTest = test(cvp); % Test set indices
% Create training dataset table
tblTr = array2table(meas(idxTrn),
blTr.Y = species(idxTrn);
```

A decision tree template having a maximum of 119 branch nodes is created using the codes given in Listing 3.56. The number of branch nodes must be $n-1$ where $n$ is the number of observations in the training set [60]. In this case,