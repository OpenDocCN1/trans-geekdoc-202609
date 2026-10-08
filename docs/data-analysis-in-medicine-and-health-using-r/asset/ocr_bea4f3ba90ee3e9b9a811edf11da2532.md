Let's add an interaction term between stroke type and diabetes:

```
fatal_mv2_ia <-
  glm(status ~ gcs + stroke_type + stroke_type:gcs + age,
      data = fatal,
      family = binomial(link = 'logit'))
```

tidy(fatal_mv2_ia)

| term | estimate | std.error | statistic | p.value |
| :--- | :--- | :--- | :--- | :--- |
| (Intercept) | 0.508 | 1.37 | 0.371 | 0.710 |
| gcs | -0.320 | 0.0800 | -4.01 | 0.000069 |
| stroke_typeHemorrhagic | 1.61 | 1.30 | 1.24 | 0.217 |
| age | 0.026 | 0.0147 | 1.60 | 0.109 |
| gcs:stroke_typeHemorrhagic | -0.0347 | 0.111 | -0.312 | 0.755 |

> $$\tilde{g}(x) = \beta_0 + \beta_1(gcs) + \beta_2(stroke\_type) + \beta_3(age) + \beta_4(gcs \times stroke\_type)$

To decide if an interaction term should be included in the model, we should consider if the interaction term indicates both biological and statistical significance. If we believe that the interaction reflects both, then we should keep the interaction term in the model.

Using our data, we can see that:

+   - the coefficient for the interaction term for stroke type and gcs is not significant at the level of significance of 5% that we set.
"- stroke experts also believe that the effect of gcs on death is not largely different between different stroke type"

Using both reasons, we decide not to keep the two-way interaction between gcs and stroke type in our multivariable logistic model.

# 8.16 Prediction from Binary Logistic Regression

The broom package has a function called augment() which can calculate:

+   1. estimated log odds
2. probabilities
3. residuals
4. hat values