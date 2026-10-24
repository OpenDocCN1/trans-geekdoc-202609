# Algorithm: AdaBoost. A boosting algorithm—create an ensemble of classifiers. Each one gives a weighted vote.

+   Input:
+   • D, a set of d class-labeled training tuples;
+   • k, the number of rounds (one classifier is generated per round);
+   • a classification learning scheme.

Output: A composite model.

+   Method:
+   (1) initialize the weight of each tuple in D to 1/d;
+   (2) for i = 1 to k do // for each round:
+   (3) sample D with replacement according to the tuple weights to obtain Di;
+   (4) use training set Di to derive a model, Mi;
+   (5) compute error(Mi), the error rate of Mi (Eq. (6.34))
+   (6) if error(Mi) > 0.5 then
+   (7) abort the loop;
+   (8) endif
+   (9) for each tuple in D that was correctly classified do
+   (10) multiply the weight of the tuple by error(Mi)/(1 − error(Mi)); // update weights
+   (11) normalize the weight of each tuple.
+   (12) endfor

+   To use the ensemble to classify tuple, X:
+   (1) initialize weight of each class to 0;
+   (2) for i = 1 to k do // for each classifier:
+   (3) wi = log (1-error(Mi)) / error(Mi); // weight of the classifier's vote
+   (4) c = Mi(X); // get class prediction for X from Mi
+   (5) add wi to the weight for class c
+   (6) endfor
+   (7) return the class with the largest weight.

# FIGURE 6.26
AdaBoost, a boosting algorithm.

through the rest of the algorithm. We can sample to form any sized training set, not necessarily of size d. Sampling with replacement is used—the same tuple may be selected more than once. Each tuple's chance of being selected is based on its weight. A classifier model, Mi, is derived from the training tuples of Di. Its error is then calculated using D as the test set. The weights of the tuples are then adjusted according to how they were classified.

If a tuple was incorrectly classified, its weight is increased. If a tuple was correctly classified, its weight is decreased. A tuple's weight reflects how difficult it is to classify—the higher the weight, the more often it has been misclassified. These weights will be used to generate the training samples for the classifier of the next round. The basic idea is that when we build a classifier, we want it to focus more on the misclassified tuples of the previous round. Some classifiers may be better at classifying some “difficult” tuples than others. In this way, we build a series of classifiers that complement each other. The algorithm is summarized in Fig. 6.26.