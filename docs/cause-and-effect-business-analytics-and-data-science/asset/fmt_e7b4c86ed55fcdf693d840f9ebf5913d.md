
The simplest and perhaps most well-known Test and Learn process is *A/B Testing*, where two treatments (treatment versus control or treatment A versus B) are compared in a test. For example, A/B Testing is frequently used in online advertising, where two methods of promotion are compared in a randomized test (see, e.g., [Kohavi et al. 2012](#chapter7.xhtml#ref7_19)). Measuring whether A or B is Page 158a better treatment is the fundamental step. Modeling (Uplift Modeling) will take it to the next level to determine the right treatment for the right targets. A/B Testing compares only two treatments at a time, and if more treatments are available, the winner of each comparison can compete with other treatments, and so on in a sequential fashion (see, e.g., [Goward 2013](#chapter7.xhtml#ref7_14), [McFarland 2013](#chapter7.xhtml#ref7_29), or [Siroker and Koomen 2013](#chapter7.xhtml#ref7_37) in the marketing context). More discussion on A/B Testing is presented in [Section 7.2.4](#chapter7.xhtml#sec7_2_4), and advanced methods of testing multiple treatments simultaneously will be discussed in [Section 7.2.5](#chapter7.xhtml#sec7_2_5).

## 7.2.3 Sampling and Sample Size Determination
In order to develop uplift models, we need to have random treatment and random control groups, and ideally, they are a random sample or a good representative sample of the larger relevant population. The most commonly used sampling schemes in business are simple random sampling and stratified random sampling (see classical texts such as [Scheaffer et al. 1990](#chapter7.xhtml#ref7_36), or [Cochran 1977](#chapter7.xhtml#ref7_8), for details). Both are straightforward to implement using common campaign software packages or statistical software. Stratified random sampling is helpful in guaranteeing enough subsamples for each subpopulation and is particularly useful when the subpopulations are relatively small. In the following [Subsections 7.2.3.1](#chapter7.xhtml#sec7_2_3_1) and [7.2.3.2](#chapter7.xhtml#sec7_2_3_2), we mainly focus on sample size determination in the context of uplift analytics. On a similar topic, [Section 7.2.4](#chapter7.xhtml#sec7_2_4) discusses randomization *between* treatment and control.

### 7.2.3.1 Standard Sample Size Determination
We revisit the standard method for sample size determination for two proportions in this subsection. Assume we have two population proportions `p1` and `p2` (for two target groups 1 versus 2, or for treatment versus control), and the pair of hypotheses

Table 7.1 Definitions of Type I and Type II Errors (and Their Probabilities of Occurrence, `α` and `β`) in Hypothesis Testing [⏎](#chapter7.xhtml#b7tbl7_1)

|  || Do Not Reject `H0` || Reject `H0` |
| --- | --- | --- |
| If `H0` is true || Correct decision (1−`α`) ☺ || Type I error (`α`) ☹[false negative] |
| --- | --- | --- |
| If `H0` is not true || Type II error (`β`) ☹[false positive] || Correct decision (1 − `β`) ☺ |

Page 159It can be shown that, given the values of `α` and `β`, the sample sizes `n1` and `n2`, would satisfy:

$$
\frac{\left( {p_{1} - p_{2}} \right)^{2}}{\left( {z_{\alpha} + z_{\beta}} \right)^{2}} = \frac{p_{1}\left( {1 - p_{1}} \right)}{n_{1}} + \frac{p_{2}\left( {1 - p_{2}} \right)}{n_{2}},
$$

(7.1)

where `z[α]` and `z[β]` are `Φ^{(-1)}(1−α)` and `Φ^{(-1)}(1−β)`, respectively, representing the standard normal critical values associated with the Type I and Type II errors. For example, if `α` = 0.05, `z[α]` = 1.645, and if `β` = 0.20, `z[β]` = 0.842.

If `n1` = `n2` = `n`, then with some algebraic manipulation of Eqn. (7.1), the minimum sample size would follow the standard formula:

$$
n = \frac{\left( {z_{\alpha} + z_{\beta}} \right)^{2}\left[ p_{1}\left( {1 - p_{1}} \right) + p_{2}\left( {1 - p_{2}} \right) \right]}{\left( {p_{1} - p_{2}} \right)^{2}}~
$$

(7.2a)

Alternatively, if `n1` is given, we can determine the minimum sample size for the second group, again from Eqn. (7.1):

$$
n_{2} = ~\frac{p_{2}\left( {1 - p_{2}} \right)}{\frac{\left( {p_{1} - p_{2}} \right)^{2}}{\left( {z_{\alpha} + z_{\beta}} \right)^{2}} - ~\frac{p_{1}\left( {1 - p_{1}} \right)}{n_{1}}}
$$

(7.2b)

The derivation of Eqns. (7.1), (7.2a), and (7.2b) can be found in most standard statistics books and will be omitted here. Equation (7.2a) is easy to apply provided that some reasonable estimates of the two population proportions, `p1` and `p2`, are available. It is also implemented in standard sample-size tools such as nQueryAdvisor. To estimate the proportions, if historical data are not available, the usual practice is to use sensitivity analysis with a reasonable range of values to arrive at a range of minimum sample sizes and select the largest sample size from the range. See [Mathews (2010)](#chapter7.xhtml#ref7_28) for determining sample sizes in a variety of situations.

### 7.2.3.2 Sample Size Determination for Uplift Analytics
For Uplift/True-lift analytics, we need to address the difference between treatment and control. Additionally, we may want to know if there is a difference in lift (treatment minus control) by some demographic group. As in [Section 7.2.3.1](#chapter7.xhtml#sec7_2_3_1), let's suppose we have two population groups (e.g., older and younger age groups, male and female, or higher versus lower income groups) and a treatment and control split within each group, which means we have four groups to handle. We now generalize the formulas in [Section 7.2.3.1](#chapter7.xhtml#sec7_2_3_1) to handle a four-group proportion comparison.

Page 160Our objective is to determine appropriate sample sizes that allow us to statistically test whether the (treatment minus control) lift in group 1 is equal to or better than the lift in group 2, which leads to the following pair of hypotheses:

`H0`: `p1t` − `p1c` = `p2t` − `p2c` and `H1`: `p1t` − `p1c` > `p2t` − `p2c`

where `p1t`, `p1c`, `p2t`, and `p2c` are response rates in group 1's treatment subgroup, group 1's control subgroup, group 2's treatment subgroup, and group 2's control subgroup, respectively. Rejection of `H0` would indicate that the demographic split between the two groups is effective in differentiating between higher and lower lift. For simpler notation, we can rewrite the above hypotheses as:

`H0`: Δ`p1` = Δ`p2` and `H1`: Δ`p1` > Δ`p2`,

where Δ denotes the lift (incremental difference) between treatment and control. It can be shown (in [Appendix 7.1)](#chapter7.xhtml#app7_1) that:

Power = Probability of detecting a difference given that `H1` is true

$$
= 1 - \,\text{P}\,\left( \text{Type~II~Error} \right) = 1 - \Phi\left( {z_{\alpha} - \frac{\left( {\Delta p_{1} - \Delta p_{2}} \right)}{I}} \right)
$$

(7.3)

where (Δ`p1` − Δ`p2`) is estimated by its sample estimate, (Δ`p̂1` − Δ`p̂2`).

Define `J` = `p̂1t`(1−`p̂1t`) + `p̂1c`(1−`p̂1c`)`R1` + `p̂2t`(1−`p̂2t`)`Rt` + `p̂2c`(1−`p̂2c`)`Rt``R2`,

(7.4)

where the following ratios chosen by the analyst are input parameters to the sample design:

$$
R_{1} = \frac{n_{1t}}{n_{1c}},~~~~R_{2} = \frac{n_{2t}}{n_{2c}},~~~~and~{~R}_{t} = \frac{n_{1t}}{n_{2t}}
$$

(7.5).

In Eqn. (7.5), `R1` is the ratio of treatment to control in Group 1, `R2` is the ratio of treatment to control in Group 2, and `Rt` is the ratio of Group 1 to Group 2 among those in treatment.

Then `n1t`, `n1c`, `n2t`, and `n2c` can be obtained as follows:
