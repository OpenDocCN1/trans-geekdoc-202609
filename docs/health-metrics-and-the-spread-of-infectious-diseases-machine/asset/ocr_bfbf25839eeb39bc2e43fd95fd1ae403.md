# The Steps of Building a Model

#> Link function: identity
#>
#> Formula:
#> deaths - s(days)
#>
#> Parametric coefficients: Estimate Std. Error value Pr(|t|)
#> (Intercept) 146.008 3.583 40.74 <2e-16 ***
# ---
#> Signif. codes: 0 *** 0.001 ** 0.01 * 0.05 ' 0.1 ' 1
#>
#> Approximate significance of smooth terms:
 edf Ref.Def p-value
#> s(days) 8.969 9 431 <2e-16 ***
#>
#> Signif. codes: 0 *** 0.001 ** 0.01 * 0.05 ' 0.1 ' 1
#>
#> R-sq (adj) = 0.914 Deviance = 91.6%
#> GCV 4818.7 Scale est. 4687 n = 365

The smooth term for days is significant, as the effective degrees of freedom (edf) for the smooth term are 8.969, suggesting a moderately flexible relationship between deaths and time. The adjusted R-squared value is 0.914, indicating that the model explains approximately 91.4% of the variance in the response variable (deaths). The deviance explained 91.6%, suggesting that the model fits the data well.

Overall, the model suggests that there is a positive relationship between increasing time and the number of deaths due to cholera, with the number of deaths increasing over time to reach a peak and eventually slow down to zero. However, it's essential to consider the context of the data and potential confounding variables before drawing conclusions about causality or making predictions based solely on this model. Other factors influencing the spread are area social behaviour and vaccination. We will talk more about infectious diseases spread in section 4 Chapter 14.

# 6.3. Example: Epidemic X

# 6.3.1 SEIR Model

In this example we simulate data of an epidemic to build a SEIR (susceptible, exposed, infected, recovered) model, a little more complicated than just making a SIR (susceptible, infected, recovered) model (Equation 6.1). More the own models will be shown in Chapter 8, Chapter 14 and in Chapter 15.

So, let's start looking at how our simple linear equation $y=eta_0 + \beta_1x$ can be changed to become a differential equation. A differential equation describes how a quantity changes with respect to another quantity, in particular in this case. So, we are interested in the variation of $y$ within time.

```
$\frac{dy}{dt} = \frac{y_1 - y_0}{t_1 - t_0} \quad (6.10)$
```