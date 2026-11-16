# 4.5.1.3 Case (A) - abrupt anomaly detection

The testing data set, which was simulated using the same PFR model, consisted of 500 data samples completely independent from the training data. Here, the feasibility of the three NLPLS-based schemes was verified to sense atypical abrupt changes (sensor bias). Three examples are presented to test the detection capability of NLPLS-based schemes to uncover abrupt faults in PFRs. To assess the abilities of the three fault detection methods, for data with SNR = 30, an additive fault was introduced in x5 between samples 300 and 350, which consists of bias of amplitude equal to 10% of the total variation in x5. In practice, this might be similar to a sudden sensor offset or miss-calibration. Table 4.5 provides a summary of detection performance by method. As the magnitude of this abrupt fault is relatively large and the level of SNR is also high (i.e., SNR = 30), the performance of the three methods is slightly comparable. We can see an improvement when applying the NLPLS-HD, compared to the conventional NLPLS-Q methods by achieving the highest AUC of 0.975.

TABLE 4.5 Detection performance by method (10% bias, SNR = 30).

| Method | TPR | FPR | Accuracy | Precision | F1Score | AUC |
|---|---|---|---|---|---|---|
| NLPLS-Q | 0.941 | 0.000 | 0.994 | 1.000 | 0.970 | 0.971 |
| NLPLS-HD | 0.980 | 0.031 | 0.970 | 0.781 | 0.870 | 0.975 |
| NLPLS-HD (filtered) | 1.000 | 0.053 | 0.952 | 0.680 | 0.810 | 0.973 |

To assess the ability of the various fault detection methods under low SNR (i.e., SNR = 5). The detection performance of the three methods is given in Table 4.6. The conventional NLPLS-Q can recognize this fault but with several missed detection and moderate AUC (TPR = 0.706 and AUC = 0.853). This highlights the sensitivity of the Q statistic to noisy data. Here, the NLPLS-HD statistic with filtered residuals achieves a better performance over the other test statistics by achieving a higher AUC of 0.983 and F1-score of 0.872. An interesting observation is that the NLPLS-HD is more robust to noise compared to the NLPLS-Q. Furthermore, applying NLPLS-HD on filtered data using a wavelet filter, which is a powerful tool to reduce noise in data, significantly improves the detection performance under low SNR values, compared with other methods.

TABLE 4.6 Detection performance by method (10% bias, SNR = 5).

| Method | TPR | FPR | Accuracy | Precision | F1Score | AUC |
|---|---|---|---|---|---|---|
| NLPLS-Q | 0.706 | 0.000 | 0.970 | 1.000 | 0.828 | 0.853 |
| NLPLS-HD | 0.961 | 0.031 | 0.968 | 0.778 | 0.860 | 0.965 |
| NLPLS-HD (filtered) | 1.000 | 0.033 | 0.970 | 0.773 | 0.872 | 0.983 |