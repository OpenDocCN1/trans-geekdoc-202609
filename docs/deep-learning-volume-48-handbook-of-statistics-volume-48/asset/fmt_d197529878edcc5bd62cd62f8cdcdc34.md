
Whole-slide histopathological (WSI) images of tumor tissues stained with Hematoxylin and Eosin (H&E) stains are used by histopathologists to understand the cellular and tissue structures of tumor samples. Histopathologists manually inspect the WS images of tumor samples and routinely determine tumor grades (Grades-I/II/III/IV) and other cellular phenotypes (astrocytoma, oligoastrocytoma, oligodendroglioma, etc.) of tumor biopsy samples of glioma patients. However, histopathologists cannot determine molecular subtypes of glioma tissue by manually inspecting the WSI. Four molecular subtypes of glioma (classical, mesenchymal, neural, and proneural), which are derived from molecular profiles of glioma patients, help understand tumor biology and prognosis (`[Kong et al., 2011](#Ch006_107-168_S0169716122000578.xhtml#bb0195)`; `[Lin et al., 2014](#Ch006_107-168_S0169716122000578.xhtml#bb0215)`). In the TCGA-LGG and TCGA-GBM cohorts, WS images of patients along with their molecular subtypes are available. Here, we have used WS images labeled with molecular subtypes to train a deep-learning CNN model and assessed its performance by evaluating AUC. During model training, the AUC value for classifying the multi-class dataset was 0.82. When applied to a blind data set of WS histopathology images, the trained DL model achieved 76% accuracy in classifying molecular subtypes of glioma tissues (`[Table 4](#Ch006_107-168_S0169716122000578.xhtml#t0025)`). This result suggests that subtle morphological differences across different molecular subtypes of tumor cells that cannot be identified in WSI under the microscope can be classified by utilizing the power of deep learning models.

###  3.3: Application of the deep learning model for the prognosis of glioma patients

For oncologists, accurate assessment of the prognosis of glioma patients, for example, determining the median overall survival (OS), is a critical task (`[Pei et al., 2020](#Ch006_107-168_S0169716122000578.xhtml#bb0290)`; `[Sun et al., 2019](#Ch006_107-168_S0169716122000578.xhtml#bb0340)`). We have trained a deep learning model using CNN by training MR images labeled with OS (in months) data of low and high-grade glioma patients of TCGA-LGG and TCGA-GBM cohorts. During training, the CNN architecture (`[Table 5](#Ch006_107-168_S0169716122000578.xhtml#t0030)`) achieved a loss function value of 0.32 and an accuracy of 0.87 in 67 epochs. The minimal value of the loss function ensures less overfitting of the model with the respective labels during training. The deep learning model with optimized parameters, when applied to the blind dataset, achieved a significant level of accuracy (85%) to determine the median OS of glioma patients.

```
[Table 5](#Ch006_107-168_S0169716122000578.xhtml#B-t0030)
```

Training performances of the model for predicting tumor molecular characteristics. 

| Data  || Performance metrics || Blind data (accuracy %) |
| --- | --- | --- |
| TPR || FPR || Precision || Recall || F-measure || AUC | 76% |
| MRI (survival) || 0.82 || 0.27 || 0.82 || 0.82 || 0.81 || 0.80 || 85% |
| MRI (mutations) || 0.89 || 0.18 || 0.90 || 0.89 || 0.89 || 0.92 || 86% |

###  3.4: Applications of DL model for predicting driver gene mutations in glioma

