
[Fig. 9.10](#Ch010_347-389_B9780443158889000108.xhtml#f0055) gives an example of a model tree formed by this algorithm for a problem with two numeric and two nominal attributes. What is to be predicted is the rise time of a simulated servo system involving a servo amplifier, motor, lead screw, and sliding carriage. The nominal attributes play important roles. Four synthetic binary attributes have been created for each of the five-valued nominal attributes `motor` and `screw` and are shown in [Table 9.1](#Ch010_347-389_B9780443158889000108.xhtml#t0010) in terms of the two sets of values to which they correspond. The ordering of these values (D, E, C, B, A for `motor` and coincidentally D, E, C, B, A for `screw` also) is determined from the training data—the rise time averaged over all examples for which `motor` = D is less than that averaged over examples for which `motor` = E, which is less than when `motor` = C, and so on. It is apparent from the magnitude of the coefficients in [Table 9.1](#Ch010_347-389_B9780443158889000108.xhtml#t0010) that `motor` = D vs E, C, B, A and `screw` = D, E, C, B vs A play leading roles in the `LM2`, `LM3`, and `LM4` models (among others). Both `motor` and `screw` also play a minor role in several of the models.

![Fig. 9.10 Model tree for a data set with nominal attributes.](images/F000108f09-10-9780443158889.jpg)

[Fig. 9.10](#Ch010_347-389_B9780443158889000108.xhtml#Bf0055) Model tree for a data set with nominal attributes.

Table 9.1

Linear Models in the Model Tree

| Model ||   || LM1 || LM2 || LM3 || LM4 || LM5 || LM6 || LM7 || LM8 || LM9 || LM10 || LM11 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `Constant term` ||   || 0.96 || 1.14 || 1.43 || 1.52 || 2.69 || 2.91 || 0.88 || 0.98 || 1.11 || 1.06 || 0.97 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Pgain ||   || −0.38 || −0.38 || −0.38 || −0.38 || −0.38 || −0.38 || −0.24 || −0.24 || −0.24 || −0.25 || −0.25 |
| Vgain ||   || 0.71 || 0.49 || 0.49 || 0.49 || 0.56 || 0.45 || 0.13 || 0.15 || 0.15 || 0.10 || 0.14 |
| Motor = D || vs E, C, B, A || 0.66 || 1.14 || 1.06 || 1.06 || 0.50 || 0.50 || 0.30 || 0.40 || 0.30 || 0.14 || 0.14 |
| Motor = D, E || vs C, B, A || 0.97 || 0.61 || 0.65 || 0.59 || 0.42 || 0.42 || −0.02 || 0.06 || 0.06 || 0.17 || 0.22 |
| Motor = D, E, C || vs B, A || 0.32 || 0.32 || 0.32 || 0.32 || 0.41 || 0.41 || 0.05 ||   ||   ||   ||   |
| Motor = D, E, C, B || vs A ||   ||   ||   ||   || 0.08 || 0.05 ||   ||   ||   ||   ||   |
| Screw = D || vs E, C, B, A ||   ||   ||   ||   ||   ||   ||   ||   ||   ||   ||   |
| Screw = D, E || vs C, B, A || 0.13 ||   ||   ||   ||   ||   ||   ||   ||   ||   ||   |
| Screw = D, E, C || vs B, A || 0.49 || 0.54 || 0.54 || 0.54 || 0.39 || 0.40 || 0.30 || 0.20 || 0.16 || 0.08 || 0.08 |
| Screw = D, E, C, B || vs A ||   || 1.73 || 1.79 || 1.79 || 0.96 || 1.13 || 0.22 || 0.15 || 0.15 || 0.16 || 0.19 |

![Image](images/T000108tabt0010.png)

### Rules From Model Trees

Model trees are essentially decision trees with linear models at the leaves. Like decision trees, they may suffer from the replicated subtree problem explained in [Section 3.4](#Ch003_67-89_B9780443158889000042.xhtml#s0025), and sometimes the structure can be expressed much more concisely using a set of rules instead of a tree. Can we generate `rules` for numeric prediction? It turns out that we can. The strategy to do this is to use a separate-and-conquer approach in conjunction with partial model trees to generate decision lists. The same strategy can be applied to extract decision rules from trees, cf. [Appendix C.2](#FigC1_655-685_B9780443158889000236.xhtml#s0060).

First build a partial model tree from all the data. Pick one of the leaves and make it into a rule. Remove the data covered by that leaf, then repeat the process with the remaining data. The question is how to build the partial model tree, that is, a tree with unexpanded nodes. This boils down to the question of how to pick which node to expand next. For decision trees the algorithm of [Fig. C.5](#FigC1_655-685_B9780443158889000236.xhtml#f0030) ([Appendix C](#FigC1_655-685_B9780443158889000236.xhtml#FigC1_655-685_B9780443158889000236), “Implementation details of trees and rules”) picks the node whose entropy for the class attribute is smallest. For model trees, whose predictions are numeric, simply use the variance instead. This is based on the same rationale—the lower the variance, the shallower the subtree and the shorter the rule. The rest of the algorithm stays the same, with the model tree learner’s split selection method and pruning strategy replacing the decision tree learner’s. Because the model tree’s leaves are linear models, the corresponding rules will have linear models on the right-hand side.

There is one caveat when using model trees in this fashion to generate rule sets. It turns out that using smoothed model trees does not reduce the error in the final rule set’s predictions. This may be because smoothing works best for contiguous data but the separate-and-conquer scheme removes data covered by previous rules, leaving holes in the distribution. Smoothing, if it is done at all, must be performed after the rule set has been generated.

### Locally Weighted Linear Regression

An alternative approach to numeric prediction is the method of locally weighted linear regression. With model trees the tree structure divides the instance space into regions, and a linear model is found for each of them. In effect the training data determines how the instance space is partitioned. Locally weighted regression, on the other hand, generates local models at prediction time by giving higher weight to instances in the neighborhood of the particular test instance. More specifically, it weights the training instances according to their distance to the test instance and performs a linear regression on the weighted data. Training instances close to the test instance receive a high weight; those far away receive a low one. In other words, a linear model is tailor made for the particular test instance at hand and used to predict the instance’s class value.

To use locally weighted regression, you need to decide on a distance-based weighting scheme for the training instances. A common choice is to weight the instances according to the inverse of their Euclidean distance from the test instance. Another possibility is to use the Euclidean distance in conjunction with a Gaussian kernel function. However, there is no clear evidence that the choice of weighting function is critical. More important is the selection of a “smoothing parameter” that is used to scale the distance function—the distance is multiplied by the inverse of this parameter. If it is set to a small value only instances very close to the test instance will receive significant weight; if it is large more distant instances will also have a significant impact on the model. One way of choosing the smoothing parameter is to set it to the distance of the `k`th nearest training instance so that its value becomes smaller as the volume of training data increases. If the weighting function is linear, say `max`(0, 1–`smoothed-distance`), the weight is zero for all instances further than the `k`th nearest one. Then the weighting function has bounded support and only the `k` − 1 nearest neighbors need to be considered for building the linear model. The best choice of `k` depends on the amount of noise in the data. The more noise there is the more neighbors should be included in the linear model. Generally an appropriate smoothing parameter is found using cross-validation.
