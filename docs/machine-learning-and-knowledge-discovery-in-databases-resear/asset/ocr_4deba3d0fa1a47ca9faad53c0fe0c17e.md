model performance, and (3) refining the posterior distribution to guide further searches. This approach efficiently identifies high-quality rules while mitigating overfitting and redundancy, ensuring an optimal balance between model accuracy and interpretability. Unlike brute-force search methods, Bayesian optimization efficiently explores the parameter space.

# 5 Experiments

# 5.1 Experimental Setup

**Datasets.** We use four real-world disease-specific datasets: AKI (Acute Kidney Injury), Stroke, Sepsis, and CAD (Coronary Artery Disease). These medical datasets are extracted from MIMIC-IV [12], a large-scale medical database that contains electronic health records. Table 1 presents the statistical information of these datasets. The number sign # denotes a summation operation. As shown in the table, these four datasets increase in size from top to bottom. In the AKI dataset, disease progression to Phase III serves as the target event. The Stroke dataset focuses on patients transitioning from moderate to severe conditions. In the Sepsis dataset, the occurrence of low urine output is tracked as a target of organ failure. In the CAD dataset, patient mortality is defined as the target event.

**Baselines.** We adopted three state-of-the-art models with explicit rule-mining capabilities: TEmporal Logic rule LearnER (TELLER) [15], Clock Logic Neural Network (CLNN) [24], and CLUSTER [14].

**Evaluation Metrics.** To assess the performance of the models, we conducted comprehensive experiments. Each dataset is randomly split into an 80% training set and a 20% test set. The evaluation metrics used to measure predictive performance include _Negative Log-Likelihood (NLL)_, _Root Mean Squared Error (RMSE)_ and _Rule Accuracy (Acc)_. Rule accuracy means the proportion of correct rules.

# Table 1. Datasets statistics.

| Dataset | # Sequences | # Types | # Events | Seq. Length | Avg. Length |
|---|---|---|---|---|---|
| AKI | 2327 | 38 | 58k | [3, 123] | 24.93 |
| Stroke | 4951 | 48 | 447k | [2, 2207] | 97.47 |
| Sepsis | 20081 | 66 | 1375k | [2, 1406] | 68.46 |
| CAD | 12459 | 56 | 3519k | [6, 7955] | 282.45 |