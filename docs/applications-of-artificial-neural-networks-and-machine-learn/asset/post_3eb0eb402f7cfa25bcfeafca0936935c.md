
![](img/4048998719320644ee88964326fd7995_195_0.png)

Typically, a feed-forward backpropagation network such as MLP uses processing units that is placed in three types of input, hidden, and output layers. Each unit in a layer is connected to units in adjacent layers with an associated weight (connection strength). It is the adjustment of these weights that is done during network training, because network training involves repeatedly changing the weights between neurons until the output signal matches the target output within the desired minimum error. When training open feedforward networks, the studied data set is usually divided into a training set and a validation set. While the training set is used to train the network, the validation set is applied to check the error performance of the network. Finally, it is common to reserve a third set of cases (the test set) for external prediction to ensure that the results in the training and validation set are real and not artifacts of the training process.

In such feedforward backpropagation networks, connection weights are set to random values at the beginning of training. Descriptor values for all parameter sets under study are passed through the network (feed forward) and the output responses are compared with the target values of the input properties to obtain an error value. Then the weights are adjusted for the second pass of the data through the network to reduce the amount of error obtained. Since the adjustment of weights starts with the correction of the last layer and then continues backward to the first layer, this mode is called backpropagation [9]. This entire procedure is repeated iteratively to minimize the amount of error. Finally, a regression coefficient may be calculated between the observed product properties and the network predicted values. In general, feedforward backpropagation networks suffer from two potential problems: (a) data overfitting in the presence of too many adjustable weights; and (b) overtraining the network if there are too many training cycles. Considering these two problems, the number of adjustable weights plays an important role, which also affects the predictability of the final network. Finding the optimal network topology to achieve a balance between those two extreme situations is an important point in network learning [10].

## 9.3 Enhanced Colliding Body Optimization Algorithm (ECBO)

Colliding bodies optimization (CBO) is a new meta-heuristic search algorithm that in this technique, one object collides with other object and they move towards a minimum energy level. The meta-heuristic ECBO algorithm is actually an improvement of the CBO algorithm. It uses memory to store a number of historical best CBs and also uses a mechanism to escape from local optima [11]. One of the advantages of this algorithm is its simplicity, which does not depend on any internal parameters.

In our recent research [2], it was found that the combination of ECBO meta-heuristic algorithm with feed-forward neural network had the best results compared to other combinations. Therefore, in this research, this combination was used to obtain the shear strength of the masonry shear wall. Figure 9.2 shows the schematic flowchart of the combination of neural network and ECBO algorithm.

In order to determine the structure of the artificial neural network, the feed-forward backpropagation model, which has a single input layer and one hidden layer with the tan-sigmoid activation function as it is shown in Eq. (9.1), and an output layer having linear activation function, is used.

![](img/4048998719320644ee88964326fd7995_196_0.png)

Fig. 9.2 The computation procedure of the ANN-ECBO

\[
\text{Tangent Sigmoid} = \frac{1}{1 + e^{-x}} \tag{9.1}
\]

## 9.4 Experimental Database Gathering

A comprehensive database is needed to use machine learning models. A database is actually a collection of input and output data in a system. In this research, the design parameters of the masonry shear wall are considered as input. In Table 9.1, the inputs are introduced along with their units. An experimental dataset totaling 255 PG masonry shear walls was compiled from 22 independent studies (Table 9.2) [12]. The collected samples are divided into 5 categories from A to E. This division is given in Table 9.3. The range of parameters used in ANN modeling is given in Table 9.4. All input and output variables in the database are normalized on a -1, 1 scale, following this formula:

\[
\text{Norm } x_i = \left[ \frac{x_i - \min(x)}{\max(x) - \min(x)} \times 2 \right] - 1 \tag{9.2}
\]

where x is the input or output variable to be normalized, \(x_i\) is its corresponding value, and \(\text{Norm } x_i\) is the calculated value. The correlation matrix related to the data values is shown in Fig. 9.3.

