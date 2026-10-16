# 6.8.2 Notes

If you need an academic reference on ROC curves, check out:

+   - Fawcett, Tom (2004). “ROC Graphs: Notes and Practical Considerations for Researchers.” *Pattern Recognition Letters* 27 (8): 882–891.

AUC has some direct relationships to well-known statistical measures. In particular, the *Gini index*—which measures the difference of two ranges of outcomes—and AUC are related by Gini + 1 = 2 × AUC. The Mann–Whitney *U* statistic is related to AUC as \(\frac{U}{n_1n_2} = \mathrm{AUC}\) where \(n_i\) is the number of elements in class *i*. If you aren’t a stats guru, don’t worry about these.

We discussed *F₁* and said it was an evenly balanced way to combine precision and recall. There are a range of alternatives called *Fβ* that can weight precision more or less depending on whether you care more about performance with respect to reality or more about the performance of a prediction.

Here are two crazy facts. (1) A learning method called *boosting* can take any learner that is minutely better than coin flipping and make it arbitrarily good—if we have enough good data. (2) If a learner for a Boolean problem is reliably bad—reliably worse than coin flipping—we can make it reliably good by flipping its predictions. Putting these together, we can take any consistent *initial* learning system and make it as good as we want. In reality, there are mathematical caveats here—but the existence of this possibility is pretty mind-blowing. We’ll discuss some practical uses of boosting in Section 12.4.

Some classifier methods don’t play well with multiple target classes. These *require* that we do one-versus-one or one-versus-rest to wrap up their predictions to work in multiclass scenarios. Support vector classifiers are an important example which we will discuss in Section 8.3.

The Hand and Till *M* is defined in:

+   - Hand, David J. and Till, Robert J. (2001). “A Simple Generalisation of the Area Under the ROC Curve for Multiple Class Classification Problems.” *Machine Learning* 45 (2): 171–186.

Although, as is often the case when you want to use a research method, I had to dig into an implementation of it to resolve a few ambiguities. It seems likely that the same technique could be used with precision–recall curves. If you happen to be looking for a master’s thesis, fame, or just glory and honor, run it past your advisor or manager.

We saw that accuracy was the default metric for *k*-NN. In fact, accuracy is the default metric for all `sklearn` classifiers. As is often the case, there’s an asterisk here: if the classifier inherits from the `ClassifierMixin` class, then they use mean accuracy. If not, they could use something else. `ClassifierMixin` is an internal `sklearn` class that defines the basic, shared functionality of `sklearn`’s classifiers. *Inheriting*—a concept from object-oriented programming (OOP)—shares that behavior with other classes. The `sklearn` documentation doesn’t have a literal table of classifiers and scorers.