## 7.5 Further reading

The general bagging idea was initially proposed by Breiman (1996), whereas the more specific random forest algorithm dates back to Ho (1995) who essentially proposed to limit the set of possible splitting variables for each tree. The idea to also use a bootstrapped data set (that is, bagging) is due to Breiman (2001).

Boosting was popularized by the introduction of AdaBoost by Freund and Schapire (1996), who were also awarded the prestigious Gödel Prize in 2003 for their algorithm. Real AdaBoost was proposed by Friedman et al. (2000), and gradient boosting by Friedman (2001) and Mason et al. (1999). Efficient and widely used implementations of gradient boosting include the XGBoost package by T. Chen and Guestrin (2016) and LightGBM by Ke et al. (2017).

## 8 Nonlinear input transformations and kernels

In this chapter we will continue to develop the idea from Chapter 3 of creating new input features by using nonlinear transformations $\phi(x)$. It turns out that the so-called kernel trick, we can have infinitely many such transformations and we can extend our basic methods, such as linear regression and k-NN, into more versatile and flexible ones. When we also change the loss function of linear regression, we obtain support regression, and its classification counterpart support vector classification, two powerful off-the-shelf machine learning methods. The concept of kernels is important to the next chapter (9), where a Bayesian perspective of linear regression and kernels leads to the Gaussian process.

### 8.1 Creating features by nonlinear input transformations

The reason for the word “linear” in the name “linear regression” is that the output is modelled as a *linear* combination of the inputs. We have not made clear definition of what an input is. Recall the stopping distance problem in Example 2.2. If the speed is as in that example, then could not also the kinetic energy—the square of the speed—be considered as another input? The answer is yes, we can in fact make use of arbitrary nonlinear transformations of the “original” input in any model, including linear regression. For example, if we have a one-dimensional input $x$, the vanilla regression model (3.2) is:

$$y = \theta_0 + \theta_1x + \varepsilon. \quad (8.1)$$

Starting from this we can create the model with $x^2, x^3, \dots, x^{d-1}$ as inputs ($d$ is a user-choice), and thus we obtain a linear regression model which is a polynomial in:

$$y = \theta_0 + \theta_1x + \theta_2x^2 + \dots + \theta_{d-1}x^{d-1} + \varepsilon = \theta^T\phi(x) + \varepsilon. \quad (8.2)$$

Since $x$ is known, we can directly compute $x^2, \dots, x^{d-1}$. Note that this is a linear regression model where the *parameters* $\theta$ appear in a linear fashion with $\phi(x) = [1 x x^2 \dots]$ as a new input. We refer to a transformation of $x$ as a *feature* and the vector of transformed inputs $\phi(x)$, a vector of dimension $d \times 1$, as a *feature*. The parameters $\theta$ are still learned in the same way, but we replace the original $X$ with the transformed $\Phi(X) = ( \Phi(x_1)^T, \Phi(x_2)^T, \vdots, \Phi(x_n)^T)^T_{n \times d} \quad (8.3)$

For linear regression, this means that we can learn the parameters by making the substitution (3.8) in the normal equations (3.13). The idea of nonlinear input transformations is not unique to linear regression, and any choice of nonlinear transformation $\phi(x)$ can be used with any supervised machine learning method. The nonlinear transformation is first applied to the input, like a pre-processing step, and the transformed input is used when training, evaluating and using the model. We illustrated this for regression already in Example 3.5 in Chapter 3, and for classification in Example 8.1.

> The original input is sometimes referred to as a feature.

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_157_0.png)

(a) A regression model with a 2nd order polynomial, trained with squared error. The line is no longer straight (as in Figure 3.1), but is merely an artifact of the plot: in a three-dimensional plot with each feature (here, x and x²) a separate axis, it will be an affine model.

(b) A regression model with a 4th order polynomial, trained with squared error. Note that a 4th order polynomial implies 5 unknown parameters, roughly means that we can expect the learned model to fit 5 points exactly, a typical case of overfitting.

