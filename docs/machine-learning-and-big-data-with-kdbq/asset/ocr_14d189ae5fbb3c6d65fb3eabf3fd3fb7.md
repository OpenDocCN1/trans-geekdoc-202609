# AdaBoost with Stumps

# 23.3 ADABOOST

We now introduce the discrete version of the AdaBoost algorithm. Let us consider a case where we have a binary variable $y$ taking values -1 and 1 and a set of features $x_0, x_1, \dots, x_n$. The range of $y$ is chosen for convenience, and any binary variable can be easily recast into this form. Concerning representing features, we require them to be of any ordinal type, i.e. such that we can order them and apply the inequality operation. Thus, aside from obvious candidates of floats, integers, and various date and time types – which are either floats or integers under the surface – we also allow for strings and characters.

The ultimate aim of the model we want to develop is to find the relationship between $x$ and $y$ that we can write:

$y = G(x_1, x_2, \dots, x_N),$

Let us function $G$ models the relationship between the features and the dependent. Let us assume that we are equipped with weak classifiers $g(x_i; \xi_i)$; where $i$ indexes the weak classifier, $\xi_i$ is the corresponding parameter set (in the case of stumps the threshold), and $x_i$ is the feature chosen for the given classifier.

Let us define the loss for a general single-valued classifier $g$ at sample $j$

$E(g(x_j), y_j) = \exp(-y_j g(x_j)).$

where the loss function distinguishes the sign and the numerical value itself, and $j$ indexes observation points with $j=1, \dots, M$. We do not need to restrict ourselves to any numerical values for the model. In the case of regression, the loss function would be the square of the differences, the one used with a least squares model is the product of error at each stage. Thus, AdaBoost aims to minimise the error of the additive model by using the exponential function which simplifies the additive exponential loss function by iterative updates of the model. It brings a computational advantage for additive modelling as the model is consecutively re-weighted as estimation progresses. It is also noted that AdaBoost with an exponential loss function is equivalent to stagewise additive modelling.

AdaBoost is defined as follows:

+   - Initialise every observation weight $w_j = 1/M$, with $j=1, \dots, M$.
- Initialise the model $G_0 \equiv 0$.
- For $l=1, \dots, L_{AdB}$:
- Fit classifier $g_l(x_i; \xi_l)$ to the data that minimizes sum of errors for misclassified observations:

$err_i = \sum_{j=1}^M w_j g_l(x_{ij}; \xi_l) \neq y_j$.