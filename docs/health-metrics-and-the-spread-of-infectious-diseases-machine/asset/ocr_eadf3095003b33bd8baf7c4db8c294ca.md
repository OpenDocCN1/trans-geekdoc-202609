# YLDs for Tuberculosis by Location and Year

![](bbox=[0.153, 0.11, 0.846, 0.381])

**Figure 9.11** YLDs for Tuberculosis by Location and Year

The disability weight for tuberculosis in 2019 is set at 0.333 for the Global region. The duration, derived from the GBD 2021 and based on a systematic review, was adjusted for treated and untreated cases: it was estimated to be 3 years for untreated cases and 6 months for treated cases.

The formula *YLDs Prevalence + year + (1|location)* specifies a linear mixed-effects model for predicting Years Lived with Disability (YLDs) due to tuberculosis. The model includes fixed effects for prevalence and year, as well as a random intercept for location ((1|location)). This allows the estimation of YLDs while accounting for variability across locations.

```
# Define the formula
formula <- YLDs - Prevalence + year + (1 | location)

# Fit the mixed-effects model
model <- lmer(formula, data = tuberculosis)
model
# Linear mixed model fit by REML ['lmerMod']
# Formula: YLDs - Prevalence + year + (1 | location)
# Data: tuberculosis
# REML criterion at convergence: 34.6921
# Random effects:
# Groups Name Std.Dev.
# location (Intercept) 0.6202
# Residual 0.1773
# Number of obs: 12, groups: 6
# Fixed Effects:
```

> ⁴Edine W. Tiersma et al., “Natural History of Tuberculosis: Duration and Fatality of Untreated Pulmonary Tuberculosis in HIV Negative Patients: A Systematic Review,” PLOS ONE 6, no. 4 (April, 2011): e17601, doi:10.1371/journal.pone.017601.