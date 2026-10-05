
## 44 | Machine learning with sklearn

This measure has the index 1 because it is the balanced choice of the more general
definition that weights the two differently:

> $F_{\beta} = \frac{(1 + \beta^2)}{\beta^2 \cdot precision + recall} \quad (3.7)$

These measures can also be generalized to more than two classes by treating the
positive class as the one investigation and lumping the others into the negative
class. There are many routines mentioned in sklearn to calculate these values for the test set. Example, the values mentioned above can be calculated for the iris example, as shown
in the following code:

Listing 3.6 IrisClassificationSklearn.ipynb (part 6) with output

```python
# Model Evaluation
print('\nthe_main_classification_metrics_for_iris_data:\n\n' + metrics.classification_report(y_test, y_predicted))
The main classification metrics for iris data:

precision    recall    f1-score   support
0           1.00      1.00      1.00       25
1           0.95      0.96      0.87       25
2           0.95      0.75      0.84       24
avg / total               0.92        0.91      0.90       74
```

There are many definitions and even different terms for the measures.
While this can be confusing it is easy to look up the specific definition. What is important
to realize is the appropriateness of these measures are not give a priori
depend on what the user is seeking. That is, a good measure should encapsulate
important that a person uses specific characteristics. This is similar to discussing
while a range of cares is better. Some might find that greater horsepower is good,
while others want a car to consume as little petrol as possible. Hence, there is
no simple, best measure.

## 3.3 Data handling

### 3.3.1 Cross-validation

The performance of a model on the training data can always be improved and even
made on the training data when making the model more complex. This is
the essence of overfitting. Basically, we can always write a model that can memorize
a finite dataset. However, machine learning is about generalization that can only be
measured with data points that have not been used during training. This is why in the
examples earlier we split our data into a training set and a test set.

Just splitting the data into these two sets is sufficient if we have enough. In practice,
having enough labeled data for supervised training is often a problem. We therefore
introduce a method that is much better in using the data to their full potential. This
method is called k-fold cross-validation for evaluating a model's performance. This method is based on the premise that all the data are used some time for training and testing (validation) at some point throughout the evaluation procedure. For this, we partition our data into k partitions as shown in Fig. 3.4 for k = 4. In this example we assumed to have a dataset with twenty samples, so that each partition would have five samples. In every step of the cross-validation procedure we are leaving one partition out validating (testing) the trained model and the other k-1 partitions for training. Here, we get k values for our evaluation measure, such as accuracy. But since we have several measures, we now have the opportunity to look at the distribution for more insights. We, we could also estimate the variance if we assume a Gaussian distribution of the performance of the different models that result from different training sets.

Of course, the next question is what should the value of k be? As always in machine learning, the answer is not so simple as merely stating a number. If we want to use as many data as possible for training, an N-fold cross-validation, where N is the number of samples, would be likely useful. This is also called leave-one-out cross validation (LOOCV). However, this procedure requires N training sessions and evaluations which might be computationally expensive with larger datasets. The choice of k is important to balance computational results. We course assume that all samples are 'nicely' distributed in that the dataset is not biased. For example, cross-validation would be biased if we have data points from one class in the first part of the dataset and the other in the second part. A random resampling of the dataset is a quick way of avoiding these errors. Sklearn is of course a good way of implementing this.

## 3.7 IrisClassification.Sklearn.ipynb (part 7)

```python
# cross-validation
x = iris.data[:,4]
y = iris.target[:,4]
CV=10

scores = model_selection.cross_val_score(SVC(kernel='linear'), x,
    y, cv=CV)

print(f"Accuracy_on_iris_data:{0:.4f}(/-{0:.4f})", (scores.mean(), scores.std()))
```We discussed the cross-validation procedure for testing a model, so a better name would be cross-testing. We will see later that this technique is often used in validation to tune hyperparameters as discussed further in this chapter, but it is good to realize that cross-validation is foremost and iterative evaluation procedure that can be used beyond hyperparameter learning.