Figure 8.1: A linear regression model with 2nd and 4th order polynomials in the input x, as in (8.2).

> Time to reflect 8.1: 8.1 shows an example of two linear regression models with transformed (polynomial) inputs. When studying one may ask how a linear regression model can result in a curved line? Are linear regression models not restricted to linear (affine) straight lines?

#### Example 8.1: Nonlinear transformations for classification

Consider the data for a binary classification problem in the left panel of Figure 8.2 with $x = [x_1, x_2]$ with a blue and a red class. By only looking at the data, we can conclude that a linear classifier would not be able to perform well on this problem.

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_157_1.png)

By adding the nonlinear transformation $x_1x_2$ as a feature, such as $\phi(x) = [x_1, x_2, x_1x_2]$, we get the situation in the right panel of Figure 8.2. With this relatively simple introduction of an extra feature, the problem appears to be much better suited for a linear classifier, since the data can be separated relatively well. The conclusion here is that for increasing the capacity of simple methods is to introduce nonlinear transformations. Polynomials are only one of (infinitely) many possible choices of features $\phi(x)$. One should take care when using polynomials higher than second order because of their behavior outside the range where the data is often useful (recall Figure 8.1). However, there are several alternatives that are more practical, such as Fourier series corresponding to $\phi(x) = [\sin(x), \cos(x), \sin(2x), \dots]$, step functions, and the use of input transformations makes simple models more flexible and applicable to (Machine Learning - A First Course for Engineers and Scientists, Andreas Lindholm, Niklas Wahlström, Fredrik Lindhson, and Thomas B. Schön 2021).

## 8.2 Kernel ridge regression

In real-world problems in order to obtain good performance, it is important to choose $\Phi(x)$ such that enough flexibility is obtained but overfitting avoided. With a very careful choice of $\Phi(x)$ good performance can be obtained but that choice is problem-specific and requires some craftsmanship. Let us instead explore the conceptual idea of letting the number of features $d \to \infty$, and combine it with regression in a sense this will automate the choice of features and leads to a family of powerful tools called kernel methods.

### Reforming linear regression

First of all we have to use some kind of regression if we are going to increase $d$ in linear regression to avoid overfitting when $d > n$. For reasons we will discuss later how to use $L^2$-regularization, the equation for $L^2$-regularized regression is:

$$\hat{\theta} = \arg \min_{\theta} \frac{1}{2} \sum_{n=1}^{n} (\theta^T \Phi(x_n) - y_n)^2 + \lambda ||\theta||^2 = (\Phi(x)^T \Phi(x) + n\lambda I)^{-1} \Phi(x)^T \mathbf{y}$$

We have not fixed the nonlinear transformations $\Phi(x)$ to anything specific but we are preparing for choosing $d > n$ of these transformations. The downside of choosing $d$, the dimension of $\Phi(x)$, is large that we also have to learn parameters when training. In linear regression, we will firstly learn and store the $d$-dimensional vector $\theta$, and thereafter we use it for computing a prediction:

$$\hat{y}(x_*) = \theta^T \Phi(x_*)$$

To be able to choose $d$ really large, eventually even $d \to \infty$, we have to reformulate the model without that there are computations or storage that deals with $d$. The first step is to realize that the prediction $\hat{y}$ can be written as:

$$\hat{y}(x_*) = (\Phi(x)^T \Phi(x) + n\lambda I)^{-1} \Phi(x)^T \mathbf{y})^T \Phi(x_*)$$
$$\underbrace{\hat{y}(x_*)}_{1\times1} = \underbrace{\theta}_{d\times1}\underbrace{(\Phi(x)^T \Phi(x) + n\lambda I)^{-1}}_{d\times d}\underbrace{\Phi(x_*)}_{1\times d}$$

With the underbraces provides the sizes of the corresponding vectors and matrices. This expression for $\hat{y}(x_*)$ means we could, for each test input $x_*$, compute the $n$-dimension vector $(\Phi(x)^T \Phi(x) + n\lambda I)^{-1}\theta$.
