
L. Stentoft (2008). American Option Pricing Using GARCH Models and the Normal Inverse Gaussian Distribution. *Journal of Financial Econometrics*, 6(4), 540-582.

G. C. G. Wei and M. A. Tanner (1990). A Monte Carlo Implementation of the EM Algorithm and the Poor Man's Data Augmentation Algorithms. *Journal of the American Statistical Association*, 85, 699-704.

## Appendix 70A: Proof of Lemma 70.2.1

From (70.8), the mean of the log-return $E(Y_t \mid \mathcal{F}_{t-1}) = m + \phi_t + \theta \nu_t$, and

$Y_t - E(Y_t) = [Y_t - E(Y_t|\mathcal{F}_{t-1})] + [E(Y_t|\mathcal{F}_{t-1}) - E(Y_t)]$
$= [\theta(g_t - \nu_t) + \varepsilon_t] + [\theta(\nu_t - E(\nu_t))].$
(70A.1)

As the random time-change $g_t$ is conditionally gamma-distributed with shape parameter $\nu_t$ and scale parameter one, the variance, skewness, and kurtosis of the random time change $g_t$ are $\nu_t$, $2/\sqrt{\nu_t}$ and $6/\nu_t$, respectively. The 2nd, 3rd, and 4th conditional moments are

$E[(Y_t - E(Y_t|\mathcal{F}_{t-1}))^2|\mathcal{F}_{t-1}] = (\theta^2 + \sigma^2)\nu_t,$
$E[(Y_t - E(Y_t|\mathcal{F}_{t-1}))^3|\mathcal{F}_{t-1}] = E[\theta^3(g_t - \nu_t)^3 + 3\varepsilon_t^2\theta(g_t - \nu_t)|\mathcal{F}_{t-1}]$
$= (2\theta^3 + 3\theta\sigma^2)\nu_t,$
$E[(Y_t - E(Y_t|\mathcal{F}_{t-1}))^4|\mathcal{F}_{t-1}] = \theta^4E[(g_t - \nu_t)^4|\mathcal{F}_{t-1}] + (6\theta^2\sigma^2 + 3\sigma^4)$
$\nu_t^2 + 3\sigma^4\nu_t = (6\theta^2\sigma^2 + 3\sigma^4)\nu_t^2 + [3\sigma^4 + 6\theta^4 + 12\theta^2\sigma^2]\nu_t.$

The 2nd, 3rd, and 4th unconditional moments are

$E[(Y_t - E(Y_t))^2] = (\theta^2 + \sigma^2)E(\nu_t) + \theta^2\operatorname{Var}(\nu_t),$ (70A.2)
$E[(Y_t - E(Y_t))^3] = (2\theta^3 + 3\theta\sigma^2)E(\nu_t) + 3\theta(\theta^2 + \sigma^2)\operatorname{Var}(\nu_t)$
$+ \theta^3E[(\nu_t - E(\nu_t))^3],$ (70A.3)
$E[(Y_t - E(Y_t))^4] = \{6\theta^2\sigma^2 + 3\sigma^4\}E(\nu_t^2) + [3\sigma^4 + 6\theta^4 + 12\theta^2\sigma^2]E(\nu_t)$
$+ 6\theta^2(\theta^2 + \sigma^2)\{E(\nu_t^3) + [E(\nu_t)]^3 - 2E(\nu_t)E(\nu_t^2)\}$
$+ 4(2\theta^4 + 3\theta^2\sigma^2)\operatorname{Var}(\nu_t) + \theta^4E[(\nu_t - E(\nu_t))^4].$ (70A.4)

The unconditional skewness and kurtosis in (70.13) and (70.14) can be obtained directly from (70A.2)–(70A.4) and the definitions of skewness and kurtosis, respectively.

## Appendix 70B: Proof of Lemma 70.2.2

