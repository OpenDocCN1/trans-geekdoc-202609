# Deep Learning-Based Forward Modeling and Inversion Techniques

# 2.1.1 Analytical Methods

Classic analytical methods contain variable separation [5, 6, 7], the Green's function [8], integral transform [9, 10, 11] and etc. In this chapter, the first two methods will be discussed for the sake of simplicity.

The variable separation method is one of the most used analytical methods for solving partial differential equations (PDEs). It assumes that the solution of the heat conduction equation is variable with respect to the spatial coordinates $x, y,$ and $z$. For the steady-state problem, if the thermal conductivity field is uniform, the temperature field satisfies the Laplace equation.

```
$$\frac{\partial^2 T(x,y,z)}{\partial x^2} + \frac{\partial^2 T(x,y,z)}{\partial y^2} + \frac{\partial^2 T(x,y,z)}{\partial z^2} = 0.$$ (2.1)
```

Supposed the temperature $T$ can be expressed

```
$T(x,y,z) = T_1(x)T_2(y)T_3(z).$ (2.2)
```

Obviously, $T(x,y,z) = 0$ is a solution of the equation. one can substitute Equation 2.2 into equation Equation 2.1, and then divide by $T(x,y,z)$, it can be obtained

```
$$\frac{1}{T_1(x)}\frac{d^2T_1(x)}{dx^2} + \frac{1}{T_2(y)}\frac{d^2T_2(y)}{dy^2} + \frac{1}{T_3(z)}\frac{d^2T_3(z)}{dz^2} = 0.$$ (2.3)
```

If each of the three terms is 0, the trivial solution can be

```
$T_1(x) = a_1x + b_1.$$ (2.4)
```

```
$T_2(y) = a_2y + b_2.$$ (2.5)
```

```
$T_3(z) = a_3z + b_3.$$ (2.6)
```

For more general cases, $T_1, T_2$ and $T_3$ satisfy

```
$$\frac{d^2T_1(x)}{dx^2} = \pmk_1^2T_1(x).$$ (2.7)
```

```
$$\frac{d^2T_2(y)}{dy^2} = \pmk_2^2T_2(y).$$ (2.8)
```

```
$$\frac{d^2T_1(x)}{dz^2} = \pmk_3^2T_1(z).$$ (2.9)
```

where

```
$$\pmk_1^2 \pm \pmk_2^2 \pm \pmk_3^2 = 0.$$ (2.10)
```

Taking $T_1$ as an example, the solution corresponding to the positive sign is a linear combination of exponential functions.

```
$T_1(x) = ae^{k_1x} + be^{-k_1x}.$$ (2.11)
```