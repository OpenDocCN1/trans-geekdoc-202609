
## 5 Learning parametric models

It turns out that repeated "sweeps" through the vector $\theta$ and updating one parameter at a time according to (5.28) is a good way to solve (5.26). This type of algorithm, where we update one parameter at a time, is referred to as *coordinate descent*, and we illustrate it in Example 5.4.

It can be shown that the cost function in (5.26) is convex. Only convexity is not sufficient to guarantee that coordinate descent will find its (global) minimum, but for $L^1$-regularized cost function (5.26) we can show that coordinate descent actually finds the (global) minimum. In practice we know that we have found the global minimum when no parameters have changed after such a full "sweep" of the parameter vector.

It turns out that coordinate descent is a very efficient method for $L^1$-regularized linear regression (5.26), and many updates will simply set $\theta_j=0$ due to the sparsity of $\theta$. This makes the algorithm fast. For most machine learning problems it can, however, not said that coordinate descent is the preferred method. We will now have to look at some more general families of optimization methods that are used widely in machine learning.

## Example 5.4: Coordinate descent

We apply coordinate descent to the objective functions from Example 5.3 and show the result in Figure 5.6. For coordinate descent to be an effective alternative, closed-form solutions for updating one parameter at a time, similar to (5.28), have to be available.

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_97_0.png)

Figure 5.6 shows how the parameters are updated in the coordinate descent algorithm, for two initial parameter vectors (blue and green trajectory, respectively). It is clear from the figure that only one parameter is updated each time, which gives the trajectory a characteristic shape. The obtained minimum is marked with a yellow dot. Note how the different initializations lead to different (local) minima in the non-convex case (right panel).

## Gradient descent

In many situations we cannot use closed-form formulations, but we do have access to the value of the objective function as well as its derivative (rather, the gradient). Sometimes we even have access to the second derivative (rather, the Hessian). In those situations, it is often a good idea to use a *gradient descent method*, which we will introduce now, or *Newton's method* that we will discuss later.

Gradient descent can be used for learning parameters $\theta$ of high dimension when the objective function $j(\theta)$ is such that it is possible to compute. Let us therefore consider the parameter learning problem

```
$$\hat{\theta} = \arg\min j(\theta) \quad (5.29)$$
```

(even though gradient descent can be used for parameters as well). We assume that

> This assumption is primarily mainly for the theoretical discussion. In practice, there are successful examples of gradient descent being applied to functions not differentiable everywhere, such as neural networks with ReLU activation functions (Chapter 6).

## 5.4 Parameter optimization

the gradient of the cost function $\nabla_\theta J(\theta)$ exists for all $\theta$. As an example, the gradient of the cost function for logistic regression (3.34) is

```
$$\nabla_\theta J(\theta) = -\frac{1}{n}\sum_{i=1}^n \frac{1}{1+e^{\theta^T x_i}}x_i. \quad (5.30)$$
```

Note $\nabla_\theta J(\theta)$ is a vector of the same dimension as $\theta$, which describes the direction in which $J(\theta)$ increases. Conversely, and more useful for us, $-\nabla_\theta J(\theta)$ describes the direction in which $J(\theta)$ decreases. That is, if we take a small step in the direction of the negative gradient, this will reduce the value of the cost function,

```
$J(\theta - \gamma\nabla_\theta J(\theta)) \le J(\theta) \quad (5.31)$
```

for some (possibly very small) $\gamma > 0$. If $J(\theta)$ is convex, the inequality in (5.31) is strict except at the minimum (where $\nabla_\theta J(\theta)$ is zero). This suggests that if we have $\theta^{(i)}$ and want to select $\theta^{(i+1)}$ such that $J(\theta^{(i+1)}) \le J(\theta^{(i)})$, we should

```
$update \theta^{(i+1)} = \theta^{(i)} - \gamma\nabla_\theta J(\theta^{(i)}) \quad (5.32)$
```

with some positive $\gamma > 0$. Repeating (5.32) gives the gradient descent Algorithm 5.1.

**Algorithm 5.1:** Gradient descent
**Input:** Objective function $J(\theta)$, initial $\theta^{(0)}$, learning rate $\gamma$
**Result:** $\hat{\theta}$
1 Set $\theta \leftarrow 0$
2 **while** $|\theta^{(t)} - \theta^{(t-1)}\|$ not small enough **do**
3 $\quad$ Update $\theta^{(t+1)} \leftarrow \theta^{(t)} - \gamma\nabla_\theta J(\theta^{(t)})$
4 $\quad$ Update $t \leftarrow t + 1$
5 **end**
6 **return** $\hat{\theta} \leftarrow \theta^{(t-1)}$

## 5 Learning parametric models

![](img/9c84a60f9e70ea0bf5c7c51ae709df3e_99_0.png)

(a) Low learning rate $\gamma = 0.05$ (b) High learning rate $\gamma = 1.2$ (c) Good learning rate $\gamma = 0.3$

**Figure 5.7:** Optimization using gradient descent of a cost function $J(\theta)$ where $\theta$ is a scalar parameter. In the different subfigures we use a too learning rate (a), a high learning rate (b), and a good learning rate (c). Remember that a good value of $\gamma$ is very much relative to the shape of the cost function; $\gamma=0.3$ might be too small (or high) for a different $J(\theta)$.

In practice we do not know $\gamma$, which determines how the $\theta$-step is at each iteration. It is possible to formulate the selection of $\gamma$ as an internal optimization problem that is solved at each iteration, a so-called line-search problem. This will result in a different value for $\gamma$ at each iteration. When viewed as a hyperparameter we can also optimize, $\gamma$, by using cross-validation, as discussed above. However this is an "external" optimization problem, contrary to line-search which is an "internal" optimization problem. Here we will consider a simpler solution where we leave the choice of $\gamma$ to the user, or more specifically it is referred to as the learning rate or step-size. Note that the gradient $\nabla_\theta J(\theta)$ will decrease and eventually approach 0 at a stationary point, that is, stationary. A stationary point is, however, not necessarily a minimum, but can be a maximum or saddle-point of the objective function. In practice one typically monitors the value of $J(\theta)$ and terminate the algorithm when it does not decrease anymore, and hope it has reached a minimum.
in non-convex problems with multiple local minima, we cannot expect gradient descent to find the global minimum. The initialization is critical for determining which stationary (or global) point is found, it therefore be a good practice (if time and computational resources permit) to run the optimization multiple times with different initializations. For highly non-convex problems such as training a deep neural network (Chapter 6) when we cannot afford to run the training, we employ method-specific heuristics and tricks to find a good initialization.
for convex problems there only one stationary point, which is also the global minimum. Hence, the initialization for convex problem can be done arbitrarily. However, by the intuition from these figures, we advise to monitor $J^{(t)}$ during the optimization,

- decrease the learning rate $\gamma$ if the cost function values $J^{(t)}$ are gone or oscillating widely (as in Figure 5.7b),
- increase the learning rate $\gamma$ if the cost function values $J^{(t)}$ are fairly constant and only decreasing (as in Figure 5.7a).

100 Andreas Lindholm, Niklas Stråle, Fredrik Dinsstrahl, and Thomas B. Schön. 2021. Draft (April 30, 2021) of Machine Learning - A First Course for Engineers and Scientists. http://ml.book.org
