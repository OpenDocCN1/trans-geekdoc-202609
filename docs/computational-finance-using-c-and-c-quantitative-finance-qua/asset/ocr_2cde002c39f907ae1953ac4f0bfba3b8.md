# Gamma

The definition of $\Gamma$ is the rate of change of $\Delta$ with asset price all other parameters remaining fixed. Thus,

```
$$\Gamma = \frac{\partial^2 f}{\partial S^2} = \frac{\partial \Delta}{\partial S}$
```

In order to evaluate $L^*$ we require at least two values of $\Delta$. The nearest this can be achieved to the root R is at step 2, where we have:

```
$$\Gamma = \frac{\Delta^*_{UV} - \Delta^*_{VW}}{S^*_{UV} - S^*_{VW}}$
```

with the midpoints

```
$S^*_{UV} = \frac{1}{2}\{S_U + S_V\}$
```

and the values of $\Delta$ at the midpoints $S^*_{UV}$ and $S^*_{VW}$ denoted by $\Delta^*_{UV}$ and $\Delta^*_{VW}$, respectively. Since

```
$$\Delta^*_{UV} = \frac{f_U - f_V}{S_U - S_V}$
```

```
$$\Delta^*_{VW} = \frac{f_V - f_W}{S_V - S_W}$
```

and

```
$S^*_{UV} = \frac{1}{2}\{S_U - S_W\}$
```

we have

```
$$\Delta^*_{UV} = \frac{v[2] - v[1]}{s[M+2] - s[M]}$
```

```
$$\Delta^*_{VW} = \frac{v[1] - v[0]}{s[M] - s[M-2]}$
```

The value of $\Gamma$ can therefore be approximated as:

```
$$\Gamma = \frac{2(\Delta^*_{UV} - \Delta^*_{VW})}{s[M+2] - s[M-2]}$
```

# Theta

The definition of $\Theta$ is the rate of change of option value with time all other parameters remaining fixed. Thus,

```
$$\Theta = \frac{\partial f}{\partial t} = \frac{\Delta f}{\Delta t}$
```

The nearest to the root R is computed using the time interval from step 0 to step 2. We then obtain the following approximation:

```
$$\Theta = \frac{f_V - f_R}{2\Delta t} = \frac{v[1] - v[5]}{2\Delta t}$
```