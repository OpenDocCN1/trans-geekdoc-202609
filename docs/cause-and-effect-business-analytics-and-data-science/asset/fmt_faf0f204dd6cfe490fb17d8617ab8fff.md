
### 4. R-learner
This method employs cross validation with a specific loss function to be minimized after adjusting for an outcome model and a propensity score model, see `Nie and Wagner (2021)` for details.

### 5. Doubly Robust (DR) learner
This methodology estimates both the propensity score and the outcome model and is effective if at least one of them is correct. This approach is an extension of the DR method for estimating average treatment effect and is particularly useful when the data are observational (i.e., non-experimental), see [Kennedy (2023)](#chapter9.xhtml#ref9_21) for details.

## Appendix 9.1: Proof of the Four Quadrant Method – Modifying the Lai Method with Addition of Probability Weights
Consider the 2 × 2 table in [Figure 9.1](#chapter9.xhtml#fig9_1b). Define our estimation objective (i.e., lift) as a function of covariates `x`:
`Z(x)` ≡ `P(R|T,x)` – `P(R|C,x)`, where `R` = event of response. `Z(x)` is the response probability difference (lift) between the treatment and control groups given a set of characteristics, `x`. It can be re-expressed as follows.
`Z(x)` = `P(R|T,x)`− (1−`P(N|C,x)`), where `N` = no response
= `P(R|T,x)`+ `P(N|C,x)` − 1
$$= \\frac{P\\left( {TR} \\middle| x \\right)}{P\\left( T \\middle| x \\right)} + \\frac{P\\left( {CN} \\middle| x \\right)}{P\\left( C \\middle| x \\right)} - 1,~by~Bayes^{'}rule$$
$$= \\frac{P\\left( {TR} \\middle| x \\right)}{P\\left( T \\right)} + \\frac{P\\left( {CN} \\middle| x \\right)}{P\\left( C \\right)} - 1,$$
(A9.1)
Page 280due to randomization of treatment and control, that is, assignment of treatment/control is random and does not depend on `x`. Note that Eqn. (A9.1) indicates that `P(TR|x)` and `P(CN|x)` have positive contributions to the lift.
Similarly, if we look at `Z(x)` in another way,
`Z(x)` = (1−`P(N|T,x)`) − `P(R|C,x)`
$$= 1 - \\frac{P\\left( {TN} \\middle| x \\right)}{P\\left( T \\right)} - \\frac{P\\left( {CR} \\middle| x \\right)}{P\\left( C \\right)},$$
(A9.2)
where Eqn. (A9.2) indicates that `P(TN|x)` and `P(CR|x)` have negative contributions to the lift.
Note that Eqns. (A9.1) and (A9.2) are the same equations except that we are expressing them differently. Adding Eqns. (A9.1) and (A9.2) together, we have:
$$2Z\\left( x \\right) = \\frac{P\\left( {TR} \\middle| x \\right)}{P\\left( T \\right)} + \\frac{P\\left( {CN} \\middle| x \\right)}{P\\left( C \\right)} - \\frac{P\\left( {TN} \\middle| x \\right)}{P\\left( T \\right)} - \\frac{P\\left( {CR} \\middle| x \\right)}{P\\left( C \\right)},or~$$
$$\\frac{~P\\left( C \\right)\\left( P\\left( {TR} \\middle| x \\right) - P\\left( {TN} \\middle| x \\right) \\right) + P\\left( T \\right)\\left( {P\\left( {CN} \\middle| x \\right) - P\\left( {CR} \\middle| x \\right)} \\right)}{P\\left( T \\right)P\\left( C \\right)}~$$
(A9.3)
Quite often, marketing programs have a larger sample in the treatment group than the control group; that is, `P(C)` < `P(T)`, as marketers often aim at gaining more revenue by contacting more individuals. It can be easily shown that [Lai (2006)](#chapter9.xhtml#ref9_23)'s method is a special situation where `P(T)` = `P(C)` = 0.5, which is not mathematically correct in general cases. However, [Lai (2006)](#chapter9.xhtml#ref9_23) also proposed using a weight based on empirical findings, but, in fact, there is a simple mathematical equation as shown in Eqn. (A9.3). Note that although this method has the same mathematical objective as Methods A1 and A2, that is, maximizing `P(R|T)` – `P(R|C)`, empirically, because of the different estimation methods, it results in different estimates.

## Appendix 9.2: Computations of Weighted Gini Coefficient and Weighted Top 15% Gini for Non-Randomized Data
This appendix is a generalization of [Appendix 6.1](#chapter6.xhtml#app6_1), that is, extending the randomized data to the non-randomized data situation, where weights are available for adjustment. As in [Appendix 6.1](#chapter6.xhtml#app6_1), assume we rank the `holdout` sample Page 281by semi-decile, that is, 20 groups with 5% in each group. Define the average lift at group `j` as:
`lift(j)` = `P(R|T,j)` − `P(R|C,j)`,
where `P(R|T,j)` and `P(R|C,j)` represent the response probabilities in semi-decile subgroup `j` in the treatment and control groups, respectively, and can be estimated by the relative frequencies of response in the `holdout` sample. Then,
$$Weighted~Gini~coefficient = {\\sum\\limits\_{g = 1}^{20}\\left( {\\text{cum}\\%\\text{lift}\\left( g \\right) - \\text{cum}\\%\\text{sam}\\left( g \\right)} \\right)},$$
where
`cum%lift(g)` = cumulative % lift up to semi-decile group `g`
$$= ~\\frac{\\overset{-}{lift}\\left( 1,\\ldots,g \\right){\\sum\\limits\_{j = 1}^{g}{\\sum\_{i}w\_{tji}}}}{\\overset{-}{lift}{\\sum\\limits\_{j = 1}^{20}{\\sum\_{i}w\_{tji}}}}~ = ~\\frac{\\overset{-}{lift}\\left( 1,\\ldots,g \\right){\\sum\\limits\_{j = 1}^{g}w\_{tj}}}{\\overset{-}{lift}{\\sum\\limits\_{j = 1}^{20}w\_{tj}}},$$
where
$$\\overset{-}{lift} = overall~weighted~lift~\\left( of~all~20~semi - deciles \\right)$$
$$= \\frac{\\sum\\limits\_{j = 1}^{20}\\left( {\\sum\_{i}{\\left. w\_{tji} \\right)~{\\overset{-}{y}}\_{tj}~}} \\right.}{\\sum\\limits\_{j = 1}^{20}{\\sum\_{i}w\_{tji}}} - \\frac{\\sum\\limits\_{j = 1}^{20}\\left( {\\sum\_{i}{\\left. w\_{cji} \\right)~{\\overset{-}{y}}\_{cj}~}} \\right.}{\\sum\\limits\_{j = 1}^{20}{\\sum\_{i}w\_{cji}}},$$
and
`lift(1,…,g)` = weighted lift from semi-deciles 1, …, `g`, (where `g` = 1,…, 20)
$$= ~\\frac{\\sum\\limits\_{j = 1}^{g}\\left( {\\sum\_{i}{\\left. w\_{tji} \\right)~{\\overset{-}{y}}\_{tj}~}} \\right.}{\\sum\\limits\_{j = 1}^{g}{\\sum\_{i}w\_{tji}}} - \\frac{\\sum\\limits\_{j = 1}^{g}\\left( {\\sum\_{i}{\\left. w\_{cji} \\right)~{\\overset{-}{y}}\_{cj}~}} \\right.}{\\sum\\limits\_{j = 1}^{g}{\\sum\_{i}w\_{cji}}}$$
$$= \\frac{\\sum\\limits\_{j = 1}^{g}{w\_{tj}~{\\overset{-}{y}}\_{tj}}}{\\sum\\limits\_{j = 1}^{g}w\_{tj}} - \\frac{\\sum\\limits\_{j = 1}^{g}{w\_{cj}~{\\overset{-}{y}}\_{cj}}}{\\sum\\limits\_{j = 1}^{g}w\_{cj}},$$
And `w[tji]` = weight associated with the treatment group, semi-decile `j`, and individual `i` in the `holdout` sample; and similarly, `w[cji]` = weight associated Page 282with the control group, semi-decile `j`, and individual `i` in the `holdout` sample. Additionally, `$w_{tj} = {\sum\limits_{i}{w_{tji}~}}$`and `$w_{cj} = {\sum\limits_{i}w_{cji}}$`, representing the total weight at semi-decile `j` for the treatment group and control group, respectively. Further,
`cum%sam(g)` = cumulative % sample up to semi-decile group `g`
$$= ~\\frac{\\sum\\limits\_{j = 1}^{g}{\\sum\_{i}w\_{tji}}}{\\sum\\limits\_{j = 1}^{20}{\\sum\_{i}w\_{tji}}} = ~\\frac{\\sum\\limits\_{j = 1}^{g}w\_{tj}}{\\sum\\limits\_{j = 1}^{20}w\_{tj}}~.$$
Similarly, the Weighted Top 15% Gini is simply focused on the top 15%, or the top 3 semi-deciles, of the Weighted Gini coefficient formula:
$$Weighted~Top~15\\%~Gini = ~{\\sum\\limits\_{g = 1}^{3}\\left( {cum\\% lift\\left( g \\right) - cum\\% pop\\left( g \\right)} \\right)}.$$

## Appendix 9.3: Proof of Propensity Score Weighting for Non-Randomized Data
Define `Y[1]` and `Y[0]` as the potential outcomes for treatment and control (untreated), respectively. In reality, only one of these two is observed for an individual. One can use the `IPW` method to compute `ATE` for the whole population, Average Treatment Effect on Treated (`ATT`) or Average Treatment Effect on Control (`ATC`). We will use `ATC` below for illustration.
The `ATC` is defined as:
`ATC` = `E(Y[1]|T=0)` − `E(Y[0]|T=0)`
