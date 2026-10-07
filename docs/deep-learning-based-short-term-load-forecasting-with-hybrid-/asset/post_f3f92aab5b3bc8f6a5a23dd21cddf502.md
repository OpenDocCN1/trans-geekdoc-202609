
[content]
energy consumption. The mutual information and RFS feature methods were applied for selecting the best features. The model was tested with SVR, CNN and RNN. The results show that an enhanced convolutional neural network outperformed other methods. The tendency issues addressed namely the temporal dependency in de-correlated load forecasting was discussed in [27] by He in the deep neural network which improved the implicit dynamics. In [28], Mohammad et al. presented a deep neural network for both day and ahead term load forecasting using CNN and LSTM models. The deep neural network and DFN were enhanced with hyperbolic tangent (tanh), and ReLU activation functions. As, the result with DNN outperformed other methods. In [29], the feature selection was based on the time series data using DNN with RNN. The DNN achieved a better prediction accuracy.

Authors [30] presented a deep neural network based model for load forecasting in the power system. The DNN was pretraining by using multiple layers of Restricted Bottleneck Machine. The BPNN was used in DNN for accurate fine-tuning and weight adjustment and yielded good prediction results. The enhanced CNN was used for forecasting electricity price in light demand market. The model achieved a reduced forecasting error than standard CNN and SVR. In [31], the CRBM and RFCM methods performed for load forecasting. Methods et al. presented a DNN for load forecasting. It handled the historical load sequences and better accuracy using ARIMA, RNN, and CNN.

With the increasing capability, the residual network can achieve a good accuracy in short term load forecasting [33]. In deep residual structure, the network of work was improved by using an ensemble strategy of adding hidden layers in the input. The deep residual network achieved higher accuracy than general DNN models. [34], Ryu et al. predicted short term load using deep neural network with RNN. The DNN with RNN having high-quality feature selection was used for load forecasting. It was constructed using MLP with RBM with discriminative pre-training. The hidden layers are changed discriminatively and pre-trained. The RNN with DNN achieved a better forecasting results.

Most of the researchers in use of deep learning methods like MLP, RNN, CNN, and LSTM. Some researchers performed only using only the historical load data without external features for improving the process. Other researchers utilized orthogonal features to identify the relevant and non-redundant features. So, they suffered from model complexity and dimensionality issues. The dimension of the dataset is reduced to achieve for the better forecasting accuracy. The temporal dependency on the load data is also an important information that helps in forecasting. Data also have the uncertainties. In this paper, the dimension of the dataset is reduced to enhance the accuracy of forecasting using hybrid selection and also uncertainty issues are taken into consideration by analyzing the temporal dependency on load data using RNN. So, the proposed RMR-HFS-LSTM data model fills these gaps by considering uncertainty, non-linearity, and overfitting of dimensionality issues and improves the load forecasting performance.

## 3. Proposed RMR-HFS-LSTM prediction model

## 3.1. Significance of R-HFS

The dataset with uncorrelated, unrelated and non-informative features may increase the dimension of dataset in which forces the model to overfit. It also causes complications for the forecasting models in generalizing the pattern. The model trained with too many features may not produce the accurate and robust results. It also observed that redundant features reduce the accuracy. The dataset may have many features. They are relevant, highly relevant and redundant features, weakly relevant and non-redundant, and strongly relevant features. The irrelevant features reduce the accuracy. These features should not be contributing to the forecasting accuracy. Instead, of that identifying the overfitting and reducing the accuracy. On the other hand, the strongly relevant and weakly relevant features help in forecasting. redundant features should be identified and removed.

In this paper, the RLeeff Recursive Information Hybrid Feature Selection (RMR-HFS) is introduced for the improvement of short term load forecasting usinging and filter feature selection methods. The method based on information filter feature selection and recursive-based feature selection wrapper method are applied to identify the subset of features. Feature selection methods are not suitable for all cases. The proposed method where RLeeff and information theoretic mutual information feature selection are used to eliminate the redundant features. The RLeeff filter selection is used for feature selection. The method identifies the relevant and non-informative features by the relationship between each feature and target feature. RLeeff does not consider the relationship between features.

Although, RMR and MI selects all the features it is general that the list of relevant features has many redundant features. The selection has the capacity of identifying and removing the redundant features using learning as a feature. So, the proposed method can improve the accuracy and avoid overfitting by using the recursive RFE base. The filter and wrapper selection method is proposed to avail the benefits of both feature selection. The optimal subset of features is given in for the deep learning LSTM model for load forecasting.

## 3.2. RMR-HFS-LSTM architecture

The proposed deep learning based model RMR-HFS-LSTM consists of three phases: data preprocessing, hybrid feature selection and prediction. In the first phase, the hourly electricity load and weather data are are treated as a single dataset. It is cleaned and normalized to prepare the data for further processing. The outliers and selection of dissimilar samples are eliminated. Then the instance based filter feature selection RLeeff and information theoretic mutual information feature selection are applied to identify the relevant features.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features.

[content]

