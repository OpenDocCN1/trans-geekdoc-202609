![](bbox=[0.31, 0.08, 0.75, 0.35])

FIGURE 1.1: Household spending. Notice that the distribution is roughly normal on the $log$ scale (look at the x-axis).

Consider the unconditional mean for the variable $\text{spend}$: the average amount of money spent online annually by households in the United States. You can estimate this mean—say, $\mu_{\text{spend}} = \mathbb{E}[\text{spend}]$—with its $sample$ $average$.

```
```
> mean(browse$spend)
[1] 1946.439
```
```

Here, you don’t think that $\mu_{\text{spend}}$ is exactly equal to $1946.439; rather, this is a good guess and the truth is ideally near to this value.

How near? Let’s review some basic statistics. Suppose you have $n$ independent random variables: $\{x_i\}_{n=1}$. In terms of our current example, this is saying that each household spends a specific amount without consideration of what the other households in the sample do online. The sample mean is then

$$\overline{x} = \frac{1}{n} \sum_{i=1}^{n} x_i. \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad (1.1)$$

The variance of this statistic can be calculated as