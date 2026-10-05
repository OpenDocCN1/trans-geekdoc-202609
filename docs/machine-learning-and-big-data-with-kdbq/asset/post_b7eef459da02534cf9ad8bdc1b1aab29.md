
# 484

# MACHINE LEARNING

As a rule of thumb, it is recommended for growing the tree, the Gini index or cross-entropy are used. For the cost-complexity pruning algorithm, any measure can be used. Many researchers prefer the misclassification rate, though.

It is worth to note that the Gini index can be obtained as a consequence of changing the majority vote into probabilistic interpretation. Many, if we interpret the outcome of a node in terms of probability to classify $m$ as class $k$, i.e., $\hat{p}_{mk}$, the training error rate of this rule in the node is $\sum_{k'}\hat{p}_{mk}\hat{p}_{mk'}$. If observed as 1 for class $k$ and 0, the variance within the node is $\hat{p}_{mk}(1-\hat{p}_{mk})$. We can sum the variance of all nodes and obtain the Gini index.

# MISCELLANEOUS

Let us summarise several observations which are useful when considering the decision trees on real examples. In this section we have covered CART, or Classification And Regression Tree, algorithm. There are other alternative successful methods to construct trees, for example, C4.5; see Quinlan (2014).

# Beyond binary trees

It is not practical to use trees which split into more than two branches at each node. The tree will cause considerable fragmentation and not enough structure can be built due to the insufficient amount of data.

# Categorical predictors

The dependent variable can be composed of categorical variables. The dependent variable is formed of $Q$ possible unordered values, then there are $2^{Q-1}-1$ possible partitions. If $Q$ is large, this becomes numerically infeasible.

# The loss matrix

In practical problems, the different outcomes can have a different impact. For example, in medicine, we need to minimise Type 2 error, i.e. failing to detect disease is as costly as opposed to producing false alarms. On the other hand, in the judicial system, Type 1 error is not acceptable as releasing a guilty person is better to sentencing an innocent one.

