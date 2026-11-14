number of decision variables (number of thresholds) in hyperspace, then,
using Eq. (3.8):

```
x = \begin{bmatrix}
x_1^1 & x_1^2 & \cdots & x_1^{d-1} & x_1^d \\
x_2^1 & x_2^2 & \cdots & x_2^{d-1} & x_2^d \\
\vdots & \vdots & \vdots & \vdots & \vdots \\
x_{N-1}^1 & x_{N-1}^2 & \cdots & x_{N-1}^{d-1} & x_{N-1}^d \\
x_N^1 & x_N^2 & \cdots & x_N^{d-1} & x_N^d
\end{bmatrix} \tag{3.14}
```

```
x_N^d = x_{min,d} + \left(x_{max,d} - x_{min,d}\right) * rand \tag{3.15}
```

To find its optimal position in the search space, the agent uses Eq. (3.14) to
build a position vector (1). \(x_{max,d}\) and \(x_{min,d}\) are maximum and minimum
limits for the decision variable where the value of rand () ranges from 0 to 1.

It is determined that the molecules of odor will diffuse from the source/
origin at an initial velocity determined by Eq. (3.15).

```
v_N^d = v_{min,N} + \left(v_{max,N} - v_{min,N}\right) * rand() \tag{3.16}
```

Every odor molecule represents a potential solution in the geometric
number space. Using the vector's position in Eq. (3.14) and the molecules'
velocity in Eq. (3.16), we are able to locate these potential solutions' positions (smell molecule). Due to the Brownian spread of the smell molecules,
Eq. (3.17) is used to update the scent molecules' velocity.

```
x_N^d \left(t+1\right) = x_N^d \left(t\right) + v_N^d \left(t+1\right) * \Delta t \tag{3.17}
```

Assuming that, during the optimization process, the agent takes only one
step at a time, t is considered to be 1. For example, until the last iteration is
reached, the algorithm's gradually increase their iteration by 1. As a result,
the scent molecules have moved to Eq. (3.18) as their new location.

```
x_N^d \left(t+1\right) = x_N^d \left(t\right) + v_N^d \left(t+1\right) \tag{3.18}
```

Each fragrance molecule's diffusion velocities are correlated with how quickly
they evaporate and move around in the search space. Since the fragrance
molecules spread out unevenly before they get to the agent's site, Eq. (3.19):

```
v_N^d \left(t+1\right) = v_N^d \left(t\right) + v \tag{3.19}
```