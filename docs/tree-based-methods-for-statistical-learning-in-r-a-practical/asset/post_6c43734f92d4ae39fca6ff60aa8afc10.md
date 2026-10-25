
than the majority class is discarded. Some implementations, like R's rpart package, further require surrogate splits to send at least two observations to each of the left and right child nodes.

Returning to the Swiss banknote example, let's find the surrogate splits for the primary split on diagonal depicted in Figure 2.18. We can find the surrogate splits using the same splitting process as before, albeit with our new target variable y*:

```
bn2 <- treemisc::banknote # load Swiss banknote data
bn2$y <- ifelse(bn2$diagonal >= 140.65, 1, 0) # new target
bn2$diagonal <- NULL # remove column
features <- c("length", "left", "right", "bottom", "top")
res <- sapply(features, FUN = function(feature) {
find_best_split(bn2, x = feature, y = "y", n = nrow(bn2))
})
rownames(res) <- c("cutpoint", "gain")
res[, order(res["gain", ], decreasing = TRUE)]
```

| | bottom | right | top | left | length |
|---|---|---|---|---|---|
| cutpoint | 9.550 | 129.850 | 10.950 | 130.050 | 215.1500 |
| gain | 0.343 | 0.169 | 0.157 | 0.137 | 0.0344 |

In this case, the ranked surrogate splits—in descending order of importance—are bottom, right, top, left, and length; the corresponding split points for each are also shown in the output (we'll verify these results in Section 2.9 using real tree software). If we were to use the decision stump in Figure 2.18 to classify a new banknote with a missing value for diagonal, the tree would use the next best surrogate split instead (in this case, whether or not bottom >= 9.550).

For each surrogate, we could also compute its agreement and adjusted agreement with the primary split, which are used in rpart's definition of variable importance (Section 2.8). The agreement between a primary split and its surrogate is just the proportion of observations they send in the same direction. The adjusted agreement adjusts this proportion by subtracting the number of observations sent one way or another using the majority rule. An example is given in Section 2.9.

### 2.7.1 Other missing value strategies

Aside from being able to handle missing predictor values directly, classification trees can be extremely useful in examining patterns of missing data [Harrell, 2015, Sec. 3.2]. For example, CART can be used to describe observations that tend to have missing values (a description problem). This can be done by growing a classification tree using a target variable that's just a binary indicator for whether or not a variable of interest is missing; see Harrell [2015, pp. 302–304] for an example using real data in R.

It can also be informative to construct missing value indicators for each predictor under consideration. Imagine, for example, that you work for a bank and that part of your job is to help determine who should be denied for a loan and who should not. A missing credit score on a particular loan application might be an obvious red flag, and indicative of somebody with a bad credit history, hence, an important indicator in determining whether or not to approve them for a loan. A similar strategy for categorical variables is to treat missing values as an actual category. As noted in van Buuren [2018, Sec. 1.3.7], the missing value indicator method may have its uses in particular situations but fails as a generic method to handle missing data (e.g., it does not allow for missing data in the response and can lead to biased regression estimates across a wide range of scenarios).

Imputation—filling in missing values with a reasonable guess—is another common strategy, and trees make great candidates for imputation models (e.g., they're fully nonparametric and naturally support both classification and regression).

Using CART for the purpose of missing value imputation has been suggested by several authors; see van Buuren [2018, Sec. 3.5] for details and several references. A generally useful approach is to use CART to generate *multiple imputations* [van Buuren, 2018, Sec. 3.5] via the *bootstrap method* (see Davison and Hinkley [1997] for an overview of different bootstrap methods); multiple imputation is now widely accepted as one of the best general methods for dealing with incomplete data [van Buuren, 2018, Sec. 2.1.2].

The basic steps are outlined in Algorithm 2.2; also see `?mice::cart` for details on its implementation in the **mice** package [van Buuren and Groothuis-Oudshoorn, 2021]. Here, it is assumed that the response $y$ corresponds to the predictor with incomplete observations (i.e., contains missing values) and that the predictors correspond to the original predictors with complete information (i.e., no missing values).

As described in Doove et al. [2014] and van Buuren [2018, Sec. 3.5], this process can be repeated $m$ times using the bootstrap to produce $m$ imputed data sets. As noted in van Buuren [2018, Sec. 3.5], Algorithm 2.2 is a form of *predictive mean matching* [van Buuren, 2018, Sec. 3.4], where the "predictive mean" is instead calculated by CART, as opposed to a regression model. An example using CART for multiple imputation is provided in Section 7.9.3.

But what if you're using a decision tree as the model, and not just as a means for imputation: should you rely on surrogate splits or a different strategy,

Unless stated otherwise, a bootstrap sample refers to a random sample of size $N$ with replacement from a set of $N$ observations; hence, some of the original observations will be sampled more than once and some not at all.

### Algorithm 2.2 Tree-based missing value imputation.

- 1) fit a decision tree (e.g., CART) to the complete observations;
- 2) find the terminal assigned to each observation with a missing y value;
- 3) for each missing y value, randomly draw an observed response value from the terminal node to which it's assigned (i.e., the complete response values from the learning sample that summarize the node) to use for the imputed value.

