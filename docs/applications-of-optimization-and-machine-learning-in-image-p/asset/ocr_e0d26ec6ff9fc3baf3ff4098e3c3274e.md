The likelihood of the ensemble classifier for the decision to be better is:

$$P_{ensemble} = \sum_{k=\lceil \frac{n}{2} \rceil + 1}^{n} \binom{n}{k} p^k (1-p)^{n-k}$$

where $n$ is the number of observations and $p$ the probability for each observation.

To predict cardiac disease, learning techniques are used. First, the data is split into train data and test data and used to train the proposed method in the view of the Ensemble of Support Vector Machine, Naïve Bayes, Decision Tree classifiers, and Random Forest method. Then the model is tested with test data for prediction to get the best accuracy and to find the model's behavior. The algorithm results in a category of 1 and 0 for the presence and absence of cardiac disease [61].

In this chapter, a comparative analysis of the proposed ensemble method with other individuals supervised algorithms (Logistic Regression, Support Vector Machines, Decision Tree classifier, Naïve Bayes classifier, and k-Nearest Neighbor classifier) has also been performed to determine the appropriate model for heart disease prediction in the view of Cleveland dataset.

# 11.3.4 Proposed Model Architecture

Classification is a supervised learning process for predicting outcomes from the extraction of information [62]. This research suggests utilizing classification algorithms to diagnose cardiac illness and employing an ensemble of algorithms to increase classification accuracy. The classification of this data is conducted using a medical dataset called the Cleveland dataset. The dataset has been separated into a training set and a test set (70:30), and, using the training data, all the individual classifiers are trained. Using the test dataset, the classifiers' efficiency is assessed. In this chapter, the operation of each classifier is thoroughly illustrated.

The system architecture provides an overview of how the system works for ensemble learning in the context of the Cleveland dataset.

The proposed system's procedure begins with gathering information, and important features of attributes are extracted in order to choose which attributes to employ in the proposed model. The relevant data is then preprocessed and converted to a suitable format [63]. The data is then separated into two categories: training and testing. The ensemble learning algorithms are used to train the model using the training data. The system's accuracy and outcomes of the model are determined by analyzing it using the testing data. In this research, the system is implemented using the following steps: