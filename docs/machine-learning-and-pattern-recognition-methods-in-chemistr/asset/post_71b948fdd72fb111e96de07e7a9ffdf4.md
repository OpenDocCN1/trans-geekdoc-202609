
example, in the case of asymmetric classification, i.e., when the focus is not on assigning all samples to one of the possible classes, but on modeling a specific category of interest, class-modeling methods may be more appropriate than the discriminant ones. In fact, these methods allow the individual modeling of the category of interest, and then all the investigated individuals can be accepted (and, therefore, predicted as belonging to the class without any further cogitation on its possible class-membership) by the model. Soft independent modeling of class analogies (SIMCA) Soft independent modeling of class analogies (SIMCA) is probably the most well-known class-modeling approach; it has been proposed by Wold in 1977 (Wold, 1976; Wold & Sjöström, 1977), and since then, various modifications have been proposed to its original formulation, in order to improve its efficiency (Derde & Massart, 1988; Pomerantsev & Rodionova, 2020).

Basically, SIMCA starts from the assumption that the main characteristics of the samples belonging to the class of interest can be captured by a principal component analysis (PCA) model of proper dimensionality. Consequently, the first step of the algorithm consists of calculating a PCA model on the training individuals belonging to the class of interest:

```
$$\mathbf{X}_g = T_g P_g^T + E_g$$
```

where the symbols have the same meaning as in Eq. (2.18), while the subscript g indicates that the model is calculated only on the training samples of class g. $E_g$ indicates the residuals after approximating the matrix $X_g$ with $A_g$ principal components. This parameter is a meta-parameter which should be optimized. This is usually accomplished by testing models with an increasing number of components and selecting the dimensionality, which leads to the highest classification efficiency (usually in cross-validation, see Section 3).

Based on the projection expressed by Eq. (2.47), a distance of any individual to the model is calculated as a combination of its orthogonal distance (i.e., the residuals after PCA projection, indicated as $Q_j$) and its (usually Mahalanobis) distance to the center of the scores space (indicated as $T_j^*$). The various implementations of SIMCA proposed in the literature differ in the way they combine scores and orthogonal distances into a single distance to the model, and as it will be discussed below, in the way they set a threshold in order to define acceptance or rejection by the class model (Pomerantsev & Rodionova, 2020).

The most popular formulation of SIMCA defines the overall distance to the model as:

```
$d_i = \sqrt{\left(\frac{T_i}{T_{0.95}}\right)^2 + \left(\frac{Q}{Q_{0.95}}\right)^2} \quad (2.48)$
```

the subscript 0.95 indicates that both the scores and the orthogonal distances, prior to being combined, need to be normalized by division to the 95th percentiles of their respective distributions under the null hypothesis.

When the overall distance to the model is defined as in Eq. (2.48), as a consequence of the normalization involved, its threshold for acceptance is set to $\sqrt{2}$. Therefore, if the i-th sample presents a $d_i \le \sqrt{2}$, the object is accepted and predicted as belonging to the modeled category; otherwise, it is rejected and considered not belonging to the class of interest.

# 3. Validation

Chemometrics modeling is of empirical nature, i.e., models are built on the collected data, to provide approximations of the system under study and formulate predictions. In this context, it is necessary to point out that, given the available data, the possible models that can be calculated are almost always more than a single one, and the quality and performances of the current candidate models can be influenced by several factors, e.g., the number of samples and their representativeness, the characteristics of the method or the algorithm for calculating the solution. In this context, it is fundamental to assess whether reliable outcomes and predictions can be drawn for a particular model, and whether they can be generalizable or not, at the same time verifying whether the interpretation of the results could be sound and meaningful. This process is called validation, and it constitutes a fundamental step of any chemometric modeling (Westad & Marini, 2015).

Operationally, validation is often conducted by applying the model to a set of data (test set) which was different and independent from the one used for model building (what was defined, in the training or calibration set). This additional set of data is treated along all analyses as if it were a new set of unknown observations, so to be able to obtain the model predictions for those data, but it is also necessary that the true values of the quantities to be predicted are known as well, in order to evaluate the model performances and to be calculate various possible diagnostics based on the value of the residuals (i.e., the differences between the true and predicted values of the responses). In order for the validation to be effective, the use of new data instead of the training samples is of the highest importance. Indeed, since the model parameters are often optimized to minimize the error on the training observation, by using the same data for model validation, one would obtain over-optimistic results by definition. On the other hand, the test set should be chosen to reflect as closely as possible all the possible sources of variability that one would expect in the routine application of the model, i.e., on future developments. In this context, when collecting a completely new set of samples is not possible, a solution is represented by the possibility of splitting all the available data into training and test sets, possibly not randomly through the use of algorithms which guarantee that the two sets span as effectively as the possible space [e.g., Kennard-Stone (Kennard & Stone, 1969) or Duplex (Snee, 1977)].

