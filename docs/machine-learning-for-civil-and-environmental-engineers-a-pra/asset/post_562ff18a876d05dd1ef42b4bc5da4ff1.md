
```
importances = xgbc.feature_importances_
indices = np.argsort(importances)
features = x.columns
pyplot.title('Feature Importances')
pyplot.barh(range(len(indices)), importances[indices], color='g', align='center')
pyplot.yticks(range(len(indices)), [features[i] for i in indices])
pyplot.xlabel('Relative Importance')
pyplot.show()
# The problem with global importance is that it gives an average overview of variable contributing to the model
# but it lacks the direction of impact means whether a variable has a positive or negative influence.
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_395_0.png)

```
#in a more perfect world, I would more prefer the use of correlations attained from mutual information (shown in the next page) and/or point-biserial correlation to Pearson or Spearman methods - since our data has binary output.
l=fire.corr()
l
```

```
sns.heatmap(l, annot=True)
sns.set(rc = {'figure.figsize':(4,3)})
pyplot.title("Pearson Correlation")
pyplot.show()
def display_correlation(df):
    r = df.corr(method="spearman")
    pyplot.figure(figsize=(22,12))
    heatmap = sns.heatmap(df.corr(), vmin=-1,
                          vmax=1, annot=True)
    pyplot.title("Spearman Correlation")
    return(r)
r_simple=display_correlation(l)
```

| Variable |
| --- |
| Water/binder ratio (%) |
| Aggregate/binder ratio (%) |
| Sand/binder ratio (%) |
| Heating rate (C/min) |
| Moisture content (%) |
| Maximum exposure temperature (C) |
| Silica fume/binder ratio (%) |
| Aggregate size (mm) |
| GGBFS/binder ratio (%) |
| FA/binder ratio (%) |
| PP fiber quantity (kg/m3) |
| PP fiber diameter(mm) |
| PP fiber length (mm) |
| Steel fiber quantity (kg/m3) |
| Steel fiber diameter(mm) |
| Steel fiber length (mm) |
| Output |

```
mi=mutual_info_classif(x,y)
len(mi)
mi
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_397_0.png)

```
import shap

explainer = shap.TreeExplainer(xgbc)
shap_values = explainer.shap_values(x_test)
shap.summary_plot(shap_values, x_test, plot_type="bar")
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_398_0.png)

```
shap.summary_plot(shap_values, x_test, show=False)
pyplot.gcf().axes[-1].set_box_aspect(50)
pyplot.gcf().axes[-1].set_aspect(100)
pyplot.gcf().axes[-1].set_box_aspect(100)
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_398_1.png)

```
shap_interaction_values = shap.TreeExplainer(xgbc).shap_interaction_values(x_test.iloc[:18, :])
```

```
shap.summary_plot(shap_interaction_values, x_test.iloc[:18, :])
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_399_0.png)

```
shap.dependence_plot("Maximum exposure temperature (C)", shap_values, x_test, interaction_index=None)
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_399_1.png)

```
shap.dependence_plot("PP fiber quantity (kg/m3)", shap_values, x_test,)
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_400_0.png)

```
shap.dependence_plot("Moisture content (%)", shap_values, x_test,xmin="percentile(30)", xmax="percentile(90)")
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_400_1.png)

```
shap.dependence_plot(3, shap_values, x_test, xmin="percentile(20)", xmax="percentile(99)")
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_401_0.png)

```
shap.dependence_plot(7, shap_values, x_test, xmin="percentile(1)", xmax="percentile(99)")
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_401_1.png)

We can use shap.approximate_interactions to guess which features may interact with maximum exposure temperature

```
inds = shap.approximate_interactions("PP fiber quantity (kg/m3)", shap_values, x_test)
```

Make plots colored by each of the top three possible interacting features

Explainer = shap.Explainer(xgbc)

```
xgb_binary_shap_values = explainer(x_test)
expected_value = explainer.expected_value
print("The expected value is ", expected_value)
shap_values_p = explainer.shap_values(x_test)[1]
shap.decision_plot(expected_value, shap_values_p, x_test)
```

