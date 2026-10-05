# Classification with Logistic Regression

The term $p(x_i|eta)$ denotes the probability of the event i given the parameter values, and the term $1-p(x_i|eta)$ denotes the probability of a non-event for outcome $i$. The exponents $y_i$ and $1-y_i$ allow for a compact expression for a Bernoulli trial. For example, if the event occurs for outcome $i$, then $y_i = 1$ and $1-y_i = 0$. It follows that

```
$p(x_i|eta)^{y_i}(1-p(x_i|eta))^{1-y_i} = p(x_i|eta)^1 (1-p(x_i|eta))^0\n= p(x_i|eta)$
```

represents the probability of an event for outcome $i$. Similarly, if the event did not occur for outcome $i$, then $y_i = 0$ and $1-y_i = 1$. It follows that

```
$p(x_i|eta)^{y_i}(1-p(x_i|eta))^{1-y_i} = p(x_i|eta)^0 (1-p(x_i|eta))^1\n= 1-p(x_i|eta)$
```

This term represents the probability of a non-event for outcome $i$.

Lastly, the product notation $\prod_{i=1}^n$ expresses the likelihood of events, For the case of three trials $(n=3)$ all resulting in events, the likelihood will be

```
$\mathcal{L}(\beta) = \prod_{i=1}^n p(x_i|\beta)^{y_i}(1-p(x_i|\beta))^{1-y_i}\n= = \prod_{i=1}^3 p(x_i|\beta)\n= = p(x_1|\beta)p(x_2|\beta)p(x_3|\beta)$
```

It is easier to work with the **log-likelihood**, or the logarithm of the likelihood, as the products become sums. It is valid to apply the logarithm, as the parameters that maximize the likelihood will also maximize the log-likelihood. This is because $log(\cdot)$ is a monotonically increasing function. The log-likelihood has the form

```
$l(\beta) = \sum_{i=1}^n y_i \ln p(x_i|\beta) + (1-y_i) \ln (1-p(x_i|\beta))$
```

This uses two properties of logarithms:

```
$log(ab) = log(a) + log(b)\nlog(a)^b = b log(a)$
```