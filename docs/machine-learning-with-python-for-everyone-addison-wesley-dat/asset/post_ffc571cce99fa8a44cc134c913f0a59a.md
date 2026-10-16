
## 6.2.3 Metrics from the Confusion Matrix

We can ask and answer questions from the confusion matrix. For example, if we are doctors, we care how well we’re able to find people who are, in reality, sick. Since we defined sick as our positive case, these are people in the first row. We are asking how well do we do on RealP: how many, within the actual real-world sick people, do we correctly detect: TP/TP+FN = TP/RealP. The term for this is sensitivity. You can think of it as “how well dialed-in is this test to finding sick folks” — where the emphasis is on the sick people. It is also called recall by folks coming from the information retrieval community.

Different communities came up with this idea independently, so they gave it different names. As a way to think about recall, consider getting hits from a web search. Of the really valuable or interesting hits, RealP, how many did we find, or recall, correctly? Again, for sensitivity and recall we care about correctness in the real-world positive, or interesting, cases. Sensitivity has one other common synonym: the true positive rate (TPR). Don’t scramble for your pencils to write that down, I’ll give you a table of terms in a minute. The TPR is the true positive rate with respect to reality.

There’s a complement to caring about the sick or interesting cases we got right: the sick folks we got wrong. This error is called a false negative. With our abbreviations, the sick people we got wrong is FN/TP+FN. We can add up the sick people we got right and the sick people we got wrong to get all of the sick people total. Mathematically, that looks like TP/TP+FN + FN/TP+FN = TP+FN/TP+FN = 1 = 100%. These equations say that I can break up all 100% of the sick people into (1) sick people that I think are sick and (2) sick people that I think are healthy.

We can also ask, “How well do we do on healthy people?” Our focus is now on the second row, RealN. If we are doctors, we want to know what the value of our test is when people are healthy. While the risk is different, there is still risk in misdiagnosing healthy people. We—playing doctors, for a second—don’t want to be telling people they are sick when they are healthy. Not only do we give them a scare and a worry, we might end up treating them with surgery or drugs they don’t need! This mistake is a case of a false positive (FP). We can evaluate it by looking at how correct we are on healthy people: TN/FP+TN = TN/RealN. The diagnostic term for this is the specificity of the test: does the test only raise a flag in the specific cases we want it to. Specificity is also known as the true negative rate (TNR). Indeed, it’s the true negative rate with respect to reality.

One last combination of confusion matrix cells takes the prediction as the primary part and reality as the secondary part. I think of it as answering “What is the value of our test when it comes back positive?” or, more briefly, “What’s the value of a hit?” Well, hits are the PredP. Inside PredP, we’ll count the number correct: TP. We then have TP/PredP = TP/TP+FP, which is called precision. Try saying, “How precise are our positive predictions?” ten times quickly.

Figure 6.1 shows the confusion matrix along with our metrics for assessing it.

One last comment on the confusion matrix. When reading about it, you may notice that some authors swap the axes: they’ll put reality on the columns and the predictions in the rows. Then, TP and TN will be the same boxes, but FP and FN will be flipped. The unsuspecting reader may end up very, very perplexed. Consider yourself warned when you read other discussions of the confusion matrix.

![](img/d94e4cd766940d79abed0bc6ba4e4344_194_0.png)

Figure 6.1 The confusion matrix of correct and incorrect predictions.

## 6.2.4 Coding the Confusion Matrix

Let's see how these evaluations work in sklearn. We'll return to our trusty iris dataset and do a simple train-test split to remove some complication. As an alternative, you could wrap these calculations up in a cross-validation to get estimates that are less dependent on the specific train-test split. We'll see that shortly.

If you haven't seen method chaining formatted like I'm doing in lines 1-3 below, it may look a bit jarring at first. However, it is my preferred method for long, chained method calls. Using it requires that we add parentheses around the whole expression to make Python happy with the internal line breaks. When I write chained method calls like this, I prefer to indent to the method access dots ., because it allows me to visually connect method 1 to method 2 and so on. Below, we can quickly read that we move from neighbors to KNeighborsClassifiers to fit to predict. We could rewrite this with several temporary variable assignments and achieve the same result. However, method chaining without unnecessary variables is becoming a common style of coding in the Python community. Stylistic comments aside, here goes:

