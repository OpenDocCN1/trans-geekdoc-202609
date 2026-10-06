![](bbox=[0.173, 0.96, 0.79, 0.255])

trees, stacked with a random forest. Another example is EMMA [24], which stacks an ensemble of separately trained deep learning-segmentation models through a majority vote. Here a range of very different architectures are trained and combined to improve the performance of brain-tumor segmentation. Finally, Rasero [37] seek to condense and combine a vast amount of features from multimodal MRI to build a sensitive prediction of fluid intelligence and other metrics of cognition.

# 7.2.15 Exercises

Complete the following exercises to test your understanding of how to implement de-cision trees and ensembles using scikit-learn.

+   1. Calculate the information gain and Gini index for the split in Fig. 7.11.
2. Using the neonatal brain deaset 'GA-brain-volumes-86-features.csv' with 86 regional brain volumes: fit a scikit-learn decision tree regression model to predict the target variable (gestational age (GA) in the first column)
    - Split the data into training and test sets, including the first 120 samples in the training set and the rest in the test set.
    - Trying a tree with the default parameters and reporting the goodness of fit using score.
    - Use scikit-learn's GridSearchCV to optimize the parameters for: criterion, max_depth, and min_samples_leaf.
3. Fit a BaggingRegressor, RandomForestRegressor and AdaboostRegressor using decision-trees as the base model:
    - Set parameters to the optimal values found for Exer. 2;

5 The datasets, skeleton code and solution is available at github.com/MachineLearningBiomedicalApplications/notebooks.