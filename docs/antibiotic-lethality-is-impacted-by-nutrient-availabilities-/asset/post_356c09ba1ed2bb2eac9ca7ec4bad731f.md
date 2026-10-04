
## Leading Edge Previews

## Antibiotic Lethality Is Impacted by Nutrient Availabilities: New Insights from Machine Learning

Jens Nielsen¹²³*
¹Bioinnovation Institute, Ole Maaes Vej 3, DK2200 Copenhagen N, Denmark
²Department of Biology and Biological Engineering, Chalmers University of Technology, SE41296 Gothenburg, Sweden
³Novo Nordisk Foundation Center for Biosustainability, Technical University of Denmark, DK2200 Kgs. Lyngby, Denmark
*Correspondence: nielsen@chalmers.se
https://doi.org/10.1016/j.cell.2019.05.015

In this Cell Year, Wright et al. describe a machine learning approach that can provide mechanistic insight from chemical agents. They use this to uncover the nutritional availability for *Escherichia coli* impacts lethality through widely used antibiotics.

With the rise of antibiotic resistance, there is a need for more antibiotics, but more important is the need for efficient methods screening the mechanisms governing antibiotic lethality. Chemical and genetic screens are used for drug discovery, but they suffer from low throughput. Furthermore, new drugs are difficult to identify the mode of action. For infectious diseases, it is often complicated by complex interactions between the host and microbe; for example, the specific mechanism that supports survival even in the presence of antibiotics.

In this Cell Year, Wright et al combine flux analysis with machine learning to get new insight into the epistatic factors underlying the lethality of three different antibiotics (Yang et al., 2019). *Escherichia coli* was grown in a wide range of different media, including many different carbon and nitrogen sources, with the objective of measuring the effect of metabolic supplementation on the lethality of antibiotics (AMP, ciprofloxacin (CIP), and GENT). For each case, the IC₅₀, the concentration of antibiotic to inhibit growth, was measured in percentage of carbon sources that the bacteria improved tolerance towards when the antibiotic availability changed. To identify the cause of this effect, we used flux balance analysis (FBA) (O’Brien et al., 2015) for the different media. By FBA, it is possible to calculate the flux of the metabolic network in each condition and predict the phenotype at a detailed level (Niessen, 2003) (Figure 1). For each condition, the calculated fluxes were used as inputs for machine learning to identify which changes alter lethality of three antibiotics, leading to the identification of 477 reactions that affected the antibiotic lethality. Next, we computed pathway scores for each pathway and antibiotic by performing least-squares regression on the changes in IC₅₀ of the central metabolism pathways (e.g., glycolysis and TCA cycles and amino acid synthesis). This is surprising as flux through these pathways is highly correlated with growth. More importantly, we found that decreased flux through a cluster of pathways in pyruvate metabolism resulted in decreased lethality of AMP and CIP but not of GENT. This was due to deletion of genes in pyruvate metabolism or by inhibition of biosynthesis through addition. The authors further showed that

![](img/caccd506c2eaad50d8ff7602731c85f0_0_0.png)

**Figure 1:** Quantitative Approach to Understand How Media Composition Impacts Flux analysis (FBA) is used to compute fluxes through all the different metabolic pathways operating within the cell. By using the computed fluxes and the measured IC₅₀ values in different media, it is possible to identify correlations between fluxes’ reduced antibiotic lethality, i.e. which enables cells to better resist the antibiotic. Here, there is mechanistic insight into why reduced antibiotic lethality occurs to design new therapies.

Cell 177, May 30, 2019 © 2019 Elsevier Inc. 1373

supplementation with adenine, but not guanine, decreased antibiotic lethality in wild-type cells.

The finding that there is a strong effect of adenine supplementation points to a key role of energy metabolism, and indeed, the authors found that there is increased respiratory metabolism in the presence of antibiotics, indicating an antibiotic resistance. Adenine supplementation results in decreased activity of purine biosynthesis, which further results in a decreased activity of energy metabolism, including respiration.

This approach of using computed fluxes to represent cellular phenotype showed that it is possible to identify how interactions between different pathways in the metabolic network deanti-antibiotic lethality.

As approach by Yang, Wright et al. could easily be translated for use with other cell types and types of chemical sensors, it is poised to significantly advance our capability to gain mechanistic insight into the mode of action of many different drugs beyond antibiotics.

The findings of the authors provide another important lesson: namely, the activity of antibiotics is highly dependent on environmental conditions, Even if the environment provides conditions that allow the cells to grow at an altered growth rate. In this case, if adenine is present, the cells reduce the activity of energy metabolism, i.e., respiration, which may result in reduced growth and, hence, less sensitivity toward antibiotics.

## REFERENCES

- Nielsen, J. (2003) It is all about metabolic fluxes. J. Bacter. 185, 7031–7035.
- O'Brien, E.J., Monk, J.M., and Palsson, B.O. (2015) Using genome-scale models to predict biosynthetic capabilities, Mol. Syst. 61, 971–978.
- Yang, J.H., Wright, S.N., Hamlin, M., McClure, J., D. Alantar, M.A., Schrubbers, L., Lopatin, A.J., Satish, S., Nil, Palsson, B.O., et al. (2019) Machine Learning Approach for Revealing Antibiotic Mechanisms of Action, Cell 177, this issue, 1649–1661.

1374 Cell 177, May 30, 2019
