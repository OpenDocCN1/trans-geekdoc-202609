
To test the efficacy of the model, you use cross-validation to provide predictions besides error estimates using `cross_val_predict` ([`https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.cross_val_predict.html`](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.cross_val_predict.html)). The dataset is split according to the cross-validation scheme, and all the predictions of the out-of-sample validation sets are pooled together. Though not a valid method to measure generalization of a model in some cases, it provides insight into the performances of the model using the data in the training set.

![Tip](images/tip.png)`cross_val_predict` is most useful when you want to make a prediction on the same test data, and when you use multiple, different models together. [Chapter 16](#c16.xhtml) explores using ensembles of models in this way.

It's time to evaluate the cross-validation predictions using the `classification_report` command. This time, apart from the usual accuracy measures, the example uses error measures that are more informative about how the spam model performs.

```
from sklearn.metrics import classification_report cr = classification_report(y_true=y, y_pred=preds, target_names=['non spam', 'spam'])print(cr)
```

The important report outputs are precision, recall, and f1 score:

```
 precision recall f1-score support non spam 0.89 0.92 0.90 2788 spam 0.87 0.82 0.84 1813 accuracy 0.88 4601 macro avg 0.88 0.87 0.87 4601weighted avg 0.88 0.88 0.88 4601
```

Precision and recall, and their conjoint optimization using the f1 score, can solve problems not addressed by accuracy. Precision is about being precise when guessing. It tracks the percentage of times, when forecasting a class, that a class was right. For example, you can use precision when diagnosing cancer in patients after evaluating data about their exams. Your precision in this case is the percentage of patients who really have cancer among those diagnosed with cancer. Therefore, if you have diagnosed ten ill patients and nine are truly ill, your precision is 90 percent.

You face different consequences when you don’t diagnose cancer in a patient who has it or you do diagnose it in a healthy patient. Precision tells just a part of the story, because there are patients with cancer that you have diagnosed as healthy, and that’s a terrible problem. The recall measure tells the second part of the story. It reports, among an entire class, your percentage of correct guesses. For example, when reviewing the previous example, the recall metric is the percentage of patients that you correctly guessed have cancer. If there are 20 patients with cancer and you have diagnosed just nine of them, your recall will be 45 percent.

When using your model, you can be accurate but still have low recall, or have a high recall but lose accuracy in the process. Fortunately, precision and recall can be maximized together using the f1 score, which uses the formula: `f1 = 2 * (precision * recall) / (precision + recall)`. Using the f1 score ensures that you always get the best precision and recall combined.

In the case of this example, you can see that the f1 signals that the model is less performing when dealing with the spam examples. This could be due to the minor number of examples from that class, in fact as oft happens with real-world problems, it's difficult and costly to get all the examples you need. Spam emails are much less frequent than regular emails in this dataset and the dataset is *imbalanced* because it doesn’t have enough spam examples.

![Tip](images/tip.png)When you want to classify and your classes are imbalanced, meaning that they have a different number of examples per class, you need to rebalance your dataset or the machine learning model could underperform. The package imbalance-learn ([`https://github.com/scikit-learn-contrib/imbalanced-learn`](https://github.com/scikit-learn-contrib/imbalanced-learn)) offers a set of possible state-of-the-art solutions, tutorials, and full compatibility with Scikit-learn algorithms.

Moreover, besides the two classes having a similar precision, the model has a lower recall for the spam emails, implying that it doesn’t detect some kinds of spam. You can solve this problem by increasing the number of examples, tuning your algorithm (if possible), or testing a new algorithm type on the problem. Catching spam isn’t that difficult in the end; the problem is to avoid discarding important emails in the process (false positives, where a positive is a spam email) and to avoid ignoring spam emails (false negatives). This is why evaluating both precision and recall is a key passage after training your spam detector.

Part 4

# Learning from Smart and Big Data

IN THIS PART …

Getting data ready for use

Understanding data through similarity

Working with linear models

Working with neural networks

Employing smart vector machines

Performing multiple levels of analysis using ensembles

Chapter 11

# Preprocessing Data

IN THIS CHAPTER

![Bullet](images/check.png)**Obtaining and cleaning data**

![Bullet](images/check.png)**Repairing and transforming data**

![Bullet](images/check.png)**Creating new meaningful features**

![Bullet](images/check.png)**Using univariate and multivariate models**

When building a new house, before.

![Remember](images/remember.png)You don’t have to type the source code for this chapter manually. In fact, using the downloadable source is a lot easier. You can find the source for this chapter in the `ML4D2E` folder of the downloadable source for Python code and the `ML4D2ER` folder of the downloadable source for the R code. The example files for this chapter will begin with `ML4D2E; 11;` (for Python) or `ML4D2E_R; 11;` (for R). See the Introduction for details on how to find these source files.

## Gathering and Cleaning Data

Although this book focuses on how machines learn from data, no magic recipe exists in the world of algorithms (as the “no-free-lunch” theorem in [Chapter 9](#c09.xhtml) states) when it comes to data. Even sophisticated and advanced learning functions hit the wall and underperform when you don't support them with the following:

*   Large enough quantities of data that are suitable for the algorithm you use
