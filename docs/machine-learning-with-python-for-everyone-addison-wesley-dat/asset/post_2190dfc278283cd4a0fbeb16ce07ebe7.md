
![](img/d94e4cd766940d79abed0bc6ba4e4344_229_0.png)

Not so much. A large part of our problem is that we’re simply predicting the low class (even with our nonbaseline methods) an awful lot of the time. We need more information to tease apart the distinguishing characteristics of the target classes.

## 6.8 EOC

### 6.8.1 Summary

We’ve added many techniques to our quiver of classification evaluation tools. We can now account for unbalanced numbers of target classes, assess our learners with respect to reality and predictions (separately and jointly), and we can dive into specific class-by-class failures. We can also determine the overall benefit that a classification system gets us over guessing a random target.

### 6.8.2 Notes

If you need an academic reference on ROC curves, check out:

- Fawcett, Tom (2004). “ROC Graphs: Notes and Practical Considerations for Researchers.” *Pattern Recognition Letters* 27 (8): 882–891.

AUC has some direct relationships to well-known statistical measures. In particular, the *Gini index*—which measures the difference of two ranges of outcomes—and AUC are related by Gini + 1 = 2 × AUC. The Mann–Whitney *U* statistic is related to AUC as \(\frac{U}{n_1n_2} = \mathrm{AUC}\) where \(n_i\) is the number of elements in class *i*. If you aren’t a stats guru, don’t worry about these.

We discussed *F₁* and said it was an evenly balanced way to combine precision and recall. There are a range of alternatives called *Fβ* that can weight precision more or less depending on whether you care more about performance with respect to reality or more about the performance of a prediction.

Here are two crazy facts. (1) A learning method called *boosting* can take any learner that is minutely better than coin flipping and make it arbitrarily good—if we have enough good data. (2) If a learner for a Boolean problem is reliably bad—reliably worse than coin flipping—we can make it reliably good by flipping its predictions. Putting these together, we can take any consistent *initial* learning system and make it as good as we want. In reality, there are mathematical caveats here—but the existence of this possibility is pretty mind-blowing. We’ll discuss some practical uses of boosting in Section 12.4.

Some classifier methods don’t play well with multiple target classes. These *require* that we do one-versus-one or one-versus-rest to wrap up their predictions to work in multiclass scenarios. Support vector classifiers are an important example which we will discuss in Section 8.3.

The Hand and Till *M* is defined in:

- Hand, David J. and Till, Robert J. (2001). “A Simple Generalisation of the Area Under the ROC Curve for Multiple Class Classification Problems.” *Machine Learning* 45 (2): 171–186.

Although, as is often the case when you want to use a research method, I had to dig into an implementation of it to resolve a few ambiguities. It seems likely that the same technique could be used with precision–recall curves. If you happen to be looking for a master’s thesis, fame, or just glory and honor, run it past your advisor or manager.

We saw that accuracy was the default metric for *k*-NN. In fact, accuracy is the default metric for all `sklearn` classifiers. As is often the case, there’s an asterisk here: if the classifier inherits from the `ClassifierMixin` class, then they use mean accuracy. If not, they could use something else. `ClassifierMixin` is an internal `sklearn` class that defines the basic, shared functionality of `sklearn`’s classifiers. *Inheriting*—a concept from object-oriented programming (OOP)—shares that behavior with other classes. The `sklearn` documentation doesn’t have a literal table of classifiers and scorers.

The school data we used came from:

- Cortez, P. and Silva, A. “Using Data Mining to Predict Secondary School Student Performance.” In: A. Brito and J. Teixeira (eds), *Proceedings of 5th Future Business Technology Conference (FUBUTEC 2008)*, pp. 5-12, Porto, Portugal, April, 2008, EUROSIS.

Here’s the code to download and preprocess it into the form used in this chapter:

```
In [40]:
student_url = ('https://archive.ics.uci.edu/' +
               'ml/machine-learning-databases/00320/student.zip')
def grab_student_numeric_discrete():
    # download zip file and unzip
    # unzipping unknown files can be a security hazard
    import urllib.request, zipfile
    urllib.request.urlretrieve(student_url,
                               'port_student.zip')
    zipfile.ZipFile('port_student.zip').extract('student-mat.csv')

    # preprocessing
    df = pd.read_csv('student-mat.csv', sep=';')

    # g1 & g2 are highly correlated with g3;
    # dropping them makes the problem significantly harder
    # we also remove all non-numeric columns
    # and discretize the final grade by 0-50-75-100 percentile
    # which were determined by hand
    df = df.drop(columns=['G1', 'G2']).select_dtypes(include=['number'])
    df['grade'] = pd.cut(df['G3'], [0, 11, 14, 20],
                         labels=['low', 'mid', 'high'],
                         include_lowest=True)
    df.drop(columns=['G3'], inplace=True)

    # save as
    df.to_csv('portuguese_student_numeric_discrete.csv', index=False)
```

