![](bbox=[0.16, 0.11, 0.44, 0.26])

# Figure 8.11 Rate error vs. number of nodes

![](bbox=[0.55, 0.11, 0.85, 0.26])

# Figure 8.12 Stop training threshold

Holdout method: in this method, which is mostly applied in machine learning tasks, some parts of the original dataset, is selected as validation dataset, as shown in Figure 8.13. The training and holdout set errors are calculated at each epoch during the training phase and plotted together at the end of the training phase. The training dataset should be more than data reserved for as a holdout validation set, usually 20% of the total dataset. Moreover, the training and holdout sets should have the same data distribution to avoid misleading results.

![](bbox=[0.16, 0.55, 0.8, 0.65])

# Figure 8.13 Training and validation dataset in holdout method

Random subsampling or repeated holdout method: in this method, the holdout method is repeating many times by randomly picking samples from the original data to create training, validation, and test datasets. The reaping holdout method decreases the overfitting chance and increases overall generalization performance. This method’s possible disadvantage is due to the possibility of selecting some samples more than others for training [20].