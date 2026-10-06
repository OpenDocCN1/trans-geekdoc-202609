# Testing and accounting for interactions between variables in linear models 117

The output appears as follows:

```
## Simultaneous Tests for General Linear Hypotheses
##
## Multiple Comparisons of Means: Tukey Contrasts
##
## Fit: lm(formula = size - compost_supp, data = compost_int)
##
## Linear Hypotheses:
##
Std. Error t value Pr(|t|)                               Estimate
## John Innes #2.Formula X1           John Innes #1.Formula X1 =\=
0 1.30865      0.13666      9.576      <1e-04 ***
## John Innes #1.Formula X1           John Innes #2.Formula X1 =\=
0 0.17780      0.13666      1.301      0.570
## John Innes #2.Formula X2           John Innes #1.Formula X1 =\=
0 0.17074      0.13666      1.247      0.603
## John Innes #1.Formula X2           John Innes #2.Formula X1 = 0
-1.13085      0.13666      <1e-04 ***
## John Innes #2.Formula X2           John Innes #2.Formula X1 = 0
-1.13821      0.13666      -8.329
## John Innes #2.Formula X2           John Innes #1.Formula X2 = 0
-0.00736      0.13666      -0.054      1.000
##
## Signif. codes: 0 '****' 0.001 '**' 0.05 '*' 0.1 '.' ' ' ' 1
## (Adjusted p values reported -- single-step method)
```

This shows that three of the interaction contrasts are likely significant. In step 4, we create a plot (Figure 5.7) using ggplot that serves as a check for these conclusions:

![](bbox=[0.121, 0.643, 0.753, 0.876])

Figure 5.7 - A plot of the data