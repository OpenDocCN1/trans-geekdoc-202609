# **18.4.2.5 Example Case Studies**

This section provides two example scenarios from the COD dataset with numeric data to clarify how the proposed ADM works and to illustrate the need for the proposed ensemble model [32]. The detailed description of the dataset can be found in our published work [7].

# **Case Study 1**

The first case study was performed to check the ADM performance on a benign sample. The prediction of the OCSVM model produces the to be −0.038 − and labels the sample as an anomaly since the output is negative. The sample is labeled as benign by the AE model since the calculated (=0.41) does not exceed threshold, E(=3.38). Moreover, the normalized OCSVM threshold, was found to be 0.84, and normalized weight, is calculated to be 0.28, which makes the normalized weight of OCSVM to be 0.28. Similarly, the value of was found to be 0.46. Since is higher than , the ensembled model prediction corresponds to the prediction of AE model. Thus the ensembled model correctly helps to reduce the false anomaly rate.

# **Case Study 2**

Case study 2 is performed on two attack samples. The attack samples are obtained from a benign sample considering two different cost increment attacks.

For the attacked sample, the OCSVM model predicted to be 0.06 and labeled the sample as an anomalous sample. However, the was found to be 1.23, which does not exceed . Hence, the sample is labeled as benign by the AE model. The measured is 0.42. Similarly, the value of was determined as 0.39. The value of being higher than the makes the ensembled decision correspond to the OCSVM prediction. Thus the ensembled model lowers the false benign rate for critical attack samples.

# **18.4.2.6 Evaluation Result**

We evaluate the effectiveness of the proposed ADM using several metrics. Figure 18.6 shows the ADM’s performance evaluation based on the cost consumption attack. The cost consumption attack attempts to measure CO₂, temperature, and occupancy sensor measurement of a smart building with an intent to increase the overall energy consumption of the building. We can observe a lot of such points in Figure 18.6, where both AE and OCSVM models differ in their opinions. However, the proposed ADM ensembles both models and can produce correct labeling in almost all cases. The OCSVM model does not provide any false benign labeling, while the AE model does not generate any false anomaly labeling in all considered attacks. That’s why those legends are missing from the figure. The proposed model performs better than the individual OCSVM and AE models based on accuracy, precision, recall, and F1-score performance metrics for all considered attacks [7].