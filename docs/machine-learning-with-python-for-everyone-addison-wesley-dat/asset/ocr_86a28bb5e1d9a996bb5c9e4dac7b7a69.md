# More Regression Methods

```
#setup
from mlwpy import *
%matplotlib inline
diabetes = datasets.load_diabetes()
d_tts = skms.train_test_split(diabetes.data,
                              diabetes.target,
                              test_size=.25,
                              random_state=42)
(diabetes_train_ftrs, diabetes_test_ftrs,
 diabetes_train_tgt, diabetes_test_tgt) = d_tts
```

We are going to dive into a few additional techniques for regression. All of these are variations on techniques we've seen before. Two are direct variations on linear regression, one splices a support vector classifier with linear regression to create a Support Vector Regressor, one uses decision trees for regression instead of classification. As such, much of what we'll talk about will be somewhat familiar. We'll also discuss how to build a learner of our own that plugs directly into sklearn's usage patterns. Onward!



As we briefly discussed in Section 5.4, we can conceptually define the goodness of a model as a cost that has two parts: (1) what we lose, or spend, when we make a mistake and (2) what we invest, or spend, into the complexity of our model. The math is pretty easy here: cost = loss(errors) + complexity. Keeping mistakes low keeps us accurate. If we keep the complexity low, we also keep the model simple. In turn, we also improve our ability to