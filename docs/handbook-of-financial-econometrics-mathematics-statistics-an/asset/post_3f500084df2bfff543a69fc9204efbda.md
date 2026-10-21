
perfect market — zero transaction costs, rational behavior on the part of investors, and the absence of tax differentials between dividends and capital gains. It is assumed that the firm is not restricted to financing its growth only by retained earnings, and that its rate of return, $\tilde{r}(t)$, is a nonstationary random variable, normally distributed with mean, $\mu$, and variance, $\sigma(t)^2$.

Let $A(0)$ represent the initial assets of the firm and $h$ be the growth rate. Then the earnings of this firm are given by equation (96.1), which is

$$
\tilde{x}(t) = \tilde{r}(t) A(0) e^{h t}, \tag{96.1}
$$

where $\tilde{x}(t)$ represents the earnings of the firm, and the tilde ($\sim$) denotes its random character.

Based upon DeAngelo and DeAngelo’s (2006) assumption, we here allow that the firm partially pays out its earnings and retains a certain amount of earnings in support of its growth. The retained earnings of the firm, $y(t)$, can therefore be expressed as follows:

$$
y(t) = \tilde{x}(t) - m(t) \tilde{d}(t), \tag{96.2}
$$

where $\tilde{d}(t)$ is the dividends per share and $m(t)$ is the total number of shares outstanding at time $t$.

Equation (96.2) further indicates that the focus of the firm’s decision making is on retained earnings, which implies that dividend $\tilde{d}(t)$ also becomes a random variable. The growth of a firm can be financed by retained earnings or by issuing new equity.

The new equity raised by the firm at time $t$ can be defined as follows:

$$
e(t) = \delta p(t) \dot{m}(t), \tag{96.3}
$$

where $p(t)$ is the price per share, $\dot{m}(t) = dm(t)/dt$, and $\delta$ is the degree of market perfection, $0 < \delta \le 1$.

The value of $\delta$ equal to one indicates that new shares can be sold by the firm at current market prices.

From equations (96.1)–(96.3), investment in period $t$ is the sum of retained earnings and funds raised by new equity, so the investment in period $t$ can be written as follows:

$$
h A(0) e^{h t} = \tilde{x}(t) - m(t) \tilde{d}(t) + \delta \dot{m}(t) p(t). \tag{96.4}
$$

This implies that

$$
\tilde{d}(t) = \frac{\left[\tilde{r}(t) - h\right] A(0) e^{h t} + \delta \dot{m}(t) p(t)}{m(t)}, \tag{96.5}
$$

and the mean and variance of the dividends per share can be expressed as follows:

$$
E[\tilde{d}(t)] = \frac{\left[\mu - h\right] A(0) e^{h t} + \delta \dot{m}(t) p(t)}{m(t)},
$$

$$
\operatorname{Var}[\tilde{d}(t)] = \frac{A(0)^2 \sigma(t)^2 e^{2 t h}}{m^2(t)}. \tag{96.6}
$$

Also, let us postulate an exponential utility function of the following form<sup>3</sup>:

$$
U[\tilde{d}(t)] = -e^{\alpha \tilde{d}(t)}, \quad \text{where } \alpha > 0. \tag{96.7}
$$

Following the moment generating function, we have

$$
E\left(-e^{-\alpha \tilde{d}(t)}\right) = -e^{-\alpha E[\tilde{d}(t)] + \frac{\alpha^2}{2} \operatorname{Var}[\tilde{d}(t)]}, \tag{96.8}
$$

where $\bar{d}(t)$ is the certainty equivalent value of $\tilde{d}(t)$.<sup>4</sup>

From equations (96.6) and (96.8), the certainty equivalent dividend stream can be written as

