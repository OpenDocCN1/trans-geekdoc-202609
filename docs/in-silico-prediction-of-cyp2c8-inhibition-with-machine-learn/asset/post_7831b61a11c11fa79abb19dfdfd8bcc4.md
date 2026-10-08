
## Table 8. Ten Privileged Substructures Detected by SARpy Analysis

| Description | Privileged Substructure | IG | $N_I^*$ ($F_I^*$) | $N_N^*$ ($F_N^*$) | Representative Structure |
| :--- | :--- | :--- | :--- | :--- | :--- |
| n1(-e2:e:x:e:x:2)e:e:c:1 | | 0.043 | 18 (1.82) | 0 (0) | |
| e1(e2:e:x:e:x:e:2)::x:e:x:e:1 | | 0.042 | 27 (1.69) | 2 (0.15) | |
| e1:c:e2:e:x:e:x:e:2:m:1 | | 0.033 | 23 (1.67) | 2 (0.18) | |
| C(-N-e1:e:x:e:x:1-C:=O):=O | | 0.033 | 14 (1.82) | 0 (0) | |
| Cl(-C#C):e:x:e:x:e:1 | | 0.031 | 13 (1.82) | 0 (0) | |
| C(-N(-C-e1:e:x:e:x:1)(=O)-c1:e:x:e:c:e:1 | | 0.023 | 10 (1.82) | 0 (0) | |
| Cl(-F):e:x:e:c:e(-C):e:1 | | 0.023 | 10 (1.82) | 0 (0) | |
| N-Cl:e:x:e:c:e(-F):e:1 | | 0.021 | 9 (1.82) | 0 (0) | |
| Cl1(-S(-N(-C(-C-C)(=O)=O):e:x:e:ee:1 | | 0.021 | 9 (1.82) | 0 (0) | |
| C(-N(=O)-c1:e:x:e(-C):e:c:e:1 | | 0.021 | 9 (1.82) | 0 (0) | |

$^*$ $N_I$ and $F_I$ represent the number and frequency of this fragment in inhibitors. $^*$ $N_N$ and $F_N$ represent the number and frequency of this fragment in noninhibitors.

In addition, eight of the nine molecular fingerprints based on SVM have higher CA values than the other algorithms.

The top five models were further validated by the test and external sets. As shown in Tables 3 and 4, the predictive accuracies of these models are relatively high, with AUC and CA values greater than 0.8 and 0.7, respectively. The best models in the test and external sets were both built based on SVM, namely, the Pub-SVM and FP-SVM models, where the AUC value of the FP-SVM model exceeds 0.9. These results indicate that the classification models based on SVM have better robustness and predictive performance. This is similar to our previous findings. Chen et al$^{43}$ used machine-learning algorithms to construct binary classification models of FXR binders and nonbinders. They pointed out that more than one-half of the top 10 models in the test and external validation sets were built using SVM and RF. Jiang et al$^{44}$ predicted the reproductive toxicity of compounds via machine learning, and they found that the Mac-SVM model had the best predictive performance.

## 4.2. Comparison of Different Molecular Fingerprints.

In this study, nine molecular fingerprints containing different lengths and structural information were employed to build classification models. From Figure 2, it is obvious that the Ext, FP, and Pub fingerprints have better performance than the others. By contrast, the models built on the AP2D and Gra fingerprints perform poorly in terms of the AUC and CA values. In addition, four of the top five models in 10-fold cross validation were built on the Ext and FP fingerprints, which were still robust for the test and external validation sets. This implies that the fingerprint with longer bits does not necessarily perform better in model construction. For example, the prediction of the Mac fingerprint (166 bits) is better than that of Gra (1024 bits), which performs worst in most models. In addition, the KR fingerprint comprising 4860 bits exhibits poor performance in the KR-KNN model with an AUC value of 0.79. Overall, our results indicate that it would be a good choice to use the Ext and Pub fingerprints to build classification models for CYP2C8 inhibition.

![](img/c231614c653e97fe1a89fe8f2f1da0bc_7_0.png)

Figure 3. Binding mode of Montelukast (A) and Troglitazone (B) in the crystal structure of the CYP2C8 complex. Hydrogen bonds and hydrophobic interactions formed by the ligand and the residues are represented by yellow and gray dashed lines, respectively.

## 4.3. Privileged Substructures Analysis.

A total of 19 unique privileged substructures was obtained, as presented in Tables 7 and 8. Among them, nitrogen-containing heterocycle substructures such as 1H-benzo[d]imidazole, 1-phenyl-1H-pyrazole, and quinoline frequently occur in the CYP2C8 inhibitors reported in the literature, such as Azilsartan, 45 Candesartan cilexetil, 14 and Nilotinib. 46 Molecules containing these fragments tend to interact with CYP2C8, possibly because it can occupy the distal hydrophobic pocket in the active cavity. For example, in the complex crystal structure of CYP2C8 (PDB code 2NNI), the chloroquinoline ring of the potent competitive inhibitor Montelukast interacts with the hydrophobic residue cluster located below helix G to stabilize its binding to CYP2C8, 47,48 as shown in Figure 3A.

The remaining privileged substructures have similar scaffolds including the benzenesulfonamide, benzamide, and N-phenyl-formamide fragments. In fact, many reported potent CYP2C8 inhibitors contain the above structural fragments, such as Zafirlukast, 49 Dabrafenib, 50 and Gliburide. 14 According to the crystal structure of PDB code 2NNI, the terminal carboxylic acid group of Montelukast forms hydrogen bonds with the polar amino acid cluster (including Ser100, Ser103, and Asn217) near helix B' in the active site (Figure 3A). In addition, in another complex crystal structure of CYP2C8 (PDB code 2VN0), the ketone oxygen in the thiazolidinedione can form hydrogen bonds with Arg241 in helix G and Asn204 in helix F. The other oxygen in the middle of the structure forms hydrogen bonds with Ser103 via the surrounding water molecules 51,52 (Figure 3B). Therefore, compounds containing sulfonamide or amide groups can form polar interactions with the polar amino acid cluster near helix B' or Arg241 and Asn204 of CYP2C8, which may explain the frequent presence of benzenesulfonamide and benzamide fragments in CYP2C8 inhibitors.

In addition, some substructures containing fluorine atoms were also identified by MoSS and SARy. In fact, fluorine atoms are present in several known CYP2C8 inhibitors such as Dabrafenib and Nilotinib. As an electron-withdrawing group, F reduces the electron cloud density of the benzene ring, thus enhancing the hydrophobicity of the molecule, 53,54 making it easier to bind to the hydrophobic cavity of CYP2C8.

## 4.4. Limitations of Our Models.

The overall accuracies of the 10-fold cross validation, test, and external sets indicate that our models have satisfactory predictive power and can provide useful information for classifying potential CYP2C8 inhibitors and noninhibitors. However, our models still have certain limitations. Due to the small quantity of experimentally measured CYP2C8 noninhibitors reported, relatively few negative compounds were used for modeling, which may result in insufficient “learning” of negative data features in our models. As can be seen from the results of the cross validation, test, and external validation sets, the S# value is slightly lower than the SE value in general. It is hoped that this problem could be solved with the increase of CYP2C8 biological experimental data in the future. In addition, the inorganic compounds were removed before modeling. Thus, our models cannot predict these species.

## 5. CONCLUSIONS

In this study, on the basis of a diverse data set of CYP2C8 enzymes, 5 machine-learning algorithms including SVM, RF, KNN, NN, and LR combined with 9 molecular fingerprints were used to develop 45 binary classification models. Considering the values of AUC, CA, SE, SP, and MCC, the 5 best-performing models by 10-fold cross validation were obtained for further assessment using the test and external validation sets. The overall predictive accuracy is satisfactory, where the AUC and CA values are over 0.8 and 0.7, respectively. In addition, our results showed that the models built with the Ext and Pub fingerprints were superior to others, and the SVM algorithm was more suitable for classifying CYP2C8 inhibitors/noninhibitors. The Euclidean distance-based applicability domain calculation was further applied, whose value was obtained by searching for parameters k and Z. Moreover, a combination of information gain and substructure frequency analysis was used to detect several privileged substructures. In conclusion, the built prediction models and the privileged substructures could be useful for quickly identifying potential CYP2C8 inhibitors in the early stage of drug design.

## 6 ASSOCIATED CONTENT

### Supporting Information

The Supporting Information is available free of charge at https://pubs.acs.org/doi/10.1021/acs.chemtoxtx.1c00078.

Parameter settings of the top five models in 10-fold cross validation; detailed results for 10-fold cross-validation of the models; related statistics of the samples; analysis of variance of different models; physicochemical properties analysis and chemical similarity heat map of the training,
