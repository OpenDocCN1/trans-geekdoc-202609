
![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_172_0.png)

## Table 5.4 List of commonly used energy-based metrics [61, 62].

| No. | Metric | Formula | Notes |
|---|---|---|---|
| 1 | Model Size Efficiency | Model Size Efficiency = Accuracy / model size | - |
| 2 | Training Time Efficiency | Training Time Efficiency = Accuracy / training time | - |
| 3 | Training Energy Efficiency | Training Energy Efficiency = Accuracy / training energy | - |
| 4 | Inference Time Efficiency | Inference Time Efficiency = Accuracy / inference time | - |
| 5 | Inference Time Energy | Inference Time Energy = Accuracy / inference energy | - |
| 6 | Estimated Energy | Estimated Energy = MS×(TT + PT) where MS: model size, TT: training time, and PT: prediction time. | • Combines model size with training and prediction time. • Smaller values are favorable. • Has a hypothetical minimum value = 1.0 MB × (0.5 + 0.5) sec = 1 MB.sec. |

## 5.6.2 Domain-specific Metrics and Indicators

Functional metrics and indicators can showcase new insights into the performance of ML models that can be more related to the mechanics of the problem itself as opposed to the data. Let me present two cases 29 that stem from my research in the structural fire engineering area [63].

Fire resistance (FR) time of columns is often measured in minutes. This FR is then compared to a range that spans 60 min, 30 i.e., < 60 min, 60–120 min, 120–180 min, and 180–240 min. Suppose a column falls after 179 min under standard heating conditions. Then, FR for this column is 179 min.

Building codes do not recognize FR, but instead adopt fire resistance rating (FRR). FRR returns FR to the closest (safest) full 60 min range. Thus, the same column of FR = 179 min would have a FRR of 120 min. 31

Unlike other regression or classification metrics, which give statistical insights into the predictivity of the ML model at the global level, a new functional metric could be applied to individual observations. This metric, to be referred to as the Clemson Metric (CM), examines the predicted FRR obtained from a ML model to the observed FRR from fire tests, as seen in Equation 5.1.

For example, say that a ML model predicts FRR of a given RC column to be 120 min; however, this column actually failed within 60 min. In this particular example, CM returns a non-zero value (i.e., [120-60]/60 = 1.0), which indicates poor fitness.

Clemson Metric (CM) = \frac{FRR_{predicted} - FRR_{ground truth}}{60} (5.1)

where CM is applicable for FRR ranging between 0.0 and 240 min, with a zero as a favorable performance that suggests a correct ML prediction. Negative scores of CM indicate conservative predictions, and positive scores indicate unconservative predictions.

To extend CM from assessing individual observations to examining the global predictivity of the ML model, the CM can be extended into another functional metric, the Cumulative Clemson Metric (CCM) – see Equation 5.2. As you can see, the CCM compares the percentage of all observations that pass the CM metric (i.e., return zero) to the total number of observations examined by the ML model.

Cumulative Clemson Metric (CCM) = \frac{\text{no.of observations of } \left( \frac{FRR_{predicted} - FRR_{ground truth}}{60} = \text{zero} \right)}{\text{total number of observations}} (5.2)

To establish the degree of model predictivity, the CCM is supplemented with four hypothetical cut-offs of <25%, 25–50%, 50–75%, and >75%. 32 These cut-offs articulate the expected goodness of a ML model. For instance, if the model predicts the correct FRR for all elements under examination with 87% 33 accuracy or higher, then this model is deemed of “excellent” fitness. Given the nature of their derivation, the CM and CCM metrics can be used in regression and classification problems. 34

Let us shift our discussion toward a more involved problem where a ML model predicts a continuous response (as opposed to a single value or class). Say we create a ML to help us predict deformation–time history 35 of load bearing members under fire conditions.

A glimpse into the above scenario shows that we are looking at a metric or indicator that also happens to be continuous. Such a metric is called the Maximum Response Deviation (MRD) indicator. This MRD evaluates ML predictions within a specified range of observations (say, during the fire exposure time, within the first 30 min of fire exposure, etc.). This indicator builds an upper and lower bound based on the largest observation obtained (i.e., temperature or deformation), then divides its value over equally spaced intervals of the duration of the fire test. 36 ML predictions, if proper, would fit within the upper and lower bounds.

Maximum Response Deviation (MRD) = Observed response_{at time,t} \pm \frac{\text{Maximum observed response}}{\text{Largest observed time} / \text{Selected time interval}} (5.3)

For example, say that the observed temperature was measured at 50 min as 500°C. Then, an engineer may construct the upper bound of the MRD indicator to the nearest 10 minutes such that:

MRD at 1 min = 25°C at 1 min + 500/(50/10) = 125°C at 1 min
MRD at 10 min = 75°C at 10 min + 500/(50/10) = 175°C at 10 min
MRD at 20 min = 153°C at 20 min + 500/(50/10) = 253°C at 20 min

And so on...

The time and corresponding temperatures as calculated from MRD can then be plotted against the observed and ML-predicted responses.

ML model predictions can then be compared across these two bounds. If all predictions lay within the bounds, then the model is said to have a perfect match. If < 25%, 25–50%, 50–75%, and > 75% of model predictions fall within these bounds,

32 <25% (poor), 25–50% (fair), 50–75% (strong), and >75% (excellent) fitness.
33 It is worth noting that this value is used herein as an example. Also note that like other traditional metrics, the CCM can be applied for training, validation, and testing stages, as well as to the whole database.
34 I am (e.g., mid-span deformation of a beam under fire loading). 38 Naturally, the deformation slowly grows. Thus, we can expect the deformation to continue to increase organically until failure. If we re-organize the ground truth data in an ascending or descending order, then we could arrive at a plot similar to Figure 5.5 which shows that the ordered ground truth points can be represented in a smooth line. 39 The same figure also shows that the predicted data pertaining to the ordered ground truths oscillates around the ground truths. 40

It is clear from the same figure that there are some *spots* where the oscillation (deviation) is small, while in others, the oscillation is large. It is also evident that the model seems to predict deformations up to 80 mm more adequately than larger deformations. In fact, the model seems to consistently underpredict deformation over 80 mm. 41, 42
