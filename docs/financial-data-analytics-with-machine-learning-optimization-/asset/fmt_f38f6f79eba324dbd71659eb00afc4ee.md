
where $\omega := \gamma_{V_L} = (1 - \alpha - \beta)V_L$. By recalling the conditional distribution of $u_i \mid \sigma_i = \sigma_i \sim \mathcal{N}(0, \sigma_i^2)$, and abbreviating $\nu_i := \sigma_i^2$, the likelihood function for $\boldsymbol{u} := (u_1, \dots, u_n)$ is

(7.14) $L(\omega, \alpha, \beta; \boldsymbol{u}) = \prod_{i=1}^{n} \frac{1}{\sqrt{2\pi\nu_i}} \exp\left(-\frac{u_i^2}{2\nu_i}\right)$

hence the log-likelihood function is

[(7.15)](#c07.xhtml#R_c07-disp-0020) $\ln L(\omega, \alpha, \beta; \boldsymbol{u}) = -\frac{n}{2}\ln(2\pi) + \frac{1}{2}\sum_{i=1}^{n}\left(-\ln(\nu_i) - \frac{u_i^2}{\nu_i}\right)$

We aim to find the parameters $\omega$, $\alpha$, $\beta$ such that the function

[(7.16)](#c07.xhtml#R_c07-disp-0021) $l(\omega, \alpha, \beta; \boldsymbol{u}) = \sum_{i=1}^{n}\left(-\ln(\nu_i) - \frac{u_i^2}{\nu_i}\right)$

is maximized. Note that the parameters are entered implicitly into function ([7.16](#c07.xhtml#c07-disp-0021)) through $\nu_i$ which satisfies the recursive relation of ([7.13](#c07.xhtml#c07-disp-0018)), so it is a rather complicated maximization problem. Let us illustrate numerically with the HSBC stock data, using $u_i = \frac{S_i - S_{i-1}}{S_{i-1}}$, the percentage change in stock price, to fit a GARCH(1, 1) model and obtain the corresponding MLEs for $\omega$, $\alpha$, $\beta$; see [Programmes 7.15](#c07.xhtml#c07-gra-00015) and [7.16](#c07.xhtml#c07-gra-00016) for Python and `R` codes, respectively.
