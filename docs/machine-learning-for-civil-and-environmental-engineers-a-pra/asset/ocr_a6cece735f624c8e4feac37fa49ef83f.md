# 26 Fitness Function Distribution (FFD)

Measures the distance between class distributions as a function of class separability.

```
FFD = \frac{|\mu_{min} - \mu_{maj}|}{\sigma_{min} + \sigma_{maj}} \times I_{(2(\mu_{min}, \mu_{maj}))}
```

+   - Used in scenarios with unbalanced data.
+   - Treats predictions as independent distributions.
+   - Measures separability (i.e., the distance between class distributions) [43] - high separability (no overlap), and this distance turn large (go to +\(\infty\)).
+   - Uses \(L_{\nu}\) to enforce zero class threshold.

# 27 Canberra Metric (CM)

Measures the distance between pairs of points in a vector space.

```
CM = \sum_{i=1}^n \frac{|E_i|}{A_i + P_i}
```

+   - Normalizes the difference of each pair of coefficients with its maximum [44-46].

# 28 Wave Hedges Distance (WHD)

-

```
WHD = \sum_{i=1}^n \frac{|E_i|}{max(A_i, P_i)}
```

# 29 Lift [47]

Measures the performance of a model at predicting or classifying cases.

```
LIFT = \frac{\% \text{ of true positives above the threshold}}{\% \text{ of dataset above threshold}}
```

+   - Measures betterness of a classifier than a baseline classifier that randomly predicts positives.
+   - A threshold is set as a static fraction of the positive dataset.
+   - Lift and Accuracy do not always correlate well.
+   - Minimizing MXE gives the maximum likelihood [35].

# 30 Mean Cross Entropy (MXE)

Measures the performance of a model where the output is a probability between zero and one.

```
MXE = -\frac{1}{N} \sum True \times \ln(Predicted) + (1 - True) \times \ln(1 - Predicted)
```

+   - (The assumptions are that Predicted \(\in [0, 1]\) and True \(\in \{0, 1\}\).)

# 31 Probability Calibration (CAL)

-

+   1) Order cases 1-100 by their predicted in the same bin.
+   2) Evaluate the percentage of true positives.
+   3) Calculate the mean prediction for true positives.
+   3) Calculate the mean prediction error for this bin (using the absolute value of the difference between the observed frequency and the mean).
+   4) Repeat steps 1-4 for cases 2-101, 3-102, etc.
+   5) CAL is calculated as the mean of these binned calibration errors [35].

+   - Lengthy.
+   - Precision = Recall

# 32 Precision-recall break-even point

The point at which the precision-recall-curve intersects the bisecting line.

+   - Defines the point when precision and recall are equal.