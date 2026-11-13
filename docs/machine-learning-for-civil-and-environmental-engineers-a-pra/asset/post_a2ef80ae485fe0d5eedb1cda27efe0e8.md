

## Example no. 1 [Python, Classification]: Predicting fire-induced spalling of concrete mixtures.

This example repeats that carried out in Example no. 1 in DataRobot. As you remember, we used a dataset of 646 test samples comprising 16 features and one target (with two labels: no spalling or spalling). Our goal is to build a ML algorithm that we can input our dataset into to arrive at a ML model that can precisely predict if a concrete mixture is going to spall or not. We will use the XGBoost algorithm to build such a model, as you can see in the script below. We will also build a web application of this model (visit the Appendix for the complete example on how to do so).

```
#Importing libraries

from xgboost import XGBClassifier
import xgboost as xgb
import seaborn as sns
from matplotlib.pyplot import pyplot
from sklearn.model_selection import train_test_split
import pandas as pd
import numpy as np
from sklearn.metrics import confusion_matrix,classification_report
from sklearn.metrics import plot_confusion_matrix
```

```
#Importing dataset

from pandas import MultiIndex, Int64Index
fire=pd.read_csv('Classification.csv')
```

```
#Printing dataset

fire
```

| | Water/binder ratio (%) | Aggregate/binder ratio (%) | Sand/binder ratio (%) | Heating rate (C/min) | Maximum exposure temperature (C) | Silica fume/binder ratio (%) | Aggregate size (mm) | GGBS/binder ratio (%) | FA/binder ratio (%) | PP fiber quantity (kg/m3) | Output |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 0.273 | 2.000 | 1.049 | 101.0 | 1034 | 0.0 | 7.0 | 0.25 | 0.0 | 0.0 | 1 |
| 1 | 0.273 | 2.000 | 1.049 | 101.0 | 1034 | 0.0 | 14.0 | 0.25 | 0.0 | 0.0 | 1 |
| 2 | 0.300 | 2.000 | 1.033 | 101.0 | 1034 | 0.0 | 20.0 | 0.25 | 0.0 | 0.0 | 1 |
| 3 | 0.218 | 1.374 | 1.199 | 101.0 | 1034 | 0.0 | 7.0 | 0.25 | 0.0 | 0.0 | 1 |
| 4 | 0.218 | 1.374 | 1.199 | 101.0 | 1034 | 0.0 | 7.0 | 0.25 | 0.0 | 0.0 | 1 |
| ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... |
| 641 | 0.200 | 0.000 | 1.040 | 15.0 | 800 | 0.2 | 0.6 | 0.00 | 0.0 | 1.0 | 1 |
| 642 | 0.200 | 0.000 | 1.040 | 15.0 | 800 | 0.2 | 0.6 | 0.00 | 0.0 | 1.5 | 1 |
| 643 | 0.200 | 0.000 | 1.040 | 15.0 | 800 | 0.2 | 0.6 | 0.00 | 0.0 | 2.0 | 1 |
| 644 | 0.200 | 0.000 | 1.040 | 15.0 | 800 | 0.2 | 0.6 | 0.00 | 0.0 | 2.5 | 1 |
| 645 | 0.200 | 0.000 | 1.040 | 15.0 | 800 | 0.2 | 0.6 | 0.00 | 0.0 | 3.0 | 0 |

646 rows x 11 columns

```
#Generate data frame [a two-dimensional data structure (tabular)]

x=fire.drop(['Output'], axis=1)
y=fire['Output']
x_train,x_test,y_train,y_test=train_test_split(x,y,test_size=0.30,random_state=111)
```

```
wb=fire['Output']
pyplot.hist(wb,edgecolor='black')
pyplot.title('Water/binder ratio')
pyplot.xlabel('Ratio')
pyplot.ylabel('No. of samples')
pyplot.show()
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_303_0.png)

```
# Plotting histograms of features
for i, col in enumerate(fire.columns):
    pyplot.figure(i)
    sns.histplot(fire[col])
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_303_1.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_303_2.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_304_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_304_1.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_304_2.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_305_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_305_1.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_305_2.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_306_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_306_1.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_306_2.png)

```
#Execute and fit the algorithm.
xgbc=xgb.XGBClassifier(objective = 'binary:logistic',missing=1,seed=42,learning_rate = 0.05 , max_depth = 3)
xgbc.fit (x_train,y_train,verbose=True,early_stopping_rounds=50,eval_metric='aucpr',eval_set=[(x_test,y_test)])
predictions = xgbc.predict(x_test)
```

[0]validation_0-aucpr:0.67211
[1]validation_0-aucpr:0.67211
[2]validation_0-aucpr:0.74269
...
...
[97]validation_0-aucpr:0.89769
[98]validation_0-aucpr:0.89683
[99]validation_0-aucpr:0.89600

