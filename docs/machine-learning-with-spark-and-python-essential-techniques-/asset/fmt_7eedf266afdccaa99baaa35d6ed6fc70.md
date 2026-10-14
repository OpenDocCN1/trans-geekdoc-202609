
[Listing 7-8](#c07.xhtml#c07-fea-0008) follows a similar outline to the code used for detecting mines. In this example, a more manual method is used to deal with class imbalance so you can visualize how this might work. The input data are separated by class and then each class is separately split into 70:30 train test sets. Then class-by-class train sets are aggregated into an overall train set and similar for the test sets.

#### [Listing 7-8](#c07.xhtml#R_c07-fea-0008): Build a Random Forest Model to Distinguish Different Glass Types—glass\_rf.py

```
__author__ = 'mike_bowles'

from math import sqrt, fabs, exp
import matplotlib.pyplot as plt
from sklearn.metrics import accuracy_score, confusion_matrix, roc_curve
from sklearn.model_selection import train_test_split
from sklearn import ensemble
import numpy as np
from Read_Fcns import list_read_glass

#read in glass data
names, xNum, labels, yOneVAll = list_read_glass()

glassNames = np.array(['RI', 'Na', 'Mg', 'Al', 'Si', 'K', 'Ca', 'Ba', 'Fe',
                       'Type'])

#number of rows and columns in x matrix
nrows = len(xNum)
ncols = len(xNum[1])

#Labels are integers from 1 to 7 with no examples of 4.
#gb requires consecutive integers starting at 0
newLabels = []
labelSet = set(labels)
labelList = list(labelSet)
labelList.sort()
nlabels = len(labelList)
for l in labels:
    index = labelList.index(l)
    newLabels.append(index)

#Class populations:
#old label     new label     num of examples
#1              0               70
#2              1               76
#3              2               17
#5              3               13
#6              4               9
#7              5               29
# 
#Drawing 30% test sample may not preserve population proportions

#stratified sampling by labels.
xTemp = [xNum[i] for i in range(nrows) if newLabels[i] == 0]
yTemp = [newLabels[i] for i in range(nrows) if newLabels[i] == 0]
xTrain, xTest, yTrain, yTest = train_test_split(xTemp, yTemp,
test_size=0.30,
                                                random_state=531)
for iLabel in range(1, len(labelList)):
    #segregate x and y according to labels
    xTemp = [xNum[i] for i in range(nrows) if newLabels[i] == iLabel]
    yTemp = [newLabels[i] for i in range(nrows) if newLabels[i] == 
                iLabel]

    #form train and test sets on segregated subset of examples
    xTrainTemp, xTestTemp, yTrainTemp, yTestTemp = train_test_split(xTemp, 
                                yTemp, test_size=0.30, random_state=531)

    #accumulate
    xTrain = np.append(xTrain, xTrainTemp, axis=0)
    xTest = np.append(xTest, xTestTemp, axis=0)
    yTrain = np.append(yTrain, yTrainTemp, axis=0)
    yTest = np.append(yTest, yTestTemp, axis=0)

num_iterations = 50
trees_per_iteration = 10
depth = None
maxFeat  = 4 #try tweaking

glassRFModel = ensemble.RandomForestClassifier(
                       n_estimators=trees_per_iteration, 
                       max_depth=depth, 
                       max_features=maxFeat,
                       oob_score=False, 
                       random_state=531, 
                       warm_start=True)    
   
missCLassError = []

for iteration in range(num_iterations):
    
    glassRFModel.fit(xTrain,yTrain)
    glassRFModel.n_estimators += trees_per_iteration
    
    #Accumulate auc on test set
    prediction = glassRFModel.predict(xTest)
    correct = accuracy_score(yTest, prediction)
  
    missCLassError.append(1.0 - correct)

print("Misclassification Error" )
print(missCLassError[-1])

#generate confusion matrix
pList = prediction.tolist()
confusionMat = confusion_matrix(yTest, pList)
print('')
print("Confusion Matrix")
print(confusionMat)

#plot training and test errors vs number of trees in ensemble
num_trees = [i * trees_per_iteration for i in range(num_iterations)]
plt.plot(num_trees, missCLassError)
plt.xlabel('Number of Trees in Ensemble')
plt.ylabel('Misclassification Error Rate')
plt.title('Random Forest Classifier Perf on Glass Data')
plt.savefig('rf_glass_perf.png', dpi=500)
#plt.ylim([0.0, 1.1*max(mseOob)])
plt.show()

# Plot feature importance
featureImportance = glassRFModel.feature_importances_

# normalize by max importance
featureImportance = featureImportance / featureImportance.max()

#plot variable importance
idxSorted = np.argsort(featureImportance)
barPos = np.arange(idxSorted.shape[0]) + .5
plt.barh(barPos, featureImportance[idxSorted], align='center')
plt.title('RF Variable Importance on Glass Data')
plt.yticks(barPos, glassNames[idxSorted])
plt.xlabel('Relative Variable Importance')
plt.savefig('rf_glass_var_importance.png', dpi=500)
plt.show()


Printed Output:
Misclassification Error
0.2272727272727273

Confusion Matrix
[[17  2  1  0  0  1]
 [ 2 18  1  2  0  0]
 [ 2  0  4  0  0  0]
 [ 0  1  0  3  0  0]
 [ 0  1  0  0  2  0]
 [ 0  2  0  0  0  7]] 
```

The code generates random forest models and plots the training progress and the variable importance. It also prints out a confusion matrix which shows how the prediction model treats each class in the data population. It show how many from each class the predictor maps to the correct class and how many it maps to the wrong classes. If the classifier is perfect, there should be no off-diagonal entries in the matrix.

### Determining the Performance of the Random Forest Model on Glass Classification

[Figure 7.15](#c07.xhtml#c07-fig-0015) shows how the performance of random forest improves as more trees are included in the ensemble. The curve generally drops as more trees are added. The rate of improvement decreases as more trees are added. It has slowed considerably at the point where the graph stops.

![Figure 7.15: The overall performance of random forests](images/c07f015.png)

[**Figure 7.15**](#c07.xhtml#R_c07-fig-0015): The overall performance of random forests

![Figure 7.16: The relative importance of the variables used by random forest](images/c07f016.png)

[**Figure 7.16**](#c07.xhtml#R_c07-fig-0016): The relative importance of the variables used by random forest

[Figure 7.16](#c07.xhtml#c07-fig-0016) is a bar chart showing the relative importance of the variables used by random forests. The chart shows that a number of the variables are roughly equal in performance. This is unusual behavior. In many cases the variable importance drops off quickly after the first few variables. This problem contains several equally important variables.

## Solving Regression Problems with PySpark Ensemble Packages

This section will run through the examples you've seen throughout the book and demonstrate how to use ensemble methods available in PySpark to build a model for each example. This section combines what you learned about in [Chapter 5](#c05.xhtml) and what you've just seen about using ensemble methods to build models. Using ensemble methods in PySpark involves the exact same data preparation steps that you saw in [Chapter 5](#c05.xhtml), and uses the same gradient boosting and random forest algorithms that you've learned so far in this chapter. The PySpark gradient boosting and random forest algorithms have the same parameters to twiddle as what you've seen earlier. Once the data is prepped as it was in [Chapter 5](#c05.xhtml), it's just a matter of learning some slight differences in notation and variable names.
