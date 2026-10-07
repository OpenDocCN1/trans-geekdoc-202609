# Iterative convolutional neural network 211

![](bbox=[0.165, 0.075, 0.785, 0.355])

**Figure 9.16** Prediction rank ($PR_{\mu}$ and $PR_{\mu} + 2 	imes PR_{\sigma}$) for various classes at iteration 1): (a) maximum $PR_{\mu}$, among all classes in each iteration and (b) maximum $PR_{\mu} + 2 	imes PR_{\sigma}$ among all classes in each iteration

# 9.8.2 Pruning neurons in FC layers

Let us sort the probabilities for each image in descending order. The rank of a class is the location of the class in the sorted array. When we set the pruning threshold ($P_{th}$) to value $L$ in a given iteration, all classes with ranks greater than $L$ are eliminated in the next iteration. Hence, computation of FC layer for these classes can be skipped. This results in significant reduction in required for FC computation, and elimination of memory transfer of parameters related to the classification of eliminated classes.

For example, let us consider the input image to be classified as a tabby cat. The first iteration of ICNN yields high probability values for tabby cat, Egyptian cat, Persian cat and possibly other animals, while the probability values associated with other categories (e.g., various types of vehicles) are close to zero. Hence, in the FC layer of next uCNN, the neurons for other low probability categories are disabled and those are eliminated.

# 9.8.3 Pruning filters in CONV layers

In addition to eliminating neurons in the FC layers, CONV filters in finallayer(s) can also be eliminated. To this end, for each class, we carry out a statistical analysis on the 1.2 million images in the training set. In this study, we identify the classes that are least affected by elimination of each CONV filters at each iteration. When we set the pruning threshold ($P_{th}$) to value $L$ in a given iteration, all classes with ranks greater than $L$ are eliminated in the subsequent iteration. Hence, the required CONV filters