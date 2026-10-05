# Protease Cleavage Pattern Discovery

to a problem. In other words, LDA requires to search for such a weight vector w so that the values of X^t w follow a density in which the bimodality is maximised. Suppose X = X_A \cup X_B, where A and B stand for two classes, for instance a class of non-cleaved peptides and a class of cleaved peptides. Thus a space can be decomposed using the following notation,

```
X^t w = X_A^t \cup X_B^t = \hat{Y}_A \cup \hat{Y}_B
```

Both \hat{Y}_A and \hat{Y}_B will form two densities. It is expected that a mixture density of \hat{Y}_A and \hat{Y}_B should be bimodal meaning that the density of \hat{Y}_A and \hat{Y}_B are well separated from each other so as to discriminate between two classes of data points, i.e., the peptides in the context or protease cleavage discovery. This requires the bimodality of the mixture density of \hat{Y}_A and \hat{Y}_B to be maximised. In other words, a discriminant analysis needs to maximise the distance between two densities of \hat{Y}_A and \hat{Y}_B and to minimise the overlap between two densities of \hat{Y}_A and \hat{Y}_B to generate an optimal LDA model. Unless these two conditions are well-satisfied, a LDA model will not work.

A linear discriminant analysis model is in the format shown in the Equation (3.2). The values of \hat{y}_n are called the projected data or the projections onto the projection direction, which are continuous values. A LDA model is a parametric model because the projection direction is parameter by w_1, w_2, \cdots w_d.

# 3.2.2 The projection direction optimisation

Because the values of \hat{y}_n are determined by w, the density of \hat{y}_n will vary if w varies. Figure 3.1 shows a classification problem, where the classifier is defined by \hat{y}_n = w_0 + w_1x_1 + w_2x_2. There are two scenarios (hence two models) of this classifier in this case, where the model parameters w takes different values in two panels, two different models. The inset densities show two different density patterns of the projections \hat{y}. The inset histogram density of \hat{y} shown in Figure 3.1(a) is bimodal. However, the inset histogram density of \hat{y} shown in Figure 3.1(b) is unimodal. If two panels (two models) of Figure 3.1 are compared, it can be seen that the key to have a bimodal distribution of projections is to optimise the projection