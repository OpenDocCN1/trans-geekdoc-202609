| Dataset | M | T | E | P | C | Me | D | Ref. | Link to Dataset |
|---|---|---|---|---|---|---|---|---|---|
| CCLE | M | T | E | P | C | Me | D | [10, 11] | https://sites.broadinstitute.org/ccle/datasets |
| NCI-60 | | | | | | | D | [12] | https://dtp.cancer.gov/discovery_development/nci-60/ |
| GDSC | M | T | E | | C | | D | [13, 14] | https://www.cancerrxgene.org/ |
| gCSI | | | | | | | D | [15] | https://www.gene.com/gCSI.GRval |
| CTRP | | | | | | | D | [16, 17] | https://portals.broadinstitute.org/ctrp/ |
| PharmacoDB | | | | | | | D | [18] | https://pharmacodb.pmgenomics.ca/ |
| CellMinerCDB | M | T | E | P | C | | D | [19, 20] | https://discover.nci.nih.gov/cellminer/cellminercdb/ |
| DrugComb | | | | | | | D | [21] | https://drugcomb.fimm.fi/ |
| DrugCombDB | | | | | | | D | [22] | http://drugcombdb.denglab.org/main |
| PDX finder | M | T | | C | | | D | [23] | https://www.cancermodels.org/ |
| PRoXE | M | T | | | | | D | [24] | https://www.proxe.org/ |
| PDMR | M | T | | C | | | D | [25] | https://pdmr.cancer.gov/ |
| Vizome | M | T | | | | | D | [26, 27] | http://www.vizome.org |

Abbreviations: C: copy number variation, D: drug sensitivity, E: epigenetic, Me: metabolomic, M: genetic mutation, P: proteomic, T: transcriptomic.

applied, including principal component analysis, backward feature elimination, high-correlation filters, and minimum redundancy maximum relevance (mRMR) [32–40]. Furthermore, due to the wide variation in biological features, one or multiple data scaling methods (normalization) such as data standardization, min-max normalization, cross-correlation, rank-invariant set normalization, or scaling to unit length may need to be applied [41].

# 4.5 DRUG SENSITIVITY PREDICTION STUDIES

Drug sensitivity prediction problems can be categorized as classification problems or regression problems. In a classification model, an algorithm learns whether a particular drug would display considerable sensitivity or resistance to a cancerous object, for example, a cancer cell line or patient-derived xenograft (PDX). In such a scenario, cell viability or death is measured in the presence of a drug covering a wide range of concentrations to fit a drug response curve that determines drug sensitivity. A fitted curve can later be used to determine quantitative parameters such as half-inhibitory concentrations (IC₅₀—half-maximal inhibitory concentration, EC₅₀—half-maximal effective concentration, or GR₅₀—half-maximal growth rate inhibition), the area under the curve, the area above the curve, or other drug sensitivity scores. Such scores can be used to develop a regression model where the prediction model is trained against drug sensitivity scores. Datasets summarized in Table 4.1 provide drug sensitivity scores that can be used to develop both classification models and regression models.