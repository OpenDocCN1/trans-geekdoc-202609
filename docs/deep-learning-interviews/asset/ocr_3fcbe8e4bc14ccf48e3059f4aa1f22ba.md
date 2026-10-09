# Forward-mode AD derivative evaluation

$v_{-1} = x_1 = e^2$
$v_0 \ = x_2 = \pi$
$\dot{v}_{-1} = \dot{x}_1 = 1$
$\dot{v}_0 \ = \dot{x}_2 = 0$
$\dot{v}_1 \ = \dot{v}_{-1}/v_{-1} = 1/e^2$
$\dot{v}_2 \ = \dot{v}_{-1} \times v_0 + \dot{v}_0 \times$
$v_{-1} = 1 \times \pi + 0 \times$
$e^2 = \pi$
$\dot{v}_4 \ = \dot{v}_1 + \dot{v}_2 = 1/e^2 +$
$\pi$
$\dot{f} \ \ = \ \dot{v}_4 \ \ = \ \ 1/e^2 \ +$
$\pi \ = \approx \ 3.2769$

TABLE 5.3: Forward-mode AD table for $v=g(x_1,x_2)=\ln(x_1)+x_1x_2$ evaluated at $(x_1,x_2)=(e^2,\pi)$ and setting $\dot{x}_1=1$ (seed values are mentioned here: 1) to compute $\frac{\partial y}{\partial x_1}.$

+   6 *The following Python code (5.22) proves that the numerical results are* *correct:*

```
```python
import autograd.numpy as np
from autograd import grad
import math

x1 = math.e**math.e
x2 = math.pi

def f1 (x1,x2):
 return (np.log(x1) + x1* x2)
```
```