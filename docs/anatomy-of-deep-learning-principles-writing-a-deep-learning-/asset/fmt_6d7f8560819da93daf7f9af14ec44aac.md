
```python
x0 = np.array([3., 4.])
print("initial point", x0, "gradient", df(x0))

path = gradient_descent(df, x0, 0.000005, 300000)
print("Extreme point：", path[-1])
```

Gradient `[25625.25 57519.]` of initial point `[3. 4.]`

Extreme points: `[2.70735828 0.41689171]`

Because the initial gradient value of `x` starts to be very large, the learning rate `α` must take a small number (such as `0.000005`), otherwise it will cause shock or infinite value, and finally converge to `[2.70735828 0.41689171]`. But it is not the best point; you can see this situation more intuitively by drawing the change of `x` during the iteration process.

```python
def plot_path(path, x, y, z, minima_, xmin, xmax, ymin, ymax):
    fig, ax = plt.subplots(figsize=(10, 6))
    ax.contour(x, y, z, levels=np.logspace(0, 5, 35), norm=LogNorm(), cmap=plt.cm.jet)
    # ax.scatter(path[0], path[1]);
    ax.quiver(path[:-1, 0], path[:-1, 1], path[1:, 0] - path[:-1, 0], path[1:, 1] - path[:-1, 1], scale_units='xy', angles='xy', scale=1, color='k')
    ax.plot(*minima_, 'r*', markersize=18)

    ax.set_xlabel('$x$')
    ax.set_ylabel('$y$')
    ax.set_xlim((xmin, xmax))
    ax.set_ylim((ymin, ymax))

path = np.asarray(path)
plot_path(path, x, y, z, minima_, xmin, xmax, ymin, ymax)
```

![](EPUB/media/file30.png "fig:")

Figure 2-10 During the iteration process, the gradient value becomes smaller and smaller, and the convergence becomes slower and slower

During the iterative process, the gradient value becomes smaller and smaller, and the same learning rate makes the update of `x` very slow. Even after 100,000 iterations, it still fails to approach the optimal solution. A natural approach is to use an adaptive learning rate, i.e., increase the learning rate when the gradient becomes small. As an exercise, the reader can try to modify the gradient descent algorithm to get to the optimal solution better and faster.

## 2.3 Parameter optimization strategy of gradient descent method

The learning rate in the basic gradient descent algorithm is a fixed value, and the gradient size is constantly changing during the iterative process. If the learning rate is too large, the variable to be solved will oscillate back and forth. If the learning rate is too small, the convergence will be very slow or even stagnant. The initial learning rate is moderate, but as the convergence approaches the optimal solution, its gradient is also close to 0, which will also cause stagnation. Naturally, the learning rate should be adjusted as it gradually converges during the iterative process, that is, a variable learning rate is used to update the variable `x` to be solved during the iterative process.

In order to ensure that the optimal solution can be approached better and faster, many improvements to the gradient descent method have been proposed. These improvements use a changing learning rate or strategy to update the solution variables (also called parameters). The update strategies or methods for variables (parameters) include: Momentum, Nesterov accelerated gradient, Adagrad, Adadelta, RMSprop, Adam, AdaMax, Nadam, AMSGrad, etc.

It should be noted that the function may be a multi-variable function; therefore, its variable `x` can be a vector `xx` composed of multiple values. Only some of the commonly used optimization strategies are described below.

### 2.3.1 Momentum momentum method

The gradient descent method uses the learning rate `α` and the negative direction of the gradient, that is, `−α∇f(x)` to update `x` each time. The update vector `−α∇f(x)ofx` depends entirely on the current calculated gradient. The Momentum momentum method updates the vector of `x` not only considering the current gradient but also considering the last update vector; that is, the updated vector is considered to have inertia. Assuming that `v[t−1]` is the vector used for update last time, the current updated vector is:

`v[t] = γv[t−1] + α∇f(x)`

Update `x` with this `v`:

`x = x − v[t]`

This vector used to update `x` is called **momentum**. The momentum method regards the update vector as the velocity of a moving object, and the velocity has inertia. Due to the combination of the previous update vector and the current gradient, it alleviates the sharp changes in the gradient at different times, making the updated vector smoother; that is, maintaining the inertia of the previous motion, so that where the gradient is small, there is still a large motion. The speed will not overshoot due to the sudden increase of the gradient. This method is like a ball with weight rolling downhill, maintaining a certain amount of inertia while looking for the steepest descent path. Ordinary gradient descent only determines the speed of movement according to the degree of steepness, just like rushing fast in steep places and hardly moving in flat places.

The initial value of `vv` is 0, which can be expressed in Python code as:

```python
v = np.zeros_like(x)
```

That is, `vv` is a tensor with the same shape as `xx` with an initial value of 0. In the iterative process, `vv` is updated first, and then the parameter `xx` of the function is updated:

```python
v = gamma * v + alpha * df(x)
x = x - v
```

The following is the gradient descent method based on the momentum method:

```python
def gradient_descent_momentum(df, x, alpha=0.01, gamma=0.8, iterations=100, epsilon=1e-6):
    history = [x]
    v = np.zeros_like(x)            # momentum
    for i in range(iterations):
        if np.max(np.abs(df(x))) < epsilon:
            print("The gradient is small enough!")
            break
        v = gamma * v + alpha * df(x)           # update momentum
        x = x - v                    # Update variables (parameters)
        
        history.append(x)
    return history
```

Use the gradient descent method of this momentum method to solve the above problem:

```python
path = gradient_descent_momentum(df, x0, 0.000005, 0.8, 300000)
print(path[-1])
path = np.asarray(path)
```

`[2.96324633 0.49067782]`

It can be seen that the solution of the momentum method is very close to the optimal solution, as the picture shows.

```python
plot_path(path, x, y, z, minima_, xmin, xmax, ymin, ymax)
```

![](EPUB/media/file31.png "fig:")

Figure 2-11 The momentum method quickly converges to a near-optimal solution

### 2.3.2 Adagrad method

According to the variable update formula of the gradient descent method `xx = xx − α∇f(xx)`, what affects the variable update is the product of the learning rate and the gradient `α∇f(xx)`. The gradient being too large or too small and the learning rate being too large or too small will affect the convergence of the algorithm.

For a multivariate function, the magnitude of the partial derivatives for each variable can vary widely. For example, the absolute values of the partial derivatives $\frac{\partial f}{\partial x_{1}},\frac{\partial f}{\partial x_{2}}$ of a function `f(x[1], x[2])` of two variables at a certain point `(x[1], x[2])` may differ greatly. It is inappropriate to use the same learning rate for them. The appropriate learning rate for one component is too large or too small for the other component, resulting in shock and stagnation. That is, it is inappropriate to directly update with the following formula:

$x_{1} = x_{1} - \alpha\frac{\partial f}{\partial x_{1}}$

$x_{2} = x_{2} - \alpha\frac{\partial f}{\partial x_{2}}$

The Adagrad method can be translated as "adaptive (ada) gradient (grad)" from the noun, which divides each gradient component by the historical cumulative value of the gradient component, so that the problem of unbalanced gradient sizes of different components can be eliminated. For 2 components `(x[1], x[2])`, if the historical cumulative value `(G[1], G[2])` of the respective components is calculated respectively, the update formula of the 2 components is:

$x_{1} = x_{1} - \alpha\frac{1}{G_{1}}\frac{\partial f}{\partial x_{1}}$
