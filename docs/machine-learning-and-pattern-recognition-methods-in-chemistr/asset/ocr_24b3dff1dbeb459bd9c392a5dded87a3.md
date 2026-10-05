# Introduction to python

Up to now, many useful packages are developed for many research areas. In chemoinformatics and bioinformatics too, many useful packages like ChemoPy, PyDPL, DeepChem, sklearn, and pyMCR are developed. In this chapter, these packages are introduced and discussed. Then, the python codes of multivariate algorithms, which are investigated in Chapter 3, are given.

# 2. ChemoPy

ChemoPy is a freely available python package, which is introduced by Cao, Xu, Hu, and Liang (2013). Many applications in chemoinformatics need to provide a discriminative representation for a small molecule. Also, there are many molecular representation algorithms in the literature: ChemoPy provides seven types of molecular fingerprints for drug molecules. These types include topological fingerprints, electro-topological state (E-state) fingerprints, MACCS keys, FP4 keys, atom pairs fingerprints, topological torsion fingerprints, and Also this package could provide a large number of 3D molecular descriptors by applying a semi-empirical quantum chemistry program MOPAC (Stewart, 1990). The last version of this package is released on January 31, 2013, and it runs on MS Windows and Linux. This package could be accessible from this link https://code.google.com/archive/p/pychem/downloads.

# 3. PyDPI

PyDPI (drug-protein interaction with Python) is another free available toolkit that is provided for drug discovery and is useful in chemoinformatics, bioinformatics, chemogenomics, and proteogenomics (Cao, Liang, et al., 2013). This package is available via https://sourceforge.net/projects/pydpicao/.

PyDPI provides the known state-of-the-art descriptors for protein sequence, molecule-protein interaction network, and protein-ligand interaction network. PyDPI computes six feature groups for protein sequence including amino acid composition (consists of three features amino acid composition, dipeptide composition, and tripeptide composition (features)), autocorrelation (consists of normalized Moreau-Broto autocorrelation, Moran autocorrelation, and Geary autocorrelation features), CTD