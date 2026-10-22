**Table 8.3** Statistical properties for training, cross-validation, and verification discharge data set.

| Statistical properties | Training | Cross-validation | Verification |
|---|---:|---:|---:|
| Data points (hours) | 15,058 | 6,453 | 5,000 |
| Maximum (m³/s) | 167.17 | 163.87 | 157.75 |
| Minimum (m³/s) | 0.84 | 1.78 | 1.36 |
| Average (m³/s) | 14.45 | 14.12 | 12.64 |
| Standard deviation (m³/s) | 21.05 | 23.11 | 19.15 |

**Table 8.4** Statistical properties for training, cross-validation, and verification rainfall data set.

| Statistical properties | Training | Cross-validation | Verification |
|---|---:|---:|---:|
| Data points (hours) | 15,058 | 6,453 | 5,000 |
| Maximum (mm) | 28.23 | 20.67 | 19.07 |
| Minimum (mm) | 0.00 | 0.00 | 0.00 |
| Average (mm) | 0.14 | 0.18 | 0.16 |
| Standard deviation (mm) | 0.88 | 1.03 | 0.93 |

and a linear model as an output layer is used to predict discharge with a maximum forecast horizon of 12 hr in Grande de San Miguel river basin in El Salvador. Each of these trained MLP-ANNs models was compared with observed data using visual inspection and goodness-of-fit functions (presented above) and they were also compared with a naïve reference model.

Figure 8.6 presents the results between the observed and simulated discharge for the verification data set and 1 hr of lead time. These results show an excellent representation of both high and low discharge in La Canoa station and confirm the fact that the MLP-ANN is capable of predicting the discharge at 1 hr ahead.

It is also important to explain how the MLP-ANN forecast model is weighting its inputs. In Figure 8.7 is shown the relation between the input variables for the 1 hr of lead time and the resulting weights for each hidden nodes or neurons in the MLP-ANN model. The figure shows that the discharge overweighs the rainfall in the network since the past discharge has a major effect on the forecast model.