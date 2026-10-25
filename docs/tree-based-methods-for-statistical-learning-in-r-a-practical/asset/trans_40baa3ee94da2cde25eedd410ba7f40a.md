

![](img/2c227bfb3620dc3d159fa5e6598afa30_281_0.png)

图 7.14：\(x_1\) 与 \(x_2\) 的散点图。原始数据以黑色显示，虚线黑线给出最大方差方向。PCA 下的旋转点以深黄色显示，并伴随最大方差的新轴；注意在二维中，这如何将点移动到沿 \(x\) 轴具有最大方差。其余颜色显示随机旋转下的数据点。

whose individual means are also normally distributed. A full description of the data generating process can be found in Hastie et al. [2009, Sec. 2.3.3] and an application to RFs is provided in Hastie et al. [2009, Sec. 15.4.3]. The raw data are available at `https://web.stanford.edu/~hastie/ElemStatLearn/data.html`. For convenience, the data are also available in the **treemisc** R package that accompanies this book, and can be read in using:
`library(treemisc)`

```
eslmx <- load_eslmx()
class(eslmx) # should be a list
#> [1] "list"
names(eslmx) # names of components
#> [1] "x" "y" "xnew" "prob"
#> [5] "marginal" "px1" "px2" "means"
```

Note that this is not a data frame, but rather a list with several components; for a description of each, see ?treemisc::load_eslmx.

The code chunk below constructs a scatterplot of the training data (i.e., component x) along with the Bayes decision boundary; see Figure 7.15. The Bayes error rate for these data—that is, the theoretically optimal error rate—is 0.210.

```
x <- as.data.frame(eslmx$x) # training data
xnew <- as.data.frame(eslmx$xnew) # evenly spaced grid of points
x$y <- as.factor(eslmx$y) # coerce to factor for plotting
xnew$prob <- eslmx$prob # Pr(Y = 1 | xnew)
```

```
# Colorblind-friendly palette
oi.cols <- unname(palette.colors(8, palette = "Okabe-Ito"))
```

```
# Construct scatterplot of training points
p <- ggplot(x, aes(x = x1, y = x2, color = y)) +
geom_point(alpha = 1, show.legend = FALSE) +
scale_colour_manual(values = oi.cols) +
theme_bw()
```

```
# Add optimal (i.e., Bayes) decision boundary
p + geom_contour(data = xnew, aes(x = x1, y = x2, z = prob),
breaks = 0.5, color = oi.cols[4],
inherit.aes = FALSE, linetype = 2)
```

Next I fit three tree-based ensembles: a traditional RF, a rotation forest, and a random rotation forest. The rotation forest was fit using the rotationForest package, while the RF and random rotation forest were fit using treemisc's rforest() function. Note that this is a poor man's implementation of Breiman's RF algorithm I wrote that optionally rotates the features at random prior to the construction of each tree. It is based on the well-known randomForest package [Breiman et al., 2018] and is missing many of the bells and whistles, hence not recommended for general use, but it works. Also, this

h As noted in Hastie et al. [2009, Chap. 2], since the data generating mechanism is known for each of these two classes, the theoretically optimal decision boundary can be computed exactly. This makes it useful to compare classifiers visually in terms of their estimated decision boundaries.

![](img/2c227bfb3620dc3d159fa5e6598afa30_283_0.png)

FIGURE 7.15: Simulated mixture data with optimal (i.e., Bayes) decision boundary.

The resulting decision boundaries from each forest are in Figure 7.16. Here, you can see that the axis-oriented nature of the individual trees in a traditional RF leads to a decision boundary with an axis-oriented flavor (i.e., the decision boundary is rather “boxy”). The RF also exhibits more signs of overfitting, as suggested by the little islands of decision boundaries. On the other hand, using feature rotation (with PCA or random rotations) prior to building each tree results in a noticeably smoother and non-axis-oriented decision boundary. The test error rates for the RF, rotation forest, and random rotation forest, under this random seed, are 0.235, 0.239, and 0.226, respectively. (As always, the code to reproduce this example is available on the companion website for this book.)