In (70.8), rewrite the innovation ε_t = σ√g_t z_t, where z_t is a standard normal random variable that is independent of the random time-change g_t, 1 ≤ t ≤ T. Then the shape parameter ν_t in (70.11) becomes

ν_t = a_0 + aσ²ν_{t-1} (z_{t-1}√{g_{t-1}/ν_{t-1}} - c/σ)² + bν_{t-1} = a_0 + W_{t-1}ν_{t-1}
= a_0{1 + W_{t-1} + W_{t-1}W_{t-2} + ⋯} + (∏_{i=0}^{t-2} W_{t-i}) ν_1, (70B.1)

where W_t = aσ²(z_t√{g_t/ν_t} - c/σ)² + b. As the random time-change g_t is gamma-distributed with shape parameter ν_t, thus E(g_t|ℱ_{t-1}) = ν_t. In addition, as z_t is a standard normal random variable, thus E(z_t²) = 1. It follows that:

E[ (z_t√{g_t/ν_t} - c/σ)² | ℱ_{t-1} ] = 1 + (c/σ)².

And E(W_t|ℱ_{t-1}) = a(σ² + c²) + b. By (70A.5), E(ν_{t+1}) = E{ E(ν_{t+1}|ℱ_t) | ℱ_{t-1}) … | ℱ_0 }, thus

E(ν_{t+1}) = a_0 ∑_{i=0}^{t-1} (a(σ² + c²) + b)^i + (a(σ² + c²) + b)^t ν_1.

As t → ∞, if a_0 > 0 and a(σ² + c²) + b < 1, one has the stationary shape parameter ν_∞

ν_∞ = lim_{t→∞} E(ν_{t+1}) = a_0[1 - (σ² + c²)a - b]^{-1}

and the lemma is proved.

## Appendix 70C: Proof of Lemma 70.3.1

For the VG NGARCH model in (70.8)–(70.12), the logarithm of joint likelihood L(Θ|g,Y) is

-T ln σ + ∑_{t=1}^{T} { -(Y_t - m - φ_t - θ g_t)² / (2σ² g_t) }
+ ∑_{t=1}^{T} { (ν_t - 1.5) log(g_t) - g_t - log(Γ(ν_t)) } + C,

where $\boldsymbol{Y} = (Y_1,\dots,Y_T)'$ are log-returns and $\boldsymbol{g} = (g_1,\dots,g_T)'$ are random time-changes, $\boldsymbol{\Theta} = (\theta,\sigma,\nu_1,\alpha)'$ denote the vector of unknown drift parameter $\theta$, the volatility $\sigma$, the initial shape parameter $\nu_1$, the NGARCH parameters $\alpha = (a_0,a,b,c)$ in (70.11), respectively. Note the constant $C = -T\log\sqrt{2\pi}$. Define

$$\varpi = \frac{\theta^2}{2\sigma^2} + 1 \quad \text{and}\quad \delta_t = \frac{(Y_t - \bar{Y} - \varphi_t)^2}{2\sigma^2}.$$

Then the joint likelihood $L(\boldsymbol{\Theta}|\boldsymbol{g},\boldsymbol{Y})$ can be rewritten as

$$\begin{aligned}
 -T\ln\sigma - \sum_{t=1}^{T} \delta_t/g_t - \sum_{t=1}^{T} \varpi g_t + \sum_{t=1}^{T} \left\{\frac{\theta(Y_t - m - \varphi_t)}{\sigma^2}\right\}
\ + \sum_{t=1}^{T} \{ (\nu_t - 1.5)\log(g_t) - \log(\Gamma(\nu_t)) \} + C.
\end{aligned}$$

Since the posterior distribution

$$p(\boldsymbol{g}|\boldsymbol{Y};\boldsymbol{\Theta}) = \frac{\exp(\mathcal{L}(\boldsymbol{\Theta}|\boldsymbol{g},\boldsymbol{Y}))}{\int \exp(\mathcal{L}(\boldsymbol{\Theta}|\boldsymbol{g},\boldsymbol{Y})) d\boldsymbol{g}}. \qquad (70C.2)$$