```
In [6]:

tgt_preds = (neighbors.KNeighborsClassifier()
    .fit(iris_train_ftrs, iris_train_tgt)
    .predict(iris_test_ftrs))

print("accuracy:", metrics.accuracy_score(iris_test_tgt,
    tgt_preds))

cm = metrics.confusion_matrix(iris_test_tgt,
    tgt_preds)
print("confusion matrix:", cm, sep="\n")
```

accuracy: 0.94
confusion matrix:
[[18 0 0]
 [ 0 16 1]
 [ 0 2 13]]

Yes, the confusion matrix is really a table. Let's make it a pretty table:

In [7]:

```
fig, ax = plt.subplots(1, 1, figsize=(4, 4))
cm = metrics.confusion_matrix(iris_test_tgt, tgt_preds)
ax = sns.heatmap(cm, annot=True, square=True,
                xticklabels=iris.target_names,
                yticklabels=iris.target_names)
ax.set_xlabel('Predicted')
ax.set_ylabel('Actual');
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_195_0.png)

Now we can literally see what's going on. In some respects *setosa* is easy. We get it 100% right. We have some mixed signals on *versicolor* and *virginica*, but we don't do too badly there either. Also, the errors with *versicolor* and *virginica* are confined to misclassifying between those two classes. We don't get any cross-classification back into *setosa*. We can think about *setosa* as being a clean category of its own. The two *v* species have some overlap that is harder to sort out.

## 6.2.5 Dealing with Multiple Classes: Multiclass Averaging

With all that prettiness, you might be forgiven if you forgot about precision and recall. But if you do remember about them, you might have gone all wide-eyed by now. We don't have two classes. This means our dichotomous, two-tone formulas break down, fall flat on their face, and leave us with a problem. How do we compress the rich information in a many-values confusion matrix into simpler values?

We made three mistakes in our classification. We predicted one versicolor as virginica and we predicted two virginica as versicolor. Let's think in terms of value of a prediction for a moment. In our two-class metrics, it was the job of precision to draw out information from the positive prediction column. When we predict versicolor, we are correct 16 times and wrong 2. If we consider versicolor on one side and everyone else on the other side, we can calculate something very much like precision. This gives us 16/18 ≈ .89 for a one-versus-rest — me-against-the-world — precision for versicolor. Likewise, we get 13/14 ≈ .93 for our one-versus-rest precision for virginica.

Those breakdowns don't seem too bad, but how do we combine them into a single value? We've talked about a few options for summarizing data; let's go with the mean. Since we're perfect when we predict setosa, that contributes 1.0. So the mean of {16/18, 13/14, 1} is about .9392. This method of summarizing the predictions is called macro by sklearn. We can calculate the macro precision by computing a value for each column and then dividing by the number of columns. To compute the value for one column, we take the diagonal entry in the column—where we are correct—and divide by the sum of all values in the column.

```
In [8]:

macro_prec = metrics.precision_score(iris_test_tgt,
                                    tgt_preds,
                                    average='macro')
print("macro:", macro_prec)

cm = metrics.confusion_matrix(iris_test_tgt, tgt_preds)
n_labels = len(iris.target_names)
print("should equal 'macro avg':",
      # correct          column          # columns
      (np.diag(cm) / cm.sum(axis=0)).sum() / n_labels)
```

macro: 0.9391534391534391

should equal 'macro avg': 0.9391534391534391

Since that method is called the macro average, you're probably chomping at the bit to find out about the micro average. I actually find the name micro a bit counterintuitive. Even the sklearn docs say that micro "calculates metrics globally"! That doesn't sound micro to me. Regardless, the micro is a broader look at the results. micro takes all the correct predictions and divides by all the predictions we made. These come from (1) the sum of the values on the diagonal of the confusion matrix and (2) the sum of all values in the confusion matrix:
