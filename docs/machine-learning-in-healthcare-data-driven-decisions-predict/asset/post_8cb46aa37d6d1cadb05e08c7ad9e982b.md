
$$
w_{t+1} \rightarrow \{w_{t+1}^1, w_{t+1}^2, \dots, w_{t+1}^K\} (7)
$$

Each client receives the latest model to begin a new local training round. The FL cycle continues over multiple communication rounds. In each round, clients retrain the model with fresh updates from the server, and the server refines the global model using new encrypted contributions. This iterative process is repeated until the model reaches a desired level of performance or converges according to predefined criteria, such as minimal changes in validation accuracy or loss. This formulation supports various enhancements such as differential privacy, client clustering etc.

### Differential Privacy (DP)

Differential privacy is integrated into the FL process to protect individual patient records from being inferred through model updates. Before transmitting updates to the server, each client injects calibrated random noise into its model parameters or gradients. Information leakage is minimized by this noise, which is derived from a probability distribution and ensures that the contribution of any one data point is unidentifiable in the final output [22]. A privacy budget, which measures the amount of information about a particular data point might be revealed, regulates the degree of privacy. Stronger privacy assurances are offered by smaller models, but they may also decrease model utility, necessitating careful trade-off adjustment. Let \(\Delta w_t^k\) be the model update from client k at round t. DP is enforced by adding Gaussian noise:

```
\(\hat{w}_t^k = \Delta w_t^k + N(0, \sigma^2 I)\) (8)
```

where \(N(0, \sigma^2 I)\) is Gaussian noise with standard deviation \(\sigma\) calibrated based on the desired privacy budget (\(\epsilon\), \(\delta\))-differential privacy.

### Secure Multiparty Computation (SMPC)

To further strengthen security against reconstruction or inference attacks, SMPC [23] is employed during model update sharing. Multiple parties can jointly compute a function over their inputs while maintaining the privacy of those inputs thanks to SMPC. To ensure that no one entity has access to the entire update, each client in the federated setup divides its model update into secret shares and distributes them around various parties or the server. Only when the shares are combined during aggregation can the server reconstruct the sum of updates without learning any individual contribution. This approach eliminates the need to trust the server with sensitive updates and protects against insider and collusion threats. Let \(\Delta w_t^k\) be the model update vector from client k. The client splits this vector into M secret shares:

```
\(\Delta w_t^k = s_1^k + s_2^k + \dots + s_M^k\) (9)
```

Each share \(s_i^k\) is distributed to a corresponding party. The central server aggregates the sum of all shares from all clients:

```
\sum_{k=1}^K \Delta w_t^k = \sum_{k=1}^K \sum_{i=1}^M s_i^k
```

As long as a subset of shares (less than M) cannot reconstruct \(\Delta w_t^k\), the client's data remains secure. The aggregation is done without reconstructing individual updates and its privacy is preserved. To increase generalization across clients with varied patient populations and data distributions, PFL is used.

PFL accounts for heterogeneity in client data distributions, which frequently occurs in multi-institutional clinical research. In PFL, each client fine-tunes the shared global model on its local dataset after global model training is finished. The model is able to learn from the shared global knowledge, while also adapting the model performance towards the clients' specific data characteristics, such as population demographics or disease prevalence. In this manner, PFL achieves generalization while maintaining privacy. PFL is especially useful in healthcare where patient populations differ greatly across different institutions. Let W_T represent the final global model after T rounds of FL. Client k performs the local fine-tuning by minimizing a personalized objective:

```
w_T^{k, PFL} = \arg\min_w [F_k(w) + \lambda ||w - w_T||^2]
```

Here, \(F_k(w)\) is the local empirical loss on client k’s data, \(\lambda ||w - w_T||^2\) is a regularization term to prevent overfitting and retain global knowledge. This is also known as local regularization and is a common PFL technique.

### Clustering-Based Aggregation

Clustering-based aggregation is implemented to significantly improve model speed and capacity when non-IID data is present. Using characteristics like label distribution, gradient similarity, or update distance, this technique creates clusters of clients with comparable data distributions. Within each cluster, models are aggregated separately, creating multiple semi-specialized models instead of a single global model. This strategy reduces the negative impact of aggregating highly dissimilar updates and improves training efficiency and accuracy for clients with aligned data characteristics. Assume the clients are portioned into C clusters \(\{C_1, ... C_c\}\) based on a similarity metric sim \((k_i, k_j)\). For each cluster \(C_v\), the server performs a cluster-wise model update:

```
w_{t+1}^{(c)} = \sum_{k \in C_c} \frac{n_k}{\sum_{j \in C_c} n_j} w_t^k
```

Each client in cluster \(C_c\) receives its corresponding cluster-specific model \(w_{t+1}^{(c)}\) for the next training round. Clustering can be based on cosine similarity of gradient updates or distributional divergence between client datasets [24].

## 4 Results and Findings

The study uses simulated datasets designed to mimic the statistical properties of real-world EHRs or actual clinical datasets from multiple healthcare institutions. These datasets include structured features (e.g., lab results, vitals, and diagnosis codes) and are distributed across institutions with varying degrees of heterogeneity in demographics and disease prevalence. Each client retains its own data silo without sharing raw records.

In an attempt to extensively evaluate both the performance of prediction and privacy protection of the proposed FL models, several important measures are employed. Accuracy measures the global accuracy of the model by measuring the rate of correct predictions for all classes. Precision examines the validity of positive predictions, that is, the proportion of positive cases predicted which are actually positive. Recall or sensitivity measures the model’s capacity to spot the actual positive cases, an important area in medical diagnosis to reduce false negatives. In addition, AUC-ROC quantifies the discriminant power of the model at different classification levels, providing a balanced measure of performance, particularly on imbalanced data. Overall, these tests form a composite framework to quantify effectiveness and reliability in privacy-concerning medical AI systems.

The efficiency of the introduced privacy-protecting FL framework is conducted with the comparative evaluation against conventional FL methods. The traditional FL baseline applies the basic federated averaging (FedAvg) algorithm without applying any extra privacy-protection enhancement, acting as a comparison point for model performance as well as privacy vulnerability. On the other hand, the suggested method PEFL in this research combines the state-of-the-art methods of DP, secure aggregation, and model customization to enable enhanced confidentiality and responsiveness across heterogeneous sources. The comparison indicates the better trade-off accomplished by the suggested method between preserving high classification accuracy and providing robust privacy assurances in collaborative healthcare scenarios.

### Table 1: Traditional FL versus privacy-enhanced FL.

| Feature/metric | Traditional FL | Proposed privacy-enhanced FL |
| :--- | :--- | :--- |
| Accuracy (%) | 88.7 | 89.9 |
| Precision (%) | 87.3 | 89.1 |
| Recall (%) | 89.0 | 90.2 |
| AUC-ROC | 0.91 | 0.92 |

Table 1 illustrates the performance of traditional FL and the proposed PEFL on key classification metrics. Accuracy improves from 88.7% to 89.9%, which indicates that the enhanced method predicts more accurately overall. Precision improves from
