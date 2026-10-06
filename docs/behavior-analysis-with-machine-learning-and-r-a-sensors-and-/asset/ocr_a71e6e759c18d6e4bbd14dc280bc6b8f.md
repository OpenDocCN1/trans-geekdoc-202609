# CHAPTER 5. PREPROCESSING BEHAVIORAL DATA

![](bbox=[0.118, 0.093, 0.881, 0.281])

Figure 5.11: Shiny app with SMOTE example.

# ## 5.5 Information Injection

The purpose of dividing the data into train/validation/test sets is to be able to accurately estimate the generalization performance of a predictive model when it is presented with previously unseen data points. So, it is advisable to construct such splits in a way that they are independent as possible. Often, before training a model and generating predictions out of it, the data needs to be preprocessed. Preprocessing operations may include imputing missing values, normalizing, and so on. During those operations, information can be inadvertently transferred from the train to the test set thus, violating the assumption that they are independent.

> Information injection occurs when information from the train set is transferred to the test set. When having train/validation/test sets information injection occurs when information from the train set leaks into the validation and/or test set. It also happens when information from the validation set is transferred to the test set.

As one of the preprocessing steps, you need to subtract the mean value for each feature for a given instance. For now, suppose a dataset has a single feature $x$ of numeric type and a categorical variable $y$. The dataset has $n$ rows. As a preprocessing step, you decide that you need to subtract the mean of $x$ from each data point. Since you want to predict $y$ given $x$, you train a classifier by splitting your data into train and test sets as usual. You proceed with the steps depicted in Figure 5.12.

First (a), you could the *mean* value of the variable $x$ from the entire dataset. This *mean* is known as the parameter. In this case, there is only one parameter but there could be several. For example, we could additionally need to know the standard deviation. Once