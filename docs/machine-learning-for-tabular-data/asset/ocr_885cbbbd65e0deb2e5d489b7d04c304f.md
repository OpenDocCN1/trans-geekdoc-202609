# CHAPTER 4 Classical algorithms for tabular data

| Fold | validation | train |
| :--- | :--- | :--- |
| Fold 1 | | train |
| Fold 2 | train | validation | train |
| Fold 3 | train | validation | train |
| Fold 4 | | validation | train |
| Fold 5 | train | | validation |

**Figure 4.9** How data is distributed between train and validation across
folds of a five-fold cross-validation strategy

and for what purpose you intend to get a performance estimate. As a general rule of
thumb, values of k as 5 or 10 are optimal choices, with k = 10 being more suitable
for precise performance evaluation and k = 5 a good value compromising precision and
computation costs for activities such as model, features, and hyperparameters evalu-
ation (it will be used for our examples).

To get a general performance estimate for your model, you will need the neces-
sary-validation iterations using a series of iterations on the KFold function (https://nng.bz/Xkne) or rely on the `cross_validate` procedure (https://mng.bz/AQyK) that
will handle everything for you and just return the results. For our purposes of testing
different algorithms, `cross_validate` is quite handy because, given the proper param-
iters, it will produce a series of metrics:

+   - Cross-validation test scores (out-of-sample performance)
- Cross-validation train scores (in-sample performance)
- Fit time and predict time (to evaluate the computational cost)
- The trained estimators on the different cross-validation folds

All we have to do is provide an estimator, which can be Seikit-learn object with a
fit method, predictors and target, a cross-validation strategy, and a single or multiple
scoring functions in a list. This estimator should be provided in the form of a call-
table to be created using the `make_scorer` command (https://mng.bz/Ziao). In the
next section, we will start seeing how we can get-validated performance estimates
using such inputs, starting with classical machine learning algorithms such as linear
regression and logistic regression.

# 4.3.1 Linear and logistic regression

In linear regression, a statistical method that models the relationship between a dep-
ent variable and one or more independent variables by fitting a linear equation to