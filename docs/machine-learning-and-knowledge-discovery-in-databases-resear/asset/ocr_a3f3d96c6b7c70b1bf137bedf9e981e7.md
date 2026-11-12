polar surface area, number of rotatable bonds, number of aromatic rings, and number of structural alarms). where d_i and W_i represent the desirability function and weight of the i-th descriptor, respectively. Typically, the weights of the eight molecular descriptors were obtained through chemical experiments. In practice, the QED score was calculated by a function in the RDKit tool. The larger the QED score, the more drug-like the molecule.

+   - Synthesizability (SA) is assessed through the SA score, denoted as SA = r_s - \sum_{i=1}^5 p_i. Here, r_s signifies the "synthetic knowledge," representing the ratio of contributions from all fragments to the total number of fragments in the molecule. In this study, r_s is computed from experimental results [8]. Each p_i (i \in \{1, \cdots, 5\}) corresponds to the ring complexity, stereo complexity, macrocycle penalty, size penalty, and bridge penalty, computed using the RDKit tool [15]. A higher SA score indicates greater ease of synthesizing the molecule.

+   - Tanimoto coefficient, which is calculated from the ECFP4 fingerprint [23] with a dimension of 2048. In practice, the ECFP4 and Tanimoto coefficients were calculated using the "GetMorganfingerprintAsBitVect" and "BulkTanimotoSimilarity" functions of the RDKit tool.

# 4.2 Gx2Mol Training

We evaluated the effectiveness of the VAE model in extracting the biological features from gene expression profiles and the capability of the LSTM model to generate new molecules experimentally.

![](bbox=[0.135, 0.54, 0.505, 0.69])

![](bbox=[0.515, 0.54, 0.905, 0.69])

Fig. 2. Distribution of fold change values in the gene expression profile of the molecule "C17H25ClN2O3" exposed in the MCF7 cell. The original gene expression profile of "C17H25ClN2O3" (green) and the reconstructed gene expression profiles (red) have similar distributions. (Color figure online)

Fig. 3. Distribution of fold change values in the average gene expression profile of all molecules exposed in the MCF7 cell. The original gene expression profiles of the training set (green) and the reconstructed gene expression profiles (red) have similar distributions. (Color figure online)

Figure 2 shows a comparison of the distribution of fold change values in the gene expression profile of a molecule between the training set and the recon-