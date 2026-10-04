# TABLE 5.2
Performance Comparison of Intrusion Detection Classifiers for Different Attack Types

| Name of the Attack | FL-ID | SVM | DT | RF | NB | k-NN |
|---|---|---|---|---|---||}{
| Fingerprinting attack | 0.93 | 0.88 | 0.85 | 0.90 | 0.82 | 0.87 |
| MITM attack | 0.92 | 0.87 | 0.83 | 0.88 | 0.79 | 0.85 |
| Password attack | 0.94 | 0.86 | 0.87 | 0.91 | 0.82 | 0.88 |
| XSS attack | 0.91 | 0.84 | 0.80 | 0.87 | 0.77 | 0.83 |
| Port_Scanner | 0.89 | 0.86 | 0.79 | 0.85 | 0.75 | 0.81 |
| Vulnerability_scanner | 0.93 | 0.89 | 0.86 | 0.89 | 0.81 | 0.87 |
| Backdoor attack | 0.92 | 0.88 | 0.85 | 0.90 | 0.80 | 0.86 |
| DDoS_TCP attack | 0.93 | 0.88 | 0.85 | 0.90 | 0.80 | 0.87 |
| Uploading attack | 0.91 | 0.84 | 0.80 | 0.87 | 0.77 | 0.83 |
| SQL_injection attack | 0.94 | 0.86 | 0.87 | 0.91 | 0.82 | 0.88 |
| DDoS_HTTP attack | 0.91 | 0.84 | 0.80 | 0.87 | 0.77 | 0.83 |
| Ransomware attack | 0.93 | 0.89 | 0.86 | 0.89 | 0.81 | 0.87 |
| DDoS_ICMP attack | 0.92 | 0.87 | 0.83 | 0.88 | 0.79 | 0.85 |
| DDoS_UDP attack | 0.94 | 0.86 | 0.87 | 0.91 | 0.82 | 0.88 |
| Normal | 0.98 | 0.97 | 0.96 | 0.95 | 0.95 | 0.87 |

Recall: The true percentage of positive instances (attacks correctly detected) out of all actual positive instances (ground truth attacks). F1-score: The harmonic mean of precision and recall, providing a balanced measure of model performance. AUC-ROC: The area under the receiver operating characteristic curve, which measures the model's ability to distinguish between positive and negative instances.

# Analysis of Results and Insights

Based on the sample results, we can make the following observations and insights:

Overall performance: The FL-ID model consistently outperforms other approaches (SVM, DT, RF, and k-NN) across different attack types and the normal class. Performance comparison of intrusion detection classifiers for different attack types is shown in Table 5.2. Accuracy: FL-ID achieves the highest accuracy for most attack types, highlighting its ability to classify instances accurately, even for different types of attacks. It also performs exceptionally well for normal instances, achieving a high accuracy of 98%.

Precision and Recall: FL-ID demonstrates competitive precision and recall scores, indicating its ability to minimize false positives and false negatives, making it robust in identifying different attack types while minimizing false alarms.