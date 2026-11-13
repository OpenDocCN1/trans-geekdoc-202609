they increase (except for fallout for which it is the opposite). Many other indicators also exist, like the false discovery rate or false omission rate, but they are not as mainstream and less cited. Moreover, they are often simple functions of the ones mentioned above.

A metric that is popular but more complex is the Area Under the (ROC) Curve, often referred to as AUC. The complicated part is the ROC curve where ROC stands for Receiver Operating Characteristic; the name comes from signal theory. We explain how it is built below.

As seen in Chapters 6 and 7, classifiers generate output that are probabilities that one instance belongs to one class. These probabilities are then translated into a class by choosing the class that has the highest value. In binary classification, the class with a score above 0.5 basically wins.

In practice, this 0.5 threshold may not be optimal and the model could very well correctly predict false instances when the probability is below 0.4 and true ones otherwise. Hence, it is a just idea to test what happens if the decision threshold changes. The ROC curve does just that and plots the recall as a function of the fallout when the threshold increases from zero to one.

When the threshold is equal to 0, true positives are equal to zero because the model never forecasts positive values. Thus, both recall and fallout are equal to zero. When the threshold is equal to one, false negatives shrink to zero and true negatives too, hence recall and fallout are equal to one. The behavior of their relationship in between these two extremes is called the ROC curve. We provide stylized examples below in Figure 10.2. A random classifier would fare equally good for recall and fallout and thus the ROC curve would be a linear line from the point (0,0) to (1,1). To prove this, imagine a sample with a \(p \in (0, 1)\) proportion of true instances and a classifier that predicts true randomly with a probability \(p' \in (0, 1)\). Then because the sample and predictions are independent, \(TP = p'p\), \(FP = p'(1 - p)\), \(TN = (1 - p')(1 - p)\) and \(FN = (1 - p')p\). Given the above definition, this yields that both recall and fallout are equal to \(p'\).

![](bbox=[0.276, 0.562, 0.727, 0.831])

**FIGURE 10.2:** Stylized ROC curves.

An algorithm with a ROC curve above the 45° angle is performing better than an average