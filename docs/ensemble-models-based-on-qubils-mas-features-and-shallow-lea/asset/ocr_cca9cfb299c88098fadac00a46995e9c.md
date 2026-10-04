# Chemical Research in Toxicology

Article

SiLS-PTOXRA Software for the DLI Prediction.
SiLS-PTOXRA software is a framework of a friendly desktop interface (see Figure 7), and the procedure can be summarized in 3 steps: (1) There is a selection of compounds from the SDF and MDL files. It is important to take into account that the 3D structure is produced it is possible to pass directly to the generation of a 3D structure (RDKit) as an intermediate step. (2) There is a selection of the predictive models and to the method(s) to evaluate. (3) There is a selection of methods to report the results.

After the screening an interface for the process of results is displayed, and with a folder of all the output information of the models is generated. Most, the test sets used in this study are provided as data sets. An experiment on the processing time per molecule was performed by using the test set 2_B_TS_47, and it was found that the process takes about 3 seconds molecule with M2, M9, E12, and E13 methods, considering the consensus method, which was used for the AD. A computer with Intel i7 processor and 4 GB of RAM was used for this experiment.

A general and qualitative comparison of our software with some of the most relevant software reported in the literature is given in Table 6. The software presented here has many advantages with respect to that was previously reported, and can be used for screening of data sets, which is described in the next section.

**Prospective Virtual Screening.** Finally, a large database of natural products, drugs, and EAD-like compounds (described in file S2, Table S1) was used. The results of computational DLI prediction using the in silico E13 model were presented in the screening of 22,678 compounds. Surprisingly, less than 93% was found. Most positive DLI compounds were found in all data sets (48), the data sets of leads and toxic compounds showed that more than 65% of the results were positive-DLI.

Special attention is attracted by the results obtained for the malaria data set, $^{73}$ showed 86% of the cases are positive. This set of molecules contains new and interesting scaffolds (40 chemistries), which were selected to make a diverse collection accessible for the prevention of diseases. Half of these compounds were selected based on their drug properties (ADME-tox rules), and the others were selected as molecular probes. The main factor to include a compound in the malaria box is to show an activity of at least 4 μM with a selectivity ratio of at least 10-fold more than that of cytotoxicity ($CC_{50}$), which was measured using the HEK-293 cell line. In this fact, data set was requested by a pharmacological test to make both data and compounds available. However, only 8% of these compounds would be found in the present (negative-DLI for the E13 model), because the results are hepatic to humans. All of the above scenarios demonstrate the applicability of the in silico E13 model for DLI screening the new candidates in early days of process.

For the 1_0_ADB data set composed of natural compounds, 3% of the molecules are positive-DLI according to the E13 model

| size of set | ACC | SE | data set | descriptor/software | year/classification technique |
|---|---|---|---|---|---||
| 151 (88±6) | 0.783 | 0.818 | training set (10-fold CV) | descriptors containing physicochemical and topological properties (RDKit version 18.3.0) | 2019/ensemble model combining 8 machine learning techniques $^{14}$ |
| 126 (66±18) | 0.817 | 0.744 | test set (10-fold CV) | 2D molecular descriptors and fingerprints (Padel Descriptor) | 2019/ensemble vote classifier containing 9 machine algorithms $^{15}$ |
| 225 (78±30) | 0.867 | 0.889 | test set (5-fold CV) | | 2020/this study, the results of ensemble for E13 are presented here |
| 105 (52±23) | 0.962 | 0.917 | test set (1_R_TS_120) | topological descriptors $^{16}$ | |
| 47 (21±24) | 0.952 | 0.708 | test set (2_B_TS_47) | | |

Table 4 continued

1866

https://doi.org/10.1021/acs.chemchem.9b05552