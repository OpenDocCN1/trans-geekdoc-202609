![](bbox=[0.27, 0.1, 0.86, 0.4])

Figure 11.6 Binary classification – nonlinear decision boundary.

# 11.5.4 Example: Circular Data

The next data set to be considered is a case where the data is separable by a circular or elliptical boundary to illustrate the effect of penalty functions, for both shrinkage (ridge), selection (LASSO) and SVM.2 The synthesized data set is shown in Figure 11.6. The two dimensional set of points are either gray (0) or black (1) and the goal of binary classification is to find a suitable separation boundary. To connect this example to a toy data science problem, let us assume that Bank ABC has given out 337 loans to customers in its immediate vicinity. After some analysis, it find that 266 loans were not repaid completely (gray points) but 71 loans were repaid (black points). This is not an acceptable ratio so the bank decides to use machine learning to make all future loans. The features to be used are age and loan size of prior customers.

The scatter plot of the data shows that middle-aged customers with mid-size loans have all paid back completely, along with some folks with high value loans. Note that there is a separation region between the two colors and there are six outliers (in black) in the upper region of the figure representing the high-value loans that were paid back. If we ignore these points, the data is clearly separable using logistic regression. We will initially use LLR and RLR to perform binary classification. However, in LLR and RLR, we need x1, x2, x1^2 and

2 We note here that we do not take advantage of circular regression which is beyond the scope of this book.