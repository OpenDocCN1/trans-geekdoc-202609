# Single asset American options

# Derivation of Eq. (5.4.48)

We will now derive an expression for the logarithmic Black-Scholes equation, and show that it agrees with Eq. (5.4.48).

Since $Z = \log S$ we have $\frac{\partial Z}{\partial S} = \frac{1}{S}$. This gives:

```
$$\frac{\partial f}{\partial S} = \frac{\partial f}{\partial Z} \frac{\partial Z}{\partial S} - \frac{1}{S} \frac{\partial f}{\partial Z}$
```

and

```
$$\frac{\partial^2 f}{\partial S^2} = \frac{\partial^2 f}{\partial Z^2} (\frac{\partial Z}{\partial S})^2 + \frac{\partial f}{\partial Z} \frac{\partial^2 Z}{\partial S^2} - \frac{2}{S} \frac{\partial^2 f}{\partial Z} \frac{\partial Z}{\partial S} - \frac{1}{S} \frac{\partial f}{\partial Z} \frac{\partial^2 Z}{\partial S} + \frac{1}{S^2} \frac{\partial f}{\partial Z}$$
$\frac{\partial^2 f}{\partial S^2} = \frac{\partial^2 f}{\partial Z^2} \frac{1}{S^2} + \frac{\partial f}{\partial Z} \frac{\partial^2 Z}{\partial S^2} - \frac{2}{S} \frac{\partial^2 f}{\partial Z} \frac{1}{S} - \frac{1}{S} \frac{\partial f}{\partial Z} + \frac{1}{S^2}$
```

So. (5.4.47) becomes

```
$$\frac{\partial f}{\partial t} + - \frac{(r-q)}{S} \frac{\partial f}{\partial Z} - \frac{\sigma^2 S^2}{2S^2} \frac{\partial^2 f}{\partial Z^2} + \frac{\sigma^2 S^2}{2S^2} \frac{\partial^2 f}{\partial Z^2} = rf$
```

thus setting $b = r - q - \sigma^2 / 2$ we obtain:

```
$$\frac{\partial f}{\partial t} + b \frac{\partial f}{\partial Z} + \frac{1}{2} \frac{\partial^2 f}{\partial Z^2} = rf$
```

We now consider the finite difference discretization of Eq. (5.4.48).

# The finite-difference method

Application of the finite-difference method to the log transformed Black-Scholes equation is very similar to that already outlined in Sections 5.4.2 and 5.4.3.

Using the $\Theta_m$ method on Eq. (5.4.48) results in:

```
$$\frac{f_{i+1,j} - f_{i,j}}{\Delta t} + b[\Theta_m f_{i+1,j} + \Theta_m^* f_{i,j}] + \frac{1}{2} \sigma^2[\Theta_m f_{i+1,j}^* + \Theta_m^* f_{i,j}'] =$\n= r[\Theta_m f_{i+1,j} + \Theta_m^* f_{i,j}]$
```

where $\Theta_m^* = 1 - \Theta_m$. Applying a uniform discretization at node $(i, j)$ we obtain:

```
$f_{i+1,j} - f_{i,j} + f_j - \frac{\b \Delta t \mathcal{A}_1}{2\Delta Z} + \frac{\sigma^2 \Delta t \mathcal{A}_2}{2\Delta Z^2} = r\Delta t[\Theta_m f_{i+1,j} + \Theta_m^* f_{i,j}] \quad (5.4.49)$
```

where

```
$$\mathcal{A}_1 = \Theta_m(f_{i,j+1} - f_{i,j-1}) + \Theta_m^*[f_{i+1,j} - f_{i,j-1}]$$\n$\mathcal{A}_2 = \Theta_m(f_{i,j+1} - 2f_{i,j} + f_{i,j-1}) + \Theta_m^*[f_{i+1,j} - 2f_{i,j} + f_{i,j-1}]$
```

Collecting like terms we obtain:

```
$B_1 f_{i,j-1} + B_2 f_{i,j} + B_3 f_{i+1,j} + C_1 f_{i,j-1} + C_2 f_{i,j} + C_3 f_{i,j+1} = 0$
```