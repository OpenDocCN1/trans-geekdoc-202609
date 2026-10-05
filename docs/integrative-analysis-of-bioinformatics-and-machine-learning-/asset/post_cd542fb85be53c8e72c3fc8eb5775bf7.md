
# Zhai et al

![](img/6c78b9f3c0cce3d45e0fba0c7bd1be6a_7_0.png)

![](img/6c78b9f3c0cce3d45e0fba0c7bd1be6a_7_1.png)

**Figure 4** Evaluation and visualization of the 22 immune cell type infiltration landscape between different tumors. The left violin plot depicts infiltrations among immune cell types between the 'hot tumor group' and the 'cold tumor group' (in the Cancer Genome Atlas (A) and the GSE32120 (C) sets). The correlation map (right) shows the correlation of immune cells between the two groups in the Cancer Genome Atlas (B) and the GSE32120 (D) sets. The within colored squares show the strength of the correlation: the larger, the stronger the correlation. Blue represents a negative correlation, and red represents a positive correlation. *P < 0.05, **P < 0.01, ***P < 0.001. Natural color.

![](img/6c78b9f3c0cce3d45e0fba0c7bd1be6a_7_2.png)

![](img/6c78b9f3c0cce3d45e0fba0c7bd1be6a_7_3.png)

# Discussion

With the development of immunotherapy and multi-omics analyses, emerging studies on molecular and cellular mechanisms within the intratum TIME have been intensively conducted, but most studies focused on immune cell phenotypes. Tumor cells usually deliver incorrect messages to immune cells by costimulatory molecule signaling and expression within the TIME further increasing immune evasion. As signals for activation of T cells, elaborations on costimulatory molecules in LUAD are still poorly understood. This study used an unsupervised clustering method for identifying subtypes based on CMGs in LUAD, with significantly highlighted comprehensive characteristics and the diagnostic value of CMGs in LUAD cohorts. Moreover, an exploratory analysis in a real-world small sample via IHC revealed that the expression level of the three CMGs had an apparently positive correlation with the pathologic response to neoadjuvant immunotherapy in GSE9157 data, the SVM model using CMGs also showed high accuracy in predicting response to immunotherapy.

In the last few years, immunotherapy, especially ICIs targeting PD-L1/cell death protein 1 and CTLA-4, has presented revolutionary, tremendous efficacy and has been recommended as both first- and second therapies improved survival outcomes for two-thirds of patients patients. However, strategies for improving response to ICIs are warranted, which may include stratifying highly patients or nonresponsive tumors. Currently, PD-L1 is the most used and applied as a predictor by US Food and Drug Administration for immunotherapy in NSCLC. For instance, pembrolizumab was not confirmed as the first-line treatment in patients with NSCLC unless a PD-L1 expression >50% on tumor cells. However, Davis et al. analyzed strategies of 45 US Food and Drug Administration approvals from 2016 to April 2019 found that PD-L1 was a predictor in only 28.9% of patients. Within the same tumor type, the PD-L1–positive response was resulted with a diverse detective assays and instability along different tissue specimens. Mutational burden has also been explored as a potential biomarker for patients with LUAD, but its practical application is limited due to the absence of standardized values for positivity and inconsistencies in its predictive ability in different settings and therapeutic strategies. Emerging studies have focused on complex interactions and immune cell interactions within time, they were subjected to the distribution, spatial associations among immune cells, and neglected signaling during the activation of immune cells.

In the current study, an integrated analysis of cytotoxic molecules, the indispensable signal for activating T cells, was performed for patients with LUAD. Zhang et al. also comprehensively assessed the landscape of cytotoxic molecules in patients with LUAD and developed a prognostic model based on CGMs. However, they established their individual-based model, which required the appropriate use of survival information (supervised). The current study used the unsupervised consensus clustering to evaluate characteristics of CGMs within the tumor microenvironment. This force the statistical power of findings by maximizing the heterogeneity of immune composition within the same cluster and heterogeneity among different cells. A total of 60 CMGs identified through machine learning algorithms, CD80, LTB, and TNFS8, were validated using TIME method, which involved estimation of lymphocytes in hematoxylin and eosin stain to verify its diagnostic validity. CD80, a glycoprotein also known as B7-1 on the surface of antigen-presenting cells.

