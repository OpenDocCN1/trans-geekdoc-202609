More informally: The Hessian matrix records how curved the loss is at a certain point. The Hessian is a matrix and not just a vector, because it describes the curvature of the loss and the curvature depends on which we look. The actual calculation of the Hessian matrix is time-consuming if we have many parameters. Koh and Liang suggested some tricks to calculate it efficiently, which goes beyond the scope of this chapter. Updating the model parameters, as described by the above formula, is equivalent to taking a single Newton step after forming a quadratic expansion around the estimated model parameters.

What intuition is behind this influence function formula? The formula comes from quadratic expansion around the parameters $	heta$. That means we do not actually know, or it is too complex to calculate how much the loss of $z$ will change when it is removed/unweighted. We approximate the function locally using information about the steepness (= gradient) and the curvature (= Hessian matrix) at the current model parameter setting. With this approximation, we can calculate the new parameters approximately look like if we upweighted instance $z$:

```
$\hat{\theta}_z \approx \theta - \frac{1}{n}I_{up,params}(z)$
```

The approximate parameter vector is basically the original parameter minus the gradient of the loss of $z$ (because we want not to decrease the loss) scaled by the curvature (= multiplied by the inverse Hessian matrix) and scaled by 1 over $n$, because that is the weight of a single training instance.

The following figure shows how the upweight works. The x-axis shows the value of the $\theta$ parameter and the y-axis the corresponding value of the loss with upweighted instance $z$. The model parameter here is 1-dimensional for demonstration purposes, but in reality it is usually high-dimensional. We move only 1 over n into the direction of improvement of the loss for instance $z$. We do not know how the loss would really change when we delete $z$, but with the first and second derivative of the loss, we create this quadratic approximation around our current model parameter and pretend that this is how the real loss would behave.

We do not actually need to calculate the new parameters, but we can use the influence function as a measure of the influence of $z$ on the parameters.

How do the $predictions$ change when we upweight training instance $z$? We can calculate the new parameters and then make predictions using the newly parameterized model, or we can also calculate the influence of $z$ on the predictions directly, since we can calculate the influence by using the chain rule: