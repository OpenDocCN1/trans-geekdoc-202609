
## Sample Selection Issues and Applications

then includes it into the second-stage regression model as an explanatory variable to yield unbiased estimators. As the sample selection rule may not always be derived from a yes–no choice, our study further utilizes Lee’s (1983) extension by applying the Multinomial Logit model into the first-stage estimation procedure to allow for its application with multi-choice sample selection rule. Since the pioneer works related to sample selection issues are mostly in the field of labor economics, we give two examples of an empirical study in labor economics to respectively demonstrate applications of the Probit correction approach and Multinomial Logit correction approach. Finally, we point out that the problem of a non-random sample is not limited to applications in economics. In the past 20 years, quite a few researchers have taken into account the issue of sample selection for studies of finance and management issues.

## Keywords
- Sample selection bias
- Heckman's two-stage estimation
- Probit model
- Multinomial logit model.

### 111.1 Introduction

Regression is a main tool of econometrics and is widely applied in many disciplines of social science, especially for empirical analyses in the fields of economics and finance. Regression deals with the dependence of one variable (commonly termed dependent variable) on other variables (commonly termed explanatory variables or independent variables). In addition, regression analysis is largely concerned with estimating the population mean value of a dependent variable on the basis of known or fixed values of the explanatory variable(s).

In terms of the parameter estimation, the method of ordinary least squares (OLS) is one of the most powerful and popular techniques used by researchers when applying regression analysis, because the OLS estimator, under certain assumptions, has very attractive statistical properties such as BLUE (best linear unbiased estimator). One of the key assumptions to assure the BLUE property of the OLS estimator is a zero mean value of the disturbance term, which implies that the dependent variable is randomly sampled along with the explanatory variables. This assumption suggests that there is no specification bias or specification error in the model used in the regression analysis.

In some applications, there are missing values for the dependent variable, but at the same time one can observe the exogenous explanatory variables. For example, in the estimation of the wage equation for women, the wage variable is missing for those women who do not work, but we can observe explanatory variables such as age and schooling for non-working women. The pioneer works of estimating the wage equation for women by Gronau (1974), Lewis (1974), and Heckman (1974) indicate that the observed distribution of wages is a censored distribution, because only those women choosing to work can have observed wages. The term “selection bias” refers to the fact that if we estimate the wage equation by OLS based on the sample of working women, then we get inconsistent estimates of the parameters, because the assumption of a zero mean value of the disturbance term in the wage regression model is violated.

Heckman (1976) proposes a two-stage estimation method to resolve the problem of sample selection bias based on the idea of correcting the specification error due to omitted variables in the regression model. The purpose of our study is to discuss some related issues of sample selection bias. Section 111.2 introduces the idea of sample selection bias in more details and presents some commonly used approaches to deal with the problem of sample selection bias. Section 111.3 offers some applications in labor economics. Section 111.4 concludes the study by giving some examples of applications in the fields of finance and management.

A non-random sample is the key reason for selection bias. In a random sample, the sample mean of the dependent variable should mirror that of the population mean. This is the basis for unbiasedness of the OLS estimator. On the one hand, a non-random sample leads to the problem of selection bias. On the other hand, it can be considered as informative sampling — that is, the mere observability of the dependent variable implies information about the regression residual. Based on this line of thinking, we can better understand the source of the sample selection bias and the rationale behind the procedure of correcting the selection bias.

Let us start with the problem of estimating the wage equation for women. The market wage equation can be specified as follows:

```
y_1 = a + b x + u_1
```

where y_1 denotes the wage variable, and x denotes the explanatory variable such as years of schooling. We do not always observe y_1 since only those who work have observed wages.

Let y2 be the index function for observability, i.e.:

y2 = { 1 if u2 > c0 + c1 x1, u2 ~ N(0,1), 0 otherwise. } (111.1)

We only observe y1 if y2 = 1. It implies that

Pr(y2 = 1) = 1 - F(c0 + c1 x1) = 1 - Φ(c0 + c1 x1). (111.2)

If we let y2* denote the unobserved reservation wage for women, then we observe wages for working women when their market wage is higher than their reservation wage according to the theory of labor supply. In other words, we observe y1 if y1 > y2*, where:

y2* = d0 + d1 x + u3, a + b x + u1 > d0 + d1 x + u3, u1 - u3 > (d0 - a) + (d1 - b)x. (111.3)

which imply that

(u1 - u3)/√Var(u1 - u3) > [(d0 - a)+(d1 - b)x]/√Var(u1 - u3). (111.4)

Here, by simple transformation, we can rewrite the labor supply decision rule (market wage > reservation wage) as an index function model as specified in equation (111.1).

We can further demonstrate the bias due to sample selection by examining the observability of y1 based on the sample selection rule: y1 > y2*. Since we do not observe y1 below y2*, the regression residual will be sampled disproportionately from the upper or lower tail of the distribution. As a result, we notice that the residual will not have a zero mean anymore.

Let us consider a simple case where the threshold is fixed, i.e., y2* = d0. We can compare the sample regression line (dotted line) and the population regression line (solid line) for this case in Figure 111.1. As shown in Figure 111.1, at x1, we sample from the left (upper) tail of the distribution. At x2, we sample from the left (upper) half of the distribution. Thus, the sample mean at both x1 and x2 will be higher than the population mean. At x3, we sample from almost the whole distribution. The observed mean is very close to the population mean at x3. As a result, when we try to fit a linear regression using the OLS method, we under-estimate the effect of x on y1 in this simple case, as Figure 111.1 illustrates.

![](img/31ee7e6fa5107b22bbf7960ec96106a1_4039_0.png)

![](img/31ee7e6fa5107b22bbf7960ec96106a1_4039_1.png)

In the fixed threshold case as shown in Figure 111.1, we can predict the direction of selection bias. However, if we allow the threshold to be stochastic, then the direction of bias will be very difficult to predict. For example, let y₂^*=d₀+u₃, where u₃ denotes a stochastic error term. As shown in Figure 111.2, we are more likely to observe y₁ when y₂^* is in the lower tail than when in the upper tail since y₁ > y₂^* is more likely to be satisfied when y₂^* is in the lower tail than when in the upper tail. We also tend to observe most of y1 when x is large since the selection criterion is more likely to be satisfied as x increases.

![](img/31ee7e6fa5107b22bbf7960ec96106a1_4040_0.png)

Figure 111.3: Comparing the sample regression line and population regression line for a stochastic threshold case where u1 and u3 are positively correlated and σ_u3 > σ_u1.

Suppose u1 and u3 are positively correlated and σ_u3 > σ_u1; we then will tend not to observe y1 in the upper tail, because of a smaller variance in u1. We are more likely to observe y1 when its residual is negative than when it is positive. The sample mean value of the observed y1 (dotted line in Figure 111.3) tends to be smaller than the population mean (solid line in Figure 111.3). In other words, we will over-estimate the slope of the regression line in this specific case as presented in Figure 111.3.

We contrarily note that if u1 and u3 are negatively correlated, then we will tend to under-estimate the slope, because we are more likely to observe y1 when its residual is positive than when it is negative. In other words, in the stochastic threshold case, there is no a priori supposition that we will under-estimate or over-estimate the slope. Thus, it is impossible to predict, a priori, the direction of selection bias. The bias depends on the correlation between u1 and u3 and how the probability of observing y1 changes as x changes.

The basic problem in the sample selection model is that the sample mean does not represent the population mean as it is in the random sampling regression model. The deviation of the sample mean from the population mean results in biased parameter estimators. In most cases, the direction of bias on the OLS coefficient for the regression model is impossible to predict on the basis of prior information. Therefore, we need to adopt a proper
