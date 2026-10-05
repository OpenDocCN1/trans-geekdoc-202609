
# Protease Cleavage Pattern Discovery

to a problem. In other words, LDA requires to search for such a weight vector $w$ so that the values of $X^t w$ follow a density in which the bimodality is maximised. Suppose $X = X_A \cup X_B$, where $A$ and $B$ stand for two classes, for instance a class of non-cleaved peptides and a class of cleaved peptides. Thus a space can be decomposed using the following notation,

```
X^t w = X_A^t \cup X_B^t = \hat{Y}_A \cup \hat{Y}_B
```

Both $\hat{Y}_A$ and $\hat{Y}_B$ will form two densities. It is expected that a mixture density of $\hat{Y}_A$ and $\hat{Y}_B$ should be bimodal meaning that the density of $\hat{Y}_A$ and $\hat{Y}_B$ are well separated from each other so as to discriminate between two classes of data points, i.e., the peptides in the context of protease cleavage discovery. This requires the bimodality of the mixture density of $\hat{Y}_A$ and $\hat{Y}_B$ to be maximised. In other words, a discriminant analysis needs to maximise the distance between two densities of $\hat{Y}_A$ and $\hat{Y}_B$ and to minimise the overlap between two densities of $\hat{Y}_A$ and $\hat{Y}_B$ to generate an optimal LDA model. Unless these two conditions are well-satisfied, a LDA model will not work.

A linear discriminant analysis model is in the format shown in the Equation (3.2). The values of $\hat{y}_n$ are called the projected data or the projections onto the projection direction, which are continuous values. A LDA model is a parametric model because the projection direction is parameterized by $w_1, w_2, \dots w_d$.

## 3.2.2 The projection direction optimisation

Because the values of $\hat{y}_n$ are determined by $w$, the density of $\hat{y}_n$ will vary if $w$ varies. Figure 3.1 shows a classification problem, where the classifier is defined by $\hat{y}_n = w_0 + w_1x_1 + w_2x_2$. There are two scenarios (hence two models) of this classifier in this case, where the model parameters $w$ takes different values in two panels, two different models. The inset densities show two different density patterns of the projections $\hat{y}$. The inset histogram density of $\hat{y}$ shown in Figure 3.1(a) is bimodal. However, the inset histogram density of $\hat{y}$ shown in Figure 3.1(b) is unimodal. If two panels (two models) of Figure 3.1 are compared, it can be seen that the key to have a bimodal distribution of projections is to optimize the projection direction or the model parameters **w**. It is this vector that determines whether the density of the projections can be bimodal or not. Thus goes to the most basic question, which is how to find the optimal model parameters **w** for constructing a LDA model for a data set. The purpose is to deliver a bimodal density of the projections and ultimately an optimal LDA model with a good discrimination power between two classes of data points, i.e., peptides.

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_96_0.png)

**Fig. 3.1.** An illustration of how the weights (model parameters) determine the bimodality of a projection density. The triangles and the crosses represent two classes of this data set. The dotted line in each panel stands for the classification boundary corresponding to the projection direction **w**. The insert plot in each panel stands for the density of the projections based on a projection direction **w**. (a) A good projection direction leads to a bimodal density of projections. (b) a poor projection direction leads to a unimodal density of projections.

Therefore, to estimate model parameters as $w_1$ and $w_2$, the bimodality of the projection density given a vector of model parameters **w** must be maximised. Unless the bimodality of the projection density has been maximised, a LDA model won't be considered a useful classifier. For instance, the classifier in Figure 3.1(b) will not be considered a proper candidate and will not be selected because the classifier will deliver a greater error when it is used to classify data points, such as peptides. On the other hand, the classifier in Figure 3.1(a) has a better discrimination power due to an obvious bimodality of the projection density. It is believed that this classifier will separate two classes of data points, such as peptides, with a good discrimination power.

