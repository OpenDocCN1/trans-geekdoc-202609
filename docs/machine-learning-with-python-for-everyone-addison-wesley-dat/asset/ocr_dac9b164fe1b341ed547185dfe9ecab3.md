matrices for pairs of classes with a class i serving as Positive and another class j serving as Negative. Then, we can calculate an AUC from that. We’ll do that both ways—each of the pair serving as positive and negative—and take the average of all of those AUCs. Basically, AUC is used to quantify the chances of a true cat being less likely to be called a dog than a random dog. Full details of the logic behind this technique—I’ll call it the Hand and Till M—are available in a reference at the end of the chapter.

The code itself is a bit tricky, but here’s some pseudocode to give you an overall idea of what is happening:

+   1. Train a model.
+   2. Get classification scores for each example.
+   3. Create a blank table for each pairing of classes.
+   4. For each pair of classes c1 and c2:
+      (1) Find AUC of c1 against c2.
+      (2) Find AUC of c2 against c1.
+      (3) Entry for c1, c2 is the average of these AUCs.
+   5. Overall value is the average of the entries in the table.

The trickiest bit of code is selecting out just those examples where the two classes of interest interact. For one iteration of the control loop, we need to generate an ROC curve for those two classes. So, we need the examples where either of them occurs. We track these down by doing a label_binarize to get indicator values, 1s and 0s, and then we pull out the particular columns we need from there.

```
In [20]:

def hand_and_till_M_statistic(test_tgt, test_probs, weighted=False):
def auc_helper(truth, probs):
    fpr, tpr, _ = metrics.roc_curve(truth, probs)
    return metrics.auc(fpr, tpr)

classes = np.unique(test_tgt)
n_classes = len(classes)

indicator = skpre.label_binarize(test_tgt, classes)
avg_auc_sum = 0.0

# comparing class i and class j
for ij in it.combinations(classes, 2):
    # use use sum to act like a logical OR
    ij_indicator = indicator[:, ij].sum(axis=1,
                                        dtype=np.bool)

    # slightly ugly, can't broadcast these as indexes
    # use .ix_ to save the day
```