
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 || 4,180 || 0.041 || 0.034 || 0.09073 || −0.03386 || 1 || 4,180 || – || 4,180 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2 || 5,650 || 0.041 || 0.038 || −0.00144 || \-0.06767 || 1 || – || – || – |
| 4 || 60,220 || 0.011 || 0.011 || 0.04790 || 0.04521 || 1 || 11,280 || – || 11,280 |
| 5 || 12,370 || 0.029 || 0.027 || 0.08154 || 0.01754 || 1 || 12,370 || – || 12,370 |
| 6 || 8,940 || 0.022 || 0.023 || 0.03109 || 0.03887 || 1 || – || – || – |
| 7 || 29,240 || 0.016 || 0.015 || 0.02632 || −0.00296 || 1 || – || – || – |
| 8 || 28,070 || 0.017 || 0.016 || 0.05868 || −0.00057 || 1 || 28,070 || – || 28,070 |
| 9 || 4,100 || 0.055 || 0.048 || 0.13404 || −0.05485 || 1 || 4,100 || – || 4,100 |
| 10 || 37,080 || 0.012 || 0.011 || 0.03800 || 0.02419 || 1 || – || – || – |
| Total || 189,850 ||  ||  ||  ||  || obj value || 4,125 || – || 4,125 |
|   ||  ||  ||  ||  ||  || Cost || $60,000 || $ || $60,000 |
|   ||  ||  ||  ||  ||  || Budget ||  ||  || $60,000 |
`TABLE 8.6b` Linear Programming Computations Using Cluster-level “Worst” Lift Values: Using Bootstrapping [⏎](#chapter8.xhtml#b8tbl8_6b)

| Cluster || Cluster Size in New Data || 5th Percentile of Men's || 5th Percentile of Women's || Cost per Treatment ($) || Decision var on Number of Men's || Decision var on Number of Women's || Total Number of Treated by Cluster |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 || 4,180 || 0.11048 || −0.02982 || 1 || 4,180 || – || 4,180 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 2 || 5,650 || −0.01111 || −0.05751 || 1 || – || – || – |
| 4 || 60,220 || 0.04894 || 0.047102 || 1 || 11,280 || – || 11,280 |
| 5 || 12,370 || 0.07908 || 0.012833 || 1 || 12,370 || – || 12,370 |
| 6 || 8,940 || 0.03861 || 0.044034 || 1 || – || – || – |
| 7 || 29,240 || 0.02547 || −0.00449 || 1 || – || – || – |
| 8 || 28,070 || 0.0611 || 0.000176 || 1 || 28,070 || – || 28,070 |
| 9 || 4,100 || 0.12311 || −0.05429 || 1 || 4,100 || – || 4,100 |
| 10 || 37,080 || 0.04383 || 0.028138 || 1 || – || – || – |
| Total || 189,850 ||  ||  || obj value || 4,212 ||  || 4,212 |
|   ||  ||  ||  || cost || $60,000 || $ || $60,000 |
|   ||  ||  ||  || Budget ||  ||  || $60,000 |

### 8.5.3 Stochastic Programming (SP)

`Stochastic Programming` (`SP`) directly addresses any uncertainty through probability distributions as opposed to employing a pessimistic scenario as in `RO` or managing variances as in `MVO`. Because of its combination of a wide range of applications and strong and established theories, `SP` itself is a key subfield of optimization theory and Operations Research and has been around for many decades – one of the earliest contributions is from [Dantzig (1955)](#chapter8.xhtml#ref8_8). For further study, see [Wallace and Ziemba (2005)](#chapter8.xhtml#ref8_36), [Cornuejols and Tutuncu (2007)](#chapter8.xhtml#ref8_7), [Zenios (2007)](#chapter8.xhtml#ref8_38), or [King and Wallace (2012)](#chapter8.xhtml#ref8_20) for practical introductions and applications, and [Birge and Louveaux (1997)](#chapter8.xhtml#ref8_4) or [Shapiro et al. (2014)](#chapter8.xhtml#ref8_30) for the more mathematically inclined. We will discuss techniques from `SP` that are most relevant and practical to uplift optimization.

Considering again `model (8.7)` in [`Section 8.2.2`](#chapter8.xhtml#sec8_2_2), one may impose an additional probability constraint to “guarantee” that a given result is achieved with a certain probability (known as chance constraint optimization, a branch of `SP`):

$$Maximize~{\\sum\\limits\_{c = 1}^{C}{\\sum\\limits\_{j = 1}^{m}{{~ \\bigtriangleup \\hat{p}}\_{cj~}x\_{cj}}}}$$  

(8.13)

Page 239subject to:

1.  $P\\left( {{\\sum\\limits\_{c = 1}^{C}{\\sum\\limits\_{j = 1}^{m}{{~ \\bigtriangleup p}\_{cj~}x\_{cj}}}}~ \\geq a} \\right) \\geq b,$ Probability Constraint (0≤*b*≤1),
2.  ${\\sum\\limits\_{c = 1}^{C}{\\sum\\limits\_{j = 1}^{m~}{{c\_{j}x}\_{cj~} \\leq Budget,}}}~Budget~Constraint,$
3.  ${\\sum\\limits\_{j = 1}^{m}{x\_{cj~} \\leq N\_{c},~for~c = 1,\\ldots,C,~}}~Cluster~Size~Constraint,~and$
4.  *x*[*c**j* ] ≥ 0, *c* = 1, …, *C*; *j* = 1, …, *m*.

Alternatively, rather than maximizing the estimated (mean) number of incremental responders, one may be interested in maximizing the probability of achieving a given number of incremental responders:

$$Maximize~P\\left( {{\\sum\\limits\_{c = 1}^{C}{\\sum\\limits\_{j = 1}^{m}{{~ \\bigtriangleup p}\_{cj~}x\_{cj}}}}~ \\geq ~z\_{0}} \\right)$$  

(8.14)

subject to (as before):

1.  ${\\sum\\limits\_{c = 1}^{C}{\\sum\\limits\_{j = 1}^{m~}{{c\_{j}x}\_{cj~} \\leq Budget,}}}~Budget~Constraint,$
2.  ${\\sum\\limits\_{j = 1}^{m}{x\_{cj~} \\leq N\_{c},~for~c = 1,\\ldots,C,~}}~Cluster~Size~Constraint,~and$
3.  *x*[*c**j* ] ≥ 0, *c* = 1, …, *C*; *j* = 1, …, *m*.

Furthermore, one may even change the objective function to another probability-related function, such as an *α*th percentile (also known as Value-at-Risk or `VaR`

$$Maximize~the~\\alpha~th~percentile~of~{\\sum\\limits\_{c = 1}^{C}{\\sum\\limits\_{j = 1}^{m}{{~ \\bigtriangleup p}\_{cj~}x\_{cj}}}},$$  

(8.15)

while keeping the same set of constraints in `Eqn. (8.14)`.

Page 240On the surface, `model (8.15)` looks similar to the Robust Optimization (`RO`) `model (8.11)`. In fact, they are different because `model (8.11)` ignores the dependency structure (correlations) among the lift values   △ *p*[*c**j* ]. For example, if two of the lift values are very negatively correlated, the chance that *both* of them will achieve their respective lower bound (say, 5th percentile) is very low. As a result, `model (8.11)` is more conservative than `model (8.15)` as the latter takes into account the dependency structure of the lift values.

Note that, unlike `LP` problems for deterministic optimization or even quadratic programming problems for `MVO`, `models`, `Eqns. (8.13)–(8.15)` may not satisfy the convexity property (see [`Appendix 8.1`](#chapter8.xhtml#app8_1)) and thus cannot guarantee global optima. Nevertheless, good heuristics are available to solve them, attempting to achieve some “good enough” solutions even though global optima are not guaranteed. See [`Appendix 8.2`](#chapter8.xhtml#app8_2) for A Brief Introduction to Simulation Optimization, a relatively simple technique employed in [`Example 8.3c`](#chapter8.xhtml#sec8_5_3_1).

#### `Example 8.3c (Continuation of Example 8.3b)`

We now include a probability constraint in the original model in [`Table 8.1`](#chapter8.xhtml#tbl8_1). Using Oracle's Crystal Ball (`CB`),

Knowing that the optimal solution in [`Example 8.1`](#chapter8.xhtml#sec8_3_1) results in 6,453 expected incremental responders (using the sample mean lift values), we now would want to have some guarantee that the actual number of incremental responders would be at least a given reasonably high quantity. Applying `model (8.13)`, the following probability constraint is included to have an 80% probability that at least 5,500 incremental responders are achieved:

*P*(*n**o*. *o**f* *i**n**c**r**e**m**e**n**t**a**l* *r**e**s**p**o**n**d**e**r**s*≥5,500) ≥ 0.80,  

$$i.e.,~P\\left( {{\\sum\\limits\_{c = 1}^{C}{\\sum\\limits\_{j = 1}^{2}{{~ \\bigtriangleup p}\_{cj~}x\_{cj}}}}~ \\geq 5,500} \\right) \\geq 0.80,$$  

*w**h**e**r**e* *C* = *n**u**m**b**e**r* *o**f* *c**l**u**s**t**e**r**s*,  while keeping the same objective and other constraints in [`Example 8.1`](#chapter8.xhtml#sec8_3_1).

See [`EPM Information Development Team (2009)`](#chapter8.xhtml#ref8_13) for details on how to use the `CB` software. The solution

`Table 8.7` Probability Constrained Optimization – Summary of Results [⏎](#chapter8.xhtml#b8tbl8_7)

| Cluster || Cluster Size in New Data || Obs. Lift in Response: Men's || Obs. Lift in Response: Women's || Cost per Treatment ($) || Decision var on Number of Men's || Decision var on Number of Women's || Total Number of Treated by Cluster |