```
class_names = ['no spalling ', 'spalling']
disp = plot_confusion_matrix(xgbc ,x_train, y_train, display_labels=class_names,colorbar=True, cmap=pyplot.cm.Blues, xticks_rotation='vertical')
pyplot.title('Training set')
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_307_0.png)

```
class_names = ['no spalling ', 'spalling']
disp = plot_confusion_matrix(xgbc, x_test, y_test, display_labels=class_names,
cmap=pyplot.cm.Blues, xticks_rotation='vertical')
pyplot.title('Testing set')
print (classification_report(y_test,predictions))
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_308_0.png)

```
r_auc=roc_auc_score(y_test,predictions)
r_auc

0.773320778405524
yhat = xgbc.predict_proba(x_train)

#Retrieve just the probabilities for the positive class
pos_probs = yhat[:, 1]

#Plotting the ROC curve
pyplot.plot([0, 1], [0, 1], linestyle='--')

#Calculating the ROC curve
fpr, tpr, _ = roc_curve(y_train, pos_probs)

#Plotting the ROC curve
pyplot.plot(fpr, tpr, marker='.', label='AUC=0.907')

#Adding axis labels
pyplot.xlabel('False Positive Rate')
pyplot.ylabel('True Positive Rate')

#Showing legend
pyplot.legend()
pyplot.title('Training set')

#Showing the plot
pyplot.show()
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_309_0.png)

```
yhat = xgbc.predict_proba(x_test)
#Retrieve just the probabilities for the positive class
pos_probs = yhat[:, 1]
#Plotting the ROC curve
pyplot.plot([0, 1], [0, 1], linestyle='--')
#Calculating the ROC curve
fpr, tpr, _ = roc_curve(y_test, pos_probs)
#Plotting the ROC curve
pyplot.plot(fpr, tpr, marker='.', label='AUC=0.866')
#Adding axis labels
pyplot.xlabel('False Positive Rate')
pyplot.ylabel('True Positive Rate')
#Showing legend
pyplot.legend()
pyplot.title('Testing set')
#Showing the plot
pyplot.show()
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_309_1.png)

Comparing the performance of the model from Python to that in DataRobot, it is clear that the latter achieves better performance in terms of the AUC metric.

## Example no. 2 [Python, Regression]: Predicting axial strength of CFSTs.

Let us repeat the second example of DataRobot. As you remember, our dataset has 1260 CFSTs where each column has the following features: column diameter, D (mm), column thickness, t (mm), column length, L (mm), compressive strength of concrete f'c (MPa), and steel yielding stress, fy (MPa). The axial compressive strength N (kN) comprises the target for each column. We will be using the Random Forest algorithm.

The Python code script for this example is provided below.

```
#Importing libraries
import pandas as pd
from pandas import MultiIndex, Int64Index
import numpy as np
import xgboost as xgb
from sklearn.ensemble import RandomForestRegressor
from sklearn.model_selection import train_test_split
from matplotlib import pyplot
import seaborn as sns
```

```
#Importing error metrics
from sklearn.metrics import mean_squared_error
from sklearn.metrics import accuracy_score
from sklearn.metrics import r2_score
```

```
#Importing dataset
CFST=pd.read_csv('CFST.csv')
CFST.head(5) #Printing the first five rows of the data
```

| D (mm) | t (mm) | L (mm) | fy (MPa) | fc (MPa) | N Test (kN) |
|---|---|---|---|---|---|
| 0 | 168.8 | 2.64 | 305.0 | 302.4 | 18.2 | 1326.0 |
| 1 | 168.8 | 2.64 | 305.0 | 302.4 | 34.7 | 1219.0 |
| 2 | 169.3 | 2.62 | 305.0 | 338.1 | 37.1 | 1308.0 |
| 3 | 169.3 | 2.62 | 305.0 | 338.1 | 34.1 | 1330.0 |
| 4 | 168.3 | 3.60 | 305.0 | 288.4 | 27.0 | 1557.0 |

```
CFST.dtypes

D (mm)    float64
t (mm)    float64
L (mm)    float64
fy (MPa)  float64
fc (MPa)  float64
N Test (kN)    float64
dtype: object
```

#Try the agg function to aggregate data into a summary
#of statistical insights for the parameters of the dataset.

```
Statistical_insights=CFST.agg(
    {
    "D (mm)": ["min", "max", "median", "skew", "std", "mean"],
    "t (mm)": ["min", "max", "median", "skew", "std", "mean"],
    "L (mm)": ["min", "max", "median", "skew", "std", "mean"],
```

