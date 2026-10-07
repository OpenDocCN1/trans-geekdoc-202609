![](bbox=[0.14754, 0.09345, 0.85246, 0.29655000000000004])

Figure 4-24. Linear decision boundary

Just like the linear model, Logistic Regression models can be regularized using $\ell_1$ or $\ell_2$ penalties. Scikit-Learn actually adds an $\ell_2$ penalty by default.

> The hyperparameter controlling the regularization strength of a Scikit-Learn LogisticRegression model is not $\alpha$ (as in other models), but its inverse: C. The higher the value of C, the less the model is regularized.

# # Softmax Regression

The Logistic Regression model can be generalized to support multiple classes directly, without having to train and combine multiple binary classifiers (as discussed in Chapter 3). This is called *Softmax Regression*, or Multinomial Logistic Regression.

The idea is quite simple: when an instance $\mathbf{x}$, the Softmax Regression model first computes $s_k(\mathbf{x})$ for each class $k$, then estimates the probability of each class by applying the *softmax function* (also called the *normalized exponential*) to the scores. The equation to compute $s_k(\mathbf{x})$ should look familiar, as it is just like the equation for Linear Regression prediction (see Equation 4-19).

```
Equation 4-19. Softmax score for class k
$s_k(\mathbf{x}) = \mathbf{x}^T\mathbf{	heta}^{(k)} $
```

That each class has its own dedicated parameter vector $\mathbf{	heta}^{(k)}$. All these vectors are typically stored as rows in a *parameter matrix* $\mathbf{\Theta}$.
Once you have computed the score of every class for the instance $\mathbf{x}$, you can estimate the probability $\hat{p}_k$ that the instance belongs to class $k$ by running the scores through the softmax function (Equation 4-20): it computes the exponential of score,

Logistic Regression | 149

WOWOW!eBook
www.wowebook.org