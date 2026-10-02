
12. Sfetsos, A. A novel approach for the forecasting of mean hourly wind speed time series. Renew. Energy 2002, 27, 163–174. [CrossRef]
13. Başaran, Ü.; Filik, T. Wind speed prediction using artificial neural networks based on multiple local measurements in Eskisehir. Energy Procedia 2017, 107, 264–269.
14. More, A.; Deo, M.C. Forecasting Wind with Neural Networks. Mar. Struct. 2003, 16, 35–49. [CrossRef]
15. Li, G.; Shi, J. On comparing three artificial neural networks for wind speed forecasting. Appl. Energy 2010, 87, 2313–2320. [CrossRef]
16. Zeng, J.W.; Qiao, W. Support vector machine-based short-term wind power forecasting. In Proceedings of the 2011 IEEE/PES Power Systems Conference and Exposition, Phoenix, AZ, USA, 20–23 March 2011; pp. 1–8.
17. Zhou, J.Y.; Shi, J.; Li, G. Fine tuning support vector machines for short-term wind speed forecasting. Energy Convers. Manag. 2011, 52, 1990–1998. [CrossRef]
18. Fazelpour, F.; Tarashkar, N.; Rosen, M.A. Short-term wind speed forecasting using artificial neural networks for Tehran. Iran. Int. J. Energy Environ. Eng. 2016, 7, 377–390. [CrossRef]
19. Fortuna, L.; Guariso, G.; Nunnari, S. One day ahead prediction of wind speed class by statistical models. Int. J. Renew. Energy Res. 2016, 6, 1137–1145.
20. Fortuna, L.; Nunnari, S.; Guariso, G. Fractal order evidences in wind speed time series. In Proceedings of the 2014 International Conference on Fractional Differentiation and Its Applications, Catania, Italy, 23–25 June 2014; pp. 1–6.
21. Mallat, S. A theory for multiresolution signal decomposition-the wavelet representation. IEEE Trans. Pattern Anal. Mach. Intell. 1989, 11, 674–693. [CrossRef]
22. Amjady, N.; Keynia, F. Short-term load forecasting of power systems by combination of wavelet transform and neuro-evolutionary algorithm. Energy 2009, 34, 46–57. [CrossRef]
23. Jang, J.S.R. ANFIS: Adaptive-network-based fuzzy inference system. IEEE Trans. Syst. Man Cybern. 1993, 23, 665–685. [CrossRef]
24. Graupe, P. Principles of Artificial Neural Networks, 2nd ed.; World Scientific: Singapore, 2007.
25. Levenberg, K. A method for the solution of certain non-linear problems in least squares. Q. J. Appl. Math. 1944, 2, 164–168. [CrossRef]
26. Michalides, C.; Loukogeorgaki, E.; Angelides, D.C. Monitoring the response of connected moored floating modules. In Proceedings of the 27th International Offshore and Polar Engineering, Anchorage, AK, USA, 30 June–5 July 2013; pp. 869–876, ISBN 978-1-880653-99-9.
27. Abdel-Aal, R.E.; Elhadidy, M.A.; Shaahid, S.M. Modeling and forecasting the mean hourly wind speed time series using GMDH-based abductive networks. Renew. Energy 2009, 34, 1686–1699. [CrossRef]
28. Kumar, G.; Malik, H. Generalized regression neural network based wind speed prediction model for western region of India. Procedia Comput. Sci. 2016, 93, 26–32. [CrossRef]
29. Troncoso, A.; Salcedo-Sanz, S.; Casanova-Mateo, C.; Riquelme, J.C.; Prieto, L. Local models-based regression trees for very short-term wind speed prediction. Renew. Energy 2015, 81, 589–598. [CrossRef]
30. Sun, G.; Chen, Y.; Wei, Z.; Li, X.; Cheung, K.W. Day-ahead wind speed forecasting using relevance vector machine. J. Appl. Math. 2014, 2014, 1–6. [CrossRef]
31. Botha, N.; van der Walt, C.M. Forecasting wind speed using support vector regression and feature selection. In Proceedings of the 2017 Pattern Recognition Association of South Africa and Robotics and Mechatronics, Bloemfontein, South Africa, 29 November–1 December 2017; pp. 181–186.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_31_0.png)

© 2019 by the authors. Licensee MDPI, Basel, Switzerland. This article is an open access article distributed under the terms and conditions of the Creative Commons Attribution (CC BY) license (http://creativecommons.org/licenses/by/4.0/).

Article

## Multivariate Temporal Convolutional Network: A Deep Neural Networks Approach for Multivariate Time Series Forecasting

Renzhuo Wan 1, Shuping Mei 1, Jun Wang 1, Min Liu 2 and Fan Yang 1,*

1 Nano-Optical Material and Storage Device Research Center, School of Electronic and Electrical Engineering, Wuhan Textile University, Wuhan 430200, China

2 State Key Laboratory of Powder Metallurgy, School of Physics and Electronics, Central South University, Changsha 410083, China

* Correspondence: yangfan@wtu.edu.cn

Received: 7 July 2019; Accepted: 5 August 2019; Published: 7 August 2019

**Abstract:** Multivariable time series prediction has been widely studied in power energy, aerology, meteorology, finance, transportation, etc. Traditional modeling methods have complex patterns and are inefficient to capture long-term multivariate dependencies of data for desired forecasting accuracy. To address such concerns, various deep learning models based on Recurrent Neural Network (RNN) and Convolutional Neural Network (CNN) methods are proposed. To improve the prediction accuracy and minimize the multivariate time series data dependence for aperiodic data, in this article, Beijing PM2.5 and ISO-NE Dataset are analyzed by a novel Multivariate Temporal Convolution Network (M-TCN) model. In this model, multi-variable time series prediction is constructed as a sequence-to-sequence scenario for non-periodic datasets. The multichannel residual blocks in parallel with asymmetric structure based on deep convolution neural network is proposed. The results are compared with rich competitive algorithms of long short term memory (LSTM), convolutional LSTM (ConvLSTM), Temporal Convolution Network (TCN) and Multivariate Attention LSTM-FCN (MALSTM-FCN), which indicate significant improvement of prediction accuracy, robust and generalization of our model.

**Keywords:** deep learning; multivariate time series forecasting; multivariate temporal convolutional network

### 1. Introduction

With the explosive growth of Internet of Things (IoT) applications and big data, multivariate time series is becoming ubiquitous in many fields, e.g., aerology [1], meteorology [2], environment [3], multimedia [4], power energy [5], finance [6], and transportation [7]. The precise trend forecasting, as well as for potential hazardous events, based on historical dynamical data are a major challenge, especially for aperiodic multivariate time series. One of the crucial reasons is aperiodic and nonlinearity among variables, which is incapable by models to capture and have self-adaption of the complex data features. Traditional methods such as Autoregressive (AR) [8] models and Gaussian Process (GP) [9] may fail. As an important part of the field of artificial intelligence, deep neural networks (DNNs) provide state-of-the-art accuracy on many tasks [10] and has been developed intensively in natural language processing (NLP), computer vision (CV), time series classifications and time series forecasting.

Enlightened by algorithms used in NLP (i.e., Sequence to Sequence [11,12] and Attention mechanism) and CV (i.e., Dilated convolution network [13] and residual structure [14]), in this paper, the M-TCN model is proposed for aperiodic multivariate time-series prediction, which constructs the aperiodic data as sequence-to-sequence and a novel multichannel and asymmetric residual blocks network. The model is cross validated by a rich set of existing competitive models with an aperiodic time series dataset. The reminder of the article is organized as follows: Section 2 reviews the background work. Section 3 presents the methodology of the proposed model. In Section 4, the experiment is analyzed and discussed. Finally, conclusions and outlook are drawn in Section 5.

### 2. Background

One of the major challenges of multivariate time series forecasting is nonlinearity and aperiodic of data originated by short-term and long-term dynamical behavior. Various models have been established based on classical statistic methods or machine learning algorithms.

The prominent classical univariate time series model is Autoregressive (AR) with classical statistic algorithms, as well as its progeny. The AR method is well used to stationary time series. The improved models, such as autoregressive integrated moving average (ARIMA) [15], autoregressive moving average (ARMA) [16], and vector auto-regression (VAR) [17], were developed by including flexible exponential smoothing techniques. However, for long-term temporal patterns, these models are inevitably prone to overfitting and high computational cost, especially for high-dimensional inputs.

Alternative methods by treating the time series forecasting problems as general regression with time-varying parameters were applied by machine learning models, e.g., linear support vector regression (SVR) [18], random forest [19], ridge regression [20] and LASSO [21] models. Those models are practically more efficient due to high quality off-the-shelf solutions in machine learning community. Still, machine learning based models may be incapable of including complex nonlinearity dependences of multivariate large datasets.

Meanwhile, the well-built deep neural networks of Convolutional Neural Networks (CNNs) and Recurrent Neural Networks (RNNs) have been widely applied in time series forecasting, which are attributed to the open source deep learning frameworks, such as Keras (Keras, available online: https://keras.io), TensorFlow (TensorFlow, available online: https://tensorflow.org) and PyTorch (PyTorch, available online: https://pytorch.org), including flexible and sophisticated mathematical libraries. Some representative models are long short-term memory (LSTM) [22] and its inheritors, convolutional LSTM (ConvLSTM) [23] and Multivariate Attention LSTM-FCN (MALSTM-FCN) [24], which overcome the challenges involved in training a recurrent neural network for a mixture of long and short-term horizons. However, these models are time consuming and non-robust for aperiodic data forecasting.

Another novel method for time-series forecasting is a hybrid multiscale approach, such as empirical mode decomposition (EMD) [25], ensemble EMD (EEMD) [26], multi-level wavelet decomposition network (mWDN) [27] and variational mode decomposition (VMD) [28]. These methods are used to decompose data into different frequencies’ components to facilitate forecasting. However, the pre-design decomposition K value is an essential prerequisite as an input of training models, which is not versatile for complicated multivariate time series prediction.

Recently, a general architecture for a predictive sequences model by convolutional and recurrent architecture on sequence modeling tasks, the Temporal Convolution Network (TCN) [29], is proposed. The prominent characteristics of TCNs are casualness in convolution architecture design and sequence length. In addition, it is also convenient to build a very deep and wide network by a combination of residual network and extended convolution. Under this background, our model is designed based on TCN and tested for PM2.5 and electric power forecasting.

For comparison, Table 1 contrasts the advantages and challenges of some common methods for multivariate time series prediction.
