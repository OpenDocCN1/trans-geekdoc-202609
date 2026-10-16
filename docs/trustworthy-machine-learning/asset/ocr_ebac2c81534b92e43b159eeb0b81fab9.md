activation function whereas isotonic regression can work with any shape of the existing calibration curve. Isotonic regression requires more data than Platt scaling to work effectively.

A post-processing method for total predictive uncertainty quantification that does not require you to start with an existing classifier score works in almost the same way as computing deletion diagnostics described in Chapter 12 for explanation. You train many attrition models, leaving one training data point out each time. You compute the standard deviation of the accuracy of each of these models and report this number as an indication of predictive uncertainty. In the uncertainty quantification context, this is known as a *jackknife* estimate. You can do the same thing for other metrics of trustworthiness as well, yielding an extended table of results that goes beyond Table 13.1 to also contain uncertainty quantification, shown in Table 13.2. Such a table should be displayed in a factsheet.

Table 13.2. *Result of testing several attrition models for multiple trust-related metrics with uncertainty quantified using standard deviation below the metric values.*

| Model | Accuracy | Accuracy with Distribution Shift | Disparate Impact Ratio | Empirical Robustness | Faithfulness |
|---|---:|---:|---:|---:|---:|
| logistic regression | 0.869<br>(±0.042) | 0.775<br>(±0.011) | 0.719<br>(±0.084) | 0.113<br>(±0.013) | 0.677<br>(±0.050) |
| neural network | 0.849<br>(±0.046) | 0.755<br>(±0.013) | 1.127<br>(±0.220) | 0.127<br>(±0.021) | 0.316<br>(±0.022) |
| decision forest (boosting) | 0.897<br>(±0.041) | 0.846<br>(±0.009) | 1.222<br>(±0.346) | 0.284<br>(±0.053) | 0.467<br>(±0.016) |
| decision forest (bagging) | 0.877<br>(±0.036) | 0.794<br>(±0.003) | 0.768<br>(±0.115) | 0.182<br>(±0.047) | 0.516<br>(±0.038) |

Chapter 12 noted that deletion diagnostics are costly to compute directly, which motivated influence functions as an approximation for explanation. The same kind of approximation involving gradients and Hessians, known as an *infinitesimal jackknife*, can be done for uncertainty quantification.¹⁹ Influence functions and infinitesimal jackknives may also be derived for some fairness, explainability, and robustness metrics.²⁰

Using a calibrated score or (infinitesimal) jackknife-based standard deviation as the quantification of uncertainty does not allow you to decompose the total predictive uncertainty into aleatoric and epistemic uncertainty, which can be important as you decide to approve the JCN Corporation proactive retention system. There are, however, algorithms applied during model training that let you estimate the aleatoric and epistemic uncertainties separately. These methods are like directly interpretable models (Chapter 12) and bias mitigation in-processing (Chapter 10) in terms of their place in the

¹⁹ Ryan Giordano, Will Stephenson, Ruping Liu, Michael I. Jordan, and Tamara Broderick. “A Swiss Army Infinitesimal Jackknife.” In: *Proceedings of the International Conference on Artificial Intelligence and Statistics*. Naha, Okinawa, Japan, Apr. 2019, pp. 1139–1147.

²⁰ Hao Wang, Berk Ustun, and Flavio P. Calmon. “Repairing without Retraining: Avoiding Disparate Impact with Counterfactual Distributions.” In: *Proceedings of the International Conference on Machine Learning*. Long Beach, California, USA, Jul. 2019, pp. 6618–6627. Brianna Richardson and Kush R. Varshney. “Addressing the Design Needs of Implementing Fairness in AI via Influence Functions.” In: *INFORMS Annual Meeting*. Anaheim, California, USA, Oct. 2021.