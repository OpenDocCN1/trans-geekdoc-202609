
# J. Ding et al./Chinese Journal of Chemical Engineering 31 (2021) 227–239

and diversity of the data also determine the performance of the machine learning model [17,72,74],

## 3. Learning in Predicting Thermodynamic Properties

The development of chemical processes such as reaction, separation and purification rely on the thermodynamic properties of industrial substances. However, researchers have many databases making it difficult to collect data for all attributes and their combinations. A predictive model is critical

### 2.2. Descriptor

Descriptors refer to the features that can be used to characterize the system [67]. They are attributes of the data and selected inputs for the machine learning model. A molecular descriptor can describe the system qualitatively or quantitatively. For instance, a descriptor for a molecule could be its molecular weight. Another descriptor can be its molecular structure. Another widely used descriptor is group description; however, the frequency of each distinct group [75–78]. Thousands of descriptors have been developed up to date but importance of selecting right ones. Generally, the descriptors should be relevant to the target, and not contain highly correlated ones (e.g., solubility and water solubility). Several methods have been developed to select descriptors in terms of eliminating and retaining the most relevant features [81–85]. Some novel methods to construct descriptors were inspired by using molecular language [86–89] and treating structures as “words” (Section 3.2). These methods learn the features of structures from classical molecular representations such as simplified input line entry (SMILES) and molecular graphs [90]. Descriptors describe such as crystalline structures and atomic properties are quite different from molecular descriptors.

Traditional predictive models use mathematical functions, such as data-driven methods. Machine learning provides an alternative and efficient way to predict thermodynamic properties, bypassing the mechanism and prior knowledge of the equation of state. A large number of databases provide the bases of thermodynamic properties such as the National Institute of Standards and Technology (NIST) chemical handbook [71] and the Design and Engineering Physics Institute (DEPI) database [70]. The combination of machine learning and these databases have been used to predict industrial properties, enthalpy of phase change and other properties.

We will illustrate the ability of machine learning using neural network vector models to predict the density and viscosity of fuel compounds. The example predicts predictions for free energy of organic solvents in generic solvents.

### 3.1. Liquid density and viscosity

Liquid density and viscosity are critical thermodynamic properties for petroleum, aviation fuel, and other fields [109,110]. The Creton group [111] developed machine learning to predict density (ρ) and viscosity (η) of compounds. They used experimental data from the DEPI database that contains hydrocarbons and organic compounds collected from different sources.

They compared two sets of descriptors, including molecular descriptors and functional group descriptors (FCCD). Molecular descriptors include geometric, topological and electronic properties. Functional group descriptors are computed for each molecule by size, bonds, branching and dipole moment. Some of these descriptors are related to molecular weight and properties, and Other features may determine physicochemical behaviors of molecules, for instance, hydrocarbons

### 2.3. Algorithm

Algorithms refer to mathematical models that can be used to predict a variable based on other variables [99]. Algorithms recognize the descriptors and predict either qualitatively or quantitatively. Such a connection helps the system to predict new data [99]. Selecting an appropriate algorithm is another key to building a successful machine learning model. The algorithm is probably one of the most active areas in machine learning [100–105]. These algorithms have been grouped into two categories: supervised learning and unsupervised learning.

Supervised learning involves learning with labeled data (known), where the model predicts the values of interest. For applications in molecular thermodynamics, these output values can be either the category of unknown compounds (classification) or variables of a system (regression). Gaussian regression [103] and support vector methods (SVM). However, unsupervised learning methods use unlabeled data to train models, which classify input data with no labels. These methods are used for clustering hierarchical clustering [106] and gaussian mixture model [107]. The features of these two categories have been extensively used in textbooks and literature

* Asterisk

# J. Ding et al./Chinese Journal of Chemical Engineering 31 (2021) 227–239

is another important model in the machine learning. Combining with the kernel method [115], SVM can transform inseparable to linear separable ones in high-dimensional space.

mental severity for several groups of homologs, they found that the predicted results are lower in the region with higher temperatures. To verify the distinguishability of isomers, they used the trained model to predict T(t) of tetrahydrofuran and itiso isomers. As shown in Fig. 5, the Andrade equation with corrected parameters can predict the T(t) of the isomers as well.

They constructed machine learning models from combinations of descriptors and algorithms. All models yielded accurate predictions with the coefficient of determination (R²) higher than 0.98. FVN and SVM have a better performance in R² and p. Compared with other methods, GCFD model had a lower mean absolute error (MAE). However, several models provided better consensus by using experimental data. Then they built a consensus model of predicted models.

These machine learning might be applied at different steps for predicting system properties. Researchers can use machine learning to map the mapping from features to properties, or use it to estimate the parameters in empirical equations. The advantage of the latter is that fewer parameters are obtained, convenient to use.

The models performance and the plot of all predicted results against experimental data. The result shows that consensus models are more robust than individual ones.

### 3.2. Solution free

Solution affects many processes such as phase equilibrium. Solution free is another important thermodynamic property and attracts researchers in the fields of chemical and biological engineering [118–120]. Three methods can derive the solution free: (a) from the formation of a cavity within the solvent, which is both physically and chemically; (b) from the solute particles from the bulk, which is entropically highly unfavorable but enthalpy favorable; (c) from the solvent-solute interactions in terms of entropy and enthalpy. It lot of methods have been made to derive solution free from thermodynamic properties or to calculate it with quantum mechanics.

Another study by Cai et al. [116] focuses on the viscosity temperature characteristic of hydrocarbons using machine learning to predict the parameters of empirical equation. They obtained the NIST database of 21 pure hydrocarbons and used them to regress an Andrade equation [117], which determines T(η) through two parameters A and B. A neural network was developed to predict B and T by 35 chemical and molecular descriptors used to classify groups in hydrocarbons (paraffins, naphthenes, and aromatics), and genetic algorithms to depict isomers.

The prediction of B and T was measured by the test set. The correlation coefficients R and p are 0.987 and 0.994, and the relative errors are 4.08% and 2.50%, respectively. The predicted values are in good agreement with the experimental data; however, comparing the predicted and

information from, collected solvent parameters, such as ESOL (Estimated Solubility) [41], FreeSol (The Free Solubility Database) [124] and MnSol (the Minnesota Solubility Database) [125]. The two provide solubility and solution free energy

![](img/0b56e4ff16105a90fd2efb280b7d8a4a_3_0.png)

| | Training set | Validation set | Test set | Total |
|---|---|---|---|---|
| R² | 0.997 | 0.996 | 0.997 | 0.997 | R² | 0.997 | 0.994 | 0.989 | 0.996 |
| RMSE | 9.5 | 10.5 | 9.2 | 7.9 | RMSE | 0.136 | 0.186 | 0.220 | 0.157 |
| AAE | 5.0 | 5.5 | 5.4 | 5.1 | AAE | 0.071 | 0.095 | 0.012 | 0.001 |
| bias | 0.4 | 0.2 | -0.3 | 0.3 | bias | 0.000 | 0.011 | -0.012 | 0

Fig. 3. Statistical performance of the consensus model and the plot of predicted results against experimental data. Reproduced (adapted) with permission from [111]. (2020) American Chemical Society.
