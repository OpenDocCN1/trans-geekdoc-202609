
# CHAPTER 4 Classical algorithms for tabular data

Interestingly, regularization is also used in neural networks. Neural networks perform sequential multiplications based on matrices of coefficients to transit from predictions, which is an extension of the working of linear regression. Neural networks have more complexities; yet in such an aspect of multiplication, they resemble a regression. Based on similar workings, you may find beneficial for your data problem to find a deep learning architecture, and in doing so, to apply an L2 penalty, so the coefficients of the networks are attenuated and distributed, or an L1 penalty, so coefficients are sparse with many of them to zero. In the next section, we will continue our discussion of linear models by discovering how to solve a classification problem.

## 4.3.3 Logistic regression

The linear regression model can be effectively extended to classification. In a binary classification problem, where you have two classes (a positive one and a negative one), you use the same approach as in a regression (feature matrix, vector of coefficients, bias). Still, you transform the target using the log function (for details about this distribution, see https://mg.bz/JY20). The transformation is called the link function. On the optimization side, the algorithm uses a Bernoulli distribution (for revising this distribution, see https://mg.bz/wjoj) instead of the normal distribution. And as you get output values from 0 to 1, representing the probability that the sample belongs to the positive class. This is called logistic regression. Logistic regression is quite an intuitive and practical approach to solving binary classification problems and multiclass and multilabel ones.

In 4.7, we recount the same approach as seen with linear regression—this time to build a model to guess if an example has a target value above the median. Please note that transformations are the same, though we use a logistic regression model time. Our target is a class that tells if the target value is above the median. Such a target is a binary balanced outcome, where half of the labels are positive and half are negative.

## 4.7 Logistic regression

```python
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import make_scorer, accuracy_score
```

accuracy = make_scorer(accuracy_score)
cv = KFold(5, shuffle=True, random_state=0)
model = LogisticRegression(solver='saga', penalty=None, max_iter=1000) # Logistic regression model instance with the 'saga' solver, no penalty, and a maximum of 1000 iterations.

```python
column_transform = ColumnTransformer(
  [('categories', categorical_onehot_encoding, low_card_categorical),
   ('numeric', numeric_standardization, continuous)],
  remainder='drop', feature_names_out=False, sparse_threshold=0.0
)
```

> Column transformer that applies one-hot encoding to categorical features and standardization to numeric features

```python
model_pipeline = Pipeline([
    ('processing', column_transform),
    ('modeling', model)])
cv_scores = cross_validate(
    estimator=model_pipeline,
    X=data,
    y=target_multiclass,
    scoring='accuracy',
    cv=cv,
    return_train_score=True,
    return_estimator=True)
```

> Pipeline that sequentially applies transformation and logistic regression modeling

```python
mean_cv = np.mean(cv_scores['test_score'])
std_cv = np.std(cv_scores['test_score'])
fit_time = np.mean(cv_scores['fit_time'])
score_time = np.mean(cv_scores['score_time'])
print(f"mean: {mean_cv:0.3f}")
print(f"fit: {fit_time:0.2f}")
print(f"secs pred: {score_time:0.2f} secs")
```

> Cross-validation using the defined pipeline and calculating accuracy scores

> Prints the mean and standard deviation of the test accuracy scores from cross-validation

The script results in the following:
0.821 (0.004) fit: 3.0 secs pred: 0.02 secs

As the feature is being processed, we just focus on how logistic regression works with respect to linear regression. In particular, can set the penalty without changing the algorithm and decide what optimizer will be used. Each optimizer allows specific penalties and can be more or less efficient based on the characteristics of your data:
- lbfgs for L2—better for smaller datasets
- newton for L2—limited to one-versus-rest schemas for multiclass problems
- newton-cg for L2
-- for no penalty—ideal for large datasets
- saga for L1, L2, elasticnet (a mix of L1 and L2)—ideal for large datasets

In listing 4.8, we use an L2 penalty on the multiclass target to handle multiple target and builds a binary model for each class using multi_class parameter set to "ovr". At prediction time, all probabilities are normalized to sum 1 (an approach used in neural networks where a vector of arbitrary values is turned into a probability distribution, the sum of all elements is 1), and the class corresponding to the highest probability taken is the predicted class. Such an approach is analogous to softmax. The alternative to the one-versus-rest approach is the multinomial option, where a single regression model models the probability distribution across classes simultaneously. The multinomial approach is preferred when inter-class relationships are important (e.g., for ranking or confidence-based decisions) or when a compact, single-model solution is desired.

Listing 4.8 L2 regularized multiclass linear regression Logistic regression model instance with L2 penalty, C=0.1, "sag" solver, "ovr" multiclass strategy

```python
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import make_scorer, accuracy_score
```

accuracy = make_scorer(accuracy_score)
cv = KFold(5, shuffle=True, random_state=0)
model = LogisticRegression(penalty="l2", C=0.1, solver="sag", multi_class="ovr", max_iter=1000)
column_transform = ColumnTransformer(
  (['categories', categorical_encoding, low_card_categorical),
   (['numeric', numeric_standardization, continuous]),
  remainder='drop',
feature_names_out=False,
sparse_threshold=0.0)
```

> Column transformer that applies one-hot encoding to categorical features and standardization to numeric features

```python
model_pipeline = Pipeline([
  ('processing', column_transform),
  ('modeling', model)])
cv_scores = cross_validate(
  estimator=model_pipeline,
  X_data,
  y=target_multiclass,
  scoring='accuracy',
  cv=cv,
  return_train_score=True,
  return_estimator=True)
```

> Pipeline that sequentially applies transformation and logistic regression modeling

```python
mean_cv = np.mean(cv_scores['test_score'])
std_cv = np.std(cv_scores['test_score'])
fit_time = np.mean(cv_scores['fit_time'])
score_time = np.mean(cv_scores['score_time'])
print(f"mean: {mean_cv:0.3f}")
print(f"fit: {fit_time:0.2f}")
print(f"secs pred: {score_time:0.2f} secs")
```

> Cross-validation using the defined pipeline and calculating accuracy scores

> Prints the mean and standard deviation of the test accuracy scores from cross-validation

Predicting the target as a class is greatly more complicated than guessing the target price is over a threshold value or not:

![](img/def89cc476fa39f4c54bd34e78d91674_144_0.png)

## 4.3.4 Generalized linear methods

The idea of extending regression to binary classification by logit transformation can be applied to distributions other than Bernoulli distribution. This is dictated by the target that may represent categorical data, count data, or other data whose distribution is known not to be normal. As we have seen in the previous paragraph, multiclass problems can be modeled using the Bernoulli distribution (the one-vs-rest strategy of fitting multiple regressions) and the multinomial one. Other problems, more typical of domains such as insurance, require different approaches. For instance, the Scikit-learn package mentions real-world applications and their best-distributions (for reference, see https://mg.bz/7py9):

- Climate modeling—Number of events per year (Poisson distribution for count data and used for modeling events such as the number of calls to a call center or the number of customers visiting a restaurant), amount of rainfall per event (using Gamma distribution, a theoretical distribution useful for modeling because of its skewness and long tail), or total precipitation per year (Tweedie distribution, a distribution which is a compound of Poisson and Gamma distributions).
- Risk modeling and insurance policy pricing—Claim of events per year (Poisson), cost per event (Gamma), the total cost per policyholder per year (Tweedie)
- Predictive maintenance—Number of production events per year (Poisson), the duration of interruption (Gamma), and the total interruption per year (Tweedie)

Figure 4.11 shows the three distributions—Poisson, Tweedie, and Gamma—for different averages. The Tweedie distribution is calculated for power equal to 1.5, a blend between the Poisson and Gamma distributions.
