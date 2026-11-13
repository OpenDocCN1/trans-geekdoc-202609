![](bbox=[0.08, 0.08, 0.9, 0.42])

Figure 7.14 LIME visualization for an individual instance [Note: Each feature has two values associated with it. The first shows the critical range related to the direction of the prediction, and the second shows the contribution of that feature to the prediction].

This plot shows that our model predicts a no spalling occurrence (which agrees with our observation). To see how the model arrives at the Zero value, we will need to sum the following contributions:

> Local prediction = base vlaue + \(\sum\) summation of features
> 
> Local prediction = 0.0 = +0.236 − 0.49 + 0.25 − 0.23 + 0.18 + 0.12 − 0.08 + 0.03 − 0.02 − 0.02. (7.8)

Further, these plots show the top features that have resulted in this prediction. For example, including PP fibers in the concrete mix of the amount of 1.5 kg/m³ and the absence of silica fume have significantly pushed the prediction toward no spalling. In contrast, relatively high moisture content of 4.1% and a heating rate of 66°C/min pushed the prediction to the opposite side. Luckily, the contribution of the first-mentioned features overcome those of the latter.

The explainability analysis from the LIME method can also be examined on the same specimen (see Figure 7.14). As you can see, the prediction probability of no spalling is 84%. Looking at this figure also shows that the same features that push toward no spalling and toward spalling are similar to those obtained from SHAP.77

Here is the Python code to repeat this example while showing different specimens.

```
#Importing the libraries
from xgboost import XGBClassifier
import xgboost as xgb
from scipy import stats
import seaborn as sns
from pandas import MultiIndex
from matplotlib import pyplot
from sklearn.model_selection import train_test_split
from sklearn.metrics import roc_curve
import pandas as pd
import numpy as np
```