When the number of samples is limited, resampling strategies, like cross-validation (CV), can also be employed. In cross-validation, the whole data set is divided into a specified number of cancelation groups, which, in turn, are used as validation sets, while the remaining individuals constitute the training set. CV has the advantage that any sample is predicted by a model which was built on a set that doesn't include it; on the other hand, since training and test sets are never completely independent from one another, the results that are obtained in general be too optimistic. Anyway, cross-validation, when applied to the training samples only, can be fruitfully exploited in the model selection stage, for instance, when the optimal values of some metaparameters, e.g., the number of components, should be identified. In that case, one can compare the performances, in CV, of the competing model and then select the value of metaparameter(s) leading to the best performances. Once the optimal model has been selected, validation of its performances on a completely external test is recommended.

# References

- Albalate, A., & Minker, W. (2013). Semi-supervised and unsupervised machine learning: Novel strategies. John Wiley and Sons. https://doi.org/10.1002/97811858793
- Baker, M., & Rayens, W. (2003). Journal of Chemometrics, 17(3), 166–173. https://doi.org/10.1002/cem.785
- Berglund, A., & Wold, S. (1997). Journal of Chemometrics, 11(2), 141–156. https://doi.org/10.1002/(S997)11:141-2
- Brereton, R. G., & Lloyd, G. R. (2010). Analytical, 135, 230–267. https://doi.org/10.1039/b19872
- Cochieri, M., Biancolilli, A., & Marini, F. (2018). Comprehensive analytical chemistry, Vol. 82 (pp. 265–299). Elsevier. https://doi.org/10.1016/j.aco.2018
- Derde, M. P., & Massart, D. L. (1988). Chemometrics and Intelligent Laboratory Systems, 4(1), 65–93. https://doi.org/10.1016/0169-7439(88)00013-3
- Fisher, R. A. (1936). Annals of, 7, 178–185. https://doi.org/10.2311
- Geldi, P., & Kowalski, B. R. (1986). Analytical Chemica Acta, 185, 1–17. https://doi.org/10.1016/00302670
- Indahl, U., Hartmann, H., & Naes, T. (2007). Journal of Chemometrics, 21(2), 529–536. https://doi.org/10.1002/chem.1061
- Jolliffe, I. T. (1982). Analytical Statistics, 3(3), 300. https://doi.org/10.2307/234805
- Jolliffe, I. T. (2002). Principal component analysis. Springer. https://link.springer.com/book/10.1007/978-0-387-5
- Kennard, R. W., & Stone, L. A. (1969). Technometrics, 11(1), 137–148. https://doi.org/10.1080/00401766.1969.90666
- Handbook of multivariate analysis: A user's perspective (2nd ed.). University Press. https://global.oup.com/academic/products/of-multivariate-analysis-978019850768
- Marini, F., Bucci, R., Magri, M., & Magi, A. (2008). Molecular Journal, 88(2), 177–185. https://doi.org/10.1016/j.molchem.2007
- Martens, H., & Naes, T. (2011). Chemometrics and Intelligent Laboratory Systems, 95(2), 192–205.
- Nézier, N.-F., Ferré, J., & Bouqué, R. (2009). Chemometrics and Intelligent Laboratory Systems, 95(2), 122–128. https://doi.org/10.1016/j.chem.2008
- Pomerantsev, A., & Rodionova, O. Y. (2020). Chemometrics, 34(8). https://doi.org/10.1002/chem.3250
- Rospal, R. (2003). Neural Network, 13(3), 291–300.
- Sjöström, M., Wolf, S., & Söderberg, S. (1986). PLS discriminant plots. In E. S. Gelssema & L. N. Kanal (eds.), Pattern recognition in chemistry (pp. 461–470). Amsterdam: Elsevier.
- Snee, R. D. (1977). Technometrics, 19(4), 415–426. https://doi.org/10.1080/00401706.1977.106081
- Stihle, W., & West, S. (1987). Journal of Chemometrics, 1(3), 185–196. https://doi.org/10.1002/cem118001036
- Westad, W., & Marini, F. (2015). Analytical Chemica Acta, 893, 14–24. https://doi.org/10.1016/j.analchem.2015.06.056
- Wold, S. (1976). Pattern Recognition, 8(3), 127–139. https://doi.org/10.1016/0031-3203(76)90014
- Wold, S., Johnson, E., & Kuboski, D. (1983). PLS: Partial least squares to project structures. In H. Kuboski (eds.), Data chemistry: Methods and applications (pp. 525–550). Leiden, The Netherlands: ESCOM Science Publisher
- Wold, S., Ketch-Tann, N., & Skagerberg, B. (1989). Chemometrics and Intelligent Laboratory Systems, 7(1–2), 55–63. https://doi.org/10.1016/0169-7439(89)80111-x
- Wold, S., Martens, H., & Wold, H. (1983). The multivariate problem in chemistry solved by the PLS method. In A. Ruhe, & B. Kåist (Eds.), Proceedings of the conference neural patterns. Lecture notes in mathematics (pp. 286–293). Heidelberg, Germany: Springer Verlag
- Wold, S., & Sjström, M. (1997). SIMCA: A method for analyzing chemical data in terms of similarity and analogy. In B. R. Kowalski (Eds.), Chemometrics: Theory and application (pp. 243–282). Washington, DC: American Chemical Society
- Wold, S., Sjström, M., & Eriksson, L. (2001). Vol. 58 (pp. 109–130). https://doi.org/10.1016/0169-7439(01)00155-1
