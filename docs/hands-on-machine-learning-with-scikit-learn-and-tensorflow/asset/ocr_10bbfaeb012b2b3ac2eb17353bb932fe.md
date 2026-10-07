treats all values equally, the harmonic mean gives much more weight to low values.
As a result, the classifier will only get a high F1 score if both recall and precision are high.

# Equation 3-3. F_1

```
$F_{1} = \frac{2}{\frac{1}{precision +rac{1}{recall}} = 2 \times \frac{precision \times recall}{precision + recall} = \frac{TP}{TP + \frac{FP}{2}}$
```

To compute the F1, score, simply check the f1_score() function:

```
>>> from sklearn.metrics import f1_score
>>> f1_score(y_train_5, y_train_pred)
0.7429062043663375
```

The F1 score favors classifiers with similar precision and recall. This is not always
what you want to: in some contexts you care about precision, and in other con-	exts you care about recall. For example, if you train a classifier to detect vid-
eos are for kids, you would probably prefer a classifier that rejects many
good videos (low recall) but keeps safe ones (high precision), rather than a class-
sifier has a much higher recall but lets a few bad videos show up in your
product (in such cases, you might even want to add a human pipeline to check the class-
sifier's selection. On the other hand, suppose you train a classifier to detect
oplillers on surveillance images: it is probable if your classifier has only 30%
precision as it has 99% recall (sure, the security guards will get a few false
alerts, but almost all shophillers will get caught).

Unfortunately, you can't have it both: increasing precision reduces recall, and
vice versa. This is what we call the precision/recall tradeoff.

# Precision/Recall Tradeoff

To understand this tradeoff, let's look at how the SGDCClassifier makes its clasifica-
tions. For each decision, it computes a score based on a decision function,
and that score is greater than a threshold, it assigns the instance to the positive
class, or else it to the negative class. Figure 3-3 shows a few digits positioned
from the lowest to the highest score on the right. Suppose the deci-
sion threshold is positioned at the central arrow (between the two 5s): you will find 4
true positives (actual 5s) on the right of that threshold, and one false positive (actually
a 6). With, that threshold, the precision is 80% (4 out of 5). But out of you
raise the threshold (move it to the arrow on the right), the false positive (the 6)
becomes a true negative, thereby increasing precision (up to 100 in this case), and
one true positive becomes a false negative, decreasing recall down to 50%. Conversely,
lowering the threshold increases recall and reduces precision.