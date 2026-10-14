
We then go on to define the column that we are going to define as the target to learn to predict:

```python
# predict 'lag_predict' ahead in advance
lag_predict = 1

# predict 'lag_predict' ahead in advance
df_lag.dropna(inplace=True)

# classify returns next day (shift = -1) : negative->-1 ; positive-> +1
df_lag['target'] = np.where(df_lag['Close_ret'].shift(-lag_predict) >= 0, 1, -1)
```

The previous line of code is probably one of the most important. It defines the class of problem we are dealing with (i.e., classification problem, the states of the world are +1 or -1 depending on the sign of the return) and designates the target column (`target`) to be learned to predict.

This column contains the next day's returns (`shift(-1)` function), which we will predict using today's information. This is the classic "one step ahead" prediction.

### Splitting and scaling

We put the target variable in the `y` (input) variable and the remaining in the `X` (output) variable:

```python
from sklearn.model_selection import train_test_split

y = df_lag.pop('target')
X = df_lag.copy()
X_train, X_test, y_train, y_test = train_test_split(X, y, shuffle=False)
```

Once this has been done, we can rescale the data. For those unfamiliar with the concept, rescaling ensures that all columns of data are on a consistent scale, simplifying the analysis process for algorithms. In particular, columns detailing trading volumes can vary widely in scale compared to return columns, which typically vary by a few percentage points:

```python
from sklearn.preprocessing import StandardScaler

sclr = StandardScaler()
X_train_tr = sclr.fit_transform(X_train)
X_test_tr = sclr.transform(X_test)
```

We are now ready to train a classifier to discriminate between positive and negative returns. For our initial approach, we opt for classifiers that are reasonable to train, aiming to minimize the development time. Our goal is to have one or more good classifiers that we can refine.

In the field of algorithmic classifiers, several stand out as foundational pillars, each with its own unique strengths and underlying principles:

*   **Linear discriminant analysis (LDA)**: LDA projects data points onto a line, aiming to maximize the separation between categories. It's robust and often used.
*   **Quadratic discriminant analysis (QDA)**: QDA, a sibling of LDA, allows for quadratic boundaries between categories, providing flexibility when classes have distinct covariance structures.
*   **Logistic regression**: Despite its name, it's a classification algorithm. It models the probability that a given instance belongs to a particular category, making it particularly effective for binary classification tasks.
*   **Decision trees (DT)**: As the name suggests, DTs make decisions based on asking a series of questions. They are intuitive and visual and can capture non-linear relationships. We have already tried out this algorithm in [Chapter 2](#chap02.xhtml), Data Feed, Backtests, and Forward Testing.
*   **Random forest (RF)**: An ensemble of decision trees, RF aggregates their outputs. This often results in increased accuracy and reduced overfitting compared to a single decision tree.
*   **Naive Bayes**: Based on Bayes' theorem, it assumes feature independence, making it especially efficient for large datasets.

These algorithms are excellent starting points due to their interpretability, ease of implementation, and historical effectiveness. The import and algorithm definition code:

```python
from sklearn.discriminant_analysis import (LinearDiscriminantAnalysis as LDA, QuadraticDiscriminantAnalysis as QDA)
from sklearn.tree import DecisionTreeClassifier
from sklearn.linear_model import LogisticRegression
from sklearn.naive_bayes import GaussianNB
from sklearn.ensemble import RandomForestClassifier, VotingClassifier

clf1 = LDA()
clf2 = QDA()
clf3 = RandomForestClassifier()
clf4 = GaussianNB()
clf5 = LogisticRegression()
clf7 = DecisionTreeClassifier()

lst_clf = [('lda', clf1), ('qda', clf2), ('nb', clf4), ('lr', clf5), ('rf', clf3), ('dt', clf7)]
```

We run the training (`fit`) for all the algorithms in the list `lst_clf`:

```python
for tpl in lst_clf:
    clf_base = tpl[1]
    clf_name = tpl[0]
    clf_base.fit(X_train, y_train)
    clf_sc = np.round(clf_base.score(X_test, y_test), 2)
    print(f"classifier {clf_name} -> accuracy score = {clf_sc}")
```

Here are the global accuracy scores (`clf_base.score`) measured on all the algorithms in the test set:

*   classifier lda -> accuracy score = 0.51
*   classifier qda -> accuracy score = 0.43
*   classifier nb -> accuracy score = 0.59
*   classifier lr -> accuracy score = 0.49
*   classifier rf -> accuracy score = 0.55
*   classifier dt -> accuracy score = 0.49

### Features selection

Following our initial iteration, we aim to enhance the prediction accuracy through feature selection. This phase identifies (sorted variable) and retains only the most influential features (`k_best`). In a conservative approach, the goal is to achieve similar prediction capabilities with fewer features, while a more ambitious approach seeks to improve performance using a trimmed feature set.

Why prioritize feature reduction? A streamlined feature set simplifies the model's task, leading to both enhanced accuracy and more straightforward subsequent implementation.

This selection is based on a score (`clf_base.feature_importances_`) calculated during the development of the decision tree algorithm:

```python
sorted = np.argsort(clf_base.feature_importances_)
k_besk = int(40/100 * len(sorted))
X_train.iloc[:, sorted[-k_besk:]].columns
columns_to_drop = X_train.columns[sorted[:-k_besk]]

# retain only k_best features
X_train = X_train.drop(columns=columns_to_drop)
X_test = X_test.drop(columns=columns_to_drop)
```

Here are the global accuracy scores measured on all the algorithms in the test set with the selected `k_best` features:

*   classifier lda -> accuracy score = 0.58
*   classifier qda -> accuracy score = 0.55
*   classifier nb -> accuracy score = 0.56
*   classifier lr -> accuracy score = 0.58
*   classifier rf -> accuracy score = 0.57
*   classifier dt -> accuracy score = 0.53

The results from the two steps provide valuable insights into the importance of feature selection in model performance:

*   **Initial performance with all features:**
    *   Naive Bayes (NB) stands out with the highest accuracy of 0.59, suggesting that the underlying assumptions of this model might be a good fit for the original feature set.
    *   LDA and logistic regression (LR), both linear classifiers, show similar performance around the 0.50 mark.
    *   QDA notably underperforms with an accuracy of 0.43, indicating potential overfitting or that the data doesn't suit a quadratic boundary.
    *   RF demonstrates decent performance at 0.55, while its simpler counterpart, DT, scores 0.49.
*   **Performance post feature selection:**
    *   Every classifier sees an improvement in accuracy, underscoring the value of selecting relevant features.
    *   LDA and LR see significant jumps to 0.58, reinforcing the idea that reducing dimensionality can help linear models. Their similar performance isn't surprising given that both algorithms aim to linearly separate data, albeit with different methodologies.
    *   QDA also improves notably, suggesting that some of the originally included features might have been introducing noise.
    *   RF and DT both benefit from the feature selection, with RF still outperforming DT, highlighting the value of the ensemble method.
    *   NB, despite an initial high performance, sees a slight drop. This could be due to the reduction of some features that the model initially found valuable.

Feature selection has proven to be critical. The improved performance of all models after retaining only the top 40% of features demonstrates the importance of using relevant predictors.

## Improving trading systems
