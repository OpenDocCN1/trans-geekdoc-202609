
This developed algorithm has been implemented in predicting short-term wind speed at the station level.

## 2.2.3.2: Multivariate LSTM model for COVID-19 prediction

The long-Short Term Memory (LSTM) Model for the prediction of COVID-19 was carried out using the Vanilla LSTM framework. The LSTM is a very useful tool in solving sequential data prediction problems. The LSTM is a special kind of RNN (Recurrent Neural network) that is capable of learning long-term dependencies. In the present study, training data for LSTM was created by splitting the long-term (685 days) COVID-19 confirmed cases and weather parameters time series data. The major portion of the data (640 days) was utilized to train the model and 45 days of data were utilized for testing the model. The control experiment (CTL) was designed with a simple univariate LSTM model by training the daily COVID-19 case data, and four sensitivity experiments were designed using the multivariate LSTM model where the model training was carried out with daily COVID-19 cases data and meteorological parameters including specific humidity (`CTL_SH`), mean temperature (`CTL_Tmean`), maximum temperature (`CTL_Tmax`), and minimum temperature (`CTL_Tmin`). The minimum error method was utilized to optimize both the LSTM models by considering different hyper-parameters (hidden layers) and utilized for forecasting purposes. The state-level (13 states are considered for the present study) daily COVID-19 caseload forecasts (1-day forecast window) were generated using univariate and multivariate LSTM models for 1st January to 14th February 2022 (45 days) with different leads (lead time: 1–14 days) and evaluated with laboratory-confirmed case data.

## 2.2.4: SNN and CNN

A modified SNN (sequential neural network) model was trained by multi-omics data of low- and high-grade glioma tissues to predict their histopathological grades. At first, three individual SNN models were created for transcriptome/gene expressions (RNA-Seq.ai), DNA methylation (Meth.ai), and copy number variations (CNV.ai) datasets. Later, a unified SNN model (ALL.ai) was created by combining molecular data of all three multi-omics datasets. The network architectures, optimum hyperparameters, and most suitable activation functions used in all four SNN models are provided in [Table 2](#Ch006_107-168_S0169716122000578.xhtml#t0015). To evaluate the performance of the SNN model, several performance metrics, such as TPR (True positive rate), FPR (False positive), F1-score, AUC (Area under the curve), and minimum losses were considered. The higher accuracy or perception with minimum loss function values was selected for the optimized models. During each SNN model training, 80% of samples were randomly chosen for model training, and the rest 20% of samples, were kept aside from the primary dataset and were not used for training purposes. These 20% samples, aka blind data sets, were utilized to evaluate the accuracy and performance of trained SNN models. Samples of multi-omics data sets were labeled with multiple classes (tumor grades), which was taken into account while calculating the loss function using categorical cross-entropy for the multi-class classification model.

[Table 2](#Ch006_107-168_S0169716122000578.xhtml#B-t0015)

The optimum hyperparameters chosen for several deep learning models using SNN.

| Parameters  || Range/diff. function varied || Best parameters for SNN architectures |
| --- | --- | --- |
| Number of hidden layer || 2–15 || 10 || 12 || 9 || 13 |
| Number of dropout layer || 1–5 || 3 || 2 || 2 || 3 |
| Maximum epochs || 10–100 || 75 || 50 || 30 || 80 |
| Number of fully connected layers || 2–15 || 10 || 12 || 9 || 13 |
| Activation functions || ReLu, Tanh, Sigmoid || ReLu || ReLu || Tanh || ReLu |
| Optimizers || SDG, Adam, RSMprop || SDG || Adam || Adam || RSMprop |
| Dropout rate ||  || 0.2, 0.2, 0.3 || 0.4, 0.5 || 0.3, 0.2 || 0.1, 0.3, 0.5 |
| Initial learning rate || 0.0001–0.01 || 0.0001 || 0.0001 || 0.001 || 0.0001 |
| Mini-batch size || 8–64 || 16 || 8 || 8 || 32 |

Deep learning using a convolutional neural network (CNN) was applied to MR and whole-slide histopathological images of tumor samples to predict cellular subtypes/histopathological grades, molecular subtypes, mutation status, and overall survival of glioma patients. In total, five distinct CNN models were trained for these predictions. Pre-processed MR images were used to construct CNN models for predicting histopathological grades/cellular subtypes (Astrocytoma, Oligoastrocytoma, Oligodendroglioma), gene mutation status of `EGFR` and `TP53` genes, and overall survival of glioma patients. Similarly, pre-processed histopathological WS images were trained using CNN to predict cellular subtypes and molecular subtypes (i.e., Classical, Mesenchymal, Neural, Proneural). The network architectures, optimized hyperparameters, and activation functions used in these CNN models are shown in [Table 3](#Ch006_107-168_S0169716122000578.xhtml#t0020). Dropout and batch normalization layers were also included in these models to lose the connection between some layers and normalize the datasets to solve the overfitting and underfitting problem of overall networks.

[Table 3](#Ch006_107-168_S0169716122000578.xhtml#B-t0020)

The optimum hyperparameters used for training different deep learning models using CNN.

| Parameters  || Range/diff. function varied || Optimum parameters used for training CNN models |
| --- | --- | --- |
| Cellular subtypes (MRI) || Cellular subtypes (WSI) || Radiomics (MRI) || Molecular subtypes (WSI) || Survival (MRI) |
| No of Convolutional + ReLU layers || 5–30 || 17 || 13 || 19 || 14 || 15 |
| No of Droupout Layers || 2–8 || 4 || 3 || 4 || 3 || 5 |
| Maximum epochs || 10–100 || 75 || 55 || 69 || 92 || 71 |
| No of fully connected layers || 3 || 3 || 3 || 3 || 3 || 3 |
| No of convolutional kernels || 8–256 || 16, 32,64 || 16, 32, 64, 128 || 8, 16, 32, 64, 128 || 16, 32, 64, 128, 256 || 16, 32, 64, 128 |
| Kernel size || (3 × 3)…(11 × 11) || 3 × 3, 5 × 5, 7 × 7, 11 × 11 || 3 × 3, 5 × 5, 7 × 7, 11 × 11 || 3 × 3, 7 × 7, 9 × 9 || 3 × 3, 5 × 5, 7 × 7, 9 × 9 || 3 × 3, 5 × 5, 7 × 7 |
| Pooling layer || Max, Min, Average || Max || Average || Max || Max || Max |
| Pooling layer windows size || (2 × 2), (3 × 3), (4 × 4) || 2 × 2, 3 × 3, 4 × 4 || 3 × 3, 4 × 4 || 3 × 3, 4 × 4, 2 × 2 || 3 × 3, 4 × 4, 2 × 2 || 3 × 3, 4 × 4, 2 × 2 |
| Optimizers || SGD, Adam, RMSprop, Adagrad || Adam || SGD || SGD || Adam || SDG |
| Dropout rate || 0.2–0.5 || 0.25, 0.5, 0.3, 0.25 || 0.25, 0.5, 0.3 || 0.3, 0.3, 0.4, 0.5 || 0.3, 0.2, 0.4 || 0.3, 0.5, 0.3, 0.3, 0.4 |
| Initial learning rates || 1e−1,…,1e−5 || 1e−2 || 1e−3 || 1e−1 || 1e−2 || 1e−5 |
| Mini-batch size || 8–256 || 128 || 16 || 32 || 64 || 16 |

## 3: Applications of DL techniques for multi-disciplinary studies

This section presents the results of various case studies carried out by the authors using the DL techniques at different CSIR laboratories in India.

### 3.1: Applications of DL models in tumor diagnosis
