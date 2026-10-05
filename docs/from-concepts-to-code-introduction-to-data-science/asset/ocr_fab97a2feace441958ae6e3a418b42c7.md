332

Model Risk

# MODEL GOVERNANCE COMMITTEE

| Name | Title | Department | Voting |
| --- | --- | --- | --- |
| Dan Johnston | Manager | Student Loans | Yes |
| Cindy Oh | SVP, Model Governance | Model Validation | Yes |
| Monica Swift | Head of Risk | Risk Management | Yes |

# END OF PERFORMANCE MONITORING PLAN

To enable effective monitoring, the metrics need to be calculated and reported in a timely fashion. Ideally, there is a reliable, automated system in place. When the model is initially launched, ideal thresholds may not be known. This may take experimentation, as an overly stringent threshold may trigger false alerts. The monitoring plan and system should be flexible to allow for adjustment.

Finally, it is important to interview the model users to understand if things are performing as intended. For example, if a model seems to make a common error, the model users override the model with human judgment. If this information is captured, it may be possible to improve the model and eliminate the override.

# 17.8.1 Dieper into Monitoring

We learned metrics will be monitored over time to understand the quality of predictive performance. What happens when metrics take a tumble and trigger a review? It will be important for analysts to dive deeper, and there are several things that can be reviewed.

Two important things that should be implemented for monitoring are making the system observable and providing relevant baselines. An observable system will capture, or log, the important steps and intermediate values for later review. The logging can reflect samples of model inputs and outputs, for example. It might reflect steps where code branching occurs, so that analysts can understand if the code took an unexpected turn. Everything is captured in real time. This level of observability will make it easier for data scientists and data engineers to spot problems, as it means less post hunting and testing.

To monitor performance over time, it is useful to first establish baselines. The baselines might include the F1 score measured on the test set, for example. Additionally, important statistics of the predictors might be included in the baseline, such as five-number summaries. Here is a small example of a JSON object that stores baseline statistics for a given date. The baseline data comprises one metric (F1 score) and a five-number summary for the variable age.