# Costimulatory Molecule Genes in LUAD

![](img/6c78b9f3c0cce3d45e0fba0c7bd1be6a_8_0.png)

- HEGAS_B_CELL_RECRUITING_PRIMARY
- HEGAS_CHEMOKINOME_SIGNALING_PRIMARY
- HEGAS_CYTOKINE_CYTOKINE_RECEPTOR_INTERACTION
- HEGAS_AXC_SIGNALING_PRIMARY
- HEGAS_DRUG_RESISTANCE_SIGNALING_CYTOXICITY
- HEGAS_T_CELL_RECEPTOR_SIGNALING_PRIMARY

![](img/6c78b9f3c0cce3d45e0fba0c7bd1be6a_8_1.png)

- GORAB_ACTIVATION_OF_IMMUNE_RESPONSE
- GORP_POSITIVE_REGULATION_OF_LYMPHOCYTE_DIFFERIATION
- GORP_NEURAL_DIFFERIATION_ACTIVATION
- GORP_T_CELL_ACTIVATION
- GORP_B_CELL_DIACTIVATION
- GORP_IMMUNE_RECEPTOR_ACTIVITY

![](img/6c78b9f3c0cce3d45e0fba0c7bd1be6a_8_2.png)

- HEGAS_B_CELL_RECRUITING_PRIMARY
- HEGAS_CHEMOKINOME_SIGNALING_PRIMARY
- HEGAS_CYTOKINE_CYTOKINE_RECEPTOR_INTERACTION
- HEGAS_T_CELL_RECEPTOR_SIGNALING_PRIMARY

![](img/6c78b9f3c0cce3d45e0fba0c7bd1be6a_8_3.png)

**Figure 5** shows a functional analysis for the "hot" tumor. The Kyoto Encyclopedia of Genes and Genomes (KEGG) enrichment analysis in The Cancer Genome Atlas (A) and the GSE32110 (C) data sets (https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=gse32110). Gene Ontology analysis for biological processes in The Cancer Genome Atlas (B) and GSE32110 (D) data sets.

# Zhai et

![](img/6c78b9f3c0cce3d45e0fba0c7bd1be6a_9_0.png)

**Figure 6** The selection of cytotoxic molecules (CMGs), A: The lower abscissa is lambda value, and the upper abscissa is the number of CMGs with non-zero coefficient; Least Absolute Shrinkage and Selection Operator (LASSO) shows the variation of each gene cross-validation in The Cancer Genome Atlas (TCGA), B: LASSO profiles of 33 candidate genes. C: Support Vector Machine–Recursive Feature Elimination (SVM-RFE) to identify markers in the TCGA data set. D: Definition of the number of CMGs with non-zero coefficients in GSE32110 data set (https://www.ncbi.nlm.nih.gov/geo/query/acc=Gse32110). E: LASSO profiles of 21 candidate genes after 10-fold cross-validation in GSE32110 data set. F: RMSE, mean square error.

LTBM, also known as non tumor necrosis factor 3, belongs to the TNF family and is able to function in the membrane-bound protein LTB2, which binds to LTFR and further increases production of cytokines, pro-inflammatory cytokines via NF-κB pathways to regulate trafficking and positioning of desired immune cells. Thus, this peptide target might be used as a potent therapeutic strategy as many tumors have persistently activated LTFR signaling. response-antigen cell death protein functions in tumor environment, progression-free survival, and overall. mechanism may be a potential target for immunotherapy, which has been explored in gastric cancer, follicular lymphoma, NSCLC, and others. After interaction with CD28, CD80 can rescue costimulatory signal to T-cell activation, maintain T-cell function and may also block T-cell function through interactions with CTLA-4.

Some limitations have been noted in the current study. First, although the characteristics and data of CMGs were analyzed in a comprehensive manner in patients with LUAD and the signature feature validated in an independent cohort set (GSE180347). Our diagnostic program on CMGs may provide potential targets for further experimental designs to pursue the molecular mechanisms behind them and explore novel therapeutic strategies for LUAD.
