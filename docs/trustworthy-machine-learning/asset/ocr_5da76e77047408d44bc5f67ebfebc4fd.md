![](bbox=[0.1, 0.08, 0.52, 0.45])

Figure 7.5. Illustration of the structural risk minimization principle. Accessible caption. A plot with p_E or R_emp on the vertical axis and increasing complexity of hypothesis spaces on the horizontal axis. The empirical risk decreases all the way to zero with increasing complexity. The generalization error first decreases and then increases. It has a sweet spot in the middle.

The hypothesis space F is the inductive bias of the classifier. Thus, within the paradigm of the structural risk minimization principle, different choices of hypothesis spaces yield different domains of competence. In the next section, you and your team of JCN data scientists analyze several different risk minimization classifiers popularly used in practice, including decision trees and forests, margin-based classifiers (logistic regression, support vector machines, etc.), and neural networks.

# 7.5 Risk Minimization Algorithms

You are now analyzing the competence of some of the most popular classifiers used today that fit into the risk minimization paradigm. The basic problem is to find the function f within the hypothesis space F that minimizes the average loss function L(y_i, f(x_i)):

```
\hat{f}(\cdot) = \arg\min_{f \in \mathcal{F}} \frac{1}{n} \sum_{i=1}^{n} L(y_i, f(x_i)).
```

Equation 7.3

This equation may look familiar because it is similar to the Bayesian detection problem in Chapter 6. The function in the hypothesis space that minimizes the sum of the losses on the training data is \hat{f}. Different methods have different hypothesis spaces \mathcal{F} and different loss functions L(\cdot,\cdot). An alternative way to control the complexity of the classifier is not through changing the hypothesis space \mathcal{F}, but through a complexity penalty or regularization term J(\cdot) weighted by a regularization parameter \lambda:

```
\hat{f}(\cdot) = \arg\min_{f \in \mathcal{F}} \frac{1}{n} \sum_{i=1}^{n} L(y_i, f(x_i)) + \lambda J(f).
```

Equation 7.4