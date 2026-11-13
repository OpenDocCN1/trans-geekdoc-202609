```
# [1] 0.03839085
```

```
mean(predict(fit_svm, test_feat_short) * testing_sample$R1M_Usd > 0) # Hit ratio
```

```
# [1] 0.5222197
```

The results are slightly better than those of the boosted trees. All parameters are completely arbitrary, especially the choice of the kernel. We finally turn to a classification example.

```
fit_svm_C <- svm(y = training_sample$R1M_Usd_C[1:1000], # Train label
 x = training_sample[1:1000, ] %>%     # Training features
 dplyr::select(features),
 type = "C-classification",          # SVM task type (see LIBSVM doc.)
 kernel = "sigmoid",                 # SVM kernel
 gamma = 0.5,                        # Parameter in the sigmoid kernel
 coef0 = 0.3,                        # Parameter in the sigmoid kernel
 cost = 0.2)                         # Slack variable penalisation
mean(predict(fit_svm_C,
 dplyr::select(testing_sample, features)) == testing_sample$R1M_Usd_C) # Accuracy
```

```
# [1] 0.5008973
```

Both the small training sample and the arbitrariness in our choice of the parameters may explain why the predictive accuracy is so poor.

# ## 8.4 Coding exercises

+   1. From the simple example shown above, extend SVM models to other kernels and discuss the impact on the fit.

+   2. Train a vanilla SVM model with labels being the 12-month forward (i.e., future) return and evaluate it on the testing sample. Do the same with a simple random forest. Compare.