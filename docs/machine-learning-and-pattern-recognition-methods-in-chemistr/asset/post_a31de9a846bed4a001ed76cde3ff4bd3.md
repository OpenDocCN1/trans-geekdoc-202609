
## 1.3.1 PLS for a single response (PLS-1)

The PLS-1 approach deals with the possibility of predicting a univariate response ($y$). Scores along the different components are then extracted to have maximum covariance with the response vector and forced to be orthogonal to one another:

```
$\argmax_{r_a} \mathbf{y}^T \mathbf{t}_{r_a} = \argmax_{r_a} \mathbf{y}^T \mathbf{X} \mathbf{r}_{r_a} \quad (2.22)$
```

where the weight vector $r_a$ is used to extract scores from the independent matrix ($t_a = \mathbf{X} \mathbf{r}_a$) and the subscript $a$ indicates that the condition is applied component-wise (i.e., the $a$th latent variable). The $X$-scores $(\mathbf{T} = [t_1 t_2 \dots t_a]$, being the number of components) are then used as predictors for the response through least-squares fitting:

```
$\hat{\mathbf{y}} = \mathbf{Tq} \quad (2.23)$
```

where the regression coefficients $q$ relating the X-scores to the Y are usually called $Y$-loadings, in analogy with the multivariate case. Similarly to what already highlighted for PCR, by exploiting the linear relation between the X-scores and the predictor matrix, it is possible to explicitly express the predicted response in terms of the original variable through linear projection, Eq. (2.19) can be rewritten in terms of the original variables:

```
$\hat{\mathbf{y}} = \mathbf{Tq} = \mathbf{XRq} = \mathbf{X b}_{PLS} \quad (2.24)$
```

where $\mathbf{b}_{PLS} = \mathbf{Rq}$, being the matrix connecting the weights for the calculation of the different components $(\mathbf{R} = [r_1 \ r_2 \dots r_a \dots r_A])$.

## 1.3.2 PLS for a multivariate response (PLS-2)

When the Y data are multivariate, the PLS algorithm is modified to account for the hypothesis that both blocks share the same latent structure, i.e., that they can be described by the same low-rank approximation, which, in turn, the $X$- and $Y$-scores lie in the same column subspace. Mathematically speaking, these assumptions can be translated to assuming the relevant variance in X can be summarized by the X-scores $(\mathbf{T} = [t_1 \ t_2 \dots t_a \dots])$ and that the systematic variation in Y can be approximated by the Y-scores $(\mathbf{U} = [u_1 \ u_2 \dots u_a \dots])$, with $\mathcal{A}$ being the number of extracted components:

```
$\mathbf{T} = \mathbf{XR} \quad (2.25)$
```

Multivariate predictive modeling and validation

```
$U = YQ \quad (2.26)$
```

where the X-weights have the same meaning as in Eq. (2.24), while $Q=[q_1 \quad q_2 \dots q_A]$ are the Y-loadings, which define the projection, leads to the Y-scores $U$. Component-wise, the X- and Y-scores are extracted to have maximum covariance with one another:

```
$$\argmax_{r_{Q,a}} \{u_d^T t_d\} = \argmax_{r_{Q,a}} \{q_d^T X r_a\} \quad (2.27)$$
```

Here, it is important to stress that, in PLS, the linear dependence between the Y- and the X-blocks is imposed at the so-called inner relationship, where it is assumed that the Y-scores can be linearly approximated (component-wise) by the X-scores:

```
$$\hat{u}_d = t_d \ c_{PLS} \quad (2.28)$$
```

with $c_{a, PLS}$ being the proportionality constant (which is estimated by univariate least squares) and the hat, indicating that the Y-scores are predicted from the X ones. In the matrix form, Eq. (2.28) can be rewritten as:

```
$$\hat{U} = T \ C_{PLS} \quad (2.29)$$
```

with $C_{PLS}$ being a diagonal matrix, whose elements are the various $c_{a,PLS}$. Predicted responses are then obtained from the estimated Y-scores by inverting the relation expressed by Eq. (2.26), i.e., through the Y-loadings:

```
$$\hat{Y} = \hat{U} Q^T \quad (2.30)$$
```

Also in the case of a multivariate Y, it is possible to express the overall regression model in terms of the original X variables, by properly combining the terms in Eqs. (2.25), (2.29), and (2.30):

```
$$\hat{Y} = \hat{U} Q^T = T \ C_{PLS} Q^T = XR \mathbf{X} B_{PLS}, \quad (2.31)$$
```

where the regression matrix relating the Y- and the X-block is given by:

```
$$\mathbf{B}_{PLS} = R \ C_{PLS} Q_T. \quad (2.32)$$
```

Since not all the information in the X-block is used for predicting the Y

## 1.4 Other techniques

Although for many problems the use of linear regression is sufficient, in these cases non-linear methods can be adopted. For instance, artificial neural networks (ANN) and support vector machines (SVM) are widely used. In the case of PCR, sometimes the non-linear relation between the Y- and the X-block is augmented as follows.

## 2. Classification

In chemometrics, “classifying” refers to the possibility of assigning samples to classes (or categories) based on the chemical data. The aims of classification are manifold; just to mention, in the context of quality control, classifiers can be applied to establish whether batches are compliant or not; otherwise, in forensic science, classification approaches are widely used to prevent adulteration.

A brief description of some of the most common classifiers is provided in the subpar below.

### 2.1 Linear discriminant analysis (LDA)

One of the first, but still widely used, discriminant linear analysis is proposed by Fisher (1936). LDA is a discriminant parametric approach seeking the linear hyperplanes which allow dividing the samples' space in an appropriate number of regions.
