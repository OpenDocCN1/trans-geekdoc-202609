
ROC curves are normally drawn in terms of sensitivity (also called true positive rate, TPR). 1 − specificity is called the false positive rate (FPR). Remember, these both measure performance with respect to the breakdown in the real world. That is, they care how we do based on what is out there in reality. We want to have a high TPR: 1.0 is perfect. We want a low FPR: 0.0 is great. We’ve already seen that we can game the system and guarantee a high TPR by making the prediction bar so low that we say everyone is positive. But what does that do to our FPR? Exactly! It sends it up to one: fail. The opposite case—cheating towards saying no one is sick—gets us a great FPR of zero. There are no false claims of sickness, but our TPR is no good. It’s also zero, while we wanted that value to be near 1.0.

## 6.3.1 Patterns in the ROC

In Figure 6.4 we have an abstract diagram of an ROC curve. The bottom-left corner of the graph represents a FPR of zero and a TPR of zero. The top-right corner represents TPR and FPR both equal to one. Neither of these cases are ideal. The top-left corner represents an FPR of 0 and a TPR of 1—perfection. In sklearn, a low threshold means moving the PredictionBar all the way to the right of the confusion matrix: we make everything positive. This occurs in the top-right corner of the ROC graph. A high threshold means we make many things negative—our PredictionBar is slammed all the way left in the confusion matrix. It’s hard to get over a high bar to be a positive. This is what happens in the bottom-left corner of the ROC graph. We have no false positives because we have no positives at all! As the threshold decreases, it gets easier to say something is positive. We move across the graph from bottom-left to top-right.

![](img/d94e4cd766940d79abed0bc6ba4e4344_201_0.png)

Figure 6.4 An abstract look at an ROC curve.

Four things stand out in the ROC graph.

- 1. The y = x line from the bottom-left corner to the top-right corner represents coin flipping: randomly guessing the target class. Any decent classifier should do better than this. Better means pushing towards the top-left of the diagram.
- 2. A perfect classifier lines up with the left side and the top of the box.
- 3. Classifier A does *strictly* better than B and C. A is more to the top-left than B and C, everywhere.
- 4. B and C flip-flop. At the higher thresholds B is better; at lower thresholds C is better.

The second point (about a perfect classifier) is a bit confusing. As we move the threshold, don't some predictions go from *right to wrong*? Ever? Well, in fact, remember that a threshold of zero is nice because everything is positive. Of the real positives, we get all of them correct even though we get all the real negatives wrong. A threshold of one has some benefit because everything is predicted negative. Of the real negatives, we get them all, even though we get all the real positives wrong. Those errors are due to the extreme thresholds—not our classifier. Any classifier would suffer under the thumb of these authoritarian thresholds. They are just “*fixed points*” on *every* ROC graph.

Let’s walk across the ROC curve for our *perfect* classifier. If our threshold is at one, even if we give something a correct score, it is going to get thrown in as negative, regardless of the score. We are stuck at the bottom-left corner of the ROC curve. If we slide our threshold down a bit, some examples can become positives. However, since we’re perfect, none of them are *false* positives. Our TPR is going to creep up, while our FPR stays 0: we are climbing the left side of the ROC box. Eventually, we’ll be at the ideal threshold that balances our FPR of zero and achieves a TPR of 1. This balance point is the *correct* threshold for our perfect classifier. If we move beyond this threshold, again, the threshold itself becomes the problem (it’s you, not me!). Now, the TPR will stay constant at 1, but the FPR will increase—we’re moving along the top of the ROC box now—because our threshold is forcing us to claim more things as positive regardless of their reality.

## 6.3.2 Binary ROC

OK, with conceptual discussion out of the way, how do we make ROC work? There’s a nice single call, `metrics.roc_curve`, to do the heavy lifting after we do a couple of setup steps. But we need to do a couple of setup steps. First, we’re going to convert the iris problem into a *binary* classification task to simplify the interpretation of the results. We’ll do that by converting the target class from the standard three-species problem to a binary yes/no question. The three species question asks, “Is it *virginica*, *setosa*, or *versicolor*?” The answer is one of the three species. The binary question asks, “Is it *versicolor*?” The answer is yes or no.

