# 29.2.2.1 *Bipower variation tests*

Under the assumption of equation (29.1), equation (29.6) shows that if the theoretical integrated volatility can be properly estimated, jumps can be measured using the difference between QV and realized integrated volatility. This is the key idea underpinning bipower variation-based tests. Barndorff-Nielsen and Shephard (2004) suggest using bipower variation to estimate integrated volatility. Barndorff-Nielsen and Shephard (2006a) propose various bipower variation-based jump test statistics.

The quadratic variation defined in equation (29.3) is a special case of power variation. Additionally, sth power variation is defined as

$\{Y\}_t^{[s]} = p \lim_{\delta \to 0} \delta^{1 - s/2} \sum_{i=1}^{t/\delta} |r_{i,t}|^s,$

where $s > 0$. The bipower variation process is defined as

$\{Y\}_t^{[s_1,s_2]} = p \lim_{\delta \to 0} \delta^{1 - (s_1 + s_2)/2} \sum_{i=1}^{[t/\delta] - 1} |r_{i,t}|^{s_1} |r_{i+1,t}|^{s_2},$

where $s_1, s_2 > 0$. When $s_1 = s_2 = 1$, $\{Y\}_t^{[1,1]}$ can be consistently estimated using realized bipower variation (BV), defined as follows:

$BV_t = \{Y_\delta\}_t^{[1,1]} = \sum_{i=2}^{[t/\delta]} |r_{i-1,t}| |r_{i,t}|. \quad (29.7)$

Barndorff-Nielsen and Shephard (2004) show that the power variation and bipower variation can be expressed as

$\mu^{-1} \{Y\}_t^{[s]} = \begin{cases} \int_0^t \sigma_u^s du & s \in (0,2), \\ [Y]_t & s = 2, \\ \infty & s > 2, \end{cases}$

and

$\mu_{s_1}^{-1} \mu_{s_2}^{-1} \{Y\}_t^{[s_1,s_2]} = \begin{cases} \int_0^t \sigma_u^{s_1 + s_2} du & \max(s_1,s_2) \in (0,2), \\ x_t^* & \max(s_1,s_2) = 2, \\ \infty & \max(s_1,s_2) > 2, \end{cases}$

where $x_t^*$ is some stochastic process.