Sample:

| P1 | P2 | P3 | P4 |
|---|---|---|---|

Partition:

- Fold 1: Test Train Train Train
- Fold 2: Train Test Train Train
- Fold 3: Train Train Test Train
- Fold 4: Train Train Train Test

Fig. 3.4 illustration of four-fold cross-validation on a dataset with twenty samples. In each fold, another partition of the data is taken out for testing the results of training the model on the rest of the data.

As earlier, cross-validation is really an evaluation procedure for a model with a given labeled dataset. In the end, which model should we choose? In practice, it is common to use cross-validation mainly for hyperparameter tuning and to report performances in scientific papers. However, it is also common to retain the model with all given data as training points for application purposes because it is assumed that a model with most training data will perform best in generalization.

### 3.3.2 Bagging and data augmentation

Having enough training data is often struggle for machine learning practitioners. The problems of not having enough training data are endless. For one, one might reinforce the problem with overfitting or even using a model of sufficient complexity at the start. Support vector machines are fairly (shallow) models that have the advantage of needing less data than deep learning methods. Nevertheless, even for these methods we might only have a limited amount of data to train the model.

A popular workaround is a method called bagging, which stands for "bootstrap aggregating." The idea is to use the original dataset to create several more datasets by sampling from the original dataset with replacement. Sampling with replacement, which is also called bootstrapping, means that we could have several copies of the same training data in the dataset. The question then is what good they can do. The answer is if we are training several models on these different datasets we get averaged averages. This regularized model can help with overfitting or challenges of shallow minima in the learning algorithm. We will discuss this point further when discussing the learning algorithms in detail later.

While being an interesting method with some practical benefits, the field of data augmentation now uses more general ideas. For example, we could just add some noise in the duplicate data of the bootstrapped training sets which will give the training algorithms some more information on possible variations of the data. We will later see that other transformation of data, such as rotations or some other form of systematic distortions for image data is now a common way to train deep neural networks for computer vision. Even using some form of models to transform the data can be helpful, such as generating data synthetically from physics-based simulations. There are a lot of possibilities that we cannot all discuss in this book, and we want to make sure such techniques are kept in mind for practical applications.

### 3.3.3 Balancing data

We have already mentioned balancing data, but it is worthwhile pausing again to look at this briefly. A common problem for many learning algorithms is a situation in which we have much data for one class than another. For example, say we have data from 100 people with a disease and data from 100,000 healthy controls. Ratios of positive and negative class are not uncommon in many applications. A trivial classifier that always predicts the majority class would then get 99.9 percent correct. In mathematical terms, this is just the prior probability of finding the class, which sets the balance somewhat for better classifications. There have many methods proposed to prevent such trivial solutions of which we will only mention a few here. One of the simplest methods to counter imbalance is to use only-sampled majority class. This is a valid procedure as the sub-sampled data still represent the important features of this class. However, it also means that we lose some information that is available to us and the machine. In the example above we would only utilize 100 of the healthy controls. Another way is to then emphasize the minority class by repeating some examples. It seems to be a bad idea that repeating examples does not seem to add any information. It has been shown that this technique does not usually improve the performance of the classifier or prevent that overfitting problem. The only reason that this something works is that it can at least make sure the learning algorithms is incremented the number of times for the majority and the minority class.

Another method is to apply different weights or learning rates to learn examples with different sizes to the training set. One problem with this is to find the right scale of increase or decrease in the training weight, but this technique has been applied successfully in many case, including deep learning.

In practice it has shown that combination of both strategies under-sampling the majority class and over-sampling the minority class can be most beneficial, in particular augmenting the over-sampling with some form of augmentation of the data. This is formalized in a method called SMOTE: synthetic minority over-sampling technique. The idea is therefore to change some characteristics of the over-sampled data such as adding noise. In this way there is at least a benefit of showing the learner variations that can guide the learning process.