Second, we need to invoke the classification scoring mechanism of our classifier so we can tell who is on which side of our prediction bar. Instead of outputting a class like *versicolor*, we need to know some score or probability, such as a .7 likelihood of *versicolor*. We do that by using `predict_proba` instead of our typical `predict`. `predict_proba` comes back with probabilities for *False* and *True* in two columns. We need the probability from the *True* column.

```
In [11]:

# warning: this is 1 "one" not l "ell"
is_versicolor = iris.target == 1

tts_1c = skms.train_test_split(iris.data, is_versicolor,
    test_size=.33, random_state = 21)
(iris_1c_train_ftrs, iris_1c_test_ftrs,
    iris_1c_train_tgt,  iris_1c_test_tgt) = tts_1c

# build, fit, predict (probability scores) for NB model
gnb = naive_bayes.GaussianNB()
prob_true = (gnb.fit(iris_1c_train_ftrs, iris_1c_train_tgt)
    .predict_proba(iris_1c_test_ftrs)[:, 1]) # [:, 1]=="True"
```

With the setup done, we can do the calculations for the ROC curve and display it. Don't get distracted by the auc. We'll come back to that in a minute.

```
In [12]:

fpr, tpr, thresh = metrics.roc_curve(iris_1c_test_tgt,
    prob_true)

auc = metrics.auc(fpr, tpr)
print("FPR : {}".format(fpr),
    "TPR : {}".format(tpr), sep='\n')

# create the main graph
fig, ax = plt.subplots(figsize=(8, 4))
ax.plot(fpr, tpr, 'o--')
ax.set_title("1-Class Iris ROC Curve\nAUC:{:.3f}".format(auc))
ax.set_xlabel("FPR")
ax.set_ylabel("TPR");

# do a bit of work to label some points with their
# respective thresholds
investigate = np.array([1, 3, 5])
for idx in investigate:
    th, f, t = thresh[idx], fpr[idx], tpr[idx]
    ax.annotate('thresh = {:.3f}'.format(th),
        xy=(f+.01, t-.01), xytext=(f+.1, t),
        arrowprops = {'arrowstyle': '->'})
```

FPR : [0. 0. 0. 0.0606 0.0606 0.1212 0.1212 0.1818 1.  ]
TPR : [0. 0.0588 0.8824 0.8824 0.9412 0.9412 1. 1. 1.  ]

![](img/d94e4cd766940d79abed0bc6ba4e4344_204_0.png)

Notice that most of the FPR values are between 0.0 and 0.2, while the TPR values quickly jump into the range of 0.9 to 1.0. Let’s dive into the calculation of those values. Remember, each point represents a different confusion matrix based on its own unique threshold. Here are the confusion matrices for the second, fourth, and sixth thresholds which are also labeled in the prior graph. Thanks to zero-based indexing, these occur at indices 1, 3, and 5 which I assigned to the variable `investigate` in the previous cell. We could have picked any of the eight thresholds that `sklearn` found. Verbally, we can call these a high, middle, and low bar for being sick—or, in this case, for our positive class of *is_versicolor* (predicted true).

| Bar | Medical Claim | Prediction |
| --- | --- | --- |
| Low | Easy to call sick | Easy to predict True |
| Mid |  |  |
| High | Hard to call sick | Hard to predict False |

Let’s look at these values.

```
In [13]:

title_fmt = "Threshold {}\n{:5.3f}\nTPR : {:.3f}\nFPR : {:.3f}"

pn = ['Positive', 'Negative']
add_args = {'xticklabels': pn,
            'yticklabels': pn,
            'square':True}

fig, axes = plt.subplots(1, 3, sharey = True, figsize=(12, 4))
for ax, thresh_idx in zip(axes.flat, investigate):
```
