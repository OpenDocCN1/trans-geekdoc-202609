
# CHAPTER 5 Decision trees and gradient boosting

- Using a linear scan and histograms, determining the best split for the feature and computing the information gain
- Picking the best solution among all the features and their best split

XGBoost has other concept improvements: the traditional splitting algorithm denoted by the exact value of the tree_method parameter. The Weighted Quantile Sketch, which referred to as "quantile_sketch" in the XGBoost API, is an exclusive feature unique to XGBoost. This split-finding technique utilizes approximations and harnesses information derived from gradient statistics. By employing quantiles, the quantiles are weighted to prior selecting candidates capable of mitigating high gradients, reducing significant prediction errors.

Weighted Quantile Sketch using histograms is now available as tree_method="hist", which, since the 2.0.0 release, is the default method. In contrast, the approx method generates a new set of bins for each iteration, the hist method reuses bins over multiple iterations.

Another feature of the algorithm is related to data storage in DMatrices. The most consuming-time part of training learning is sorting. To reduce the sorting cost, we propose storing the data in in-memory units: a block. This also linearly scanning over the presorted entries and parallelizing, giving us an efficient algorithm for split finding.

After the successful histogram aggregation implementation in LightGBM, XGBoost adopt it. Histogram aggregation is also the main feature of HistGradientBoosting, The Scikit-learn histogram-based gradient boosting we will present after LightGBM.

## 5.4.4 Applying early stopping to XGBoost

Section 5.3 illustrates how early stopping works with Scikit-learn's gradient boosting. XGBoost also supports early stopping. You can specify early stopping by adding a few arguments when instantiating a XGBClassifier or XGBRegressor:

- early_rounds: This is the number of rounds to wait patiently without improvement in the validation score before stopping the training. If you set to a positive integer, the training will stop when the validation set hasn't improved in that many rounds.
- eval_metric: This is the evaluation metric to use for early stopping. By default, XGBoost uses rmse for regression's mean squared error and error for accuracy in classification. You can specify any other from a long list (available at https://mng.biz/XR2W) as well specify your own metric (which will be discussed in the next chapter on advanced machine learning topics).

In addition to setting these parameters, you also have to specify, at fitting time, a dataset with its target where to monitor the evaluation metric. This is done by the parameter eval_set, which contains a list of tuples containing all the validation samples and target responses. In our example, we use one validation set. Still, if there are multiple samples to monitor, XGBoost will consider only the last tuple of data and response for stopping purposes.

In 5.15, we replicate the same approach we experimented with splitting our data into a train and a test set. However, to properly monitor the evaluation metric, we properly split the train set to extract a validation set from it.

### Listing 5.15 Applying early stopping to XGBoost

```python
train, test = train_test_split(
    range(len(data)),
    test_size=0.2,
    random_state=0
)
validation = train_test_split(
    train,
    test_size=0.2,
    random_state=0)
```
# Splits the indices of the data into training and test sets using a fixed random seed

# Further splits the training set into training and validation sets using the same random seed

```python
xgb = XGBClassifier(bootstrap='gtree',
    objective='logistic',
    n_estimators=1000,
    max_depth=4,
    min_child_weight=3,
    early_stopping_rounds=100,
    eval_metric='error')
```
# Initializes an XGBoost classifier with an early stopping patience for 100 rounds

```python
X = column_transform.fit_transform(data.iloc[train])
y = target_median[train]
```
# Uses the 'error' parameter, equivalent to accuracy, an evaluation metric

```python
Xv = column_transform.transform(data.iloc[validation])
yv = target_median[validation]
```
# Fits the XGBoost classifier to the training data X and performance on the validation data Xv and yv

```python
xgb.fit(X, y, eval_set=[Xv, yv]), verbose=False)
preds = xgb.predict(Xt)
score = accuracy_score(y_true, y_pred)
print(f"Accuracy: {score:.5f}")")
```
# Prints the accuracy score comparing the predicted labels with the true labels

After completing the training, we managed to get this accuracy measure, which is slightly underperforming in respect of our previous cross-validation results because it is obtained by training on fewer examples—that is, 64% of available data since we reserved 20% for test and 16% for validation:

Accuracy: 0.82657

During the evaluation, the evaluation metric is constantly checked, and the procedure is fixed if it doesn't improve from iterations than specified by early_stopping_rounds. The best iteration is automatically recorded and used at prediction time. Thus, you have nothing more to do with the model. If you need to verify how many iterations it took before stopping, you can obtain it by inquiring the model using the best_iteration attribute. In our example, xgb.best_iteration returns 200.

## 5.5 Introduction to LightGBM

LightGBM was introduced in a 2017 paper titled "LightGBM: A Highly Efficient Gradient Boosting Tree" by Guolin Ke and his team at Microsoft (https://mng.bz/AQtz). The package reached the 4.3 version, which we tested in this book. According to the authors, the term "light" in LightGBM highlights the algorithm's faster training and lower memory usage than traditional gradient boosting trees. The paper demonstrated effectiveness through experiments on multiple public datasets, the algorithm's efficiency and its ability to speed up the training process of conventional gradient boosting trees while maintaining almost the same accuracy. LightGBM made available as open-source software on GitHub (https://github.com/microsoft/LightGBM/), quickly gaining popularity among scientists and machine learning practitioners.

On paper, LightGBM shares many characteristics similar to those of XGBoost, as support for missing values, native handling of categorical variables, GPU training, networked parallel training, and monotonicity constraints. We will tell you more about all that in the next chapter. In addition, LightGBM also supports sparse data. However, its major advantage lies in its speed, as it is significantly faster than XGBoost. The Kaggle community quickly took notice of LightGBM and began incorporating it into their competitions alongside the always-popular XGBoost. In mlcontents.com, a website that tracks the data science scene, in 2022 LightGBM became the preferred tool over competition winners, surpassing XGBoost. An impressive 25% of reported solutions for tabular problems were based on LightGBM. While LightGBM has comparable success across data science practitioners, XGBoost remains more popular. For example, the XGBoost repository has more GitHub stars than the LightGBM repository.

LightGBM is a cross-platform machine learning library available for Windows, Linux, and MacOS. It can be installed using various tools, such as pip or conda, from source code (see the complete installation guide at https://mng.bz/ZIEP). Its usage syntax is similar to Scikit-learn, making it easy for users who are familiar with Scikit-learn to transition to LightGBM. When optimizing gradient descent, LightGBM follows the footsteps of XGBoost by utilizing the Newton-aph update, which involves dividing the gradient by the Hessian matrix. Guolin Ke's answer on GitHub confirms (see https://github.com/microsoft/LightGBM/issues/5223).

Let's put the algorithm to test on the same problem we previously examined with Scikit-Learn's GradientBoosting and XGBoost.
