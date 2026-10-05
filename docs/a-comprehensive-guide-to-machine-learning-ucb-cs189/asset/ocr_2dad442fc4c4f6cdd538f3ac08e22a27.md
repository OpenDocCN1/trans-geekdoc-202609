One drawback of LS-SVM is that the hyperplane decision boundary it computes does not necessarily make sense for the sake of classification. For example, consider the following set of data points, color-coded according to the class:

![](bbox=[0.296, 0.203, 0.683, 0.427])

Figure 6.4: Reasonable fit LS-SVM

LS-SVM will classify every data point correctly, since all the +1 points lie on one side of the decision boundary and all the -1 points lie on the other side. Now if we add another cluster of points as follows:

![](bbox=[0.296, 0.603, 0.683, 0.83])

Figure 6.5: Poor fit LS-SVM

The original LS-SVM fit would still have classified every point correctly, but now the LS-SVM