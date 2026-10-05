# Ongoing Model Performance Monitoring

```
{
  'baseline_date': {
    '2023-01-31': {
      'metrics': {
        'F1 score': 0.68
      },
      'predictors': {
        'age': {
          'min': 25,
          'q1': 30,
          'median': 37,
          'q3': 55,
          'max': 95
        }
      }
    }
  }
}
```

The baseline information may be stored in a data lake or managed with a cloud-provider service such as AmazonMaker. It can be accessed and used programmatically.

In the event that metrics trigger an alert, data scientists can start leveraging the logs and the baselines. They first check the logs for indicators of problems. Next, they can investigate if there was a change in the distribution of the predictors, for example. To statistically test if the distribution of a variable changed between times $t_1$ and $t_2$, the two-sample Kolmogorov-Smirnov test (K-S test) could be beyond the scope of this book, but more details can be found in [30].

A change in a predictor's distribution over time is called factor drift, and can be problematic. Since this model learned specific relationships between predictors and a target from a training set, if the distribution of a predictor changes, its relationship with the target may change as well. We would need to retain the new data to capture the change. There is no guarantee, however, that the predictor will continue to provide the same level of predictive ability.

Other potential areas for investigation occur earlier in the data pipeline. There may be defects in the processed data, the raw data, or the data feeds. Perhaps there was a step where an integer was expected, but a string was input. If the code was not properly written to handle such a case, an issue may arise. There might have been a period of time when a certain data feed was working properly, and an important predictor was not supplied to the model. Diving deeper into the data can take a lot of time and effort, and reinforces the importance of system observability.