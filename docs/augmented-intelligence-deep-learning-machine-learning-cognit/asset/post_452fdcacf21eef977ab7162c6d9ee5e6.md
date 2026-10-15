
could have negative effects on consumer health [63]. On the other hand, values below 50 ppb were considered permissive. It was in our interest to classify the samples as suitable for consumption (tylosin concentrations < 50 ppb) or unsuitable for consumption (tylosin concentrations ≥ 50 ppb). For this, the multilayer perceptron neural network (MLP) technique was used.

The MLP operated in multistart mode, obtaining a better fit with a network with architecture consisting of two hidden layers (6,3), using a logistic activation function. A multiclass factor that corresponds to the origin of the milk was included in the data set due to the effect related to the complexity of the matrix (including interferences such as sugars, proteins, fat, urea and other soluble solids) alongside other 16 wave numbers (cm⁻¹) of interest. The performance in the discriminant analysis of real milk samples by several machine learning algorithms, logistic regression (LogR), partial least squares discriminant analysis (PLS-DA), CART, GBT and RF are compared below with the MLP reference previously developed (Table 3.3).

## Table 3.3. Quality parameters of the discriminatory analysis of a test subset containing 33 milk samples by the logistic regression model (LogR), PLS-DA, CART, GBT, RF and MLP.

| Model | True + | False + | True - | False - | Accuracy | CI - | CI + | Kappa | Sensitivity | Specificity | p |
|---|---|---|---|---|---|---|---|---|---|---|---|
| LogR | 8 | 7 | 6 | 12 | 0.424 | 0.255 | 0.608 | -0.13 | 0.461 | 0.400 | 0.989 |
| PLS-DA | 17 | 11 | 2 | 3 | 0.576 | 0.392 | 0.745 | 0.004 | 0.154 | 0.850 | 0.706 |
| CART | 20 | 13 | 0 | 0 | 0.606 | 0.421 | 0.771 | 0 | 0 | 1.000 | 0.575 |
| GBT | 18 | 2 | 11 | 2 | 0.878 | 0.718 | 0.966 | 0.746 | 0.846 | 0.900 | 6.02E-4 |
| RF | 18 | 1 | 12 | 2 | 0.909 | 0.757 | 0.981 | 0.812 | 0.923 | 0.900 | 1.16E-4 |
| MLP [28] | 20 | 0 | 13 | 0 | 1.000 | 0.894 | 1.000 | 1.000 | 1.000 | 1.000 | 6.65E-8 |

Taking into account the low concentrations of the contaminant, it is expected that the matrix effect will become very prevalent. For the same reasons discussed in the previous section, GBT and RF obtained satisfactory results in predicting the classes compared to the other algorithms, obtaining only two false negatives and a prediction accuracy > 0.85, with a confidence interval, CI, which includes the level of accuracy obtained by MLP. Classification trees, on the other hand, was insensitive to the negative class (C < 50 ppb) and irrelevant results were obtained with the parametric algorithms (LogR and PLS-DA). This is a strong indication of the trend of the non-linear distribution of the response. Only the last three models, including the two techniques based on an ensemble of decision trees with a resampling mechanism, produced statistically significant results (p <0.05).

## CONCLUSION

The association of spectroscopy and multivariate calibration methods has enabled the analysis of complex spectra of multicomponent systems, and for that reason, in this chapter, we present some tree-based tools and highlight features of interest compared to other machine learning algorithms. The selection of subsets of attributes by a wrapper algorithm based on random forest, Boruta, proved to be as effective in selecting variables as evolutionary algorithms that are very popular among specialists. In regression problems in the high dimensional space, the ensembles of trees such as random forest and gradient boosting trees proved to be more predictive than the chemometric techniques already established by the literature and, in particular, the random forests proved robust to noise at equal or higher levels to 35%. In the discriminatory analysis of a trace-level contaminant in a complex matrix, RF and GBT proved to be as predictive as multilayer perceptron neural networks, with the advantage that the first two are less computationally costly.

## NOTES

The method based on genetic regression (GR) was also presented. However, since the author chose to present a genetic expression instead of the pure attributes, we chose to suppress these findings here.

## CONSENT FOR PUBLICATION

Not applicable.

## CONFLICT OF INTEREST

The authors declare no conflict of interest, financial or otherwise.

## ACKNOWLEDGEMENTS

Declared none.

## REFERENCES

