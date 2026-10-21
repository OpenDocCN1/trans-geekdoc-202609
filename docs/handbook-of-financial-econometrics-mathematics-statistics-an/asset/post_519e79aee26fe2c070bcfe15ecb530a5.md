
process that tests the residuals of a regression of the linear model against a Taylor expansion of the transition function. In the case of the E-STR model (Luukkonen et al., 1988) a quadratic function is used:

$$u_t = \beta'_0 x_t + \beta'_1 x_t z_t + \beta'_2 x_t z_t^2 + \varepsilon_t.$$ (125A.14)

In the case of the L-STR model the series is expanded to the third power (equation 125A.17).

These two tests do not allow selection between the L-STR and E-STR models. Teräsvirta (1994) combines the two tests to produce a three step procedure that tests the null hypothesis of linearity and, assuming linearity is rejected, then selects between E-STR and L-STR models. Granger and Terasvirta (1993) provide an accessible description of the procedure in their textbook and we follow this methodology closely.

The first step is to estimate the linear model:

$$y_t = \beta' x_t + u_t.$$ (125A.15)

The residuals of this regression are calculated

$$\hat{u}_t = y_t - \beta' x_t.$$ (125A.16)

The auxiliary regression can then be estimated:

$$u_t = \beta'_0 x_t + \beta'_1 x_t z_t + \beta'_2 x_t z_t^2 + \beta'_3 x_t z_t^3 + \varepsilon_t.$$ (125A.17)

The LM is

$$LM = T R^2.$$ (125A.18)

T is the sample size (number of time periods) and R^2 is the coefficient of multiple determination from the estimation of the auxiliary regression (equation 125A.17). The LM has a χ²-distribution. Teräsvirta (1994) suggests that using an F-test may provide a more accurate method of testing the hypothesis. This tests the null hypothesis:

$$H_0 : \beta_1 = \beta_2 = \beta_3 = 0.$$ (125A.19)

If we cannot reject this hypothesis, we can conclude that there is no nonlinear relationship defined in terms of the transition variable, z_t. It remains possible that another transition variable could result in rejecting linearity. More detailed analysis of the procedure can be described in Van Dijk et al. (2002).

Once the hypothesis of a linear relationship has been rejected, the next step is the selection of the appropriate nonlinear model, L-STR or E-STR.

The tests for this are based on the results of the auxiliary regression (equation 125A.17) and are tested through a series of nested F-tests.

H3 : β3 = 0, (125A.20)
H2 : β2 = 0|β3 = 0, (125A.21)
H1 : β1 = 0|β2 = β3 = 0. (125A.22)

From Saikkonen and Luukkonen (1988) we see that the E-STR expansion, equation 125A.14, does not have a cubic term, therefore rejecting H3 also rejects the E-STR model. Consequently rejecting H3 is consistent with an L-STR model.

Accepting H3 and rejecting H2 indicates a function with a symmetric, quadratic form, consistent with E-STR transition function. Finally accepting both H3 and H2 while rejecting H1 indicates an L-STR model. It can be noted that the tests of H1 and H2 only provide indicative answers. Granger and Terasvirta (1993) argue that strict application of this sequence of tests may lead to incorrect conclusions, where H3 is accepted and both H2 and H1 are rejected. They suggest an alternative approach to the selection problem in this case. Both hypotheses, H1 and H2 are tested, and if both are rejected the form of the transition function is selected based on the stronger of the two results, that is the test with the lowest p-value.

A similar approach can be used to select from different candidates for the transition variable, z_t. The linear model (equation 125A.15) and the auxiliary regression (equation 125A.17) are run for each potential variable. The hypothesis H3 is tested for all candidate variables, the variable generating the strongest test, smallest (significant) p-value, is selected.

## 125A.3 Model estimation

Estimating an STR model is a standard optimization problem and most statistical software packages provide the necessary functionality. The algorithms are usually based on nonlinear least squares but maximum likelihood methods are sometimes used (Granger and Terasvirta, 1993). As further discussion of the underlying algorithms is outside the scope of this work, we finish with a discussion of a number of practical issues that can arise during estimation, highlighted in Teräsvirta (1994). These occur when the optimization converges at a local minimum, struggles to estimate a parameter or fails to converge.

