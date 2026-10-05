# Classification with Logistic Regression

$p(t) = \sigma(t) = \frac{1}{1+e^{-t}}$

An example sigmoid function is shown in Figure 14.1. The function is useful because it has domain $(-\infty, \infty)$ and range $(0,1)$. Given this range, the output can be treated as the probability of the event. Notice the $S$ shape and horizontal asymptotes at zero and when the input tends to $-\infty$ and $\infty$, respectively.

![](bbox=[0.313, 0.329, 0.683, 0.497])

FIGURE 14.1: Sigmoid Function

The $odds$ of an event is the ratio of the probability of the event taking place divided by the probability it does not take place, $p/(1-p)$. We first simplify $1-p$, showing the dependence on $t$:

```
$1-p(t) = 1 - \frac{1}{1+e^{-t}}\n= \frac{1+e^{-t}}{1+e^{-t}} - \frac{1}{1+e^{-t}}\n= \frac{e^{-t}}{1+e^{-t}}$
```

Then the odds form

```
$$\frac{p(t)}{1-p(t)} = \frac{1/(1+e^{-t})}{e^{-t}/(1+e^{-t})}
= \frac{1}{e^{-t}}\n= e^t$
```