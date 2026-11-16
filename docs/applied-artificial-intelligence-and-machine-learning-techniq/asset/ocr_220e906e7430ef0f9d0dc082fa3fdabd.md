# 4.2.3 Molecular Representation

In machine learning, fingerprints are numerical representations of molecular structures and properties, enabling the analysis and comparison of molecules. Structural fingerprints, such as MACCS and Morgan, encode molecular information into a format that can be processed by algorithms [12]. These fingerprints are used in various applications, including virtual screening to identify potential drug candidates, QSAR modeling to predict biological activity, molecular similarity searching, and clustering/classification to group molecules by similarity or activity [13]. By leveraging fingerprints, machine learning models can efficiently process and analyze large molecular datasets, accelerating drug discovery and development [14].

MACCS (molecular access system) encodes molecular structure and properties into a 166-bit binary vector. MACCS is a widely used fingerprinting method in cheminformatics and drug discovery. In this, four different fingerprints were chosen. Utilizing a hashing algorithm, MACCS captures various molecular features, including atom types and counts, bond types and counts, ring systems and connectivity, and functional groups and fragments [15].

Morgan fingerprints, specifically Morgan 2 and Morgan 3, are circular fingerprints that capture molecular structure and atom neighborhoods, providing a more comprehensive representation of molecular topology [16].

A substructure fingerprint is a type of molecular fingerprint that identifies the presence of specific substructures or functional groups within a molecule. This fingerprinting method breaks down a molecule into its constituent parts, such as rings, chains, and functional groups, and generates a binary vector indicating the presence or absence of each substructure [17]. Machine learning models were built here with these fingerprints to choose the best with the best performing model.

# 4.2.4 Machine Learning Models Construction

Machine learning models were built for each of the four fingerprints, making it 32 models with each peptidase enzymes-ligands dataset. Eight ML algorithms were generated using the prepared enzymes bioclass dataset. To create ML models, Google Colab Notebook was used. First, the necessary Python packages were imported onto the workspace, including Matplotlib, RDKit, sklearn, and others. Subsequently, the following models were accessed to predict the status of breast cancer.

# 4.2.4.1 Random Forest Classifier

This is an ensemble technique for machine learning that makes multiple decision trees based on random subsets of data for the purpose of classifying, regressing, and more [18].

# 4.2.4.1.1 Logistic Regression

Logistic regression focuses on the relationship between a predictor variable and an outcome variable that would have applications in predicting binary or multi-class outcomes and thus is an important technique in health care and beyond [19].