Identifying the mutational landscape of low and high-grade glioma tumors is highly beneficial for oncologists to decide on the right course of diagnosis and prognosis for the patients (`[Chang et al., 2018](#Ch006_107-168_S0169716122000578.xhtml#bb0095)`; `[Zinn et al., 2017](#Ch006_107-168_S0169716122000578.xhtml#bb0420)`). We have developed a radio-genomics deep learning model for identifying the mutation status of cancer hallmark genes `EGFR` and `TP53`. The overall performances of this model in both training and blind datasets are shown in `[Table 5](#Ch006_107-168_S0169716122000578.xhtml#t0030)`. With this model, we were able to classify MR images of brain tumors into three mutational classes: `TP53`^(*mutant*)/`EGFR`^(*wild-type*), `TP53`^(*wild-type*)/`EGFR`^(*mutant*), and `TP53`^(*mutant*)/`EGFR`^(*mutant*). The model achieved good accuracies and relative performance metrics in both training (TPR = 0.885, FPR = 0.1671, Precision = 0.902, Recall = 0.885, F-measure = 0.890, AUC = 0.924) and blind data sets (86% accuracy) as presented in `[Fig. 11](#Ch006_107-168_S0169716122000578.xhtml#f0060)`. The 95% confidence interval of the AUC value was 0.91–0.97, suggesting MR images could provide better accuracies for identifying the mutation status of cancer hallmark genes.

![Fig. 11 Application of deep learning model in radiogenomics study of glioma tumors.](images/S0169716122000578/f06-11-9780443184307.jpg)

[Fig. 11](#Ch006_107-168_S0169716122000578.xhtml#B-f0060) Application of deep learning model in radiogenomics study of glioma tumors.

The model showed a higher level of accuracy and minimal values of the loss function in both training and validation data sets.

###  3.5: Application of Time Division LSTM for short-term prediction of wind speed

The atmosphere consists of multiple interdependent parameters whose variations cause significant changes in weather patterns. Each of these parameters has a significant impact on the environment. One of the major atmospheric variables, wind speed helps in generating green energy which is responsible for reducing pollution. Considering the importance of wind in various sectors like environmental, societal, economic, etc., a detailed study has been carried out and the “Time Division Ensemble” algorithm is used for short-range wind speed prediction, i.e., 3 h ahead at station scale from two locations New Delhi and Bangalore with given inputs as atmospheric temperature (T), humidity (H), pressure (P), wind speed (V) (`[Marndi et al., 2020](#Ch006_107-168_S0169716122000578.xhtml#bb0240)`).

Hence, the input can be represented as quadruple `I[n]` *=`(T[n], P[n], V[n], H[n])`* where, *n* is the index at the current timestamp, *n* + 1 for the future, and *n* − 1 for past timestamps. As data were collected in 30 min intervals, there is 30 min gap between two consecutive input data. It is required to predict wind speed at six-time stamps ahead, i.e., `V[n + 6]` to achieve 3 h advance prediction as a requirement of LSTM1.

The capability of LSTM is utilized by considering data from multiple timestamps. In the second non-ensemble mode (LSTM2), input data `I[n-2,]*I[n-1,]*I[n],` is formed by considering data from three consecutive timestamps and to achieve 3 h ahead prediction wind speed is predicted at *(n + 6)th* step ahead, i.e., `V[n + 6]`. The generalized version of LSTM1 and LSTM2 (`[Fig. 8A and B](#Ch006_107-168_S0169716122000578.xhtml#f0045)`) can be modified as `[Fig. 12A and B](#Ch006_107-168_S0169716122000578.xhtml#f0065)`.

![Fig. 12 Standard LSTM (A) LSTM1 (Single time step Multiple variables) and (B) LSTM2 (Multiple variables at Multiple time steps).](images/S0169716122000578/f06-12-9780443184307.jpg)

[Fig. 12](#Ch006_107-168_S0169716122000578.xhtml#B-f0065) Standard LSTM (A) LSTM1 (Single time step Multiple variables) and (B) LSTM2 (Multiple variables at Multiple time steps).

####  3.5.1: Performance evaluations of Time Division LSTM for short term wind speed prediction

The Time Division LSTM model is compared with two data-driven models and one classical model for predicting short-term wind speed. The training and validation losses are calculated to determine the number of epochs to be considered for prediction. It is observed that training validation loss is converged after 60 epochs for New Delhi station whilst in the case of Bengaluru, a loss is converged at 30 epochs. Hence for New Delhi and Bengaluru stations, epochs are fixed at 60 and 30 respectively. The same configuration is maintained in the case of the second-level LSTM of LSTM4 which is hierarchical in nature.
