# Machine Learning with mlr3

```
nucleoli", "Mitoses", "Class")

task <- as_task_classify(selected, target="Class")

resamp_kcv <- rsmp("cv")
resamp_kcv$param_set$values = list(folds = 3)

result_kcv <- resample(task, p_learner, resamp_kcv)
measures <- msrs(c("class.precision", "class.specificity",
"class.sensitivity")
result_kcv$score(measures)
```

This code gives us the results of a PCA.

# How it works..

Step 1 is to start creating pipeline objects—the parts of the pipeline we will string together. We can do this with the po function and the name of the object. For the preprocessing step, we have chosen a "scale" and a "pca". These have no further options, though many of the pipeline objects we could create do. In step 2, we string the parts into a pipeline using the magrittr pipeline %>% operator. The resulting pipeline pipel object has a $plot method we can use to view the pipeline, as seen in Figure 11.6:

![](bbox=[0.437, 0.517, 0.562, 0.725])

Figure 11.6 – A basic pre-processing pipeline