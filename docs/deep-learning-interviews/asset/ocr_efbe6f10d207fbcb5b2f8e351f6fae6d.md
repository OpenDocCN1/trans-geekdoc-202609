```
sigmoid = 1 / (1 + sympy. exp(-y))
```

FIGURE 5.23: Sigmoid in SymPy

# 2 Second:

```
sig_der=sym. diff(sigmoid, y)
```

FIGURE 5.24: Sigmoid gradient in SymPy

# 3 Third:

```
sig_der. evalf(subs= {y:0 })
> 0.25
```

FIGURE 5.25: Sigmoid gradient in SymPy

# 4 The plot is depicted in 5.26 .

```
p= sym. plot(sig_der);
```

![](bbox=[0.23, 0.59, 0.79, 0.87])

FIGURE 5.26: SymPy gradient of the Sigmoid() function