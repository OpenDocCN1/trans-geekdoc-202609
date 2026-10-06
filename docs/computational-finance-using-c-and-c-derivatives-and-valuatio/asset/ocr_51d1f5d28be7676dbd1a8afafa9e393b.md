# 148 CHAPTER | 5 Single Asset American Options

```
$$\tilde{a}_j = \Theta_{\Delta t} \left\{ \frac{\sigma^2 S_j^2 \Delta X_j^+}{D} - \frac{(r-q)S_j(\Delta X_j^+)^2}{D} \right\ \quad (5.4.44)$
```

```
$$\tilde{b}_j = 1 - \Theta_{m\Delta t} \left\{ \frac{(r-q)S_j \{ (\Delta X_j^+)^2 - (\Delta X_j^-)^2 \} }{D} + \frac{\sigma^2 S_j^2 \{ \Delta X_j^+ + \Delta X_j^- \} }{D} \right\$ \quad (5.4.45)$
```

```
$$\tilde{c}_j = \Theta_{m\Delta t} \left\{ \frac{(r-q)S_j}{D} + \frac{\sigma^2 S_j^2 \Delta X_j^-}{D} \right\$ \quad (5.4.46)$$
```

As, equation (5.4.39), is as the case for equation (5.4.14) in Section 5.4, provides the relationship between the three option values $f_{i+1,j-1}$, $f_{i,j}$, and $f_{i,j+1}$ at time index $i+1$, and the three option values. It can also be seen that equation (5.4.39) is the nonuniform grid equivalent of equation (5.4.14) given in Section 5.4. We will now show that equation(5.4.39) and equation(5.4.14) are identical when a uniform grid is used, that, $\Delta X_j^+ = \Delta X_j^-$. We proceed as follows:

Let $\Delta X_j^+ = \Delta X_j^-$ and $S_j = j\Delta S$.

```
$So$$
$$D=(\Delta X_j^+)^2 + (\Delta X_j^-)^2\Delta X_j^2 = 2(\Delta S)^3,$$
$$\frac{(\Delta X_j^+)^2}{D} = \frac{(\Delta X_j^-)^2}{D} = \frac{1}{2(\Delta S)^3} 2\Delta S',$$
$$\frac{\Delta X_j^+}{D} = \frac{\Delta X_j^-}{D} = \frac{1}{2\Delta S^2},$$
$$((\Delta X_j^+)^2 - (\Delta X_j^-)^2 = 0.$$$
```

If we substitute the above values into equation (5.4.41) to equation (5.4.46), we obtain the following expressions for the coefficients in equation (5.4.39).

```
$a_j = (1 - \Theta_{\Delta t}) \left\{ \frac{(r-q)S_j}{2\Delta S} \frac{\sigma^2 S_j^2}{2\Delta S^2} \right\ = (1 - \Theta_{\Delta t}) \frac{1}{2}\{(r-q)j - \sigma^2 j^2\},$
$$b_j = 1 + \Delta t(1 - \Theta_{m\Delta t}) \left\{ r + \frac{\sigma^2 S_j^2}{\Delta S^2} \right\ = 1 + (1 - \Theta_{m\Delta t})\Delta t \{r + \sigma^2 j^2\},$$$
$$c_j = (1 - \Theta_{m\Delta t}) \left\{ \frac{(r-q)S_j}{2\Delta S} \frac{\sigma^2 S_j^2}{2\Delta S^2} \right\ = -(1 - \Theta_{m\Delta t}) \frac{1}{2}\{(r-q)j + \sigma^2 j^2\},$$$
$$$\tilde{a}_j = \Theta_{\Delta t} \left\{ \frac{\sigma^2 S_j^2}{2\Delta S^2} - \frac{(r-q)S_j}{2\Delta S} \right\ = -\Theta_{\Delta t} \frac{\Delta t}{2}\{(r-q)j - \sigma^2 j^2\}.$$
```