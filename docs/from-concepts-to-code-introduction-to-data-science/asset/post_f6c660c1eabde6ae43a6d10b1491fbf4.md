
Ongoing Model Performance Monitoring

## METRICS, STATUS, AND THRESHOLDS

| Metric | Alert Level | Threshold |
|---|---|---|
| F1 score | YELLOW | < 0.8 or drop exceeding 10% |
| F1 score | RED | < 0.7 or drop exceeding 20% |
| ... | ... | ... |

## ACTIONS AND ESCALATION POLICY

In the event that the YELLOW threshold is crossed, these stakeholders will be alerted:

| Product Manager |
| Engineering Manager |
| Data Science Manager |

The model development team and the engineering team will review the model components and data. The model may be retrained to include recent data.

In the event that the RED threshold is crossed, these stakeholders will be alerted:

| VP of Product |
| VP of Engineering |
| VP of Data Science |
| Product Manager |
| Engineering Manager |
| Data Science Manager |

The model will be taken out of production so that it can be redeveloped. The model development team and the engineering team will review the model components and data.

## ROLES AND RESPONSIBILITIES

| Role | Name | Title |
|---|---|---|
| Model developer | John Smith | Data Scientist |
| Manager of model development | Jane Cooper | Data Science Manager |
| Model validator | Xie Xu | VP, Model Validation |
| Manager of model validation | Carlos Juarez | SVP, Model Validation |
| ... | ... | ... |

332

Model Risk

## MODEL GOVERNANCE COMMITTEE

| Name | Title | Department | Voting |
| --- |---|---|---|
| Dan Johnston | Manager | Student Loans | Yes |
| Cindy Oh | SVP, Model Governance | Model Validation | Yes |
| Monica Swift | Head of Risk | Risk Management | Yes |

## END OF PERFORMANCE MONITORING PLAN

To enable effective monitoring, the metrics need to be calculated and reported in a timely fashion. Ideally, there is a reliable, automated system in place. When the model is initially launched, ideal thresholds may not be known. This may take experimentation, as an overly stringent threshold may trigger false alerts. The monitoring plan and system should be flexible to allow for adjustment.

Finally, it is important to interview the model users to understand if things are performing as intended. For example, if a model seems to make a common error, the model users override the model with human judgment. If this information is captured, it may be possible to improve the model and eliminate the override.

### 17.8.1 Deeper into Monitoring

We learned metrics will be monitored over time to understand the quality of predictive performance. What happens when metrics take a tumble and trigger a review? It will be important for analysts to dive deeper, and there are several things that can be reviewed.

Two important things that should be implemented for monitoring are making the system observable and providing relevant baselines. An observable system will capture, or log, the important steps and intermediate values for later review. The logging can reflect samples of model inputs and outputs, for example. It might reflect steps where code branching occurs, so that analysts can understand if the code took an unexpected turn. Everything is captured in real time. This level of observability will make it easier for data scientists and data engineers to spot problems, as it means less post hunting and testing.

To monitor performance over time, it is useful to first establish baselines. The baselines might include the F1 score measured on the test set, for example. Additionally, important statistics of the predictors might be included in the baseline, such as five-number summaries. Here is a small example of a JSON object that stores baseline statistics for a given date. The baseline data comprises one metric (F1 score) and a five-number summary for the variable age.

## Ongoing Model Performance Monitoring

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

Other potential areas for investigation occur earlier in the data pipeline. There may be defects in the processed data, the raw data, or the data feeds. Perhaps there was a step where an integer was expected, but a string was input. If the code was not properly written to handle such a case, an issue may arise. There might have been a period of time when a certain data feed was de-

352

### 17.9 Case Study: Fair Lending

This section will provide a detailed example.

### 17.9.1 Fair Lending Background

In finance, banks and other lenders typically use machine learning models to make lending decisions. The underwriting decision may use a logistic regression model. Given approval, the pricing decision may use a linear regression model.

The model predictors should capture the ability and willingness of borrowers to repay the loan. The predictors should not use protected class information, as this can discriminate and promote unfair lending.

Federal regulatory agencies such as the Office of the Comptroller of the Currency have developed approaches to address unfair and deceptive practices. The Fair Housing Act and the Equal Credit Opportunity Act protect consumers by prohibiting discrimination in credit and real estate transactions based on factors like:

- Race or color
- National origin
- Religion
- Sex
- Age (provided the applicant is old enough to enter a contract)

A protected class refers to groups of individuals protected by anti-, such as:

- Individuals over the age of 65
- Black, Hispanic, and Native American individuals

Illegal disparate treatment occurs when a lender bases its decision on one or more discriminatory factors covered by fair lending laws. For example, a bank using a lending process where females are offered an auto loan with a higher interest rate than males would be a violation of fair lending laws.

### 17.9.2 Numerical Example

We will explore fair lending risk with a synthetic mortgage lending dataset. The data can be found here:

```
semester2/datasets/mortgage_lending.csv
```

The fair lending notebook can be found here:

```
semester2/week_15_16_fair_lending_application/
IDS_hw4_fair_lending_intro.ipynb
```

This dataset includes a subset of what a typical file would look like. It includes:

- The demographic variable: gender
- The credit factor fico (for FICO score)
- The credit factor loan.term
- The loan attribute rate.type
- The target denied, where 1=denied, 0=approved
