data as previously described [28], using around 25,828 annotated cellular pathways obtained across seven well-annotated gene sets obtained from the Human Molecular Signatures Database (MSigDB). The significantly identified pathways were then subjected to the normal GSEA considering the significance cut-off of p-value < 0.05. The significantly activated pathways were further processed to identify the differentially enriched genes between the MDD patients and HCs. As parameters, we used; random permutations=1000, permutation type=sample labels and correlation-based weighting=1. Top leading gene analysis was applied for all significant gene sets to identify the core leading genes for each pathway. Only genes, with fold (FC)>1.5 were considered as upregulated and FC<0.5 considered as downregulated, were further explored in the downstream analysis.

# 2.4. Machine Learning pipeline

ML analysis was performed on the same mapped gene expression list from the GSE98793 dataset using SkLearn v.1.2.1 in Python v3.9. To examine various ML models with different feature selection (FS) approaches a common ML pipeline applied [29]. The ML pipeline selection involves FS and hyperparameter optimization for different models including Logistic Regression (LR), Random Forest (RF), XGBoost (XGB), Support Vector Machine Classifier (SVM) and K-Nearest Neighbors (KNN) with 10-fold cross-validation (Figure 1.C). The prediction performance of each classification model was estimated by accuracy, F1 score and ROC-AUC measures. The accuracy is the proportion of correctly predicted subjects among all subjects. Its formula is presented below:

> Accuracy = \frac{TP*TN}{TP+FP+FN}

where TP = True Positive; FP = False Positive; TN = True Negative; FN = False Negative

The F1 score is the harmonic mean of precision and recall. The precision is the fraction of truly predicted subjects related to a certain class among all subjects for which a classification model was assigned to this class. The recall is the fraction of truly predicted subjects related to a certain class among all subjects related to this class. We used the F1-macro score, where averaged

F1 scores.

> Precision = \frac{TP}{TP+FP}

> Recall = \frac{TP}{TP+FN}

all

per-class