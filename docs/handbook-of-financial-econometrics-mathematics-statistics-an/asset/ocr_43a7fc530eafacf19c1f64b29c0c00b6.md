# 85.4 The Log-Normal Distribution and its Relationship to the Normal Distribution

By comparing the PDF of normal distribution given in equation (85.1) and the PDF of log-normal distribution given in equation (85.7), we know that

$$f(x) = \frac{f(y)}{x}.\tag{85.16}$$

In addition, from equation (85.6), it is easy to see that

$$dx = x\,dy.\tag{85.17}$$

The CDF for the log-normal distribution can be expressed as

$$F(a) = \Pr(X \le a) = \Pr(\log X \le \log a)$$
$$= \Pr\left(\frac{\log X - \mu}{\sigma} \le \frac{\log a - \mu}{\sigma}\right),$$
$$= N(d),\tag{85.18}$$

where

$$d = \frac{\log a - \mu}{\sigma},\tag{85.19}$$

and $N(d)$ is the CDF of the standard normal distribution which can be obtained from Normal Table; $N(d)$ can also be obtained from S-plus or other software package. Alternatively, the value of $N(d)$ can be approximated by the following formula:

$$N(d) = a_0 e^{-\frac{d^2}{2}} (a_1 t + a_2 t^2 + a_3 t^3),\tag{85.20}$$

where
$$t = \frac{1}{1 + 0.33267 d}$$
$a_0 = 0.3989423,\ a_1 = 0.4361936,\ a_2 = -0.1201676,\ a_3 = 0.9372980.$

In case we need $\Pr(X > a)$, then we have

$$\Pr(X > a) = 1 - \Pr(X \le a) = 1 - N(d) = N(-d).\tag{85.21}$$

Since for any $h$, $E(X^h) = E(e^{hY})$, the $h$th moment of $X$, the following moment generating function of $Y$, which is normally distributed with mean