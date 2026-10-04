# Using GPUs for machine learning

This section will focus on how easy it is to replace the Scikit-learn algorithms with the RAPIDS cuML package. Currently, this package includes implementations for linear models, k-NN, and SVMs, as well as for clustering and dimensionality reduction. The following listing shows the code for testing the support vector classifier for the radial basis function kernel we tried in the previous section in its RAPIDS implementation (using a P100 GPU).

Listing B.3 Support vector classifier from RAPIDS cuML

```
from cuml.svm import SVC
from sklearn.metrics accuracy_score

accuracy = make_score(accuracy_score)
c = CV(5, shuffle=True, random_state=0)
model = SVC(
    C=1.0,
    kernel='rbf',
    gamma='scale',
    probability=False)
```

Creates a scoring function using the accuracy_metric

Creates a five-fold cross-validation with shuffling and a fixed random state

Creates an instance of a Support Vector Classifier from the GPU-accelerated cuML library with hyperparameters

```
column_transform = ColumnTransformer(
    ['categorical', categorical_encoding, low_card_categorical],
    ['numeric', numeric_standardization, continuous]),
    remainder='drop',
    verbose_feature_names_out=False,
    sparse_threshold=0.0)

model_pipeline = Pipeline(
    ['processing', column_transform),
    ['modeling', model])

cv_scores = cross_validate(estimator=model_pipeline,
    X=data,
    y=target_median,
    scoring=accuracy,
    cv=cv,
    return_train=True,
    return_estimator=True)
```

Defines a ColumnTransformer to preprocess categorical features with low cardinality and standardization to numerical features

Creates a pipeline that sequentially applies the column transformation and to the data

Performs cross-validation on the data using the defined pipeline, with accuracy scoring

```
mean_cv = np.mean(cv_scores['test_score'])
std_cv = np.std(cv_scores['test_score'])
fit_time = np.mean(cv_scores['fit_time'])
score_time = np.mean(cv_scores['score_time'])
print(f"mean_cv:{0.3f} {std_cv:0.3f}")
print(f"fit_time:{0.2f}")

fsecs pred: {score_time:0.2f} secs
```

Prints the mean and standard deviation of test scores

The results we obtained are

0.821 (0.004) fit: 4.09 secs pred: 0.1 secs