[1] J.B. Ghasemi, and H. Tavakoli, "Application of random forest regression to spectral multivariate calibration", Anal. Methods, vol. 5, no. 7, pp. 1863-1871, 2013. [http://dx.doi.org/10.1039/c3ay26338j]

[2] A.M. Jiménez-Carvelo, A. González-Casado, M.G. Bagur-González, and L. Cuadros-Rodríguez, "Alternative data mining/machine learning methods for the analytical evaluation of food quality and authenticity - A review", Food Res. Int., vol. 122, pp. 25-39, 2019. [http://dx.doi.org/10.1016/j.foodres.2019.03.063] [PMID: 31229078]

[3] V. Svetnik, A. Liaw, C. Tong, J.C. Culberson, R.P. Sheridan, and B.P. Feuston, "Random forest: a classification and regression tool for compound classification and QSAR modeling", J. Chem. Inf. Comput. Sci., vol. 43, no. 6, pp. 1947-1958, 2003. [http://dx.doi.org/10.1021/ci034160g] [PMID: 14632445]

[4] F.A. Vega, J.M. Matías, M.L. Andrade, M.J. Reigosa, and E.F. Covelo, "Classification and regression trees (CARTs) for modelling the sorption and retention of heavy metals by soil", J. Hazard. Mater., vol. 167, no. 1-3, pp. 615-624, 2009. [http://dx.doi.org/10.1016/j.jhazmat.2009.01.016] [PMID: 19200658]

[5] S.M. Tan, J. Jiao, X-L. Zhu, Y-P. Zhou, D-D. Song, H. Gong, and R-Q. Yu, "QSAR studies of a diverse series of antimicrobial agents against Candida albicans by classification and regression trees", Chemom. Intell. Lab. Syst., vol. 103, no. 2, pp. 184-190, 2010. [http://dx.doi.org/10.1016/j.chemolab.2010.07.005]

[6] D. Custers, T. Cauwenbergh, J.L. Bothy, P. Courselle, J.O. De Beer, S. Apers, and E. Deconinck, "ATR-FTIR spectroscopy and chemometrics: An interesting tool to discriminate and characterize counterfeit medicines", J. Pharm. Biomed. Anal., vol. 112, pp. 181-189, 2015. [http://dx.doi.org/10.1016/j.jpba.2014.11.007] [PMID: 25476739]

[7] L. Rokach, "Decision forest: Twenty years of research", Inf. Fusion, vol. 27, pp. 111-125, 2016. [http://dx.doi.org/10.1016/j.inffus.2015.06.005]

[8] F.B. de Santana, W. Borges Neto, and R.J. Poppi, "Random forest as one-class classifier and infrared spectroscopy for food adulteration detection", Food Chem., vol. 293, pp. 323-332, 2019. [http://dx.doi.org/10.1016/j.foodchem.2019.04.073] [PMID: 31151619]

[9] X. Jin, S. Li, W. Zhang, J. Zhu, and J. Sun, "Prediction of soil-available potassium content with visible near-infrared ray spectroscopy of different pretreatment transformations by the boosting algorithms", Appl. Sci. (Basel), vol. 10, no. 4, p. 1520, 2020. [http://dx.doi.org/10.3390/app10041520]

[10] J. Xiu, Z. Xianzhi, L. Shaowen, W. Wencai, and Q. Haijun, "Predicting soil available phosphorus by hyperspectral regression method based on gradient boosting decision tree", Jiguang Yu Guangdianzixue Jinzhan, vol. 56, no. 13, p. 131102, 2019. [http://dx.doi.org/10.3788/LOP56.131102]

[11] G. James, D. Witten, T. Hastie, and R. Tibshirani, An Introduction to Statistical Learning. vol. 103. Springer New York: New York, NY, 2013. [http://dx.doi.org/10.1007/978-1-4614-7138-7]

[12] L. Rokach, and O. Maimon, Decision trees. Data mining and knowledge discovery handbook. Springer: Boston, MA, 2005, pp. 165-192. [http://dx.doi.org/10.1007/0-387-25465-X_9]

[13] R.S. DeFries, M. Hansen, J.R.G. Townshend, and R. Sohlberg, "Global land cover classifications at 8 km spatial resolution: The use of training data derived from Landsat imagery in decision tree classifiers", Int. J. Remote Sens., vol. 19, no. 16, pp. 3141-3168, 1998. [http://dx.doi.org/10.1080/014311698212435]

[14] K. Zhang, X. Wu, R. Niu, K. Yang, and L. Zhao, "The assessment of landslide susceptibility mapping using random forest and decision tree methods in the Three Gorges Reservoir area, China", Environ. Earth Sci., vol. 76, no. 11, pp. 404-424, 2017. [http://dx.doi.org/10.1007/s12665-017-6731-5]

[15] E. Pekel, M.C. Akkoyunlu, M.T. Akkoyunlu, and S. Pusat, "Decision tree regression model to predict low-rank coal moisture content during convective drying process", Int. J. Coal Prep. Util., vol. 40, no. 8, pp. 505-512, 2020. [http://dx.doi.org/10.1080/19392699.2020.1737527]

[16] O.F. Althuwaynee, A. Balogun, and W. Al Madhoun, "Air pollution hazard assessment using decision tree algorithms and bivariate probability cluster polar function: evaluating inter-correlation clusters of PM10 and other air pollutants", GISci. Remote Sens., vol. 57, no. 2, pp. 207-226, 2020. [http://dx.doi.org/10.1080/15481603.2020.1712064]
