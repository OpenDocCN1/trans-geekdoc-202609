
# 使用自定义数据类型

在某些机器学习应用中，标准数据类型如 `float32` 或 `float64` 可能不足以满足特定精度要求或需要专门的数值行为。例如，你可能需要定点运算、自定义舍入行为，或针对特定硬件优化的表示形式。`JAX` 默认支持标准数值类型，但为了满足项目的特殊需求，你需要在 `JAX` 的框架内实现并使用自定义数据类型。这里的挑战是将这些自定义类型集成到 `JAX` 中，使其能够参与 `JAX` 的转换，同时确保正确且高效的计算。

因此要使用自定义数据类型，你可以通过创建 `jax.lax_dtype` 的子类或使用 `jax.custom_dtype` 机制来定义新的数据类型。需要说明的是：`JAX` 并未设置好用于处理自定义数据类型。作为替代方案，你可以通过使用标准类型表示它们并重载必要的操作来模拟自定义数据类型。另一个选择是使用 `JAX` 对自定义 `JVPs`（雅可比-向量积）和 `VJPs`（向量-雅可比积）的支持，以在自动微分期间为某些用例定义自定义行为。

在本教程中，我们将探讨如何使用 `Custom VJP` 和 `Custom JVP` 函数来实现自定义数据类型，以便为涉及你专门数值类型的函数定义自定义的前向和反向行为。

## 模拟自定义数据类型

首先，我们的方法将使用现有类型来模拟自定义数据类型。例如，你可以使用整数类型表示定点数并相应地定义操作。

假设你想实现具有特定缩放因子的定点运算。

```python
import jax
import jax.numpy as jnp
# Define a fixed-point class
class FixedPoint:
    def __init__(self, value, scale=1000):
        self.value = jnp.asarray(value)
        self.scale = scale
    def to_float(self):
        return self.value / self.scale
    def __add__(self, other):
        return FixedPoint(self.value + other.value, self.scale)
    def __mul__(self, other):
        return FixedPoint((self.value * other.value) // self.scale, self.scale)
    # Add other necessary methods...
# Example usage
a = FixedPoint(1000)  # Represents 1.0
b = FixedPoint(2000)  # Represents 2.0
c = a + b  # Represents 3.0
d = a * b  # Represents 2.0
```

## 使用 JAX 自定义转换

现在，要将自定义操作与 `JAX` 集成，你可以使用 `jax.custom_jvp` 或 `jax.custom_vjp` 装饰器来定义自定义的前向和反向传递。

假设你有一个在自定义数据类型上运行的函数，并且你希望定义它在微分期间的行为。

考虑以下自定义平方函数的示例：

```python
@jax.custom_jvp
def custom_square(x):
    return x ** 2
# Define the custom JVP rule
@custom_square.defjvp
def custom_square_jvp(primals, tangents):
    x, = primals
    x_dot, = tangents
    primal_out = custom_square(x)
    tangent_out = 2 * x * x_dot  # Derivative of x^2 is 2x
    return primal_out, tangent_out
x = jnp.array(3.0)
y = custom_square(x)
dy_dx = jax.grad(custom_square)(x)
print("y =", y)          # y = 9.0
print("dy/dx =", dy_dx) # dy/dx = 6.0
```

我们还需要确保自定义数据类型可以与 `JAX` 转换一起使用。为此，让我们定义一种可微分的定点数的自定义数据类型。

```python
# Define JVP rules
@add.defjvp
def add_jvp(primals, tangents):
    a, b = primals
    a_dot, b_dot = tangents
    primal_out = FixedPoint.add(a, b)
    tangent_out = a_dot + b_dot
    return primal_out, tangent_out

@multiply.defjvp
def multiply_jvp(primals, tangents):
    a, b = primals
    a_dot, b_dot = tangents
    primal_out = FixedPoint.multiply(a, b)
    tangent_out = (a_dot * b.value + b_dot * a.value) // a.scale
    return primal_out, tangent_out
```

## 使用自定义数据类型

现在，你可以在计算中使用 `FixedPoint` 并应用

```python
def compute(a_value, b_value):
    a = FixedPoint(a_value)
    b = FixedPoint(b_value)
    c = FixedPoint.multiply(a, b)
    return c.value
# Compute gradient with respect to a_value
grad_fn = jax.grad(compute)
gradient = grad_fn(1000.0, 2000.0)  # Inputs are scaled integers
print("Gradient:", gradient)
```

## 使用自定义 PyTree

你也可以将自定义数据类型表示为 `PyTree`，以便 `JAX` 可以遍历它。

```python
from jax import tree_util
def fixedpoint_flatten(fp):
    return (fp.value,), fp.scale
def fixedpoint_unflatten(scale, value):
    return FixedPoint(value[0], scale)
tree_util.register_pytree_node(FixedPoint, fixedpoint_flatten, fixedpoint_unflatten)
```

现在，你可以在 `FixedPoint` 实例上使用 `JAX` 函数

```python
def compute_sum(a_value, b_value):
    a = FixedPoint(a_value)
    b = FixedPoint(b_value)
    c = a.value + b.value
    return c
grad_fn = jax.grad(compute_sum)
gradient = grad_fn(1000.0, 2000.0)
print("Gradient:", gradient)
```

这种方法允许 `JAX` 在转换中处理 `FixedPoint` 实例，但你仍需要确保操作正确定义并且与 `JAX` 的期望兼容。对于高级用例，你可以按如下所示定义自定义原语：

```python
def compute(a_value, b_value, scale=1000):
    a = jnp.asarray(a_value)
    b = jnp.asarray(b_value)
    c = fixed_mul(a, b, scale)
    return c
grad_fn = jax.grad(compute)
gradient = grad_fn(1000.0, 2000.0)
print("Gradient:", gradient)
```

如果你使用 `JAX` 的自定义转换和原语与自定义数据类型，你可以让 `JAX` 为你做更多事情，尤其是在处理特殊数值情况时。这种方法要求你仔细思考如何定义操作并在它们之间进行区分。但它让你将自定义类型集成到 `JAX` 的生态系统中，这意味着你可以使用其自动微分和编译功能。
