![](bbox=[0.165, 0.12, 0.33, 0.25])

![](bbox=[0.42, 0.12, 0.59, 0.25])

![](bbox=[0.66, 0.12, 0.83, 0.25])

FIGURE 6.10 Decision boundaries by different classifiers. Note that this example is linearly separable, meaning that a linear classifier (c) can perfectly separate all the positive training tuples from all the negative training tuples. If the training set is linearly inseparable, we could still use a linear classifier, at the expense that some training tuples are on the 'wrong' side of the decision boundary. In Chapter 7, we will introduce techniques (e.g., support vector machines) to handle linearly inseparable case.

fiers, including (1) perception, which is one of the earliest linear classifiers, and (2) logistic regression which is one of the most widely used linear classifiers. Additional linear classifiers will be introduced in Chapter 7, such as linear support vector machines.

# 6.5.1 Linear regression

Linear regression is a statistical technique that predicts a continuous value based on one or more independent attributes. For example, we might want to predict the housing price based on the living area or to predict the future income of a student based on which college she attended, in which major and the overall GPA, etc. Since linear regression aims to predict a continuous value, it cannot be directly applied to the classification task, where the output is a categorical variable. Nonetheless, the core techniques in linear regression form the basis of linear classifiers. Therefore, let us first briefly introduce linear regression.

Suppose we have n tuples, each of which is represented by p attributes xi = (xi,1, ..., xi,p)T and a continuous output value yi (i = 1, ..., n). In linear regression, we want to learn a linear function that maps the p input attributes xi to the output value yi, that is, ŷi = wTxi + b = Σj=1p wjxi,j + b, where ŷi is the predicted output value for the ith tuple, w = (w1, ..., wp)T is a p-dimensional weight vector and b is the bias scalar. In other words, linear regression assumes that the output value is a linear weighted summation of the p input attribute values, offset by the bias scalar b. The entries in the weight vector wj (j = 1, ..., p) tell how important the corresponding attribute xi,j is in predicting the output variable ŷi. In the aforementioned examples, a linear regression model would assume that the housing prices are linearly correlated with the living area; the future income of a student can be predicted by a linear weighted combination of the college she attended, the major, and the overall GPA (plus a bias scalar b). If we know the weight vector w and the bias scalar b, we can make a prediction of the output value based on its p input attribute values.

“So, how can we determine the weight vector w and the bias scalar b?” Intuitively, we want to learn the “best” weight vector w and the “best” bias scalar b from the training data, so that the lin-