### 6.8.3 Exercises

Try applying our classification evaluation techniques against the wine or breast cancer datasets which you can pull in with datasets.load_wine and datasets.load_breast_cancer.

This page intentionally left blank

## Evaluating Regressors

```
In [1]:
# Setup
from mlwpy import *
%matplotlib inline

diabetes = datasets.load_diabetes()

tts = skms.train_test_split(diabetes.data,
                            diabetes.target,
                            test_size=.25,
                            random_state=42)

(diabetes_train_ftrs, diabetes_test_ftrs,
 diabetes_train_tgt,  diabetes_test_tgt) = tts
```

We’ve discussed evaluation of learning systems and evaluation techniques specific to classifiers. Now, it is time to turn our focus to evaluating regressors. There are fewer ad-hoc techniques in evaluating regressors than in classifiers. For example, we don’t have confusion matrices and ROC curves, but we’ll see an interesting alternative in residual plots. Since we have some extra mental and physical space, we’ll spend a bit of our time in this chapter on some auxiliary evaluation topics: we’ll create our own sklearn-pluggable evaluation metric and take a first look at processing pipelines. Pipelines are used when learning systems require multiple steps. We’ll use a pipeline to standardize some data before we attempt to learn from it.

### 7.1 Baseline Regressors

As with classifiers, regressors need simple baseline strategies to compete against. We’ve already been exposed to predicting the middle value, for various definitions of middle. In sklearn’s bag of tricks, we can easily create baseline models that predict the mean and the median. These are fixed values for a given training dataset; once we train on the dataset, we get a single value which serves as our prediction for all examples. We can also pick arbitrary

constants out of a hat. We might have background or domain knowledge that gives us a reason to think some value—a minimum, maximum, or maybe 0.0—is a reasonable baseline. For example, if a rare disease causes fever and most people are healthy, a temperature near 98.6 degrees Fahrenheit could be a good baseline temperature prediction.

A last option, quantile, generalizes the idea of the median. When math folks say generalize, they mean that a specific thing can be phrased within a more general template. In Section 4.2.1, we saw that the median is the sorted data’s middle value. It had an interesting property: half the values are less than it and half the values are greater than it. In more general terms, the median is one specific percentile—it is called the 50th percentile. We can take the idea of a median from a halfway point to an arbitrary midway point. For example, the 75th percentile has 75% of the data less than it and 25% of the data greater.

Using the quantile strategy, we can pick an arbitrary percent as our break point. Why’s it called quantile and not percentile? It’s because quantile refers to any set of evenly spaced break points from 0 to 100. For example, quartiles—phonetically similar to quarters—are the values 25%, 50%, 75%, and 100%. Percentiles are specifically the 100 values from 1% to 100%. Quantiles can be more finely grained than single-percent steps—for example, the 1000 values 0.1%, 0.2%, …, 1.0%, …, 99.8%, 99.9%, 100.0%.

In [2]:

```
```python
baseline = dummy.DummyRegressor(strategy='median')
```
```

In [3]:

```
```python
strategies = ['constant', 'quantile', 'mean', 'median', ]
baseline_args = [{"strategy":s} for s in strategies]

# additional args for constant and quantile
baseline_args[0]['constant'] = 50.0
baseline_args[1]['quantile'] = 0.75

# similar to ch 5, but using a list comprehension
# process a single argument package (a dict)
def do_one(**args):
    baseline = dummy.DummyRegressor(**args)
    baseline.fit(diabetes_train_ftrs, diabetes_train_tgt)
    base_preds = baseline.predict(diabetes_test_ftrs)
    return metrics.mean_squared_error(base_preds, diabetes_test_tgt)

# gather all results via a list comprehension
mses = [do_one(**bla) for bla in baseline_args]

display(pd.DataFrame({'mse':mses}, index=strategies))
```
