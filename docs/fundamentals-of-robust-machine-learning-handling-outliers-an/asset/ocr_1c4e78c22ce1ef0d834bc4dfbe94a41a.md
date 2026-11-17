The method generally used to minimize a convex function is called gradient descent. There are many variations of this technique but for now it suffices to understand the basic idea. In gradient descent, we start with a random initial point on the function and find the gradient at that point. This is shown in the vicinity of the minimum B for the non-convex case and in the vicinity of the minimum A for the convex case in Figure 2.4. If the slope is negative, as in this case, then the minimum lies to the right of the point. Conversely, if the slope is positive, the minimum lies to the left of the initial guess. Using f(x) as the loss function and t as the iteration index, we can update the value of our next guess of the optimal value of x using

```
x^{(t+1)} = x^{(t)} - \frac{df(x)}{dx}|_{x^{(t)}}.
(2.5.19)
```

The negative sign reflects the fact that we should move in the opposite direction of the slope. However, it may not make sense to take a large step in one direction or the other due to the fact that we could oscillate back-and-forth or go well beyond the optimal value. For this reason, we introduce a factor called (in the parlance of machine learning) the learning rate, \(\ell\), to tune the step size, as follows:

```
x^{(t+1)} = x^{(t)} - \ell \times \frac{df(x)}{dx}|_{x^{(t)}}.
(2.5.20)
```

The value of \(\ell\) can be fixed or adjusted during each iteration to enable faster convergence. Using this simple approach in the convex case would produce a minimum at A but in the non-convex case, it might produce a minimum at B, which is local minima. Clearly, the advantage of the convex optimization is that the global minimum is always obtained (considering some mild assumptions about the existence and continuity of the function and its first derivative).

**Exercise:** Consider the function f(x) = (x - 2)<sup>2</sup>. Use the update equation

```
x^{(t+1)} = x^{(t)} - \frac{df(x)}{dx}|_{x^{(0)}}
```

and the initial condition x<sup>(0)</sup> = 3 to find the minimum. Apply only two steps of the iteration.

**Ans.:** The derivative is df(x)/dx = 2(x - 2).

Iteration 1:

```
x^{(1)} = x^{(0)} - 2(x^{(0)} - 2) = 3 - 2(3 - 2) = 1
```

Iteration 2:

```
x^{(2)} = x^{(1)} - 2(x^{(1)} - 2) = 1 - 2(1 - 2) = 3
```

This will not convergence as it will oscillate from one side to the other.

**Exercise:** Consider the function f(x) = (x - 2)<sup>2</sup> again. This time, use the update equation

```
x^{(t+1)} = x^{(t)} - \ell \times \frac{df(x)}{dx}|_{x^{(0)}}
```

and the initial condition x<sup>(0)</sup> = 3 to find the minimum. Apply only two steps of the iteration using \(\ell = 1/2\).