The basic principle of LDA is thus to discover the best projection direction **(w)** among all possible projection direction candidates. The judgement whether a projection direction is optimal is based on the evidence by which the separation between two densities ($\hat{Y}_A$ and $\hat{Y}_B$) can be maximised or the density bimodality is maximised.

Suppose the projection direction (**w**) has been maximised as well as the bimodality of the projection direction has been maximised. The next issue is to classify data points or discriminate between two classes of data points (objects). An example is shown in Figure 3.2, where the estimated projection direction shown as the dotted line is supposed to have been optimised. Looking at the distribution of the data points separated by the projection direction, it is sure that the projection direction is perhaps an optimal one. Using this optimised projection direction, all data points of two classes have been mapped to the projection direction resulting in projections ($\hat{y}$). A density of the projections is constructed. The top-left inset of Figure 3.2 shows this density. Its bimodality looks good.

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_97_0.png)

Fig. 3.2. The illustration of examining whether data points are mapped to the right locations of the projection direction using LDA. The triangles and the crosses for two classes of data points. Three validation points are denoted by three letters ($A, B$ and $C$). The dotted line stands for the optimised projection direction as the classification boundary. The inset at the bottom-left corner stands for the density estimated for the projections based on the projection direction using the histogram approach. The inset at the top-left panel shows how three validation points are mapped in their correct positions in the density function. The inset at the bottom-right panel shows the posterior probability curves generated using the Bayes rule, where three validation points are also mapped. The solid line is the posterior probability curve for the class of the triangles. The dotted line is the posterior probability curve for the class of the crosses. The Bayes rule will be introduced in this chapter.

To show what the discrimination power is between two classes of data points, three validation points labelled by $A$, $B$, and $C$ were inserted into this data space. They belonged to two classes. When mapping all data points to the projection direction, these three validation points were mapped onto the projection direction as well. Therefore, they should show their proper positions in the density function. The top-left inset of Figure 3.2 shows three validation points. It can be seen that the validation points $A$ and $C$ were mapped to the right cluster of the density and the validation point $B$ was mapped to the left cluster of the density. They were correct indeed. Incorporating with the priors, the density function (likelihood) was converted to the posterior probability using the Bayes rule. The Bayes rule will be introduced below in this chapter. The bottom-right inset in Figure 3.2 shows the curves of the posterior probabilities, in which three data points stayed well at the proper positions they should go. For instance, the validation points $A$ and $C$ stayed on the right side of the crossover point while the validation point $B$ stayed on the left side of the crossover point. The bottom-left inset shows a good bimodal density of projections.

## 3.2.3 The formulation of LDA

Suppose the mean vectors of two Gaussian distributions are denoted by $\mathbf{u}_1$ and $\mathbf{u}_2$. A mapping vector of a projection direction is denoted by $\mathbf{w}$. The following formula is used to denote the mapping centres $(	au_1$ and $	au_2)$ of two clusters of a data set in the mapping space (the $\hat{\mathbf{y}}$ space),

```
$$\tau_1 = \mathbf{w}^t\mathbf{u}_1$$
$$\tau_2 = \mathbf{w}^t\mathbf{u}_2$$ (3.5)
```

It must be noted that $	au_1 \in \mathcal{R}$ and $	au_2 \in \mathcal{R}$ are two of many mapping points in the mapping space. These two mapping centres $(	au_1$ and $	au_2)$ should stay in the centres of two mapping clusters. The distance between two mapped centres in the $\hat{\mathbf{y}}$ space is defined as,

```
$S_B = \tau_2 - \tau_1 = \mathbf{w}^t\mathbf{u}_2 - \mathbf{w}^t\mathbf{u}_1$$ (3.6)
```

The above equation defines the relationship between two sets of centres (the multi-dimensional centres $\mathbf{u}_1$ and $\mathbf{u}_2$ as well as the projection centres in the mapping space $	au_1$ and $	au_2$).