Note any term in the joint likelihood $L(\boldsymbol{\Theta}|\boldsymbol{g},\boldsymbol{Y})$ that do not involve the random time-changes $\boldsymbol{g} = (g_1,\dots,g_T)'$ will be canceled out in (70C.2). One has the posterior distribution

$$p(\boldsymbol{g}|\boldsymbol{Y};\boldsymbol{\Theta}) \propto \prod_{t=1}^{T} \exp\big(-\varpi g_t - \delta_t/g_t + (\nu_t - 1.5)\log(g_t)\big)$$

and the lemma is proved.

This page intentionally left blank

## Chapter 71

### Why do Smartphone and Tablet Users Adopt Mobile Banking?

Veronika Belousova and Nikolay Chichkanov

### Contents
- 71.1 Introduction . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2462
- 71.2 Literature Review . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2464
- 71.3 Research Model and Hypothesis . . . . . . . . . . . . . . . . . . . . 2466
- 71.4 Methodology and Data Collection . . . . . . . . . . . . . . . . . . 2471
- 71.5 Results and Discussion . . . . . . . . . . . . . . . . . . . . . . . . 2473
- 71.6 Conclusion . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2477
- Acknowledgments . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2478
- Bibliography . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 2479
- Appendix 71A: Items and Sources . . . . . . . . . . . . . . . . . . . . . 2482
- Appendix 71B: Reliability and Validity . . . . . . . . . . . . . . . . . 2483

### Abstract

Purpose: Increased penetration of mobile phones has built great opportunities for increasing the level of financial inclusion around the world. Digital channels help banks in not only attracting new customers but also in ensuring that the existing ones remain loyal. This chapter studies the incentives to encourage the use of mobile banking by smartphone and tablet users.

**Design/methodology/approach:** An online survey is conducted to explore possible relations between the potential determinants of the intention to use mobile banking. The model is assessed with Partial Least Squares Structural Equation Modelling (PLS-SEM) technique.

**Findings:** The results show that perceived usefulness and perceived efforts tend to be the most significant factors in the adoption of mobile banking. However, such factors as perceived risks, compatibility with lifestyle and social influence are found to be insignificant due to some cultural and institutional features attributed to CIS countries.

**Originality/value:** This chapter contributes to the field of m-banking studies by focusing on both smartphone and tablet users. At least, the majority of respondents represent Y and Z generations who seem to move from traditional banking to digital channels.

### Keywords

Mobile banking ● Technology acceptance ● User adoption ● Intention.

### 71.1 Introduction

In recent decades, information communication technologies have expanded rapidly and provided great opportunities for innovations in delivering financial services (Prause and Thurner, 2014). Since the late 1970s, most banking operations with the advent of computers have become computerized “for reasons of speed, accuracy and economy” (Oliveira and von Hippel, 2011, p. 806). For the same reasons, banks have exploited computers as a channel for interacting with their clients. As a result, many bank customers have moved from traditional banking to online banking. Mobile banking, as a part of online banking services, is considered one of the most important technological innovations (Lin, 2011; van der Boor et al., 2014).

The prospects of m-banking are fascinating. Nowadays, mobile devices have become extremely popular. According to the International Telecommunication Union, the number of mobile-cellular telephone subscribers in 2017 exceeded the global population (103.5 subscriptions per 100 inhabitants) (ITU, 2018). However, only half of the world population had access to traditional banking services (Shaikh and Karjaluoto, 2015). Opportunities to retain the existing customers and attract new ones encourage banks to use this channel to build sustained relationships with customers.

Actually, several advantages for banks and customers push the development of m-banking channels from traditional banking services like money transactions towards unique mobile content as personal savings plans with a linkage to the fitness activity. The growth of mobile banking is leveling off, but the use of branches is declining very slowly. One of the biggest challenges is to organize the migration of customers to digital channels (Bain &
