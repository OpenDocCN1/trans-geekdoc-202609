
### 7.5.2.2 Conditional permutation importance

A major drawback of permutation-based importance measures is the inherent assumption of independent features (e.g., the features are uncorrelated). For example, if x1 and x2 have a strong dependency, then it doesn’t make sense to randomly permute x1 while holding x2 constant (or vice versa). To this end, [Strobl et al., 2008b] describe a conditional permutation importance measure that adjusts for correlations between predictor variables. In particular, the conditional permutation importance of each variable is computed by permuting within a grid defined by the covariates that are associated with the variable of interest. According to Strobl et al. [2008b], the resulting variable importance scores are conditional in the sense of coefficients in a regression model, but represent the effects of a variables in both main effects and interactions. When missing values are present in the predictors, the procedure described in Hapfelmeier et al. [2014] can be used to measure variable importance. While this idea applies in general to any type of RF, its implementations currently seem limited to the conditional inference trees and forest provided by the party and partykit packages in R; see, for example, ?partykit::varimp.

## 7.6 Casewise proximities

So far in this book, we’ve mainly discussed tree-based methods for supervised learning problems. However, not every problem is supervised. For example, it is often of interest to understand how the data clusters—that is, whether the rows of the data form any “interesting” groups. (This is an application of unsupervised learning.) Many clustering methods rely on computing the pairwise distances between any two rows in the data, but the challenge becomes choosing the right distance metric. Euclidean distance (i.e., the “ordinary” straight-line, or “as the crow flies” distance between two points), for example, is quite sensitive to the scale of the inputs. It’s also rather awkward to compute the Euclidean distance between two rows of data when the features are a mix of both numeric and categorical types. Fortunately, other distance (or distance-like) measures are available which more naturally apply to mixed data types.

Another useful output that can be obtained from an RF, provided it’s implemented, are pairwise case proximities. RF proximities are distance-like measures of how similar any two observations are, and can be used for

- clustering in supervised and unsupervised (Section 7.6.3) settings;
- detecting outliers/novel cases (Section 7.6.1);
- imputing missing values (Section 7.6.2).

To compute the proximities between all pairs of training observations in an RF, do the following:

- 1) pass all of the data, both training and OOB, down each tree;
- 2) every time records i and j cohabitate in the same terminal node of a tree, increase their proximity by one;
- 3) At the end, normalize the proximities by dividing by the number of trees in the forest.

So how does this measure similarity between cases? Recall that RFs (and bagged decision trees in general) intentionally build deep, overgrown decision trees. In order for two observations to land in the same terminal node, they have to satisfy all of the same conditions leading to it. If two observations occupy the same terminal node across a majority of the trees in the forest, then they are likely very similar to each other in terms of feature values. Note that using all the training data can lead to unrealistic proximities. To circumvent this, proximities can be computed on only the OOB cases. It is also possible to compute proximities for new cases (an example application is given in Section 7.6.4).

The end result is an N x N proximity matrix, where N is the sample size of the data set proximities are being computed for. As it turns out, this matrix is symmetric (since prox (i, j) = prox (j, i)), positive definite (i.e., has all positive eigenvalues), and bounded above by one, with the diagonal elements equal to one (since prox (i, i) = 1). Consequently, for any two cases i and j, we can treat 1 - prox (i, j) as a squared distance-like metric, which can be used as input into any distance-based clustering algorithm. For example, Shi et al. [2005] used RF proximities to help identify fundamental subtypes of cancer. A brief example using the Swiss banknote data is provided in Section 7.6.3.1.

The proximities from an RF provide a natural measure of similarity between records when the predictor variables are of mixed types (e.g., numeric and categorical) and measured on different scales; they are invariant to monotone transformations and naturally support categorical variables. The biggest drawback, as with any pairwise distance-like metric, is that it requires storing an N x N matrix; although, since the casewise proximity matrix is symmetric, you only need to store the upper or lower triangular part (see, for example, ?treemisc::proximity). Proximities are also not implemented in most open source RF software. However, if you can obtain the N x B matrix of terminal node assignments (which is available in most open source RF software), then it is rather straightforward to compute the proximities yourself; an example, specific to the R package ranger [Wright et al., 2021], can be found at https://mnwright.github.io/ranger/r/oob-proximity-matrix/, while a C++ implementation is available in treemisc's `proximity()` function. The next two sections discuss more specific uses of proximities that are useful in a supervised learning context.

### 7.6.1 Detecting anomalies and outliers

Outliers (or anomalies) are generally defined as cases that are removed from the main body of the data. In the context of an RF, Leo Breiman defined outliers as cases whose proximities to all other cases in the data are generally small. For classification, he proposed a simple measure of “outlyingness” based on the RF proximity values. Define the average proximity from case m in class j to the rest of the training data in class j as

```
prox^*(m) = \sum_{k \in class j} prox^2(m, k),
```

where the sum is over all training instances belonging to class j. The outlyingness of case m in class j to all other cases in class j is defined as

```
out(m, j) = \frac{N}{prox^*(m)},
```

where N is the number of training instances. Generally, a value above 10 is reason to suspect the case of being an outlier [Breiman, 2002]. Obviously, this measure is limited to smaller data sets and RF implementations where proximities can be efficiently computed. In Section 7.8.5, I’ll look at a specialized RF extension that’s more suitable for detecting outliers and anomalies, especially in higher dimensions. An interesting use case for the proximity-based outlyingness measure is presented in the next section.

### 7.6.1.1 Example: Swiss banknotes

An interesting use case for the proximity-based outlyingness measure is in detecting potentially mislabeled response classes in classification problems. Consider, for example, the Swiss banknote data from Section 1.4.1. Before fitting a default RF, I switched the label for observation 101; this observation is supposedly a counterfeit banknote (y = 1), but I switched the class label to genuine (y = 0). The proximity-based outlyingness scores are displayed in Figure 7.9. There are two obvious potential outliers, labeled with their corresponding row number. Here, you can see that the counterfeit banknote I mislabeled as genuine (observation 101) received the largest outlier score. Observation 70 is also interesting and worth investigating; perhaps it was also mislabeled?

![](img/2c227bfb3620dc3d159fa5e6598afa30_268_0.png)

FIGURE 7.9: Proximity-based outlier scores for the Swiss banknote data. The largest outlier score corresponds to observation 101, which was a counterfeit banknote that was mislabeled as genuine.

### 7.6.2 Missing value imputation

Many decision tree algorithms can naturally handle missing values; CART and CTree, for example, employ surrogate splits to handle missing values (Section 2.7). Unfortunately, the idea does not carry over to RFs. I suppose that makes sense: searching for surrogates would greatly increase the computation time of the RF algorithm. Although some RF software can handle missing values without casewise deletion (e.g., the h2o package in both R and Python), most often they have to be imputed or otherwise dealt with.

Breiman also developed a clever way to use RF proximities for imputing missing values. The idea is to first impute missing values with a simple method (such as using the mean or median for numeric predictors and the most common value for categorical ones). Next, fit an initial RF to the N complete observations and generate the N × N proximity matrix. For a numeric feature, the initial imputed values can be updated using a weighted mean over the non-missing values where the weights are given by the proximities. For categorical variables, the imputed values are updated using the most frequent non-missing values where frequency is weighted by the proximities. Then just iterate until some convergence criterion is met (typically 4-6 runs). In other words, this method just imputes missing values using a weighted mean/mode with more weight on non-missing cases.