like imputation? Feelders [2000] suggests that imputation (especially multiple imputation), if done properly, tends to outperform trees based on surrogate splits. However, one should still consider whether or not the potential for improved performance outweighs the additional effort required in specifying an appropriate imputation scheme. Feelders further notes that with "...moderate amounts of missing data (say 10% or less) one can avoid generating imputations and just use surrogate splits."

## 2.8 Variable importance

In practice, it may be useful, or even necessary, to reduce the number of features in a model. One way to accomplish this is to rank them in some order of importance and use a subset of the top features. Loh [2012] showed that using a subset of only the important variables can lead to increased prediction accuracy. Reducing the number of features can also decrease model training time and increase interpretability. However, lack of a proper definition of "importance" has led to many variable importance measures being proposed; see Greenwell and Boehmke [2020] for some discussion and further references.

Decision trees probably offer the most natural model-specific approach to quantifying the importance of predictors. In a binary decision tree, at each node A, a single predictor is used to partition the data into two homogeneous groups. The chosen predictor is the one that maximizes (2.3). The relative importance of predictor x is the sum of the squared improvements over all internal nodes of the tree for which x was chosen as the primary splitter; see Breiman et al. [1984] for details. This idea also extends to regression trees and ensembles of decision trees, such as those discussed in Chapters 5–8.

When surrogate splits are enabled, they can be accounted for in the quantification of variable importance. In particular, a variable may appear in the tree more than once, either as a primary or surrogate splitter. The variable importance measure for a feature is the sum of the gains associated with each split for which it was the primary variable, plus the gains (adjusted for agreement) associated with each split for which it was a surrogate. The notation is a bit involved, but the interested reader is pointed to Loh and Zhou [2021, Sec. 3].

Including surrogate information can help improve interpretation when you have strongly correlated or redundant features. For instance, imagine two features x1 and x2 that are essentially redundant. If we only counted gains where each variable was a primary splitter, these two features would likely split the importance, with neither showing up as important as they should. Comparing the variable importance rankings with and without competing splitters (i.e., non-primary splitters) can also be informative. Variables that appear to be important, but rarely split nodes, are probably highly correlated with the primary splitters and contain very similar information.

The relative variable importance standardizes the raw importance values for ease of interpretation. The relative importance is typically defined as the percent improvement with respect to the most important predictor, and is often reported in statistical software. The relative importance of the most important feature is always 100%. So, if x3 is the most important feature, and the relative importance of another feature, say x5, is 83%, you can say that x5 is roughly 83% as important as x3.

It is well known, however, that CART-like variable importance scores are biased; see Loh and Zhou [2021] for a thorough (and more recent) review. According to Loh and Zhou, a variable importance procedure is said to be unbiased if all predictors have the same mean importance score when they are independent of the response. Solutions to CART's variable importance bias, which really stems from CART's split selection bias (Section 2.4.2), are discussed in several places throughout this book; see, for example, the discussion in Section 7.5.1.

## 2.9 Software and examples

Packages rpart and tree [Ripley, 2021] provide modern implementations of the CART algorithm in R, although rpart is recommended over tree, and so we won't be discussing the latter. The name rpart comes from the acronym for (binary) Recursive PARTitioning. Beyond simple classification and regression trees, rpart can also be used to model Poisson counts (e.g., the number of occurrences of some event per unit of time), and censored outcomes. Note
