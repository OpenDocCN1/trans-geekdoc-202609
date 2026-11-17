```
df,
target_column = "output_loan_status",
prediction_column = "output_prediction",
score_column="output_score"
)

profile = results.profile()
profile.set_dataset_timestamp(date_time)

print("writing profiles to whylabs...")
results.writer("whylabs").write()
```

Since this is a classification example, use log_classification_metrics() to log the classification model metrics and pass the following four arguments as to why.

# **log_classification_metrics():**

+   * input DataFrame: Entire DataFrame df
+   * target_column: Actual target column
+   * prediction_column: Predicted target column
+   * score_column: score

WhyLabs will identify a column in data as an output column if the column header contains output text.

WhyLabsWriter() will publish the summary on the WhyLabs platform. Go to the Summary tab in WhyLabs. It offers a compact and single view for multiple widgets like Data profiles, Input Health, Model Health, Model Performance, and alerts, as shown in the following figure:

![](bbox=[0.133, 0.702, 0.867, 0.929])

Figure 14.21: WhyLabs–Summary