### 7.8.4 Extremely randomized trees

Just as RFs offer an additional layer of randomization to bagged decision trees, *extremely randomized trees* (or extra-trees) [Geurts et al., 2006] are essentially an RF with an additional randomization step. In particular, the split point for any feature at each node in a tree is essentially selected at random from a uniform distribution. The extra randomization can further

![](img/2c227bfb3620dc3d159fa5e6598afa30_284_0.png)

FIGURE 7.16: Traditional RF vs. random rotation forest on the mixture data from Hastie et al. [2009]. The random rotation forest produces a noticeably smoother decision boundary than the axis-oriented decision boundary from a traditional RF.

decrease variance, but sometimes at the cost of additional bias [Geurts et al., 2006]; this is especially true if the data contain irrelevant features. To combat the extra bias, extra-trees utilize the full learning sample to grow each tree, rather than bootstrap replicas (another subtle difference from the bagging and RF algorithms). Note that bootstrap sampling can be used in extra-trees ensembles, but Geurts et al. argue that it can often lead significant drops in accuracy¹.

¹Most open source implementations of extra-trees optionally allow for bootstrap sampling.

The primary tuning parameters for an extra-trees ensemble are $K$ and $n_{min}$, where $K$ is the number of random splits to consider for each candidate splitter, and $n_{min}$ is the minimum node size, which is a common parameter in many tree-based models and can act as a smoothing parameter. A common default for $K$ is

```
\( K = \begin{cases} \sqrt{p} & \text{for classification} \\ p & \text{for regression} \end{cases} \)
```

where $p$ is the number of available predictors. The optimal split is chosen from the sample of $K$ splits in the usual way (i.e., the split that results in the largest reduction in node impurity). Note that \(n_{min}\) has the same defaults as it does in an RF (Section 7.2).

The extra-trees ensemble still makes use of the RF \(m_{try}\) parameter, but note that, in the extreme case where \(K=1\), an extra-trees tree is unsupervised in that the response variable is not needed in determining any of the splits. Such a *totally randomized tree* [Geurts et al., 2006] can be useful in detecting potential outliers and anomalies, as will be discussed in Section 7.8.5. Extra-trees can be fit in R via the **ranger** package. In Python, an implementation of the extra-trees algorithm is provided by the **sklearn.ensemble** module.

### 7.8.5 Anomaly detection with isolation forests

While the proximities of an RF can be used to detect novelties and potential outliers, they're rather computationally expensive to compute and store, especially for large data sets; also, as previously mentioned, many RF implementations do not support proximities. A more general approach to anomaly detection, called an *isolation forest*, was proposed in Liu et al. [2008]. An isolation forest is essentially an ensemble of *isolation trees* (IsoTrees). IsoTrees are similar to extra-trees with \(K=1\) (Section 7.8.4), except that the splitting variables are also chosen at random; hence, IsoTrees are unsupervised in the sense that the tree building process does not make use of any response variable information.

So how does it work? Isolation forests are quite simple actually. The core idea is to “isolate” anomalous observations, rather than creating a profile for “normal” ones—the latter seems to be the more common approach taken by other methods in practice. Isolation forests assume that

- 1) anomalies are rare in comparison to “normal” observations;
- 2) anomalies differ from “normal” instances in terms of the values of their features.

In other words, isolation forests assume anomalies are “few and different” [Liu et al., 2008]. If anomalies are “few and different”, then they are susceptible to *isolation* (i.e., easy to separate from the rest of the observations).

In an IsoTree, observations are recursively separated until all instances are isolated to their own terminal node; since the split variables and split points are determined completely at random, no response information is needed. Anomalous observations tend to be easier to isolate with fewer random partitions compared to normal instances. That is to say, the relatively few instances of anomalies tend to have shorter path lengths in an IsoTree when compared to normal observations. The path length to each observation can be computed for a forest of independently grown trees and aggregated into a single *anomaly score*. The anomaly score for an arbitrary observation \(\boldsymbol{x}\) is given by

