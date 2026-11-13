# Table 5.5 Comparison of metrics.

| | MAE (mm) | RMSE (mm) | R² (%) |
|---|---|---|---|
| Full dataset | 6.97 | 9.55 | 91.50 |
| Deformations up to 80 mm | 6.55 | 8.47 | 85.50 |
| Deformations more than 80 mm | 9.57 | 14.52 | 45.80 |
| 50% of data points were randomly selected from the full dataset (1st trail) | 7.26 | 9.89 | 91.90 |
| 50% of data points were randomly selected from the full dataset (2nd trail) | 6.28 | 8.90 | 91.40 |

sub-sets. The results of my analysis are listed in Table 5.5. As you can see, the D&S analysis also agrees with the spot analysis in which the sub-set representing deformations larger than 80 mm performed the poorest in terms of all metrics.
In addition, I also carried out two trials of randomly selecting half of the number of data points for a D&S analysis. The results, not surprisingly, are similar to that obtained from the full dataset.55

# 5.7.4 Rational Vetting*

In the _rational vetting_ technique, we hope to test our model's prediction capability by using a series of rational tests pertinent to our domain knowledge or physics. Say that our model includes the level of applied loading as a feature to predict the deformation of beams. A rational vetting would imply that for a given same beam, reducing the level of loading should result in lesser deformation. If the model fails to predict such rational expectation, then the model might not capture the reality of the problem on hand – whether for this particular beam or for most/all beams.
The following could also serve as another example. Say that our ML model predicts an event-based stimulus (e.g., cracking due to elevated temperatures). In this example, the response is the degree of cracking, and the event-based stimulus is the occurrence of heating (i.e., fire – which could serve as the only feature to predict the response). In such a model, cracking is assumed to be solely tied to the occurrence of heating. Thus, a rational vetting would imply that if the value of the elevated temperature feature was to be set at 25°C, then the model should, in theory, predict zero/minimal cracking (due to the absence of stimulus). If the model predicts a considerable degree of cracking at ambient temperature, then the model is likely to be faulty.56

# 5.7.5 Confidence Intervals*

When we develop a ML model, we train, validate, and test this model on the data we have. Therefore, we can easily quantify the fitness of the model by comparing how far57 its predictions are from the ground truth. In the event wherein the model is deployed and is fed with new data that it has not seen before or input with data that we do not know its ground truth, then how could we quantify the predictivity of the model?
Here is where we can augment our model with confidence intervals.58 Such intervals are limits that can quantify the uncertainty of a prediction via two bounds, an upper and a lower bound. I would generally advise incorporating confidence