# Optimization of the Hyperparameters

+   - In GPs, the parameters $w$ can be integrated out in closed form
- Yet, no closed form solution exists for the hyper-parameters

Objective: Log-likelihood of the training data on the prior

$\beta^* = \arg \max_{\beta} \log \mathcal{N}(\boldsymbol{y}|\mathbf{0}, \boldsymbol{C}_\beta)$$
= \arg \max_{\beta} - \frac{1}{2} \log |\boldsymbol{C}_\beta| - \frac{1}{2} \boldsymbol{y}^T \boldsymbol{C}_\beta^{-1} \boldsymbol{y} - \frac{N}{2} \log(2\pi)$

+   - Need to be optimized via gradient descent (only batch)
- Non-convex, multiple optima
- Only a small number of hyper-parameters
- Very flexible representation, beware of overfitting (would be better to do that on validation set!)