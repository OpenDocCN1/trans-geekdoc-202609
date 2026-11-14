
vanishing. Although the scalable architecture can provide flexible configurations for multiple tasks of modelling QSPRs, it becomes more challenging to optimize more hyper-parameters. Herein, four FNNs corresponding to the four flammability-related properties (i.e., FPT, AIT, UFL, LFL) were configured with same structural parameters for lower complexity of optimization.

## 2.2 MDNN implementation and training

As the proposed MDNN includes a dynamic neural network (i.e., Tree-LSTM network), it was implemented on an open-source software platform supporting dynamic networks, PyTorch.50 All tasks of training, validation and testing were finished on the hardware platform with NVidia GTX1060 and Intel i5 8400. A parser based on RDKit51 was developed and Faulon’s algorithm40 was implemented in Python, to translate SMILES expressions into DAGs in Python. Meanwhile, a simple implementation of word embedding algorithm52 was utilized to train the embedding vectors in TensorFlow.53 After all programs were prepared, a multi-task prediction model of the four flammability-related properties was obtained using the procedure illustrated in Fig. 3.

In the workflow of Fig. 3, a regression algorithm named Adam54 was employed as optimizers to train the proposed MDNN. Eight optimizers were configured with different hyper-parameters for each task in alternate training. Meanwhile, another optimizer was employed to carry out the joint training on the entire MDNN. Additionally, early stopping was used to avoid overfitting, i.e., once there was no improvement on loss values of validation sets for a specified time (e.g., twenty epochs), the training process would be terminated.

### 2.2.1 Data analysis and preparation.

The experimental data involving FPT, AIT, LFL and UFL were used to train the MDNN, which were extracted from an authoritative database named DIPPR801.55 The database, DIPPR801, provides the uncertainty and acceptance for each experimental data point in which all data had been checked and reviewed by database maintainers. Hence, it was employed in many QSPR studies as a reliable data source. A list of molecular structures was gathered from PubChem56 representing isomeric SMILES, including all the available compounds in DIPPR801 and other compounds. Some compounds involving inorganic gas, salts, metal-organics and metallic elements were excluded from the employed data set, as molecular structures of these unemployed compounds are significantly different from most conventional organics and their flammability property data are often unavailable. The employed datasets only including accepted and experimental values were stored in (Comma-Separated Values) CSV format. The lists of employed compounds are provided in the section S4 of ESI.†

As for different units and numerical levels among the four flammability-related properties, it is necessary to standardize the raw data sets for easier training models. The reason is that the different numerical metrics could result in big gaps of gradient among each task. Note that the raw experimental data sets should be standardized in a linear transformation to guarantee that distribution shapes are not changed. The Z-score transformation as shown in eqn (1) was employed that can always produce a distribution with a mean of 0 and a standard deviation of 1.

```
\(\hat{x}_i^{\text{exp}} = \frac{x_i^{\text{exp}} - \bar{x}^{\text{exp}}}{\sigma}\)
```

where \(\hat{x}_i^{\text{exp}}\) represents the transformed property values and \(x_i^{\text{exp}}\) refers to the original values, \(\bar{x}^{\text{exp}}\) and \(\sigma\) are the average value and standard deviation of a data set, respectively. It should be noticed that the \(\bar{x}^{\text{exp}}\) and \(\sigma\) must be calculated on training sets, then two parameters are used to transform the validation and test sets.

![](img/ad669faf9aa9b269abc88758f2d39753_4_0.png)

Fig. 3 The overview of the methodology for formulating a multi-task QSPR model based on deep learning.

All available data were employed in the initial correlation, in which outliers were not excluded. The final correlation based on the proposed MDNN was implemented without outliers. Tables 2 and 3 list the used data points for the flammability-related properties in the initial and final correlation, respectively. Table 4 shows information related to the ranges of raw data collected from DIPPR801 database. For training and optimizing the multi-task model, the data set was split into three sets including a training set, a validation set and a test set. The transformation should be only implemented on the training set of each property. The term "validation set" refers to the dataset utilized to determine the hyper-parameters and observe trends of loss for early stopping in training models. The test set was employed to test model performance finally after a deep learning model was well trained with determined hyper-parameters. All compounds both in the validation and test sets were sampled randomly.

