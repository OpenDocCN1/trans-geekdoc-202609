# Algorithm 7.1 Traditional RF algorithm for classification and regression.

+   1) Start with a training sample, \( d_{trn} \), and specify integers, \( n_{min} \) (the minimum node size), \( B \) (the number of trees in the forest), and \( m_{try} \le p \) (the number of predictors to select at random as candidate splitters prior to splitting the data at each node in each tree).

+   2) For \( b \) in \( 1, 2, \dots, B \):

+   (a) Select a bootstrap sample \( d^*_{trn} \) of size \( N \) from the training data \( d_{trn} \).

+   (b) **Optional:** Keep track of which observations from the original training data were not selected to be in the bootstrap sample; these are called the out-of-bag (OOB) observations.

+   (c) Fit a decision tree \( \mathcal{T}_b \) to the bootstrap sample \( d^*_{trn} \) according to the following rules:

+   (i) Before each attempted split, select a random sample of \( m_{try} \) features to use as candidate splitters.

+   (ii) Continue recursively splitting each terminal node until the minimum node size \( n_{min} \) is reached.

+   3) Return the “forest” of trees \( \{\mathcal{T}_b\}_{b=1}^B \).

+   4) To obtain the RF prediction for a new case \( x \), pass the observation down each tree and aggregate as follows:

+   • Classification: \( \hat{C}^{rf}_B(x) = vote \left\{ \hat{C}_b(x) \right\}_{b=1}^B \), where \( \hat{C}_b(x) \) is the predicted class label for \( x \) from the \( b \)-th tree in the forest (in other words, let each tree vote on the classification for \( x \) and take the majority/plurality vote).

+   • Regression: \( \hat{f}^{rf}_B(x) = \frac{1}{B} \sum_{b=1}^B \hat{f}_b(x) \) (in other words, we just average the predictions for case \( x \) across all the trees in the forest).

vote (multiclass outcome) is used to determine the overall classification of an observation.

With categorical outcomes, however, we often care more about the predicted probability of class membership, as opposed to directly predicting a class label. In an RF (or a bagged tree ensemble) there are two ways to obtain predicted probabilities: