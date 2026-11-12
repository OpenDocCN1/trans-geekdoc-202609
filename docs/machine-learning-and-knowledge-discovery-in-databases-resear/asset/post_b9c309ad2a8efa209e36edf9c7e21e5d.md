
For continuous regression, we model aleatoric uncertainty through Beta variance analysis. Given hidden representations \(\mathbf{h} \in \mathbb{R}^d\), distribution parameters are generated via:

\[
\alpha = \sigma(\mathbf{w}_\alpha^\top \mathbf{h} + b_\alpha) + \epsilon, \quad \beta = \sigma(\mathbf{w}_\beta^\top \mathbf{h} + b_\beta) + \epsilon \tag{13}
\]

where \(\sigma(\cdot)\) is the sigmoid function, \(\mathbf{w}_\alpha, \mathbf{w}_\beta \in \mathbb{R}^d\) learnable weights, and \(\epsilon = 10^{-6}\) prevents numerical instability. The predictive uncertainty is characterized by the Beta variance:

\[
\text{Var}(p) = \frac{\alpha\beta}{S^2(S+1)}, \quad S = \alpha + \beta \tag{14}
\]

with the regression output corresponding to the distribution mean:

\[
\hat{y} = \mathbb{E}[p] = \frac{\alpha}{S} \tag{15}
\]

This unified framework enables end-to-end optimization of both molecular representation learning and uncertainty-aware predictions. The integration with dual-view contrastive learning (Sect. 3.2) further enhances model robustness through joint optimization of predictive accuracy and reliability.

## 3.4 Deep Evidence Learning for MS

The TrustworthyMS framework implements end-to-end optimization through joint minimization of predictive fidelity and contrastive alignment objectives. Our architecture processes dual molecular representations from both atomic (\(G\)) and bond-interaction (\(G^r\)) graphs, synthesizing their evidential outputs through learnable fusion mechanisms. Let Beta\((p_i|\alpha_i, \beta_i)\) denote the predicted Beta distribution for \(i\)-th instance, we formulate task-specific loss functions with theoretical guarantees.

**Classification Paradigm.** For binary stability prediction, we derive a Beta-expectation loss through cross-entropy minimization over distribution space:

\[
\mathcal{L}_i^{\text{Beta}} = \int \text{BCE}(y_i, p_i) \text{Beta}(p_i|\alpha_i, \beta_i) dp_i = y_i (\psi(\alpha_i + \beta_i) - \psi(\alpha_i)) + (1 - y_i) (\psi(\alpha_i + \beta_i) - \psi(\beta_i)) \tag{16}
\]

where \(\psi(\cdot)\) is the digamma function, the goal of the loss function is to minimize the expectation of Binary Cross Entropy over the distribution.

**Regression Paradigm.** For continuous half-life prediction with normalized targets \(y_i \in (0, 1)\), we extend the expectation principle to MSE minimization:

\[
\mathcal{L}_i^{\text{Beta}} = \mathbb{E}_{p_i \sim \text{Beta}(\alpha_i, \beta_i)} [(y_i - p_i)^2] = \underbrace{\left(\frac{\alpha_i}{\alpha_i + \beta_i} - y_i\right)^2}_{\text{Mean squared error}} + \underbrace{\frac{\alpha_i \beta_i}{(\alpha_i + \beta_i)^2(\alpha_i + \beta_i + 1)}}_{\text{Uncertainty penalty}} \tag{17}
\]

The final optimization unifies contrastive learning and evidential prediction through adaptive weighting:

\(\mathcal{L} = \mathcal{L}_G + \mathcal{L}_{G^r} + \lambda\mathcal{L}_{\text{CL}}\) (18)

where \(\lambda\) modulates the contrastive learning intensity.

## 4 Experiments

In this section, we empirically evaluate TrustworthyMS across multiple dimensions to validate its performance and reliability. Our experiments include In-Distribution Evaluation on two benchmark datasets for classification and regression tasks, Out-of-Distribution Evaluation to assess generalization under structural dissimilarity, and Ablation Study to quantify the contributions of key components. Additionally, we examine Uncertainty-Aware Prediction Reliability through adaptive confidence thresholding, analyze robustness via Parameter Sensitivity Analysis, and provide interpretability insights in a Case Study. These evaluations collectively demonstrate TrustworthyMS's superior predictive accuracy, calibrated uncertainty quantification, and robust generalization capabilities, establishing its effectiveness for real-world drug discovery applications.

### 4.1 Experimental Setup

**Datasets and Tasks.** We establish a rigorous evaluation protocol spanning both in-distribution and out-of-distribution (OOD) generalization scenarios to comprehensively assess model performance. The benchmark design adheres to previous work [21].

For in-distribution evaluation, we employ two benchmark datasets with complementary characteristics: (1) **Human Liver Microsomes (HLM) Classification** [10]: Contains 5,876 drug-like compounds (3,782 stable/2,094 unstable) with human hepatic metabolic profiles, capturing binary stability outcomes in liver microsomal environments. (2) **Half-Life (HL) Regression** [1]: Comprises 656 compounds with experimentally determined half-life values, standardized via z-score normalization to ensure scale-invariant learning of continuous metabolic stability metrics. These datasets respectively enable classification of metabolic stability phenotypes and regression of degradation kinetics, forming a comprehensive evaluation framework for both discrete and continuous prediction paradigms.

For out-of-distribution (OOD) evaluation, we construct a composite **OOD dataset** by integrating two cross-domain datasets: (1) Clinical Candidates [20] – 111 late-stage therapeutic compounds (82 stable/29 unstable). (2) Rat Microsomes [14] – 499 cross-species metabolites (208 stable/291 unstable). Following standardized protocols [21], we enforce strict structural dissimilarity between training and OOD sets through Tanimoto distance thresholds (< 0.35), ensuring unbiased assessment of model generalization capabilities.

**Baselines.** To comprehensively evaluate the performance differences between the proposed TrustworthyMS model and the nine comparative models, which are categorized into two architectural paradigms. First, we select three *Feature engineering-based machine learning i.e.,* GBDT [10], XGBoost [10] and PredMS [19]. Second, we select *GNN-based methods* which can utilise available graph structure, *i.e.,* MGCN [18], AttentiveFP [24], D-MPNN [10], GAT [10] CMMS-GCL [2] and MS-BACL [21].

**Implementation.** Our experimental framework rigorously follows established benchmarking protocols for metabolic stability prediction [21]. The datasets were partitioned using 10-fold cross-validation to ensure distributional fairness. Classification performance is quantified through four canonical metrics: Area Under the ROC Curve (*AUC*), Accuracy (*ACC*), F1-Score, and Matthews Correlation Coefficient (*MCC*). Regression tasks employ Root Mean Square Error (*RMSE*), Mean Absolute Error (*MAE*), Coefficient of Determination (*R²*), and Spearman’s Rank Correlation (*P*). Implementation details follow original papers with unified hyperparameters. For the feature engineering baselines, we implement the methodologies provided in previous works [10]. For the GNN-based baselines, we adopt the settings from prior research [2, 21]. All models underwent unified training on an NVIDIA RTX 4060Ti (16GB VRAM) using Adam optimizer (initial learning rate is 5e-4), with batch sizes 256. Reported results aggregate mean ± standard deviation over 10 independent runs.

### 4.2 Experimental Results

**In-Distribution Evaluation.** Our comprehensive benchmarking reveals TrustworthyMS’s superior predictive capabilities across both classification and regression paradigms. As quantified in Tables 1 and 2, the proposed architecture establishes new state-of-the-art results through systematic integration of bond-graph modeling and evidential learning.

For classification task, TrustworthyMS achieves class-balanced superiority on HLM classification with 0.866 F1-Score (+0.7% over MS-BACL) and 0.622 MCC (+3.5%), outperforming all graph learning baselines. The 9.8% MCC gain over AttentiveFP (0.564→0.622) and 9.0% improvement versus CMMS-GCL (0.566→0.622) validate the necessity of explicit bond-interaction modeling. Notably, graph-based approaches (GAT: 0.533 MCC) consistently surpass traditional ML methods (XGBoost: 0.548), confirming molecular topology’s critical role in stability assessment. For regression task, TrustworthyMS demonstrates unprecedented accuracy with 0.091 RMSE (-17.5% vs MS-BACL) and 0.833 P-score (+27.8%). Notably, the 43.1% RMSE reduction over CMMS-GCL (0.160→0.091) underscores the limitations of bond-agnostic graph learning in continuous property prediction.
