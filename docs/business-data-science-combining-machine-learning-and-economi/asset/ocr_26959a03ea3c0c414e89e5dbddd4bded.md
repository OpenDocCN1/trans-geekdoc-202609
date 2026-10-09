![](bbox=[0.47, 0.24, 0.57, 0.31])

# # Classification

Many of the prediction questions that we face are classification questions. You might want to predict a website user's intent among several options, a speaker's political affiliation among a few parties, or the subject of an untagged image. These examples fit in our usual regression framework, where response $y$ is a function of inputs $x$. The difference is that $y$ now represents membership in a category: $y \in \{1, 2, \dots, m\}$. The prediction question is, given a new $x$, what is our best guess at the response category, $\hat{y}$?

# ## NEAREST NEIGHBORS

We have already worked with two-category classification via logistic regression, where $y \in \{0, 1\}$ and p(y = 1 | x) is modeled with a logit link. This binary logistic regression is a special case of general multinomial logistic regression for more than two classes. We'll return to that modeling approach later in this chapter, but first we cover a simple and intuitive classifier: the nearest neighbor algorithm.

The K nearest neighbor (K-NN) algorithm predicts class $\hat{y}$ for $x$ by asking, “What is the most common class for observations around $x$?” Figure 4.1 illustrates the K-NN routine in Algorithm 11. The black point is $x_f$, where we'd like to predict the class label. For a K = 3 routine, the dashed lines indicate the nearest neighbors: two white and one dark gray. The modal neighbor is thus white and the 3-NN prediction is $\hat{y}_f = \text{white}$. The neighbors