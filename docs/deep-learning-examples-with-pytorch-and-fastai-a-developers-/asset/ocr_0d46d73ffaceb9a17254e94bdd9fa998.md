# 26.1 Using the fastshap Library

Readers’ Caveat : The fastshap library doesn’t look for real causalities within the model. It provides an insight into how the model behaves, given specific inputs.

First we have to import the library:

```
from fastinference.tabular import *
```

Now we can create a ShapInterpretation object. It expects your Learner along with some test data to look at and any keywords that SHAP can use. If you don’t pass anything in, it will use a subset of your validation data for analyzing.

```
exp = ShapInterpretation(learn, df.iloc[:100])
```

# 26.1.1 Decision Plot

The decision plot will visualize a model’s decision by looking at the “SHAP” values for a particular row. You can think of a “SHAP” value as something like the feature importance from our importance permutation model. If you plot too many samples at once it can make your plot illegible.

We are just focusing on the 10th row of our dataframe:

```
df.iloc[10]
```

As we can see, our y value is ‘<50k’. Let’s look at how the model performed and what could have been influencing our result negatively. In other words we are analyzing how each of the features affected the model’s decision.

```
exp.decision_plot(class_id=0, row_idx=10)
```

We can see that if we pass in a class_id of zero and a row_idx, the model determines that we are using a classification model and it is looking for the score of the class <50k. If we want to use a different class, we only have to change the class_id parameter.