The temporal dependency on the load data is also an important information that helps in forecasting. Data also have the uncertainties. In this paper, the dimension of the dataset is reduced to enhance the accuracy of forecasting using hybrid selection and also uncertainty issues are taken into consideration by analyzing the temporal dependency on load data using RNN. So, the proposed RMR-HFS-LSTM data model fills these gaps by considering uncertainty, non-linearity, and overfitting of dimensionality issues and improves the load forecasting performance.

## 3. Proposed RMR-HFS-LSTM prediction model

## 3.1. Significance of R-HFS

The dataset with uncorrelated, unrelated and non-informative features may increase the dimension of dataset in which forces the model to overfit. It also causes complications for the forecasting models in generalizing the pattern. The model trained with too many features may not produce the accurate and robust results. It also observed that redundant features reduce the accuracy. The dataset may have many features. They are relevant, highly relevant and redundant features, weakly relevant and non-redundant, and strongly relevant features. The irrelevant features reduce the accuracy. These features should not be contributing to the forecasting accuracy. Instead, of that identifying the overfitting and reducing the accuracy. On the other hand, the strongly relevant and weakly relevant features help in forecasting. redundant features should be identified and removed.

In this paper, the RLeeff Recursive Information Hybrid Feature Selection (RMR-HFS) is introduced for the improvement of short term load forecasting usinging and filter feature selection methods. The method based on information filter feature selection and recursive-based feature selection wrapper method are applied to identify the subset of features. Feature selection methods are not suitable for all cases. The proposed method where RLeeff and information theoretic mutual information feature selection are used to eliminate the redundant features. The RLeeff filter selection is used for feature selection. The method identifies the relevant and non-informative features by the relationship between each feature and target feature. RLeeff does not consider the relationship between features.

Although, RMR and MI selects all the features it is general that the list of relevant features has many redundant features. The selection has the capacity of identifying and removing the redundant features using learning as a feature. So, the proposed method can improve the accuracy and avoid overfitting by using the recursive RFE base. The filter and wrapper selection method is proposed to avail the benefits of both feature selection. The optimal subset of features is given in for the deep learning LSTM model for load forecasting.

## 3.2. RMR-HFS-LSTM architecture

The proposed deep learning based model RMR-HFS-LSTM consists of three phases: data preprocessing, hybrid feature selection and prediction. In the first phase, the hourly electricity load and weather data are are treated as a single dataset. It is cleaned and normalized to prepare the data for further processing. The outliers and selection of dissimilar samples are eliminated. Then the instance based filter feature selection RLeeff and information theoretic mutual information feature selection are applied to identify the relevant features.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The selected features of M and Rleff are combined to get (COMPS) to find the most relevant features. However, the tuned wrapper feature selection, is, to improve the filter method, produces the optimal subset of features. In the third phase, the LSTM prediction model is built and trained. The parameters of the constructed models are tuned using the time series cross validation on validation data. Finally, the performance of the proposed R-HFS-LSTM with all features compared against several baseline models in terms of error metrics such as MAPE and MAE. The result is shown in Fig.

The temporal dependency on the load data is also an important information that helps in forecasting. Data also have the uncertainties. In this paper, the dimension of the dataset is reduced to enhance the accuracy of forecasting using hybrid selection and also uncertainty issues are taken into consideration by analyzing the temporal dependency on load data using RNN. So, the proposed RMR-HFS-LSTM data model fills these gaps by considering uncertainty, non-linearity, and overfitting of dimensionality issues and improves the load forecasting performance.

### 3.2.1.1. Rleff

The Recursive Regression (Rleff) feature selection is It randomly selects and removes features from the original instance. Then, it selects k number of features using the variance function.

```
P(A|B) = P(difference|nearest instances)
```

```
P(AG) = P(difference|nearest instances)
```

```
P(AG|ABC) = P(difference of A and nearest instances)
```

```
W[A] = P(AG|ABC) * (1 - P(A|B)) / (1 - P(A))
```

The feature with the highest weight is considered as the best feature among other features. Rleff has the same time complexity as simple regression.

### 3.2.1.2. Mutual information selection

The mutual information is a non linear correlation filter selection that calculates the correlation between two or more of features. The features have common information with other feature is called a dependent feature. On the other hand, the features with no common information are called independent features. The mutual information method utilizes the dependency between the features related to the target as a base for finding the relevant feature. The amount of information shared between features is called mutual information. If there are two features, then the mutual information between them is measured as I(A;B). When 'A' and 'B' are independent, the mutual information I(A;B) is 0. The data is in continuous. For continuous random variables, the mutual information of the feature 'A' is calculated as

```
I(A;B) = sum p(A,B) * log (p(A,B)/(p(A)p(B))) dB
```

where 'a' and 'b' represents the number of values in 'A' and 'B'. Then, the P(a,b) is the joint probability density of 'A' and 'B'. The pa and pb are marginal probability density function of 'A' and 'B'.

### 3.2.1.3. Recursive elimination.

The recursive elimination is the type of wrapper feature selection. Generally, it selects the

![](img/8f28a644aa4b94b031efafb7a94e5d53_3_0.png)

Fig. R-HFS-LSTM Prediction Model.
