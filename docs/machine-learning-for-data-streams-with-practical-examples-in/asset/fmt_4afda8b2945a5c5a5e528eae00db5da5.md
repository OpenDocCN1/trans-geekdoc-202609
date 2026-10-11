
## 6.2.4 Multinomial Naive Bayes

The Multinomial Naive Bayes classifier [171] is an extension of Naive Bayes for document classification that often yields surprisingly good results. Multinomial Naive Bayes considers a document as a bag of words, so it takes into account the frequency of each word in a document and not just its presence or absence. Since word frequency is usually relevant for text classification, this method is preferred over Naive Bayes for text mining.

Let `n[wd]` be the number of times word `w` occurs in document `d`. Then the probability of class `c` given a test document is calculated as follows:

```
Pr(c|d) = Pr(c) * ∏ Pr(w|c)^n[wd] / Pr(d)
```

where `Pr(d)` can be thought of as a normalization factor.

But a key difference with Naive Bayes is the interpretation of `Pr(w|c)`: here it is the ratio between the number of occurrences of `w` in documents of class `c` over the total number of words in documents of class `c`. In other words, it is the probability of observing word `w` at any position of a document belonging to class `c`. Observe that, again unlike Naive Bayes, the absence of a word in a document does not make any class more likely than any other, as it translates to a 0 exponent.

Conveniently, `n[wd]`, `Pr(w|c)` and `Pr(c)` are trivial to estimate on a data streams by keeping the appropriate counters. Laplace correction can be added by initializing all the counts to 1 instead of 0.

**Example 6.2** Suppose we want to build a Multinomial Naive Bayes classifier using the tweets in example 6.1. First we compute the number of occurrences of each word in each document. We use Laplace correction, setting each entry to 1 before starting to count occurrences:

![](images/pg99-1.png)

And now the probabilities for each class are:

*   `Pr(+|T5) = Pr(+) · Pr(glad|+) · Pr(pleasant|+) · Pr(miserable|+) · Pr(sad|+)`,

![](images/pg99-2.png)

*   `Pr(−|T5) = Pr(−) · Pr(glad|−) · Pr(pleasant|−) · Pr(miserable|−) · Pr(sad|−)`,

![](images/pg99-3.png)

In this case, we see that `Pr(+|T5) > Pr(−|T5)` and the Multinomial Naive Bayes classifier predicts that the new tweet has positive polarity, in contrast to regular Naive Bayes, which predicted negative polarity.

# 6.3 Decision Trees

*Decision trees* are a very popular classifier technique since it is very easy to interpret and visualize the tree models. In a decision tree, each internal node corresponds to an attribute that splits into a branch for each attribute value, and leaves correspond to classification predictors, usually majority class classifiers. [Figure 6.2](#chapter_6.xhtml#fig6-2) shows an example.

![Figure 6.2 A dataset describing email features for deciding whether the email is spam, and a decision tree for it.](images/Fig6-2.png)

[**Figure 6.2**](#chapter_6.xhtml#rfig6-2)

A dataset describing email features for deciding whether the email is spam, and a decision tree for it.

The accuracy of decision trees can be improved using other classifiers at the leaves, such as Naive Bayes, or using ensembles of decision trees, as we will see later on.

The basic method to build a tree is to start by creating a root node at the beginning `node = root`, and then do the following:

1.  If training instances are perfectly classified at the node, then stop. Else:
2.  Assign `A` to be the "best" decision attribute for `node`.
3.  For each value of `A`, create new descendant (leaf) of `node`.
4.  Split the training instances according to the value of `A`, and pass each split to the corresponding leaf.
5.  Apply this method recursively to each leaf.

Two common measures are used to select the best decision attribute:

*   **Information gain**, that is, the difference between the entropy of the class before and after splitting by the attribute. Recall that the entropy `H` of a sample `S` is `H(S) = -∑ p[c] log p[c]`, where `p[c]` is the probability in `S` of class label `c`. The entropy of `S` after splitting on attribute `A` is `H(S,A) = ∑ (|S[a]|/|S|) H(S[a])`, where `S[a]` is the subset of `S` where `A` has value `a`. The information gain of `A` is then `IG(S,A) = H(S) − H(S,A)`. This measure was made popular after the C4.5 decision tree algorithm.
*   **Gini impurity reduction**, that is, the difference between the Gini index before and after splitting by the attribute. This measure was made popular after the CART decision tree algorithm. The Gini index of a random variable `C` is another nonlinear measure of the dispersion of `C`, defined as `Gini(C) = 1 - ∑ p[c]^2`.

## 6.3.1 Estimating Split Criteria

The measures above need to be estimated from finite samples, but in a way that generalizes to future examples (that is, whether it is made now or in a month, year, or decade hence, it will still be the same decision, assuming stationarity). This calls for concentration inequalities in the spirit of those presented in section 4.2, which bound the probability that an estimate over a finite sample is far off its expectation.

Hoeffding's inequality has often been used for estimating measures like information gain or the Gini index. Unfortunately, these measures cannot be expressed as a sum of independent random variables, and so Hoeffding's bound is argued in recent work by Rutkowski et al. [218] to be the wrong tool.

A generalization of Hoeffding's inequality called McDiarmid's inequality can, however, be used for making split decisions using these measures as it works explicitly on functions of the data [218]. For information gain `IG`, the following can be shown for any two attributes `A` and `B`: if `E[S][IG(S,A) − IG(S,B)] > ε`, then with probability `1 − δ` we have `IG(S,A) − IG(S,B) > 0`, where `ε = √( (ln(1/δ)) / (2n) ) * (log n_c)`, `n` is the size of `S`, and `n[c]` is the number of classes. The formulation for the Gini index is simpler: it suffices to have `ε = √( (ln(1/δ)) / (2n) )`. Similar bounds are given in [215]. Misclassification error can also be used [217], eventually giving a bound very similar to Hoeffding's bound.

Note that our description of work on decision trees for streaming takes a historical perspective. The use of McDiarmid's bound is cutting-edge for this particular method and represents a relatively new result. Hoeffding trees may, in the future, be proven *incorrect* in the sense of being based on assumptions that do not hold, however, they are still very effective in practice, and so worthy of study.

## 6.3.2 The Hoeffding Tree
