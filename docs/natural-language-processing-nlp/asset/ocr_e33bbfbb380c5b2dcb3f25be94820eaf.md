# 2.5.2 Gradients

Logistic loss is minimized by optimization along the gradient. Specific algorithms are described in the next section, but first let's compute the gradient with respect to the logistic loss of a single example:

$\ell_{\text{LOGREG}} = -\boldsymbol{\theta}\cdot\boldsymbol{f}(\boldsymbol{x}^{(i)}, y^{(i)}) + \log\sum_{y'\in\mathcal{Y}} \exp\left(\boldsymbol{\theta}\cdot\boldsymbol{f}(\boldsymbol{x}^{(i)}, y')\right)$ [2.61]
$\frac{\partial\ell}{\partial\boldsymbol{\theta}} = -\boldsymbol{f}(\boldsymbol{x}^{(i)}, y^{(i)}) + \frac{1}{\sum_{y''\in\mathcal{Y}} \exp\left(\boldsymbol{\theta}\cdot\boldsymbol{f}(\boldsymbol{x}^{(i)}, y'')\right)} \times \sum_{y'\in\mathcal{Y}} \exp\left(\boldsymbol{\theta}\cdot\boldsymbol{f}(\boldsymbol{x}^{(i)}, y')\right) \times \boldsymbol{f}(\boldsymbol{x}^{(i)}, y')$ [2.62]
$= -\boldsymbol{f}(\boldsymbol{x}^{(i)}, y^{(i)}) + \sum_{y'\in\mathcal{Y}} \frac{\exp\left(\boldsymbol{\theta}\cdot\boldsymbol{f}(\boldsymbol{x}^{(i)}, y')\right)}{\sum_{y''\in\mathcal{Y}} \exp\left(\boldsymbol{\theta}\cdot\boldsymbol{f}(\boldsymbol{x}^{(i)}, y'')\right)} \times \boldsymbol{f}(\boldsymbol{x}^{(i)}, y')$ [2.63]
$= -\boldsymbol{f}(\boldsymbol{x}^{(i)}, y^{(i)}) + \sum_{y'\in\mathcal{Y}} \mathrm{p}(y'\mid\boldsymbol{x}^{(i)},\boldsymbol{\theta}) \times \boldsymbol{f}(\boldsymbol{x}^{(i)}, y')$ [2.64]
$= -\boldsymbol{f}(\boldsymbol{x}^{(i)}, y^{(i)}) + E_{Y\mid X}[\boldsymbol{f}(\boldsymbol{x}^{(i)}, y)]$ [2.65]

The final step employs the definition of a conditional expectation (§ A.5). The gradient of the logistic loss is equal to the difference between the expected counts under the current model, $E_{Y|X}[f(x^{(i)}, y)]$, and the observed feature counts $f(x^{(i)}, y^{(i)})$. When these two vectors are equal for a single instance, there is nothing more to learn from it; when they are equal in sum over the entire dataset, there is nothing more to learn from the dataset as a whole. The gradient of the hinge loss is nearly identical, but it involves the features of the predicted label under the current model, $f(x^{(i)}, \hat{y})$, rather than the expected features $E_{Y|X}[f(x^{(i)}, y)]$ under the conditional distribution $p(y \mid x; \theta)$.

The regularizer contributes $\lambda\theta$ to the overall gradient:

$L_{\text{LOGREG}} = \frac{\lambda}{2}||\theta||_2^2 - \sum_{i=1}^{N} \left( \theta\cdot f(x^{(i)}, y^{(i)}) - \log \sum_{y'\in\mathcal{Y}} \exp \theta\cdot f(x^{(i)}, y') \right)$ [2.66]
$\nabla_\theta L_{\text{LOGREG}} = \lambda\theta - \sum_{i=1}^{N} \left( f(x^{(i)}, y^{(i)}) - E_{y|x}[f(x^{(i)}, y)] \right)$ [2.67]

# 2.6 Optimization

Each of the classification algorithms in this chapter can be viewed as an optimization problem:

+   - In Naïve Bayes, the objective is the joint likelihood $\log p(x^{(1:N)}, y^{(1:N)})$. Maximum likelihood estimation yields a closed-form solution for $\theta$.