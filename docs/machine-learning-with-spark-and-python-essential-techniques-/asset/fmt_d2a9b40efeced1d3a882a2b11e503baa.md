
# Gradient Boosting

Gradient boosting was developed by Stanford professor Jerome Friedman, who also developed the coordinate descent algorithm used to solve the ElasticNet problem (in [Chapters 4](#c04.xhtml) and [5](#c05.xhtml)). Gradient boosting develops an ensemble of tree-based models by training each of the trees in the ensemble on different labels and then combining the trees. For a regression problem where the objective is to minimize MSE, each successive tree is trained on the errors left over by the collection of earlier trees. For the derivation of the algorithm, see the "References" section at the end of this chapter. The easiest way to see how gradient boosting works is to look at some code implementing the algorithm.

## Basic Principle of Gradient Boosting Algorithm

[Listing 6-6](#c06.xhtml#c06-fea-0006) details the gradient boosting algorithm for the synthetic problem introduced earlier in this chapter. The early part of the code uses the process from earlier to build the synthetic data set.

### [Listing 6-6](#c06.xhtml#R_c06-fea-0006): Gradient Boosting for Simple Problem—simpleGBM.py

```python
__author__ = 'mike-bowles'

import numpy as np
import matplotlib.pyplot as plt
from sklearn import tree
from sklearn.tree import DecisionTreeRegressor
from math import floor
from numpy.random import choice

# Build a simple data set with y = x + random
nPoints = 1000

# x values for plotting
x = np.linspace(-0.5, 0.5, nPoints)
x_feat = x.reshape([-1, 1])

# y (labels) has random noise added to x-value
# set seed
np.random.seed(1)
y = x + np.random.randn(nPoints) * 0.1

# take fixed test set 30% of sample
indices = list(range(nPoints))
nSample = int(nPoints * 0.30)
idxTest = choice(indices, nSample, replace=False)
idxTest.sort()
idxTrain = [idx for idx in indices if not (idx in idxTest)]

# Define test and training attribute and label sets
xTrain = x_feat[idxTrain]
xTest = x_feat[idxTest]
yTrain = y[idxTrain]
yTest = y[idxTest]
idx_Train = list(range(len(xTrain)))

# train a series of models on random subsets of the training data
# collect models in a list and check error of composite as list grows

# maximum number of models to generate
numTreesMax = 30

# tree depth - typically at the high end
treeDepth = 5

# initialize a list to hold models
modelList = []
predList = []
eps = 0.3

# initialize residuals to be the labels y
residuals = yTrain

for iTrees in range(numTreesMax):

    modelList.append(DecisionTreeRegressor(max_depth=treeDepth))
    modelList[-1].fit(xTrain, residuals)

    # make prediction with latest model and add to list of predictions
    latestInSamplePrediction = modelList[-1].predict(xTrain)

    # use new predictions to update residuals
    residuals -= eps * latestInSamplePrediction

    latestOutSamplePrediction = modelList[-1].predict(xTest)
    predList.append(latestOutSamplePrediction)


# build cumulative prediction from first "n" models
mse = []
allPredictions = []
for iModels in range(len(modelList)):

    # add the first "iModels" of the predictions and multiply by eps
    prediction_i = np.zeros_like(predList[0])
    for i in range(iModels):
        prediction_i += predList[i] * eps

    allPredictions.append(prediction_i)
    errors = yTest - prediction_i
    mse.append(np.average(errors * errors))

nModels = [i + 1 for i in range(len(modelList))]

plt.plot(nModels, mse)
plt.axis('tight')
plt.xlabel('Number of Models in Ensemble')
plt.ylabel('Mean Squared Error')
plt.title('Error vs Ensemble Size - Depth = ' + str(treeDepth))
plt.savefig('simple_gbm_error_vs_trees_' + str(treeDepth) + str(eps) +
            '.png', dpi=500)
plt.ylim((0.0, max(mse)))
plt.show()

plotList = [0, 3, 29]
lineType = [':', '-.', '--']
plt.figure()
for i in range(len(plotList)):
    iPlot = plotList[i]
    textLegend = 'Prediction with ' + str(iPlot + 1) + ' Trees'
    plt.plot(xTest, allPredictions[iPlot], label=textLegend,
             linestyle=lineType[i])
plt.plot(xTest, yTest, label='True y Value', alpha=0.25)
plt.legend(bbox_to_anchor=(1, 0.3))
plt.axis('tight')
plt.xlabel('x value')
plt.ylabel('Predictions')
plt.title('Actual vs Predictions - Depth= ' + str(treeDepth))
plt.savefig('simple_gbm_real_vs_pred_' + str(treeDepth) + str(eps) +
            '.png', dpi=500)
plt.show()
```

## Parameter Settings for Gradient Boosting

The first thing that looks unfamiliar is the comment about setting the depth parameter for the individual trees being trained in a gradient boosting ensemble. Gradient boosting differs from bagging and random forests in that it can reduce bias in addition to reducing variance. Gradient boosting has the useful property that it will often perform as well as low MSE values with stumps as with deeper trees. With gradient boosting, tree depth is only required to the extent that there's a significant interaction between variables. Performance improvement from increasing tree depth serves as a gauge of variable interaction in your problem.

The next thing that looks a little different is the definition of a variable called `eps`. This variable is a step size control of the sort that you may be familiar with from optimization problems. Gradient boosting takes gradient descent steps and, as with other gradient descent processes, if the steps are too large the optimization can diverge instead of converging. If the step size is too small, the process can take too many iterations. After generating some results, the chapter will talk about how to tune `eps`, the step size.

The next unfamiliar element of the code is the definition of a variable called `residuals`. The term *residuals* is commonly used to denote prediction errors (that is, observed values minus predicted values). The gradient boosting algorithm will make a series of refinements to its predictions of the labels. At each step along the way, the residuals will get recalculated. At the beginning of the process, gradient boosting initializes predictions to null (or zero) values so that the residuals are equal to the observed labels.

## How Gradient Boosting Iterates toward a Predictive Model

The loop on `iTrees` begins by training a tree using the attributes, but training on the residuals instead of the labels. Only for the first pass are the raw labels used for training targets. Subsequent passes take the predictions generated by training and subtract `eps` of them from the residuals before training. As mentioned, the subtraction of the residuals amount to a gradient descent and the reason for multiplying by the step size control parameter `eps` is to make sure that the iterative process converges. The code uses a fixed holdout set to measure out-of-sample performance and then plots the MSE as a function of the number of trees trained, and also plots the function showing predicted values versus the single attribute.

## Getting the Best Performance from Gradient Boosting

The first pair of plots (see [Figures 6.18](#c06.xhtml#c06-fig-0018) and [6.19](#c06.xhtml#c06-fig-0019)) shows the MSE versus number of trees and the plot of the prediction functions with `eps = 0.1` and `treeDepth = 1`. [Figure 6.18](#c06.xhtml#c06-fig-0018) shows that the error decreases smoothly and reaches roughly 0.014 after training 30 trees, and the MSE is heading down, indicating that it could be reduced further by training still more trees.

![Figure 6.18: MSE versus number of trees for synthetic problem—eps = 0.1, treeDepth = 1](images/c06f018.png)

**Figure 6.18**: MSE versus number of trees for synthetic problem—eps = 0.1, treeDepth = 1
