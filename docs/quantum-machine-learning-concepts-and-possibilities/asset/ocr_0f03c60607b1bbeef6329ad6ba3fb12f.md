# 4.6.1 Drug discovery and molecular property prediction

Quantum inference methods have found early applications in the pharmaceutical industry, particularly for predicting molecular properties such as solubility, toxicity, and bioactivity. These tasks are typically posed as binary or multiclass classification problems, where the input is a molecular descriptor or graph-based encoding, and the output is a label indicating a chemical or biological property.

Quantum kernels have been applied to the QM7 and QM9 datasets (quantum chemistry benchmarks), where quantum circuits encode molecular fingerprints and compute similarity via fidelity-based kernels. Studies have shown comparable performance to classical kernels when regularly regularized and noise-mitigated [19].

Variational quantum classifiers trained on binary classification tasks involving molecular datasets (e.g. predicting HIV inhibition) using angle-encoded features. These methods demonstrate feasibility on NISQ hardware remain limited by circuit depth and expressivity [20, 21].

Despite the current performance gap with classical deep learning models, these studies demonstrate the potential for quantum models to serve as subroutines in larger quantum chemistry workflows, in particular where quantum structure can be directly encoded.

# 4.6.2 High energy physics

In experimental high-energy physics (HEP), machine learning is widely used for classifying particle signatures in collider experiments. Quantum inference models have been used as alternatives or supplements to classical classifiers in scenarios such as jet tagging in events from the Large Hadron Collider (LHC), where quantum models classify jets as originating from particles based on high-dimensional event features [22].

Quantum kernel methods [23, 24] and variational classifiers trained on simulated HEP datasets have shown comparable performance to shallow models, in particular when the input dimensionality is reduced via preprocessing or principal component analysis (PCA) [25].

HEP applications are particularly attractive because they involve high-dimensional, structured data, offering an opportunity to leverage the leverage of quantum models. However, achieving state-of-the-art performance remains challenging the maturity of the classical pipeline in this field.

# 4.6.3 Finance

In the financial sector, quantum kernel methods have been proposed for detecting anomalies in transaction networks by computing fidelity-based similarity scores between customer profiles [26].

These applications benefit from the ability of quantum models to capture nonlinear correlations in noisy, structured datasets. However, deployment remains at the proof-of-concept stage due to stringent performance requirements and regulatory considerations.