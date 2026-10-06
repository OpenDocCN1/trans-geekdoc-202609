# # Gradient Descent

Start at some point, follow the gradient towards (a) minimum

```
$x_0 \leftarrow \text{init}, t = 0$
while termination condition does not hold do
$x_{t+1} = x_t - \eta\nabla f(x_t), \quad t = t + 1$
end while
```

![](bbox=[0.678, 0.246, 0.985, 0.638])

+   - $\eta \dots$ learning rate or step size
- Gradient always points in the direction of steepest ascent