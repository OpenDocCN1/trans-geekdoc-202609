
the parameters \(\theta\) as targets for a multiparameter boosting algorithm similar to gradient boosting (Algorithm 8.1). We say “multiparameter” because NGBoost fits a separate model for each parameter at every iteration.

The “natural” in “natural gradient boosting” refers to the fact that NGBoost uses something called the *natural gradient*, as opposed to the ordinary gradient. The natural gradient provides the direction of steepest descent in *Riemannian space*; this is necessary since gradient descent in the parameter space is not gradient descent in the distribution space because distances don’t correspond. The important thing to remember is that NGBoost approximates the gradient of a proper scoring rule—similar to a loss function, but for predicted probabilities and probability distributions of the observed data—as a function of \(\theta\). Compared to alternative probabilistic regression methods, NGBoost is fast, flexible, scalable, and easy to use. An example, albeit in Python, is given in Section 8.9.2. NGBoost is available in the **ngboost** package for Python. For more info, check out the NGBoost GitHub repository at https://github.com/stanfordmlgroup/ngboost.

## 8.8 Specialized implementations

In this section, I’ll take a look at three specialized implementations of GBMs that are quite popular for supervised learning tasks, probably due to their availability across platforms and ability to scale to incredibly large data sets, even on a single machine where the data cannot fit into memory.

### 8.8.1 eXtreme Gradient Boosting: XGBoost

XGBoost [Chen and Guestrin, 2016] is one of the most popular and scalable implementations of GBMs. While XGBoost follows the same principles as the standard GBM algorithm, there are some important differences, a few of which are listed below:

- more stringent regularization to help prevent overfitting;
- a novel sparsity-aware split finding algorithm;
- weighted quantile sketch for fast and approximate tree learning;
- parallel tree building (across nodes within a tree);
- exploits out-of-core processing for maximum scalability on a single machine;
- employs the deep-learning concept of *dropout* to mitigate the problem of *overspecialization* [Vinayak and Gilad-Bachrach, 2015].

With these differences, XGBoost can scale to billions of rows in distributed or memory-limited settings (e.g., a single machine), hence the “extreme” in extreme gradient boosting. It has also been shown to be more accurate than the more traditional implementation of GBM (e.g., the R package **gbm**). There are a number of interfaces to XGBoost, including R, Python (with a scikit-learn interface), Julia, Scala, Java, Ruby, and C++. There’s also a command-line interface. General tuning strategies for XGBoost (with examples in R) are given in Boehmke and Greenwell [2020, Section 12.5.2]. For more details, including installation, visit the XGBoost GitHub repository at https://github.com/dmlc/xgboost.

In contrast to ordinary GBMs, which use CART-like regression trees for the base learners (i.e., splits are determined using the sum of squares criteria described in Section 2.3), XGBoost uses a regularized second-order approximation to the loss function in its split search algorithm. Let $g_{jb}$ (defined previously in Section 8.2) and $h_{jb} = \partial^2 L(y_i, f_{b-1})/\partial f_{b-1}^2$ be the gradient and *hessian* (i.e., second-order gradient) values of the loss function $L$ at the $b$-th iteration evaluated at the $j$-th observation (what a mouthful!). Further, let $I_L$ and $I_R$ be the set of observations in the left and right daughter nodes resulting from split $s$. The set of instances in the parent node is denoted by $I = I_L \cup I_R$. In XGBoost, splits are selected that result in the largest gain (or reduction in loss) which can be written as

$\mathcal{L}_{split} = \frac{1}{2} \left[ \frac{(\sum_{i \in I_L} g_i)^2}{\sum_{i \in I_L} h_i + \lambda} + \frac{(\sum_{i \in I_R} g_i)^2}{\sum_{i \in I_R} h_i + \lambda} - \frac{(\sum_{i \in I} g_i)^2}{\sum_{i \in I} h_i + \lambda} \right] - \gamma.$ (8.7)

For brevity, I dropped the $b$ subscript in $g_i$ and $h_i$. Here, $\gamma \in [0, \infty)$ is the minimum gain required to make a further split in the tree, with larger values resulting in a more conservative algorithm (i.e., fewer splits). Similarly, $\lambda \in [0, \infty)$ can be viewed as an $L_2$ penalty (similar to the one used in *ridge regression*), with larger values resulting in a more conservative algorithm. Both parameters provide a form regularization that constrains the model’s complexity and guards against overfitting. Eventually, XGBoost included an additional regularization parameter, $\alpha \in [0, 1)$, which acts as an $L_1$ penalty (similar to the one used in the LASSO). Consequently, these can be viewed as additional hyperparameters to be tuned.

Aside from the exhaustive greedy search employed by CART, XGBoost provides an optional approximate search algorithm that is more efficient in distributed settings or when the data cannot easily fit into memory. In essence, the continuous feature values are mapped to buckets formed by the percentiles of each feature’s distribution in the training data. The best split for each feature is found by searching through this reduced set of candidate split values. For details, see Chen and Guestrin [2016]. A modification for weighted data, called a weighted quantile sketch, is also discussed in Chen and Guestrin [2016].

Around early 2017, XGBoost introduced fast histogram binning (Section 8.7.2) to even further push the boundaries of scale and computation speed. In contrast to the original approximate tree learning strategy, which generates a new set of bins for each iteration, the histogram method re-uses the bins over multiple iterations, and therefore is far better suited for large data sets. XGBoost also introduced the option to grow trees leaf-wise, as opposed to just level-wise (the default), which can also speed up fitting, albeit, at the risk of potentially overfitting the training data (Section 8.7.1).

Sparse data are common in many situations, including the presence of missing values and one-hot encoding. In such cases, efficiency can be obtained by making the algorithm aware of any sparsity patterns. XGBoost handles sparsity by learning an optimal “default” direction at each split in a tree. When an observation is missing for one of the split variables, for example, it is simply passed down the default branch. For details, see Chen and Guestrin [2016].

One drawback of XGBoost is that it does not currently handle categorical variables—they have to be re-encoded numerically (e.g., using one-hot encoding). However, at the time of writing this book, XGBoost has experimental support for categorical variables, although it’s currently quite limited. An example of using XGBoost is given in Section 8.9.4. Note that XGBoost can also be used to fit RFs in a distributed fashion; see the XGBoost documentation for details.

### 8.8.2 Light Gradient Boosting Machine: LightGBM

LightGBM [Ke et al., 2017] offers many of the same advantages as XGBoost, including sparse optimization, parallel tree building, a plethora of loss functions, enhanced regularization, bagging, histogram binning, and early stopping. A major difference between the two is that LightGBM defaults to building trees leaf-wise (or best-first). Unlike XGBoost, LightGBM can more naturally handle categorical features in a way similar to what’s described in Section 2.4. In addition, the LightGBM algorithm utilizes two novel techniques, gradient-based one-side sampling (GOSS) and exclusive feature bundling (EFB).

GOSS reduces the number of observations by excluding rows with small gradients, while the remaining instances are used to estimate the information gain for each split; the idea is that observations with larger gradients play a more important role in split selection. EFB, on the other hand, reduces the
