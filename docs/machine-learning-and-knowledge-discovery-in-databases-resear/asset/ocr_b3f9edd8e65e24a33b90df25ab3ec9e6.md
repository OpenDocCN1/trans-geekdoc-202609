# Algorithm 1. Procedure for the Gx2Mol model

```
1: Data: Gene expression profiles G and SMILES strings X1:n
2: Initialization: the feature extractor Fθ, the molecule generator Gφ
3: // Train the feature extractor.
4: for i = 1 → f_epochs do
5:     Update Fθ using G according to the loss function of Eq. (2).
6: end for
7: // Train the molecule generator.
8: for i = 1 → g_epochs do
9:     Update Gφ using X1:n according to the loss function of Eq. (5).
10: end for
11: // Generate hit-like molecules from scratch.
12: Extract the features FGx using G according to Eq. (4).
13: Generate the corresponding SMILES representation from FGx.
14: // Test the generation task.
15: Calculate the Tanimoto coefficient using known ligands.
16: Select the molecule with the maximum Tanimoto coefficient score as the candidate molecule.
```

# 4 Experiments

Datasets. In this study, we used chemically induced gene expression profiles as training data to train the Gx2Mol model. In addition, we analyzed target protein-perturbed expression profiles with eight knockdown genes and two overexpressed genes to generate hit-like molecules, and disease reversal gene expression profiles as a case study to generate therapeutic medicines.

+   Chemically-induced gene expression profiles were collected from the Library of Integrated Network-based Cellular Signatures (LINCS) database [7]. LINCS database stores the gene expression profiles with a dimension of 978 for 77 human cultured cell lines exposed to various molecules. We analyzed the gene expression profiles of the MCF7 cell line treated with 13,755 molecules whose SMILES string lengths were less than 80 at a concentration of 10 μM.

+   Target protein-perturbed gene expression profiles were collected from the LINCS database. We analyzed the RAC-alpha serine / threonine-protein kinase (AKT1), RAC-beta serine / threonine-protein kinase (AKT2), Aurora B kinase (AURKB), cysteine synthase A (CTSK), epidermal growth factor receptor (EGFR), histone deacetylase 1 (HDAC1), mammalian target of rapamycin (MTOR), phosphatidylinositol 3-kinase catalytic subunit (PIK3CA), decapentaplegic homologue 3 (SMAD3), and tumor protein p53 (TP53), which have been verified to be useful therapeutic target proteins against cancers. The gene expression profiles for the first eight proteins were obtained from gene knockdown profiles of the MCF7 cell line, while those for the latter two proteins were obtained from gene overexpression profiles. When multiple profiles were measured under different experimental conditions for a