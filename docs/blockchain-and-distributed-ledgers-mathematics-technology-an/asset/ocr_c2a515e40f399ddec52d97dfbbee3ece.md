# 296 | Blockchain and Distributed Ledgers: Mathematics, Technology, and Economics

![](bbox=[0.088, 0.087, 0.473, 0.318])

![](bbox=[0.525, 0.087, 0.911, 0.318])

(a)

(b)

![](bbox=[0.088, 0.337, 0.473, 0.569])

![](bbox=[0.525, 0.337, 0.911, 0.569])

(c)

(d)

Figure 10.2 BTC, ETH, XRP, and MRKT price series on a log scale. Own graphics. Source: coinmarketcap.com.

The kernel density estimator estimates a pdf for a random variable under consideration and is defined as follows:

```
$$\hat{f}_h(x) = \frac{1}{Nh} \sum_{n=1}^{N} K\left(\frac{x-x_n}{h}\right),\quad (10.1)$$
```

$x_1, x_2, \dots, x_N$ are random samples from an unknown distribution of BTC returns, $N$ is the sample size, $K(*)$ is the kernel smoothing function, and $h$ is the bandwidth. The kernel density is similar to a histogram. On the one hand, it represents the probability distribution using the sample data. On the other hand, in contrast to a histogram, which places values over discrete bins, the kernel density sums the component smoothing functions and produces a continuous probability curve.

We choose the following Epanechnikov kernel:

```
$$K(x) = \frac{3}{4}(1-x^2),\\quad (10.2)$$
```