$$
\bar{d}(t) = \frac{(\mu - h) A(0) e^{t h} + \delta \dot{m}(t) p(t)}{m(t)} - \frac{\alpha' A(0)^2 \sigma(t)^2 e^{2 t h}}{m(t)^2}, \tag{96.9}
$$

where $\alpha' = \alpha/2$. Therefore, taking advantage of exponential utility, we can obtain a risk adjusted dividend stream. Furthermore, $\bar{d}(t)$ will reduce to the certainty case, if we assume $\sigma(t)^2 = 0$.

In accordance with the capital asset pricing theory developed by Sharpe (1964), Lintner (1963), and Mossin (1966), the total risk can be decomposed into systematic risk and unsystematic risk, that is, $\tilde{r}(t)$ can be defined as follows:

$$
\tilde{r}(t) = a + b \tilde{I}(t) + \tilde{\varepsilon}(t), \tag{96.10}
$$

Then, equation (96.20) can be obtained from equations (96.18) and (96.19), implying that the initial value of a stock can be expressed as the summation of present values of its earnings stream adjusted by the risk taken by the firm.

$$
p(0) = \frac{1}{m(0)^{\delta}} \int_{0}^{T} \left\{ (a + b \bar{I} - h) A(0) e^{t h} m(t)^{\delta - 1} - \alpha' A(0)^{2} \rho(t)^{2} \sigma(t)^{2} e^{2 t h} m(t)^{\delta - 2} \right\} e^{-k t} dt. \tag{96.20}
$$

To maximize firm value, the Euler-Lagrange condition for the optimization of $p(0)$ is given by equation (96.21),<sup>8</sup>

$$
\begin{aligned}
&(\delta - 1)(a + b \bar{I} - h) A(0) e^{t h} m(t)^{\delta - 2} \\
&\quad - \alpha' A(0)^{2} \rho(t)^{2} \sigma(t)^{2} e^{2 t h} m(t)^{\delta - 3} (\delta - 2) = 0.
\end{aligned} \tag{96.21}
$$

Therefore, the optimal shares outstanding at time $t$ can be derived.

$$
m(t) = \frac{(2 - \delta) \alpha' A(0) e^{t h} \rho(t)^{2} \sigma(t)^{2}}{(1 - \delta)(a + b \bar{I} - h)}. \tag{96.22}
$$

From equations (96.18), (96.19), and (96.22), we can obtain the maximized stock value

$$
p(t) = \frac{(a + b \bar{I} - h)^{2} (1 - \delta) e^{k t - t h} \delta \int_{t}^{T} e^{\delta h s - k s} (\rho(s) \sigma(s))^{2 \delta - 2} ds}{\alpha' (2 - \delta)^{2} \rho(t)^{2 \delta} \sigma(t)^{2 \delta}}. \tag{96.23}
$$

From equation (96.22), we also obtain the optimal number of shares of new equity issued at time $t$

$$
\dot{m}(t) = \frac{\left\{ h (2 - \delta) \alpha' A(0) e^{t h} \rho(t)^{2} \sigma(t)^{2} + (2 - \delta) \alpha' A(0) e^{t h} \left[ \rho(t)^{2} \dot{\sigma}(t)^{2} + \sigma(t)^{2} \dot{\rho}(t)^{2} \right] \right\}}{(1 - \delta)(a + b \bar{I} - h)}. \tag{96.24}
$$

From equations (96.23) and (96.24), we have the amount generated from issuing new equity

$$
\dot{m}(t) p(t) = \frac{(a + b \bar{I} - h) e^{k t - (\delta - 1) t h} A(0) \left( h \rho(t)^{2} \sigma(t)^{2} + \rho(t)^{2} \dot{\sigma}(t)^{2} + \sigma(t)^{2} \dot{\rho}(t)^{2} \right) \int_{t}^{T} e^{s(\delta h - k)} (\rho(s) \sigma(s))^{2 \delta - 2} ds}{(2 - \delta) \rho(t)^{2 \delta} \sigma(t)^{2 \delta}}. \tag{96.25}
$$

From equations (96.5) and (96.25), we can obtain $\bar{D}(t) = m(t) \bar{d}(t)$. From equations (96.1) and (96.10), we can obtain $\bar{x}(t) = (a + b \bar{I}) A(0) e^{h t}$. When $\delta$ approaches unity, we can derive the optimal payout ratio as

$$
\frac{\bar{D}(t)}{\bar{x}(t)} = \frac{(a + b \bar{I} - h)}{(a + b \bar{I})} \left\{ 1 + \frac{\left[ e^{(h - k)(T - t)} - 1 \right]}{(h - k)} \left( h + \frac{\dot{\sigma}(t)^2}{\sigma(t)^2} + \frac{\dot{\rho}(t)^2}{\rho(t)^2} \right) \right\}. \tag{96.26}
$$

Equation (96.26) implies an optimal payout ratio when we use an exponential utility function to derive the stochastic dynamic dividend policy model. This result does not necessarily imply that the dividend policy results derived by M&M (1961) are false because we allowed free cash flow to be paid out partially as assumed by DeAngelo and DeAngelo (2006) instead of paying out all free cash flows as assumed by M&M (1961).

In the following section, we use equation (96.26) to explore the implications of the stochasticity, the stationarity (in the strict sense), and the non-stationarity of the firm’s rate of return for its dividend policy.<sup>9</sup> We also investigate in detail the differential effects of variations in the systematic and unsystematic risk components of the firm’s stream of earnings on the dynamics of its dividend policy.

## 96.5 Relationship Between the Optimal Payout Ratio and the Growth Rate

In this section, we investigate the relationship between the optimal payout ratio and the growth rate in terms of both exact and approximate approaches. Taking the partial derivative of equation (96.26) with respect to the growth rate, we obtain

$$
\frac{\partial [\bar{D}(t)/\bar{x}(t)]}{\partial h} = \left( -\frac{1}{a + b \bar{I}} \right) \left[ \frac{-k + h e^{(h - k)(T - t)}}{h - k} \right] + \left( 1 - \frac{h}{a + b \bar{I}} \right) \left[ \frac{\left[ (-k) + h (h - k)(T - t) \right] e^{(h - k)(T - t)} + k}{(h - k)^2} \right]. \tag{96.27}
$$

The sign of equation (96.27) is not only affected by the growth rate ($h$) but also by the expected rate of return on assets ($a + b \bar{I}$), the duration of future dividend payments ($T - t$), and the cost of capital ($k$).

Since the sign of equation (96.27) cannot be analytically determined, we use a sensitivity analysis approach to investigate the sign of equation (96.27).

Table 96.1 shows the sign of partial derivatives of equation (96.27) under different values of the growth rate and the rate of return on assets as well as duration ($T - t$). We find that the relationship between the optimal payout ratio and the growth rate is always negative when the growth rate is higher than the rate of return on assets. If the growth rate is lower than the rate of return on assets, the direction of the relationship essentially depends on the duration of the dividend payment ($T - t$). We find that the sign of equation (96.27) is negative if the duration ($T - t$) is small and the growth rate and rate of return on assets are within a reasonable range. In addition, the curved lines in Table 96.1 also indicate a nonlinear relationship between the growth rate and the optimal payout ratio. We can therefore conclude that the relationship between the optimal payout ratio and the growth rate is nonlinear and generally negative.

Based upon equation (96.27), Figure 96.1 plots the change in the optimal payout ratio with respect to the growth rate in different durations of dividend payments and costs of capital. We find a negative relationship between the optimal payout ratio and the growth rate, indicating that a firm with a higher rate of return on assets tends to pay out less when its growth opportunities increase. Moreover, a firm with a lower growth rate and higher expected rate of return will not decrease its payout when its growth opportunities increase, but a firm with a lower growth rate and a higher expected rate of return on assets is not a general case in the real world. We also find that the duration of future dividend payments is an important determinant of the dividend payout decision, but the effect on the cost of capital is relatively minor.

In the finite growth case, if $(h - k)(T - t) < 1$, then following the Maclaurin expansion, the optimal payout ratio under no change in risk defined in equation (96.26) can be written as

$$
[\bar{D}(t)/\bar{x}(t)] \approx \left( 1 - \frac{h}{a + b \bar{I}} \right) (1 + h(T - t)). \tag{96.28}
$$

The partial derivative of equation (96.28) with respect to the growth rate is

$$
\frac{\partial [\bar{D}(t)/\bar{x}(t)]}{\partial h} \approx \left( \frac{[(a + b \bar{I}) - h](T - t) - h(T - t) - 1}{a + b \bar{I}} \right). \tag{96.29}
$$

Equation (96.29) indicates that the relationship between the optimal dividend payout and the growth rate depends on the firm’s level of growth, the rate of return on assets, and the duration of future dividend payment.
