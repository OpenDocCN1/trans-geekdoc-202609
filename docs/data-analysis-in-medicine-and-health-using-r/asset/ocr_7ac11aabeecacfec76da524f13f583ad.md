• patients are withdrawn from the study
In censored patients, we do not know the exact time for them to develop the event.
To explore how to incorporate a regression model-like structure into the hazard function, we can model the hazard function using:

```
$h(t) = \theta_0$$
```

The hazard function is a rate, and because of that it must be strictly positive. To constrain $\theta$ at greater than zero, we can parameterize the hazard function as:

```
$h(t) = \exp^{	heta_0}$$
```

So for a covariate $x$ the log-hazard function is

```
$ln[h(t.x)] = \beta_0 + \beta_1(x)$
```

and the hazard function is

```
$h(t.x) = e.exp^{	heta_0+\beta_1(x)}$
```

This is the exponential distribution which is one example of a fully parametric hazard function. Fully parametric models accomplish two goals simultaneously:

+   • It describes the underlying distribution of survival time (error component)
• It characterizes how distribution changes as a function of the covariates (system-atic component).

However, even though fully parametric models can be used to accomplish the above goals, the assumptions required for their error components may be unnecessarily stringent or unrealistic. One option is to have a fully parametric regression structure but leave their dependence on time unspecified. The models that utilize this approach are called semiparametric regression models.

# 11.10.1 Cox proportional hazards regression

If we take our dataset, for example, where to compare the survival experience of stroke patients on different types of stroke (Ischemic stroke or Hemorrhagic stroke), one form of a regression model for the hazard function that addresses the study goal is:

```
$h(t,x,\beta) = h_0(t)r(x,\beta)$
```

We can see that the hazard function is the product of two functions:

+   • The function, $h_0(t)$, characterizes how the hazard function changes as a function of survival time.