The frequency distribution of the experimental data to express the parameters of the samples, including \(A_{scaled}\), \(M / VL\), \(A_{net} / A_{gross}\), \(f'_{m,eff,corrected}\), \(\rho_l f_{yv}\), \(\rho_h f_{yh}\), \(\sigma_{gross}\), \(V_{avg}\) is shown in Fig. 9.4. As can be seen, the empirical data collected covers a wide range. Therefore, these parameters can be suitable inputs for model development.

**Table 9.1** Input variables adopted in the study

| Type | Number | Symbol | Unit |
| :--- | :--- | :--- | :--- |
| Wall geometry | 1 | \(A_{scaled}\) | mm\(^2\) |
| | 2 | \(M / VL\) | - |
| Partial grouting | 3 | \(A_{net} / A_{gross}\) | - |
| Masonry materials | 4 | \(f'_{mcor, eff}\) | MPa |
| Vertical reinforcement | 5 | \(\rho_l f_{yv}\) | MPa |
| Horizontal reinforcement | 6 | \(\rho_h f_{yh}\) | MPa |
| Axial stress | 7 | \(\sigma_{gross}\) | MPa |
| Experimental shear capacity | 8 | \(V_{avg}\) | kN |

**Table 9.2** Database collected in this study [12]

| References | No. of samples | Proportion% |
| :--- | :--- | :--- |
| Scrivener (1967) | 12 | 5 |
| Mayes et al. (1976) | 2 | 1 |
| Chen et al. (1978), Hidalgo (1978) | 4 | 1.5 |
| Thurston and Hutchinson (1982) | 3 | 1 |
| Matsumura (1987) | 29 | 11 |
| Tomažević and Lutman (1988) | 10 | 4 |
| Johal and Anderson (1988) | 16 | 6 |
| Ghanem et al. (1992) | 4 | 1.5 |
| Schultz (1996) | 6 | 2.5 |
| Schultz et al. (1998) | 6 | 2.5 |
| Voon and Ingham (2006) | 2 | 1 |
| Haach et al. (2007) | 4 | 1.5 |
| Maleki et al. (2009) | 5 | 2 |
| Elmapruk (2010) | 6 | 2.5 |
| Minaie et al. (2010) | 4 | 1.5 |
| Baenziger and Porter (2011) | 8 | 3 |
| Nolph et al. (2012) | 5 | 2 |
| Oan (2013) | 66 | 26 |
| Hoque (2013) | 18 | 7 |
| Hamedzadeh (2013) | 21 | 8 |
| Rizaee (2015) | 14 | 5.5 |
| Ramirez et al. (2016) | 10 | 4 |
| | 255 | 100 |

## 9.5 Quality Assessment Criteria

In this study, several quality evaluation criteria such as Mean Square Error (MSE), Root Mean Square Error (RMSE), Mean Absolute Error (MAE), Mean Absolute Percentage Error (MAPE), Normalized Mean Absolute Error (NMAE), Normalized Root Mean Square Error (NRMSE), correlation coefficient (R) were used to evaluate and compare the models. The following equations show the formulation of these criteria:

\[
RMSE = \sqrt{\sum_{i=1}^{N} (z_0 - z_p)^2 / N} \tag{9.3}
\]

**Table 9.3** PG dataset variations for neural network analysis

| Description | Complete | A | B | C | D | E | F |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Number of specimens | 255 | 255 | 150 | 150 | 120 | 120 | 120 |
| Data synthetization | ⋆ | ⋆ | ⋆ | ⋆ | ⋆ | ⋆ | ⋆ |
| Specimens without sufficient information to predict \( f'_{m,eff} \) removed | | ⋆ | ⋆ | ⋆ | ⋆ | ⋆ | ⋆ |
| Monotonic specimen removed | | | ⋆ | ⋆ | ⋆ | ⋆ | ⋆ |
| ESECMaSE specimen removed | | | | | ⋆ | ⋆ | ⋆ |
| Horizontal reinforcement modified | | | | ⋆ | | ⋆ | ⋆ |
| Boundary vertical reinforcement neglected; only interior vertical bars considered | | | | | | | ⋆ |

**Table 9.4** Range of parameters used in ANN modelling

| Input | Variable | Minimum value | Maximum value | Mean | StD | Skewness |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Input 1 | \( A_{scaled} [m^2] \) | 0.66 | 19.42 | 3.686 | 2.883 | 1.992 |
| Input 2 | \( M / VL \) | 0.25 | 2.30 | 0.739 | 0.320 | 1.881 |
| Input 3 | \( A_{net} / A_{gross} \) | 0.36 | 0.81 | 0.611 | 0.095 | -0.594 |
| Input 4 | \( f'_{m,eff,corrected} [MPa] \) | 4.30 | 22.30 | 12.448 | 3.830 | 0.221 |
| Input 5 | \( \rho_v f_{yv} [MPa] \) | 0.00 | 4.82 | 1.149 | 1.029 | 0.993 |
| Input 6 | \( \rho_h f_{yh} [MPa] \) | 0.00 | 1.29 | 0.315 | 0.260 | 0.584 |
| Input 7 | \( \sigma_{gross} [MPa] \) | 0.00 | 2.78 | 1.087 | 0.854 | 0.334 |
| Input 8 | \( V_{avg} [kN] \) | 23.10 | 772.2 | 219.1 | 131.483 | 1.020 |

\[
R = \sqrt{1 - \frac{\sum_{i=1}^N (z_0 - z_p)^2}{\sum_{i=1}^N (z_0 - \bar{z_i})^2}} \tag{9.4}
\]

\[
MAE = \frac{1}{N} \sum_{i=1}^N |z_0 - z_p| \tag{9.5}
\]
