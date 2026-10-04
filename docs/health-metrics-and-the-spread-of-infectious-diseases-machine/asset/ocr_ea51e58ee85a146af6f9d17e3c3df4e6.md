# Practical Insights and Examples

# Table 11.3 Model p-values

| term | p.value_mod1 | p.value_mod2 | p.value_mod3 |
|---|---|---|--|
| s(smoking) | 0 | 7.69e-05 | 0.000000 |
| s(pm25) | 0 | 0.00e+00 | 0.697803 |

In the second model (mod2), both the smoking and PM2.5 have p-values below 0.05, indicating that they are statistically significant predictors of meningitis mortality. However, when incorporating temporal and spatial effects in mod3, the significance of these exposure changes — most notably, PM2.5 is no longer statistically significant. This shift suggests that the apparent association in the simpler model may be confounded by trends or country-level differences, highlighting the importance of accounting for structured variation in space and time.

Let's use both models to predict() function to obtain the predicted values for the model. The predicted values are added to the original dataset as a new column called predicted.

```
meningitis$predicted_mod2 <- predict(mod2)
meningitis$predicted_mod3 <- predict(mod3)
```

```
ggplot(meningitis,
  aes(x = year, y = deaths, color = location) +
  geom_line() +
  geom_line(aes(y = predicted_mod2),
    linetype = "dashed") +
  facet_grid(location = ., scale = "free") +\n  labs(title = "Meningitis Death Rates by Country",
    subtitle = "Observed vs Predicted",
    y = "Death Rate", x = "Year") + 
  theme(legend.position = "none")
```

```
ggplot(meningitis,
  aes(x = year, y = deaths, color = location) +
  geom_line(aes(y = predicted_mod3),
    linetype = "dashed") +
  facet_grid(location = ., scale = "free") +\n  labs(title = "Meningitis Death Rates by Country",
    subtitle = "Observed vs Predicted",
    y = "Death Rate", x = "Year") + 
  theme(legend.position = "none")
```

We can notice that the model fits the data, with the predicted values closely following the observed values, with mod3 slightly overfitting the data.

Let's check the residuals of mod2:

```
meningitis %>%%
  # calculate the residuals to see how well the model fits the data
  mutate(residuals = deaths - predicted_mod2) %>%
  select(deaths, predicted_mod2, residuals) %>%%
```