In order to take this into account, we define a $K \times K$ loss matrix $L$, with $L_{kk'}$ being the loss for classifying a true class $k$ as class $k'$. The diagonal of $K$ contains zeros. Consequently, the Gini index is modified as:

```
$Loss(T) = \sum_{k' \neq k} L_{kk'}\hat{p}_{mk}\hat{p}_{mk'}.\quad(24.20)$
```

The loss matrix $K$ can be interpreted in Bayesian language as prior probabilities imposed on the classes.

# Trees 485

# Additive structure

Decision trees can successfully describe non-linear patterns in the data. However, the trees have a blind spot, which is nothing but models with additive structure. Let us illustrate it on a simple example where the dependent variable is a function of two factors $x_1$ and $x_2$ where the underlying data generating process results:

```
$Y_i = c_1(x_1 < \xi_1) + c_2(x_2 < \xi_2) + \epsilon_i, \quad (24.21)$
```

where $\epsilon_i$ is a zero-mean noise. It is not difficult to see that the decision needed such a model. In case of more complex additive models, the decision trees may need a large amount of data to work. A more suitable method is using Multivariate Adaptive Splines; see Friedman (1991). This method provides smoother models as opposed to decision trees, which are by nature rough.

# Decision dependence

Decision trees are data dependent, where small variation in a data set can easily result in a completely different decision tree structure. This instability is a disadvantage when we want to interpret the data as a set of rules. On the other hand, data dependence which allows us to construct forests of trees will lead to a significant improvement in fitting models. The next chapter will be devoted to forests and how they address this issue.

However, before we do that, let us illustrate a way to build trees using q.

# 24.5 IMPLEMENTATION OF TREES

We now look at a sample use case, using the famous Iris data set, and build our code around it. First, we load our data:

```
iris::read("csv")@enlist:irisData.csv;
```

iris

| sepLength | sepWidth | petalLength | petalWidth | class |
|---|---|---|---|---|
| 5.1 | 3.5 | 1.4 | 0.2 | setosa |
| 4.9 | 3.0 | 1.4 | 0.2 | setosa |
| 4.7 | 3.2 | 1.3 | 0.2 | setosa |
| 4.6 | 3.1 | 1.5 | 0.2 | setosa |
| 5.4 | 3.9 | 1.7 | 0.4 | setosa |
| 4.6 | 3.4 | 1.4 | 0.3 | setosa |
| 5.0 | 3.4 | 1.5 | 0.2 | setosa |
| 5.4 | 2.9 | 1.4 | 0.2 | setosa |
| 4.9 | 3.1 | 1.5 | 0.1 | setosa |
| 5.4 | 3.7 | 1.5 | 0.2 | setosa |
| 4.8 | 3.4 | 1.6 | 0.2 | setosa |
| 4.8 | 3.0 | 1.4 | 0.1 | setosa |
| 4.3 | 3.0 | 1.1 | 0.1 | setosa |

# 486

# MACHINE LEARNING

We use our q sample implementation by creating a function which can classify real values into integer values. This will enable us to fit a classification where our predicted variable takes values $0,...,K-1$ using 0 as the first class, in q's natural indexing.

```
.qtrees.classifier:[breakpoints;y] asc y;
```

For our loss, we choose to implement a function which calculates entropy according to formula:

```
.qtrees.entropy:[y;classes]
// y -- vector of sampled variable
// classes -- domain we wish to classify y, the distinct classes
p:(sum(y)%count x)each classes;neg p log p;
```

Information gain for a given classification in each split is given by:

```
.qtrees.info:[yp;split;classes]
// yp -- the parent node classification set of attributes
// split -- the node classification set of attributes after split
// classes -- the set of classes
uncond:.qtrees.entropy[yp][classes];
cond:(wsum).flip([count[y]%count x])[yp];qtrees.entropy[classes])split;
uncond -- cond;
};
```

Let us validate these definitions with a few intuitive examples. The entropy of a sample from 0 1 2 containing only 1's is 0:

```
0=.qtrees.entropy[1 1 1;0 2]
```

Increasing the randomness increases the entropy:

```
.qtrees.entropy[0 1 1;0 2]
0.8112781
```

```
.qtrees.entropy[0 1 2;0 2]
1.584963
```

# 487

Similarly, we observe an increase of information gain as we lower the entropy we create when splitting a parent node into children:

```
.qtrees.infogain[1 1 2;(enlist 1 1 2);0 1 2]
0.1225562
```

```
.qtrees.infogain[1 1 2;(1 1 1 2);0 1]
0.3112781
```

```
.qtrees.infogain[1 1 2;(1 1;enlist 2);0 1 2]
0.8112781
```

We also define a couple of utility functions which will affect our splitting rule of choice:

```
.qtrees.applyRule:[cbm;bmi;xi;rule;j]
// cbm count of the bitmap: number of sampled points for predicted
// predictor variable
// bmi bitmap indicating indices of the sampled variables at this
// node
// xi the ith predicted variable
// rule to split on
// j split xi at point j based on rule
(:bitmap applied!((@zb;cbm;bmi;]) not b);
// bitmap applied!((@zb:cbm@b; bmi;]) b=eval(rule;xi;j); ((:))
;
```

```
.qtrees.runRule:[rule;i;j] rule[x i j]
```

In the above definition of applyRule we also carry a bitmap of indices of the initial sample data and return a dictionary- to do so allows us to envisage the tree structure and contents at each node, enabling us to observe and study the tree at every step.

We can now move to the higher levels of functions choosing the split and finally growing the tree:

```
.qtrees.chooseSplitXi:[{yy;y;cbm;bmi;rule;classes;xi]}
// yy predicted variable, all sample points
// y predicted variable at node
// cbm count of the bitmap: number of sampled points for predicted
// predictor variable
// bmi bitmap indicating indices of the sampled variables at this
// node
// xi the ith predicted variable
```

# 512

# 488

# MACHINE LEARNING

```
j: asc distinct xi;
info:[[yy;cbm;xi;rule;classes]
split: .qtrees.applyRule[cbm;bmi;xi;rule;j]
  .qtrees.infogain[x where y]]each split;
```

Choose optimal split for a node and the find that maximises information gain by iterating over all splits

```
-qtrees.growTree:[xy;treeinput]
// treeinput -- dictionary with splitting information
// xy -- dictionary of
// predictor (`x) set
// predicted (`y) vector
// distinct vector of k classification classes (`classes`
// number of predictor vectors to sample (`m
// maximum tree depth (`maxdepth
:[xy;r]
if[{1]=count distinct xy['y]where r`bitmap
  or xy['maxdepth]<=count r`rulepath;
  ];;
```
