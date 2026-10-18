# K-Nearest Neighbors (KNN) Model

The principle of KNN uses the majority of neighbors to classify data by locating the closest neighboring points and classifying them accordingly. There are several ways to break a tie in this situation. Nevertheless, because KNN runs over all of the training data iteratively, determining the nearest neighbor each time, is not appropriate for huge datasets (Beyer et al., 1999). The Euclidean distance function (Di) is utilized in the following ways to get the feature vector’s closest neighbor

$D_i = \sqrt{(x_1 - x_2) + (y_1 - y_2)^2}$ (1)

where, x₁, x₂, y₁, and y₂ are parameters for input data.

# Decision Tree (DT)

The Decision Tree (DT) is an uncomplicated, fundamental method that bases judgments on pertinent input variable values. After utilizing entropy to determine the root parameter, the weights of the other factors are assessed. DT bases its judgments on a range of values derived from certain qualities, arranging all variable selections into an orderly framework. Research has demonstrated that decision tree models function effectively with imbalanced data. Nonetheless, group techniques for instance, Gradient Boosting (GB) and Random Forest (RF) consistently beat individual decision trees (Malek et al., 2022). Decision-tree-based models have the advantages of being very efficient, robust in lieu of missing values, and competent to handle both standard attributes along data. When it comes to short-term forecasting, decision-tree-based techniques are more appropriate than other machine learning algorithms and frequently provide faster computation speed (Lu and Ma, 2020).

# Machine Learning for Different Water Quality Parameter Assessment

As machine learning provides insights into causative variables and complex variable interactions, it turns out to be a valuable tool for forecasting water quality (Najah Ahmed et al., 2019). In many different disciplines, a variety of machine learning models are widely used (Tikhamarine et al., 2020). For instance, to anticipate water quality, Liao and Sun (Liao and Sun, 2010) combined decision tree techniques with artificial neural networks (ANN). Four machine learning techniques were used in Shafi et al.’s classification of water quality: SVM, Neural Networks (NN), Deep Neural Networks (DNN), and KNN across various water bodies (Shafi et al., 2018). It was noted that DNN had the greatest accuracy of these methods, at 93%. The existence of molecular oxygen in the aquatic environment, or dissolved oxygen, is influenced by several elements including salinity, temperature, and air pressure.

# Biochemical Oxygen Demand Prediction

Aquatic organic contamination can be detected using the commonly used biochemical oxygen demand (BOD) test. It calculates how much oxygen aerobic bacteria need in