
- **Alert system for important events**: You cannot track 100+ metrics manually 24x7; hence, the alert system should be part of the monitoring solution. Not everything needs an alert. You may be tracking 20+ metrics; however, only a few metrics need high attention. For instance, if input data drift is exceeding the threshold, then the alert system should send the notification to the responsible team or Data Scientists. The whole purpose of the alert system is to notify concerned teams or individuals so that issues or errors can be avoided or can be solved at the earliest to ensure consistency in ML model performance.

- **Root cause analysis and debugging**: Once you get the alert, you may need to act on it. You can start the root cause analysis to determine the issue and fix it by debugging. For instance, if model accuracy is going below the threshold, it could be because of a change in the distribution of input data or anomalies.

To design an efficient monitoring system, you need to consider existing pipelines and infrastructure. There are mainly three pillars of monitoring:

- **Processing and Storage**: It processes and stores the critical metrics in a database or data source with a timestamp. You can query the metrics when required.

- **Graphs and Dashboard**: It will query or fetch the monitoring metrics from a connected database or data source. You can choose the visualization as per the type of metrics. Here, you have to decide the metrics that need to be displayed. It should summarize overall monitoring with intuitive graphs.

- **Alert**: Finally, it should send an alert to the concerned team or data scientists to take immediate action, if required. This helps to prevent future failures or mitigate the impact.

The following figures show the three pillars of the monitoring system for effective monitoring:

## Pillars of Monitoring System

![](img/cc4299656808e62a294f1843a1e18e72_408_0.png)

Figure 14.1: Pillars of the monitoring system

Before setting up any monitoring system, here is the list of questions that need to be answered:

- What do you plan to monitor?
- What tools and language are you using?
- What platform or library will be used for monitoring?
- How do you plan to integrate the monitoring setup with the existing environment and tools?
- What threshold is to be used for alerts?
- What action should be taken after detecting an issue or failure?

Finally, as per the model life cycle, monitoring should complete the feedback loop, that is, after detecting an issue or failure, it should send a notification to the concerned team or data scientists so that they can take necessary action, such as retraining the ML model.

## Metrics for monitoring your ML system

You need to decide which type of metric to monitor. Operational metrics will enable developers to track system or server-related failures or warnings, such as high resource usage that can increase the latency, which will affect end-user experience. Tracking operational metrics is essential because the server should be in good condition to run the ML model and other tasks. Another factor is the cost. Operational teams have to set limits on the cost and need to track which resource or service causes higher costs.

Here are a few important operational metrics:

- System or Server
  - Resource usage
  - Availability
  - Latency
  - Throughput
- Cost
  - Infrastructure cost
  - Storage cost
  - Additional service (if any)

Once the server is up and running without any issues, you can focus on functional or ML model metrics. You will study the detection of model monitoring metrics and ways to address them in this chapter.

The following are a few important model metrics:

- Input data
  - Model version
  - Data drift
  - Outliers
- ML model
  - Model version
  - Model hyperparameters
  - Metadata
  - Predictions or Output
  - Classification model evaluation metrics
    - Accuracy
    - Confusion Matrix
    - ROC-AUC Score
    - Precision and Recall Scores
    - F1-Score
  - Regression model evaluation metrics
    - Root Mean Square Error (RMSE)
    - R-Squared and Adjusted R-Square
    - Mean Absolute Error (MAE)
    - Mean Absolute Percentage Error (MAPE)
- Prediction drift

You can decide which metrics to track closely and which metrics need alerts.

## Drift in ML

Model drift means a change in the behavior of ML models or that the model is not performing as expected or per the Service Level Agreement (SLA). Model performance may degrade after deploying it to production, as the model can receive data that was not introduced during model training.

### Types of drift in ML

There are mainly three types of drift in ML:

- Data drift
- Prediction drift
- Concept shift

### Data drift

Data drift is when the distribution or characteristics of input features change with reference to training data. It is also known as feature drift, population drift, or covariate shift. If the distribution of input data changes, then its predictions might get affected as the model is not prepared for it.

If a new category gets added to the feature post-deployment, then it may cause an error while making the prediction, as it was not there at the time of model training.

Another example could be, suppose there is a feature called **Credit Rating** in training data, and it has high weightage, which means a change in this feature may cause a major change in model output. Now, the business decided to go with Moody’s credit rating instead of S&P. This will cause a change in input data. For instance, S&P’s AA- is equivalent to Moody’s Aa3 rating.

The following equation shows that the distribution of training data does not match the distribution of reference (production) data.

Mathematically, data drift can be defined as follows:

```
P(X) ≠ Pref(X)
```

Where P(X) denotes the input data probability distribution.

### Prediction drift

As input data changes with data drift, this may cause a change in the target or prediction variable. It refers to a change in predictions over time. It is also named a prior probability shift, label drift, or unconditional class shift. This can also occur due to the removal or addition of new classes. Retraining the model can help mitigate the model degradation owing to prediction drift.

Mathematically, prediction drift can be defined as follows:

```
P(Y) ≠ Pref(Y)
```

Where P(Y) denotes the prior probability distribution of target labels.

### Concept shift

A concept shift occurs when the relationship between independent variables and dependent or target variables changes. It is also known as posterior class shift, conditional change, or real concept drift. It refers to changes in the relationship between the input variables and the target variables. If you detect any significant concept shift, it is very likely that your model's predictions are unreliable. A **Concept** in Concept shift refers to the relationship between independent and dependent variables.

For instance, a car insurance company changes its claim policy that a claim for a specific part of the car will be rejected. Suppose that part of the car got damaged in an accident, the customer's claim for it will be rejected. In this scenario, mapping between the input feature and target feature changes even though the distribution of input data remains the same.

Mathematically, concept shift can be defined as follows:

$P(Y|X) \neq Pref(Y|X)$

Where $P(Y|X)$ denotes the posterior probability distribution of the target labels.

Following are the patterns of concept shift:

- Sudden or abrupt
- Gradual
- Recurring or cyclic
- Incremental
- Temporary

![](img/cc4299656808e62a294f1843a1e18e72_412_0.png)

Figure 14.2: Different patterns of concept shift

## Techniques to detect the drift in ML

Statistical distance measurement using distance metrics between two distributions is useful for detecting drift in ML.

If there are many independent variables in the dataset, then you can use dimensionality reduction techniques, such as PCA. Tracking many features can increase the load on the monitoring system and sometimes it becomes difficult to mitigate drift by targeting specific features.

Basic statistical metrics, such as mean value, standard deviation, correlation, and minimum and maximum values comparison, can be used for calculating the drift between training and current independent variables.

Distance measures like Population Stability Index (PSI), Characteristic stability index (CSI), Kullback–Leibler divergence (KL-Divergence), Jensen–Shannon divergence (JS-Divergence), and Kolmogorov–Smirnov (KS) statistics can be used for continuous features.