As with most optimization problems, the algorithm can converge at a local rather than global solution. It is possible to test for this by repeating the optimization with different initial values and confirming the same solution is reached. The optimizer may be slow to converge when γ is large. Very large changes in the value of γ will have little effect on the value of the transition function and a large number of observations in the region of c would be needed to estimate γ accurately. Teräsvirta (1994) suggests rescaling the parameters (scaling γ down and c up) to solve this problem. Finally, under certain circumstances, the optimizer may fail to converge due to the complexity of the problem. In this event, Teräsvirta (1994) suggests simplifying the problem by solving it in two stages. In the first stage, the value of γ is fixed, setting γ = 1 is recommended, and the other regression coefficients are estimated. These estimated coefficients are then fixed in a second regression and the value of γ estimated.

This page intentionally left blank

## Chapter 126

## Application of Discriminant Analysis, Factor Analysis, Logistic Regression, and KMV-Merton Model in Credit Risk Analysis*

Cheng Few Lee and Hai-Chin Yu

## Contents

- 126.1 Introduction . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4314
- 126.2 Credit Analysis . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4315
- 126.3 Bankruptcy and Financial Distress Analysis . . . . . . . . . . . . 4319
- 126.4 Applications of Factor Analysis to Select Useful Financial Ratios . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4323
- 126.5 Bond Rating Forecasting . . . . . . . . . . . . . . . . . . . . . . . . 4325
- 126.6 Ohlson’s and Shumway’s Methods for Estimating Default Probability . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . 4328
- 126.6.1 MIDAS Logit Model . . . . . . . . . . . . . . . . . . . . . . . . . . 4332
- 126.7 Merton Distance Model and KMV-Merton Model . . . . . . . . . . . 4332
- 126.7.1 Merton distance model . . . . . . . . . . . . . . . . . . . . . . . 4332
- 126.7.2 A Naïve alternative . . . . . . . . . . . . . . . . . . . . . . . . . 4333
- 126.7.3 KMV-Merton model . . . . . . . . . . . . . . . . . . . . . . . . . . 4335

Cheng Few Lee
Rutgers University
e-mail: cfee@business.rutgers.edu

Hai-Chin Yu
Chung Yuan University
e-mail: haichin@cycu.edu.tw

*This paper draws upon Chapter 4, “Application of discriminant analysis and factor analysis in financial management,” in Financial Analysis, Planning and Forecasting: Theory and Application, 3rd edition, World Scientific, Singapore.

126.8 Capital Structure Determination and Naïve Default Probability ........ 4336

126.9 Empirical Comparison ........ 4337

126.10 Summary and Concluding Remarks ........ 4337

Bibliography ........ 4338

Appendix 126A Logistic Model, Probit Model and MIDAS Logit Model ........ 4342

Appendix 126B SAS Code for Hazard Model in Bankruptcy Forecasting ........ 4344

Appendix 126C Application of Merton Distance to Default Model . 4345

## Abstract

The main purposes of this paper are to review and integrate the applications of discriminant analysis, factor analysis, and logistic regression in credit risk management. First, we discuss how the discriminant analysis can be used for credit rating such as calculating financial z-score to determine the chance of bankruptcy of the firm. In addition, we also discuss how discriminant analysis can be used to classify banks into problem banks and non-problem banks. Secondly, we discuss how factor analysis can be combined with discriminant analysis to perform bond rating forecasting. Thirdly, we show how logistic and generalized regression techniques can be used to calculate the default risk probability. Fourthly, we will discuss the KMV-Merton model and Merton distance model for calculating default probability. Finally, we compare all techniques discussed in previous sections and draw conclusions and give suggestions for future research. We propose using CEV option model to improve the original Merton DD model. In addition, we also propose a modified naïve model to improve Bharath and Shumway's (2008) naïve model.

## Keywords

Discriminant analysis ● Factor analysis ● Logistic regression ● KMV-Merton model ● Probit model ● MIDAS logit model ● Hazard model ● Merton distance model ● Financial z-score ● Default probability.

## 126.1 Introduction

Discriminant analysis, factor analysis, logistic regression, and the KMV-Merton model have been used to perform credit analysis for almost four decades. The main purposes of this paper are to review and integrate the applications of Discriminant Analysis, Factor Analysis, and logistic and generalized regressions in credit risk management. First, we will discuss how the discriminant analysis can be used for credit rating such as calculating financial z-score to determine the chance of bankruptcy of the firm. In addition, we also discuss how discriminant analysis can be used to classify banks into problem banks and non-problem banks. Secondly, we will discuss how factor analysis can be combined with discriminant analysis to perform bond
