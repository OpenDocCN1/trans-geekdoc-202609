# 10 Inference for Regression

inclusion of a factor in a model, we always need to test the factor levels at once. Based on the output, the test statistic is F = 4.83 and the associated p-value is 0.003. We reject the null hypothesis and conclude that the full model was needed, alternatively, it is appropriate to add the factor continent_of_origin to a model that already has aroma, flavor, and moisture_percentage.

# 10.5.5 Model fit and diagnostics

As we did for simple linear regression we use the residuals to determine the fit of the model and whether some of the assumptions are met. In particular, we continue using the plot of residuals against the fitted values and if no model violations present the plot should be close to a null plot.

While most of the treatment and interpretations are similar to those presented for simple linear regression, when the plot of residuals against fitted values is not a null plot, we know that there is some sort of violation of one or more of the assumptions of the model. It is not met. There is no longer clear what the reason for this is, but at least one assumption is not met. On the other hand, if the residuals against fitted values plot appears to be close to a null plot, none of the assumptions have been broken and we can proceed with the use of this model.

```
# Fit regression model:
mod_mult_final <- lm(total_cup_points ~ aroma + flavor + continent_of_origin)
# Fitted values and residuals:
fit_and_res_mult <- get_regression_points(mod_mult_final)
```

```
g1 <- fit_and_res_mult >
gpgplot(aes(x = total_cup_points, y = residual)) + 
geom_point() + 
labs(x = "fitted values (total cup points)", y = "residual") + 
geom_hline(intercept = 0, col = "blue")
g2 <- ggplot(fit_and_res_mult, aes(sample = residual)) + 
geom_qq() + 
geom_qq_line(col="blue", linewidth = 0.5)
grid.arrange(g1, g2, ncol=2)
```