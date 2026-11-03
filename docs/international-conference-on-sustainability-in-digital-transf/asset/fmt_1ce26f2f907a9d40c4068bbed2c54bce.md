
1. [Naithani, A., Parashar, B, Bhatia, P. K., and Taneja, G.](#ch45.xhtml#R_ref45_1) (2013). Cost benefit analysis of a 2-out -of -3 induced draft fans system with priority for operation to cold standby over working at reduced capacity. Advanced Modelling and Optimization, 499‑509.

2. [Kumar, A., Garg, D., and Goel, P.](#ch45.xhtml#R_ref45_2) (2019). Mathematical modelling and behavioral analysis of a washing unit in a paper mill. International Journal of System Assurance Engineering and Management, 10(6), 1639‑1645.

3. [Adaramola, B. A.](#ch45.xhtml#R_ref45_3) (2020). A systematic approach of turbo generator performance evaluation maintenance for continuous power generation. Journal of Advancement in Engineering and Technology, 1-5.

4. [Yousefi, N., Tsianikas, S., and Coit, D. W.](#ch45.xhtml#R_ref45_4) (2020). Reinforcement learning for dynamic condition-based maintenance of a system with individually repairable components. Quality Engineering, 32(3), 1-21.

5. [Modibbo, U. M., Arshad, M., Abdalghani, O., and Ali, I.](#ch45.xhtml#R_ref45_5) (2021). Optimization and estimation in system reliability allocation problem. Reliability Engineering & System Safety, Elsevier, 212(C).

6. [Singla, S. and Dhawan, P.](#ch45.xhtml#R_ref45_6) (2022). Mathematical analysis of regenerative point graphical technique (RPGT). A mathematical analysis and its contemporary applications, pp. 49-56.

7. [Singla, S., Verma, S., Malik, S., and Gupta, A.](#ch45.xhtml#R_ref45_7) (2022). Perform ability evaluation, validation and optimization for the steam generation system of a coal-fired thermal plant. Methods X.

8. [Naithani, A., Khanduri, S., and Gupta, S.](#ch45.xhtml#R_ref45_8) (2022). Stochastic analysis of main unit with two non-identical replaceable subunits working with partial failure. International Journal of System Assurance Engineering and Management, 13(3), 1467-1473.

9. [Kumari, S., Singla, S., and Khurana, P.](#ch45.xhtml#R_ref45_9) (2022). Particles swarm optimization for constrained cost reliability of a rubber plant. Life Cycle Reliability and Safety Engineering, 11(3). doi:[10.1007/s41872-022-00199-y](https://doi.org/10.1007/s41872-022-00199-y).

# 46 Analysis of the constant failure density of a component and its reliability

Neeraj Singh^([^(45)](#fn45))

DOI: [10.1201/9781003534136-46](https://dx.doi.org/10.1201/9781003534136-46)

## Abstract

In this manuscript, we must define when the failure rate is constant then the component must be constant throughout the procedure. Only one component is tested and repairable so that the procedure can continue after each failure. The failure rate and the unit hour’s amount to the straight procedure time and define a structure that reliability (unreliability) must either decrease at the same time or must be held constant through the entire procedure.

**Keywords:** Random variable, Probability, Mean time between failures, Failure rate, Failure density

## 1 Introduction

When a component’s projected failure rate remains constant over the course of equivalently lengthy operating periods [[6](#ch46.xhtml#ref46_6)], yet the component is solely susceptible to random failures, its reliability is:

`R(t) = exp(−λt)`

Where `λ` a constant, called the failure rate and `t` is the operating time. The failure rate needs to be stated in `t` hours, typically, and in the same time units. The reciprocal value of the failure rate that we commonly use is the mean time between failures, or `m`.

The MTBF is `m = 1/λ`

The Reliability function can be written as `R(t) = exp(−t/λ)`

As discussed by Reddy [[1](#ch46.xhtml#ref46_1)] a component’s reliability can be ascertained by comparing the proportion of components that pass a test to the total number of components at the beginning of the process. If a fixed number `n[0]` of components are tested there will be, after a time `t`, `n[S](t)` components that survive the procedure and `n[f](t)` components which are failed [[3](#ch46.xhtml#ref46_3)].

Therefore, `n[0] = n[S](t) + n[f](t)` is a constant throughout the procedure ([Tyagi et al., 2015](#ch46.xhtml#ref46_11)). The reliability expressed as a fraction by the probability at any time `t` during the procedure is:

$$R(t) = \\frac{n\_{S}(\\mathbf{t})}{n\_{0}} = \\frac{n\_{S}(t)}{n\_{S}(t) + n\_{f}(t)}$$

According to Sharma et al. [[4](#ch46.xhtml#ref46_4)], the probability of failure (or unreliability) `Q` as

$$Q(t) = \\frac{n\_{f}(t)}{n\_{0}} = \\frac{n\_{F}(t)}{n\_{S}(t) + n\_{f}(t)}$$

It is at once evident that at any time `t`, `R(t) + Q(t) = 1`

### Working Analysis of Failure Data

Results from life tests, which involve testing a large number of models till failure and monitoring the failure rate features over time, can be used to understand the process of failures [[5](#ch46.xhtml#ref46_5), [9](#ch46.xhtml#ref46_9)]. Therefore, is to link reliability with experimental or field-failure data [[[8](#ch46.xhtml#ref46_8)]] the observation on the system at time `t[1]`, `t[2]`, `t[3]`,…, etc. Then we can define the failure density function as follows:

(2.1)

$$f(t) = \\frac{n\_{S}\\left( t\_{i} \\right) - n\_{S}\\left( t\_{i + 1} \\right)}{n\_{0}\\left( {t\_{i + 1} - t\_{i}} \\right)};t\_{i} < t \\leq t\_{i + 1}$$

Zhou and Han [[7](#ch46.xhtml#ref46_7)] and Wenjuan [[10](#ch46.xhtml#ref46_10)] shows that failure rate over the interval `t[i] < t ≤ t[i][+1]` is defined as the ratio of the number of failures occurring in the time interval to the number of survivors at the beginning of the time interval, divided by the length of the time interval. It is determined as the number of failures occurring in the interval to the size of the original population divided by the length of the interval.

(2.2)

$$\\lambda(t) = \\frac{n\_{S}\\left( t\_{i} \\right) - n\_{S}\\left( t\_{i + 1} \\right)}{n\_{S}\\left( t\_{i} \\right)\\left( {t\_{i + 1} - t\_{i}} \\right)};t\_{i} < t < t\_{i + 1}$$

Whereas, `λ(t)` measures the instantaneous speed of failures, the failure density function `f(t)` measures the overall speed at which failures are occurring.

![](images/fig46_292_1_C.jpg)

## Numerical Discussion of Failure Data Analysis

The failure data for a component in time is:

| **Failure no.** || 1 || 2 || 3 || 4 || 5 || 6 || 7 || 8 || 9 || 10 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **Operating time** || 8 || 15 || 18 || 22 || 27 || 32 || 38 || 42 || 48 || 56 |

Table 46.1 Computation of failure density and

| Time interval (hrs.) || Failure density || Failure rate |
| --- | --- | --- |
| 0-8 || 0.0125 || 0.0125 |
| --- | --- | --- |
| 8-15 || 0.0079 || 0.0088 |
| 15-18 || 0.0067 || 0.0091 |
| 18-22 || 0.0079 || 0.0114 |
| 22-27 || 0.0054 || 0.0093 |
| 27-32 || 0.0039 || 0.0082 |
| 32-38 || 0.0035 || 0.0095 |
| 38-42 || 0.0028 || 0.0106 |
| 42-48 || 0.0017 || 0.0106 |
| 48-56 || 0.0018 || 0.0120 |

![Figure 46.1 Difference between failure density and failure rate](images/fig46_1_C.jpg)

Figure 46.1 Difference between failure density and failure rate

## Conclusion and Future Work

We must measure the constant failure rate of a component population conveniently and measuring a constant failure rate is to keep the number of components in the procedure constant by immediately replacing the failed components with good ones also the number of alive components `N[S](t)` is then equal to `N[0]` throughout the procedure. Of course, this procedure for determining the failure rate can be applied only if `λ` is constant.

## Acknowledgment

I would like to sincerely appreciate and express my gratitude to Prof. D K Ghosh and Prof. Ashok Kumar for their insightful advice, which helped us to conduct present work.

## Author Contribution
