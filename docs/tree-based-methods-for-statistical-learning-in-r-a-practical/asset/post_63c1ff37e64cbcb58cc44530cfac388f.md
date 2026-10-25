
In other words, an RF is just a bagged tree ensemble with an additional layer of randomness produced by selecting a random subset of candidate splitters prior to partitioning the data at every node in every tree—extremely randomized trees (Section 7.8.4), take this randomization a step further in an attempt to reduce variance even more. Let \( m_{try} \le p \) be the number of candidate splitters selected at random from the entire set of \( p \) features prior to each split in each tree. Setting \( m_{try} << p \) can often dramatically improve performance compared to bagged decision trees; note that setting \( m_{try} = p \) will result in an ordinary bagged tree ensemble.

That's it. That's essentially the difference between an ordinary bagged tree ensemble and an RF.

The general steps for constructing a traditional RF are given in Algorithm 7.1 (compare this to Algorithm 5.1).

The recommended default values for \( m_{try} \) (the number of features randomly sampled before each split) and \( n_{min} \) (the minimum size of any terminal node) depend on the type of outcome:

- For classification, the typical defaults are \( m_{try} = \lfloor \sqrt{p} \rfloor \), where \( p \) is the number of features, and \( n_{min} = 1 \).
- For regression, the typical defaults are \( m_{try} = \lfloor p/3 \rfloor \) and \( n_{min} = 5 \).

These default values may vary slightly from one implementation to another. Note that \( \lfloor x \rfloor \) is just \( x \) rounded down to the nearest integer. As we'll see in Section 7.4, generalization performance is typically most sensitive to the value of \( m_{try} \), but the default is usually in the ballpark, and the tuning space for \( m_{try} \) is simple since \( m_{try} \in \{1, 2, \dots, p\} \), where \( p \) is the total number of available features.

Traditionally, CART was used for the base learners in an RF, but any decision tree algorithm will work (e.g., GUIDE or CTree); I'll use CTree in Section 7.2.3 to build an RF from scratch. Also, the traditional RF algorithm used the Gini splitting criterion (2.1) for classification and the SSE splitting criterion (2.6) for regression. However, many other splitting criteria can be used to great effect. For example, Ishwaran et al. [2008] proposed several splitting rules more appropriate for right-censored outcomes, including a log-rank splitting rule that splits nodes by maximization of the log-rank test statistic; see also Segal [1988], LeBlanc and Crowley [1992].

## 7.2.1 Voting and probability estimation

The voting scheme for classification outlined in step 4) of Algorithms 5.1 and 7.1 is called hard voting. In hard voting, each base learner casts a direct vote on the class label, and a majority vote (binary outcome) or plurality

## Algorithm 7.1 Traditional RF algorithm for classification and regression.

- 1) Start with a training sample, \( d_{trn} \), and specify integers, \( n_{min} \) (the minimum node size), \( B \) (the number of trees in the forest), and \( m_{try} \le p \) (the number of predictors to select at random as candidate splitters prior to splitting the data at each node in each tree).
- 2) For \( b \) in \( 1, 2, \dots, B \):
  - (a) Select a bootstrap sample \( d^*_{trn} \) of size \( N \) from the training data \( d_{trn} \).
  - (b) **Optional:** Keep track of which observations from the original training data were not selected to be in the bootstrap sample; these are called the out-of-bag (OOB) observations.
  - (c) Fit a decision tree \( \mathcal{T}_b \) to the bootstrap sample \( d^*_{trn} \) according to the following rules:
    - (i) Before each attempted split, select a random sample of \( m_{try} \) features to use as candidate splitters.
    - (ii) Continue recursively splitting each terminal node until the minimum node size \( n_{min} \) is reached.
- 3) Return the “forest” of trees \( \{\mathcal{T}_b\}_{b=1}^B \).
- 4) To obtain the RF prediction for a new case \( x \), pass the observation down each tree and aggregate as follows:
  - Classification: \( \hat{C}^{rf}_B(x) = vote \left\{ \hat{C}_b(x) \right\}_{b=1}^B \), where \( \hat{C}_b(x) \) is the predicted class label for \( x \) from the \( b \)-th tree in the forest (in other words, let each tree vote on the classification for \( x \) and take the majority/plurality vote).
  - Regression: \( \hat{f}^{rf}_B(x) = \frac{1}{B} \sum_{b=1}^B \hat{f}_b(x) \) (in other words, we just average the predictions for case \( x \) across all the trees in the forest).

vote (multiclass outcome) is used to determine the overall classification of an observation.

With categorical outcomes, however, we often care more about the predicted probability of class membership, as opposed to directly predicting a class label. In an RF (or a bagged tree ensemble) there are two ways to obtain predicted probabilities:

- 1) Take the proportion of votes for each class over the entire forest.
- 2) Average the class probabilities from each tree in the forest. (In this case, \(n_{min}\) should be considered a tuning parameter; see, for example, Malley et al. [2012].)

The first approach can be problematic. For example, suppose the probability that \(\boldsymbol{x}\) belongs to class \(j\) is \(\text{Pr}(Y=j|\boldsymbol{x})=0.91\). If each tree correctly predicts class \(j\) for \(\boldsymbol{x}\), then \(\widehat{\text{Pr}}(\boldsymbol{x})=1\), which is incorrect. If \(n_{min}=1\), the two approaches are equivalent and neither will produce consistent estimates of the true class probabilities (see, for example, Malley et al. [2012]). Which approach is better for probability estimation? Hastie et al. [2009, p. 283] argue that the second method tends to provide improved estimates of the class probabilities with lower variance, especially for small \(B\).

Malley et al. [2012] make a similar argument for the binary case, but from a different perspective. In particular, they suggest treating the 0/1 outcome as numeric and fitting a regression forest using the standard MSE splitting criterion (an example of a so-called *probability machine*). It seems strange to use MSE on a 0/1 outcome, right? Not really. Recall from Section 2.2.1 that the Gini index for binary outcomes is equivalent to using the MSE. Malley et al. recommend using a minimum node size equal to 10% of the number of training cases: \(n_{min} = \lfloor 0.1 \times N \rfloor\). However, for probability estimation, it seems natural to treat \(n_{min}\) as a tuning parameter. Devroye et al. [1997, Chap. 21–22] provide some guidance on the choice of \(n_{min}\) for consistent probability estimation in decision trees.

The predicted probabilities can be converted to class predictions (i.e., by comparing each probability to some threshold), which gives us an alternative to hard voting called *soft voting*. In soft voting, we classify \(\boldsymbol{x}\) to the class with the largest averaged class probability. This approach to classification in RFs tends to be more accurate since predicted probabilities closer to zero or one are given more weight during the averaging step; hence, soft voting attaches more weight to votes with higher confidence (or smaller standard errors; Section 7.7).

## 7.2.1.1 Example: Mease model simulation

To illustrate the difference between a classification and regression forest for probability estimation with binary outcomes, I'll expand upon one of the simulation studies in Malley et al. [2012], the Mease example, in particular [Mease et al., 2007]. This is a two-dimensional circle problem with a binary outcome (0/1) and two independent features. The features are independent \(\mathcal{U}(0, 50)\) random variables (i.e., the points are generated at random in the square \([0, 50]^2\)). The probability function is defined as

\( p(\boldsymbol{x}) = \text{Pr}(Y=1|\boldsymbol{x}) = \begin{cases} 1, & r(\boldsymbol{x}) < 8 \\ \frac{28-r(\boldsymbol{x})}{20}, & 8 \le r(\boldsymbol{x}) \le 20 \\ 0, & r(\boldsymbol{x}) \ge 28 \end{cases} \quad (7.1) \)

where \( r(\boldsymbol{x}) \) is the Euclidean distance from \( \boldsymbol{x}=(x_1, x_2) \) to the point \( (25, 25) \). A sample of \( N=1000 \) observations from the Mease model is displayed in Figure 7.3; note that the observed 0/1 outcomes were generated according to the above probability rule \( p(\boldsymbol{x}) \). (As always, the code to reproduce the simulation is available on the companion website.)

![](img/2c227bfb3620dc3d159fa5e6598afa30_251_0.png)

FIGURE 7.3: A sample of \( N=1000 \) observations from the Mease model.

Figures 7.4–7.5 display the results of the simulation. In Figure 7.4, the median predicted probability across all 250 simulations was computed and plotted vs. the true probability of class 1 membership; the dashed 45-degree line corresponds to perfect agreement. Here it is clear that the regression forest (i.e., treating the 0/1 outcome as continuous and building trees using the MSE splitting criterion) outperforms the classification forest (except when \( n_{min} = 1 \), in which case they are equivalent.) This is also evident from Figure 7.5, which shows the distribution of the MSE between the predicted class probabilities and the true probabilities for each case. In essence, for binary outcomes, regression forests produce consistent estimates of the true class probabilities.\(^a\) This goes to show that \( m_{try} \) isn’t the only important tuning parameter when

\(^a\)By consistent, I mean that \( \widehat{\text{Pr}}(Y=1|\boldsymbol{x}) \to \text{Pr}(Y=1|\boldsymbol{x}) \) as \( N \to \infty \).