The expected value is -1.0156575

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_402_0.png)

```
test_objects = [x_test.iloc[0:17], x_test.iloc[191:192]]
for float in test_objects:
    print ('Probability of class 1 = {:.4f}'.format(xgbc.predict_proba(float)[0][1]))
    print ('Formula raw prediction = {:.4f}'.format(xgbc.predict(float)[0]))
    print ('\n')
```

Probability of class 1 = 0.5410
Formula raw prediction = 1.0000

Probability of class 1 = 0.0275
Formula raw prediction = 0.0000

```
shap.initjs()
def p(j):
    explainer
    xgbc_shap_values = explainer.shap_values(x_test)
    return(shap.force_plot(explainer.expected_value, xgbc_shap_values[j,:, x_test.iloc[j,:], link='logit'))
p(0)
```

The waterfall is another way of plotting the force plot.

```
shap.plots.waterfall(xgb_binary_shap_values[0])
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_403_1.png)

```
def xgb_shap_transform_scale(original_shap_values, Y_pred, which):
    from scipy.special import expit

    #Compute the transformed base value, which consists in applying the logit function to the base value
    from scipy.special import expit #Importing the logit function for the base value transformation
    untransformed_base_value = original_shap_values.base_values[-1]

    #Computing the original_explanation_distance to construct the distance_coefficient later on
    original_explanation_distance = np.sum(original_shap_values.values, axis=1)[which]

    base_value = expit(untransformed_base_value)  # = 1 / (1+ np.exp(-untransformed_base_value))

    #Computing the distance between the model_prediction and the transformed base_value
    distance_to_explain = Y_pred[which] - base_value

    #The distance_coefficient is the ratio between both distances which will be used later on
    distance_coefficient = original_explanation_distance / distance_to_explain

    #Transforming the original shapley values to the new scale
    shap_values_transformed = original_shap_values / distance_coefficient

    #Finally resetting the base_value as it does not need to be transformed
    shap_values_transformed.base_values = base_value
    shap_values_transformed.data = original_shap_values.data

    #Now returning the transformed array
    return shap_values_transformed

obs = 0

print("The prediction is ", predictions[obs])
shap_values_transformed = xgb_shap_transform_scale(xgb_binary_shap_values, predictions, obs)
shap.plots.waterfall(shap_values_transformed[obs])
shap.force_plot(shap_values_transformed[obs])
```

The prediction is 1

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_405_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_405_1.png)

```
import numpy as np
import pandas as pd
from sklearn.datasets import make_hastie_10_2
from sklearn.ensemble import GradientBoostingClassifier
from sklearn.inspection import PartialDependenceDisplay
```

```
features = ["#PP fiber quantity (kg/m3)",
"Moisture content (%)", "Maximum exposure temperature (C)", "Silica fume/binder ratio (%)",
#"Heating rate (C/min)","Sand/binder ratio (%)","Water/binder ratio (%)","FA/binder ratio (%)"
]

PartialDependenceDisplay.from_estimator(xgbc, x_train, features, kind='both')

#display.plot(n_cols=5)
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_406_0.png)

```
from sklearn.inspection import PartialDependenceDisplay

common_params = {   "subsample": 200,
    "n_jobs": 2,
    "grid_resolution": 20,
    "random_state": 0,
    #   "subsample": 300,
    #   "n_jobs": 2,
    #   "grid_resolution": 20,
    #   "random_state": 0,
}

print("Computing partial dependence plots...")

display = PartialDependenceDisplay.from_estimator(
    xgbc,
    X_test,
    features=["#PP fiber quantity (kg/m3)",
              #   "Moisture content (%)",
              #   "Maximum exposure temperature (C)",
              #   "Silica fume/binder ratio (%)",
                  # "Heating rate (C/min)",
              #   "Sand/binder ratio (%)",
                  # "Water/binder ratio (%)",
                  "FA/binder ratio (%)"
              ],
    kind="both",
    **common_params,
)
```
