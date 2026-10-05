# 424

# MACHINE LEARNING

Let us proceed more specifically, where we are equipped with a training data set as the previous method, which contains N independent variables, $x_i$, all of the numeric type. We us further assume that these variables are normalised using the z-score. Further, the data contains one dependent variable, $f$, which is of integer value. The support of $f$ is finite, and we further assume that cardinality of each value of the variable $f$ is large. This is not a mathematical constraint but rather a practical constraint, where the reader should appropriately treat all the pathological cases with having isolated values. Let us assume the dependent variable $f$ takes L different values which we need to classify.

The following algorithm defines the prototype method based on the nearest neighbours:

+   - Split the sample by the value of the dependent variable $f$ into $L$ subsamples. Further, proceed for each subsample independently
  - For each subsample, choose $R$ observations randomly. These observations are centres or the prototypes for a given sample.
  - For each centre, find $k$ neighbours from the sample.
  - Replace the centre by the new centre, which is the average of the $k$ neighbours and the centre itself.
  - Iterate this procedure until convergence.
- Replace the training sample by $L 	imes R$ centres. Each centre carries information about the value of $f$.
- Predict the class of the out-of-sample observation by the class of the nearest neighbour.

This procedure is known in the literature as $k$-clustering.
Let us implement the prototype method using the following: each observation is formed by $(x_1, x_2, f)$, where $x_i \in [0, 1]$, for $i = 1, 2$, and the dependent variable is defined

> $f = I_{(x_1^2+x_2^2\le1)}.$

where $I$ is the indicator function taking value when the argument is true and otherwise. We thus have a dependent variable which classifies whether the point - in feature space - lies within a circle with origin and radius equal to one. Such data can be generated as follows:

```
tableKNN([], x1:10000?\.0;x2:10000?\.0);
tableKNN: update f1:(x1*x1)+(x2*x2) tableKNN
```

We have generated 10,000 points. We can illustrate the data using the following "trick":

```
select x1,x2_0:x2 from tableKNN where f=0 ) select x1,x2_1:x2 from
tableKNN where f=1
```

which can be depicted with the scatter plot option. Figure 21.1 depicts the results, where all points within the unit circle are dark gray and the remaining ones are plotted in light gray.