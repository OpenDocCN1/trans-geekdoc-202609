
Decision tree learners, on the other hand, deal with numeric attributes on a local basis, examining attributes at each node of the tree, when it is being constructed, to see whether they are worth branching on. It’s only at that point that the best place to split continuous attributes is decided. We discuss such an algorithm in [Appendix C](#FigC1_655-685_B9780443158889000236.xhtml#FigC1_655-685_B9780443158889000236), Implementation details of trees and rules, though it only considers binary splits of continuous attributes. Alternatively, one can imagine a full discretization taking place at that point, yielding a multiway split on a numeric attribute. The pros and cons of the local vs. global approach are clear. Local discretization is tailored to the actual context provided by each tree node and will produce different discretizations of the same attribute at different places in the tree if that seems appropriate. However, its decisions are based on less data as tree depth increases, which compromises their reliability. If trees are developed all the way out to single-instance leaves before being pruned back, as with the normal technique of backward pruning, it is clear that many discretization decisions will be based on data that is grossly inadequate.

When using global discretization before applying a learning scheme, there are two possible ways of presenting the discretized data to the learner. The most obvious is to treat discretized attributes like nominal ones; that is, each discretization interval is represented by one value of the nominal attribute. However, because a discretized attribute is derived from a numeric one, its values are ordered, and treating it as nominal discards this potentially valuable ordering information. Of course, if a learning scheme can handle ordered attributes directly, the solution is obvious; each discretized attribute is declared to be of type “ordered.”

If the learning scheme cannot handle ordered attributes, there is still a simple way of enabling it to exploit the ordering information—transform each discretized attribute into a set of binary attributes before the learning scheme is applied. If the discretized attribute has `k` values, it is transformed into `k` – 1 binary attributes. If the original attribute’s value is `i` for a particular instance, the first `I` – 1 of these new attributes are set to `false` and the remainder are set to `true`. In other words, the (`I` – 1)th binary attribute represents whether the discretized attribute is less than `i`. If a decision tree learner splits on this attribute, it implicitly utilizes the ordering information it encodes. Note that this transformation is independent of the particular discretization method being applied; it is simply a way of coding an ordered attribute using a set of binary attributes.

### Unsupervised Discretization
There are two basic approaches to the problem of discretization. One is to quantize each attribute in the absence of any knowledge of the classes of the instances in the training set, so-called *unsupervised* discretization. The other is to take the classes into account when discretizing, thus called *supervised* discretization. The former is the only possibility when dealing with clustering problems where the classes are unknown or nonexistent.

The obvious way of discretizing a numeric attribute is to divide its range into a predetermined number of equal intervals, that is, a fixed, data-independent yardstick. This is frequently done at the time when data is collected. But, like any unsupervised discretization method, it runs the risk of destroying distinctions that would have turned out to be useful in the learning process by using gradations that are too coarse or by unfortunate choices of boundary that needlessly lump together many instances of different classes.

*Equal-interval binning* often distributes instances very unevenly; some bins contain many instances while others contain none. This can seriously impair the ability of the attribute to help build good decision structures. It is often better to allow the intervals to be of different sizes, choosing them so that the same number of training examples fall into each one. This method, *equal-frequency binning*, divides the attribute’s range into a predetermined number of bins based on the distribution of examples along that axis—sometimes called *histogram equalization* because if you take a histogram of the contents of the resulting bins, it will be completely flat. If you view the number of bins as a resource, this method makes best use of it.

However, equal-frequency binning is still oblivious to the instances’ classes, and this can cause bad boundaries. For example, if all instances in a bin have one class, and all instances in the next higher bin have another except for the first, which has the original class, surely it makes sense to respect the class divisions and include that first instance in the previous bin, sacrificing the equal-frequency property for the sake of homogeneity. Supervised discretization—taking classes into account during the process—certainly has advantages. Nevertheless it has been found that equal-frequency binning can yield excellent results, at least in conjunction with the Naïve Bayes learning scheme, when the number of bins is chosen in a data-dependent fashion by setting it to the square root of the number of instances. This method is called *proportional k-interval discretization*.

### Entropy-Based Discretization
Because the criterion used for splitting a numeric attribute during the formation of a decision tree works well in practice, it seems a good idea to extend it to more general discretization by recursively splitting intervals until it is time to stop. In [Appendix C](#FigC1_655-685_B9780443158889000236.xhtml#FigC1_655-685_B9780443158889000236), Implementation details of trees and rules, we show how to sort the instances by the attribute’s value and consider, for each possible splitting point, the information gain of the resulting split. To discretize the attribute, once the first split is determined, the splitting process can be repeated in the upper and lower parts of the range, and so on, recursively.

To see this working in practice, we revisit the example given earlier for discretizing the temperature attribute of the weather data, whose values are

| 64 || 65 || 68 || 69 || 70 || 71 || 72 || 75 || 80 || 81 || 83 || 85 |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

| Yes || No || Yes || Yes || Yes || No ||  

No

Yes

 ||  

Yes

Yes

 || No || Yes || Yes || No |

![Image](images/T000078tabt0025.png)

(repeated values have been collapsed together). The information gain for each of the 11 possible positions for the breakpoint is calculated in the usual way. For example, the information value of the test `temperature` < 71.5, which splits the range into four `yes`’s and two `no`’s vs. five `yes`’s and three `no`’s, is