Before proceeding with the training, all molecular structures were converted into DAGs attached embedding vectors as mentioned above. Since the generation of embedding vectors does not need property data, many more compounds can be employed by the word embedding algorithm. In this work, 23 709 compounds depicted in SMILES expressions were employed to train the embedding vectors for each vertex of

Table 2 Data points of the flammability-related properties used in the initial correlation

| Property | Whole dataset | Training set | Validation set | Test set |
| :--- | :--- | :--- | :--- | :--- |
| FPT | 1176 | 822 | 177 | 177 |
| AIT | 501 | 349 | 76 | 76 |
| LFL | 449 | 315 | 67 | 67 |
| UFL | 350 | 243 | 53 | 54 |

Table 3 Data points of the flammability-related properties used in the final correlation

| Property | Whole dataset | Training set | Validation set | Test set |
| :--- | :--- | :--- | :--- | :--- |
| FPT | 1176 | 822 | 177 | 177 |
| AIT | 480 | 334 | 70 | 76 |
| LFL | 443 | 309 | 67 | 67 |
| UFL | 329 | 226 | 49 | 54 |

Table 4 Ranges of used datasets on the flammability-related properties

| Property | Minimum | Maximum | Average | Standard deviation |
| :--- | :--- | :--- | :--- | :--- |
| FPT | 87.1 | 570 | 330 | 63.4 |
| AIT | 363 | 1283 | 651 | 120 |
| LFL | 0.0454 | 16.9 | 2.24 | 2.41 |
| UFL | 2.40 | 100 | 12.7 | 9.31 |

DAGs. At this stage, 170 symbols were extracted from all vertexes of the DAGs and each one was represented by a 48-dimensional vector. The symbols are listed in the section S2 of ESI.$^\dagger$

### 2.2.2 Training and evaluating a deep learning based QSPR model.

Unlike single-task DNNs, there are two strategies to train multi-task DNNs as usual, _i.e._, alternate training and joint training.$^{57}$ With joint training for property prediction, a distribution of vectors representing molecules in the chemical latent space is simultaneously organized by the four properties and commonalities among the four tasks which could be learned. There is a requirement on the training data for joint training, _i.e._, the experimental values of four properties must be available simultaneously in one data row. Therefore, all parameters of the MDNN can be trained in each epoch of the joint training. After the joint training had been conducted, alternate trainings were employed to train each FNN as well as the Tree-LSTM network in one epoch. It is not necessary to fill all training data matrices in the alternate training which could transfer some information from rich data sets to sparse ones. In the alternate training, only the corresponding FNN is updated for the current task during each iteration, while all parameters of other task-specific FNNs are frozen. Two types of loss function were employed in the two types of training methods. For the joint training, all parameters of the whole network were updated to minimize a combined loss function eqn (2).$^{58}$

```
\(L(W, \sigma_1, \sigma_2, \dots, \sigma_i) = \sum_l \left( \frac{1}{2\sigma_l^2} L_i(W) + \log \sigma_i \right) \quad (2)\)
```

```
\(L(W, \sigma_i) = \frac{1}{2\sigma_i^2} L_i(W) + \log \sigma_i \quad (3)\)
```

where \(W\) is used to represent model parameters and \(\sigma_i\) is the observation noise variable (_i.e._, standard deviation) of each task. This loss function weighs the losses of all tasks using the homoscedastic uncertainty of each task, which allows each task corresponding to each property to be learned simultaneously. \(L_i(W)\) representing the loss function for each task was calculated by mean square error (MSE) between the estimated values and the experimental values. It should be noted that the loss function \(L_i(W)\) was employed for each FNN and the weighted loss function \(L_i \ (W, \sigma_i)\) was used to train the Tree-LSTM encoder in the alternate training. The details related to model training are presented in the section S5 of ESI.$^\dagger$

### 2.2.3 Determination of hyper-parameters.

It is significant to determine the optimal configuration of hyper-parameters for a deep learning model. In general, two parts of hyper-parameters should be determined: the structural parameters of deep neural network (_e.g._, number of hidden layers, number of neurons, types and parameters of activation functions) and parameters of training optimizers. Unfortunately, there is no such a universal configuration that can work well for all models and data sets. It is necessary to optimize the hyper-parameters for different models separately.
