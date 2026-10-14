near the boundary where the probability of being positive is close to ½. For multiclass problems, uncertainty sampling can query points that are least confident.

$x_{LC}^* = \arg\max_x 1 - P_\theta(\hat{y}|x)$  (7.24)

Here, $y \in \{1, ..., K\}$ is the class label with the highest posterior probability under the model $\theta$. The criterion for the least confident strategy only considers information about the most probable label. We can use max margin sampling to preserve information about the remaining label distribution.

$x_M^* = \arg\min_x P_\theta(\hat{y}_1|x) - P_\theta(\hat{y}_2|x)$  (7.25)

Here, $y_1$ and $y_2$ are the first and second most probable class labels under the model, respectively. Intuitively, instances with large margins are easy to classify. Thus, points with small margins are ambiguous, and knowing their labels would help the model to more effectively discriminate between them. However, for multiclass problems with very large label sets, the margin strategy still ignores much of the output distribution for the remaining classes. A more general uncertainty sampling strategy is based on entropy.

$x_H^* = \arg\max_x - \sum_i P_\theta(y_i|x) \log P_\theta(y_i|x)$  (7.26)

By learning labels that have the highest entropy, we can reduce label uncertainty. Uncertainty sampling also works for regression problems, in which case the learner queries the point with the highest output variance in its prediction.

# QUERY BY COMMITTEE

Another query selection framework is the query by committee (QBC) algorithm, which involves maintaining a committee $C = \{\theta^1, ..., \theta^C\}$ of models that are all trained on the current labeled set $L$ but represent competing hypotheses. Each committee member is then allowed to vote on the labels of query candidates, and the most informative query is considered an instance about which they most disagree. The objective of QBC is to minimize a set of hypotheses that are consistent with the current labeled training data $L$. Two main approaches have been proposed for measuring the level of disagreement: vote entropy and KL divergence. Vote entropy is defined as follows.

$x_{V_E}^* = \arg\max_x - \sum_i \frac{V(y_i)}{C} \log \frac{V(y_i)}{C}$  (7.27)

Here, $y_i \in \{1, ..., K\}$ is the class label, $V(y_i)$ is the number of votes a label received from the committee members, and $C$ is the size of the committee. Notice the similarity to equation 7.26. The KL divergence for QBC voting is defined as follows.