# Regularization

+   Regularization:
- We have seen huge errors on the test set for too complex models
- **Problem**: Weights can get very large to fit the data exactly
- **Solution**: Limit the model (i.e. weights) such that it can not fit the training data perfectly any more

# Simple form of regularization: forcing the weights **w** to be small

+   - Small weights will lead to a smoother function
- Introduce “regularization term” in cost-function

```
$L = E_D(\mathbf{w}) + \lambda E_W(\mathbf{w})$
$Loss = Data term + Regularization term$
```

+   - where $\lambda$ is the regularization factor
- Needs to be tuned manually in most cases