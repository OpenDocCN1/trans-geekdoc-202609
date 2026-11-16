| Method | TPR | FPR | Accuracy | Precision | F1Score | AUC |
|---|---|---|---|---|---|---|
| NLPLS-Q | 1.000 | 0.069 | 0.947 | 0.811 | 0.896 | 0.966 |
| NLPLS-HD | 0.971 | 0.000 | 0.993 | 1.000 | 0.985 | 0.985 |
| NLPS-HD (filtered) | 0.981 | 0.032 | 0.971 | 0.902 | 0.940 | 0.974 |

# 4.5.1.4 Case (B) – intermittent anomaly detection

Here, we present the capacity of NLPLS-based Q and HD techniques in uncovering intermittent faults. A bias of amplitude 10% of the total variation in the temperature variable $T_5$ is added to the testing measurements for samples in [200, 250] and a bias of 15% is injected between [400, 450]. Table 4.7 provides a summary of detection performance for the three methods. Results showed that the NLPLS-HD had a better detection performance compared to the conventional NLPLS-HD. In the second example, biases of amplitude 3%, 4%, and 5% were injected respectively between samples intervals [200, 250], [300, 350], and [400, 450]. The NLPLS-Q is not able to detect these faults; it is less sensitive to small changes. Table 4.8 shows a summary of detection performance for the NLPLS-HD methods based on unfiltered residuals and filtered residuals using the wavelet denoising approach. As no detection is flagged by the NLPLS-Q approach, its results are not presented in the summary. Results in Table 4.8 highlight the capability of the NLPLS-HD in uncovering these intermittent faults. Furthermore, the NLPLS-HD based on filtered residuals exhibits better detection compared to the NLPLS-HD using raw residuals.

| Method | TPR | FPR | Accuracy | Precision | F1Score | AUC |
|---|---|---|---|---|---|---|
| NLPLS-HD | 0.708 | 0.030 | 0.880 | 0.924 | 0.801 | 0.839 |
| NLPS-HD (filtered) | 0.994 | 0.114 | 0.922 | 0.818 | 0.897 | 0.940 |

# 4.5.1.5 Case (B) – drift anomaly detection

Now, the capability of the NLPLS-based FD methods in monitoring a sensor drift fault is investigated. A gradual ramp fault with a slope of 0.01 (resembling an aging sensor fault) is injected into data of temperature variable $T_5$ at sample 300. Fig. 4.17A–C displays the monitoring results of the three NLPLS-based methods. Fig. 4.17 indicates that the NLPLS-based Q, HD, and HD using filtered residuals methods sense this drift fault respectively at sample 372, 328, and 309. The results clearly suggest that the NLPLS-HD scheme is capable to detect drift fault the earliest compared with the conventional NLPLS-HD scheme.