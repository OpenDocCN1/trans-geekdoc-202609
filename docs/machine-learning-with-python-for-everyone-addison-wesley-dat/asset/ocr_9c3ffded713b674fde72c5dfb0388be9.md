# Table 9.1 The different mathematical forms for penalized regression and SVR.

| Name | Penalty | Math |
|---|---|---|
| GOF Linear Regression | None | ∑ᵢ (yᵢ − w xᵢ)² |
| Lasso | L₁ | ∑ᵢ (yᵢ − w xᵢ)² + C ∑ⱼ wⱼ |
| Ridge | L₂ | ∑ᵢ (yᵢ − w xᵢ)² + C ∑ⱼ wⱼ² |
| SVR | L₁ | ∑ᵢ max(|yᵢ − w xᵢ| − ε, 0) + C ∑ⱼ wⱼ |

# Table 9.2 Common losses and penalties in regression models.

| Name | Loss | Penalty |
|---|---|---|
| GOF LR | L₂ | 0 |
| Lasso (L₁-Penalty LR) | L₂ | L₁ |
| Ridge (L₂-Penalty LR) | L₂ | L₂ |
| SVR | Hinge | L₂ |

dataset. As a practical matter, the choice between these models may depend on outside constraints. For some statistical goals —like significance testing, which we aren’t discussing in this book—we might prefer not using SVR. On very complex problems, we probably don’t even bother with GOF linear regression—although it might be a good baseline comparison. If we have lots of features, we may choose the lasso—L₁-penalized—to eliminate features entirely. Ridge has a more moderate approach and reduces—but doesn’t eliminate—features.

# 9.2.3 Just Do It—SVR Style

There are two main options for SVR in sklearn. We won’t dive into the theory, but you can control different aspects with these two different regressors:

+   - ε-SVR (Greek letter epsilon-SVR): you set the error band tolerance. ν is determined implicitly by this choice. This is what you get with the default parameters to SVR in sklearn.
+   - ν-SVR (Greek letter nu-SVR): you set ν, the proportion of kept support vectors with respect to the total number of examples. ε, the error band tolerance, is determined implicitly by this choice.

```
In [20]:
```python
svrs = [svm.SVR(),  # default epsilon=0.1
        svm.NuSVR()] # default nu=0.5

for model in svrs:
    preds = (model.fit(diabetes_train_ftrs, diabetes_train_tgt)
             .predict(diabetes_test_ftrs))
    print(metrics.mean_squared_error(diabetes_test_tgt, preds))
```
```