
## 2. Materials and Methods

### 2.1. Transcriptome MDD datasets

The Gene Expression Omnibus database (GEO) was searched for publicly available MDD and HCs transcriptomic datasets (https://www.ncbi.nlm.nih.gov/geo/) to choose the appropriate gene expression datasets. The selection criteria included studies for Homo sapiens and MDD patients recruited as international practice guidelines in psychiatry. Studies with no healthy control samples or with a large batch effect were excluded. The GSE98793 dataset, which met all the inclusion criteria, was selected and processed [27]. The samples were performed in two batches, with each batch information was extracted from phenotypic data. This dataset consists of high-resolution gene expression sets retrieved from whole blood samples of 128 MDD patients and 64 healthy controls (HCs). The Affymet Human Genome U133-Plus 2.0 gene-chip was used. The MDD patients were diagnosed if at least two episodes of depression satisfying DSM-IV or ICD10 criteria were identified using the semi-structured Schedule for Clinical Assessment in Neuropsychiatry (SCAN). The demographic and clinical details of the GSE98793 dataset are listed in Supplementary Table S1.

### 2.2. Microarray Normalization and Adaptive Filtering

The Affymetrix microarray covers more than 54,000 probes. The raw CEL files were downloaded and analyzed using an in-house R script pipeline. Logarithmic transformation and batch effect correction were performed to eliminate the experimental effect on the datasets. Next, to normalize and filter out the background noise, MAS5 and GCRMA packages from Bioconductor (https://www.bioconductor.org/) were applied. Non-specific filtering was used to extract the common variant probes, while adaptive filtering was applied to identify probes with MAS5 value > 50 and a coefficient of variation > 10% in GCRMA. Then, processed probes were intersected across all MDD patients and HCs to identify common variant probes. The filtered common probes between all samples from the two batches of the dataset were combined into a data matrix and mapped to the gene list using Broad Institute software (https://www.gsea-sigdb.org/gsea/index.jsp). For the collapse of gene symbols, probes with maximum expression were selected as the expression value for the gene. Probes mapping to housekeeping genes or not assigned to any gene were excluded. The workflow of the bioinformatics analysis is shown in Figure 1.A.

### 2.3. Gene Set Enrichment Analysis

The mapped gene expression list was thereafter subjected to the absolute Gene Set Enrichment Analysis (GSEA) to identify the activated and enriched cellular pathways in MDD patients in comparison to HCs (Figure 1.B). The absolute GSEA search was carried out on the expression data as previously described [28], using around 25,828 annotated cellular pathways obtained across seven well-annotated gene sets obtained from the Human Molecular Signatures Database (MSigDB). The significantly identified pathways were then subjected to the normal GSEA considering the significance cut-off of p-value < 0.05. The significantly activated pathways were further processed to identify the differentially enriched genes between the MDD patients and HCs. As parameters, we used: random permutations=1000, permutation type=sample labels and correlation-based weighting=1. Top leading gene analysis was applied for all significant gene sets to identify the core leading genes for each pathway. Only genes, with fold (FC) > 1.5 were considered as upregulated and FC < 0.5 considered as downregulated, were further explored in the downstream analysis.

### 2.4. Machine Learning pipeline

ML analysis was performed on the same mapped gene expression list from the GSE98793 dataset using SkLearn v.1.2.1 in Python v3.9. To examine various ML models with different feature selection (FS) approaches a common ML pipeline was applied [29]. The ML pipeline selection involves FS and hyperparameter optimization for different models including Logistic Regression (LR), Random Forest (RF), XGBoost (XGB), Support Vector Machine Classifier (SVM) and K-Nearest Neighbors (KNN) with 10-fold cross-validation (Figure 1.C). The prediction performance of each classification model was estimated by accuracy, F1 score and ROC-AUC measures. The accuracy is the proportion of correctly predicted subjects among all subjects. Its formula is presented below:

Accuracy = $\frac{TP \cdot TN}{TP+FP+FN}$

where TP = True Positive; FP = False Positive; TN = True Negative; FN = False Negative

The F1 score is the harmonic mean of precision and recall. The precision is the fraction of truly predicted subjects related to a certain class among all subjects for which a classification model was assigned to this class. The recall is the fraction of truly predicted subjects related to a certain class among all subjects related to this class. We used the F1-macro score, where averaged per-class F1 scores are:

Precision = $\frac{TP}{TP+FP}$

Recall = $\frac{TP}{TP+FN}$

F1 = $2 \cdot \frac{precision \cdot recall}{precision + recall}$

ROC-AUC is the area under the error curve, which evaluates the quality of the model without being tied to a specific threshold. For building the ROC curve, TPR against the FPR is plotted, and then the area under the resulting curve was calculated.

TPR = $\frac{TP}{TP + FN}$

FPR = $\frac{FP}{FP + TN}$

### 2.5. Feature selection using MI.

Transcriptomic data consists of a large number of genes (features) that are much more than the number of samples, which leads to overfitting. We used mutual information (MI) to select features.

### 2.6. Machine Learning

(Note: This section in the OCR text contained highly repetitive/fragmented content from the source, cleaned up based on the context provided in the 2.4 and 2.7 sections).

### 2.7. Evaluation Measures of the Classification Performance

In order to provide a performance assessment of the best-built classifiers that were trained on the merged (batch 1 and 2) discovery dataset, evaluation measures of the classification were performed in independent external datasets. We used F1-score and ROC-AUC as evaluation metrics.

### 2.8. Functional mapping and annotation of biomarkers to Human brain regions

To evaluate the brain structures among MDD patients associated with the identified biomarkers, functional mapping and annotation of the Human brain regions were performed using the Allen Human Brain Atlas (AHBA).
