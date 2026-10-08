
# Atmospheric Pollution Research 14 (2023) 101833

Contents lists available at ScienceDirect

# Atmospheric Pollution Research

journal homepage: www.elsevier.com/locate/apr

# Deep learning methods for atmospheric PM₂₅ prediction: a comparative study of transformer and CNN-LSTM attention

Bowen Cui a¹, Minyi Liu a¹, Shangjian Li b¹, Zhifan Jin c², Yu Zeng a¹, Xiaoling Lin b¹

* * College of Environment and Urban Construction, Fujian University of Technology, Fuzhou, 350108, China
* College of Science and Mathematics, Fujian University of Technology, Fuzhou, 350108, China
* c Fuzhou Environmental Monitoring Center, Fuzhou, 350118, China
* f Fuzhou Environmental Impact Assessment Technology Center, Fuzhou, 350003, China

# ARTICLE INFO

# ABSTRACT

A transformer-based method was firstly developed to predict the hourly PM₂₅ concentration at 12 monitoring stations in Beijing. Convolutional neural network short-term memory-attention mechanism (CNN-LSTM attention) were introduced to compare with Transformer models. Experiments on long time series and future prediction were conducted to evaluate the model performance and generalization ability over a period of time. The results, namely the mean variance score (EVS), R² absolute error, mean square error (MSE), and R values of Transformer were 12%, 6%, and 30% higher than those of the CNN-LSTM attention, respectively. The results show that the Transformer outperformed the CNN-LSTM model in terms of prediction accuracy. The capture-turn attention mechanism identifies patterns affected by abruptly meteorological conditions and trends with significant seasonal changes, in autumn and winter when the pollution situation is more complex. Transformer has obvious advantages in overcoming the independence problem of learning, providing a new method for the long-term prediction of air quality.

# 1. Introduction

China's air quality has greatly improved since the implementation of the Air Pollution Prevention and Control Plan in 2013, PM₂₅ concentrations in some cities still exceed the limits recommended by the World Health Organization (10 μg/m³). China still faces challenges in improving air quality in autumn and winter when pollution concentration in northern China sometimes exceeds the recommended limit (Guo et al., 2014). Regional pollution, which is mainly driven by PM₂₅, has been observed extensively in China (Zheng et al., 2008; Zhou et al., 2016). Air quality monitoring stations are densely distributed in urban areas and can provide the public with real-time air quality data, but the public needs a more accurate air quality prediction. The key is to use monitoring data from one or more stations to predict pollutant concentrations (Xu et al., 2021). Statistical and deterministic methods used in air quality prediction. Methods such as the multiple linear regression (Vloshchinski et al., 2011) and autoregressive moving average (ARMA) (Kumar and Jain, 2010) were used in short-term air quality prediction. However, the linear models cannot address the complex nonlinear effects of atmospheric pollutants and meteorological factors on pollutant concentrations. Furthermore, the photochemical models approach only focuses on individual pollutants that are directly measurable and is computationally intensive. In addition, physical models developed alone fail to accurately predict nonlinear air pollution processes due to improper conditions settings and even a lack of model parameters.

Free review under responsibility of Turkish National Committee for Air Pollution Research and Control.

* Corresponding author.

* E-mail: linaxy@fjut.edu.cn (X. Lin).

* 1 Contribution.

https://doi.org/10.1016/j.jpr.2023.101833

Received 15 March 2023; Received in form 4 June 2023; Accepted 2 July 2023

Available online 20 July 2023
1309-1042© 2023 Turkish National Committee for Air Pollution Research and Control. Production and hosting by Elsevier B.V. All rights reserved.

# B. Cui et al.

# Atmospheric Pollution 24 (2023) 108833

Neural networks (NNs) are used as a powerful machine learning (ML) model for natural language processing (Han et al., 2016) and air quality prediction (Fan et al., 2017; Ma and Zhang, 2016; Wang et al., 2019; Xing et al., 2020). NNs can automatically extract features from input data and predict target data through their end-to-end learning capability (Huang et al., 2021; Mehmod et al., 2022), they can be deployed as an effective model to model complex relationships in atmospheric systems and estimate concentration of environmental pollutants from measured data.

Convolutional neural networks (CNNs) can process data from multiple monitoring stations in a map-like manner based on the spatial distribution of features (Zhu and Xie, 2022) and can provide a higher prediction accuracy than fully neural networks (NNs) (Wu et al., 2018). The hybrid air quality index (AQI) has been used for air quality prediction through spatial decomposition, and some algorithms showed a good AQI prediction performance in Beijing (Gu and Lin, 2019). To observe the ability of learning the long-term dependence of air pollution, recurrent neural networks (RNNs) were introduced (Li et al., 2021).

Recurrent neural networks (RNNs) are considered to be superior to artificial neural networks (NNs) in modeling the changes of air quality. On the other hand, the effective performance of RNNs is limited by their inability to capture spatial dependencies. Recent studies, in exploiting spatial features (Fan et al., 2017; Tao et al., 2019; Wen et al., 2019), have combined RNNs and CNNs to capture the spatial and temporal features of air pollution-related pollutants, such as the concentration of various chemical species (SWCs) and PM2.5, but the prediction accuracy of RNNs depends on the number of observation input (Kocijan et al., 2018; Li et al., 2021).

Some meteorological factors drive the air quality evaluation patterns, suggesting the need to model different factors using different models. In air pollution, pollution may be influenced by meteorological factors, meteorological processes, atmospheric phenomena, and other factors. These may be localized and widespread, with complex relationships between the influencing factors and the pollutant concentration. Moreover, air quality also changes with sequential dependencies. Over time, the air quality will undergo periodic changes, suggesting a need to quickly predict future air quality based on known patterns of pollutant concentration from pollutant data as well as other meteorological factors. Although many ML models can improve prediction accuracy, they do not address the lag or long-term dependencies predicted by these models (Zhang et al., 2016).

Deep learning (DL) techniques, such as LSTM (Wang et al., 2019) and GRU (2018), are effective and can extract more information from time series data. Wang et al. developed a spatial-temporal integration model to predict the air quality in Beijing based on meteorological factors and the Granger causality (Cho et al., 2014). However, it was found that modeling long-term temporal dependencies will degrade the DL model's performance in terms of providing reliable predictions.

Transformer model is a type of sequence-to-sequence model, which was proposed by Google researchers in 2017. Such a model is an attention-based mechanism of DL, not involving any convolutional and recurrent units (Dosovitskiy et al., 2020; Han et al., 2021; Vaswani et al., 2017). The model output outperforms other NNs such as convolutional and recurrent NNs in terms of understanding and generation of complex data. However, the Transformer is constrained by the scale of the training data and the size of the model, which facilitates efficient training and allows the capture of the long-range features (Li et al., 2019; Li et al., 2021). The Transformer can be used for air quality prediction in the variety of time series (Li et al., 2021; Wen et al., 2022). The Transformer can model temporal factors and relative absolute position in the input and output sequences through continuous attention.

Recent studies have shown that the Transformer can model dependencies in continuous data (Chen et al., 2022; Sun et al., 2021; Manshu et al., 2022). The Transformer can be better understood as a model that learns the paths between different tokens, where the ability of the model to learn the dependencies is in. In CNNs and RNNs, the path length increases with the distance between two points, but in the Transformer, the path length is constant. Thus, self-attention mechanism allows the model to capture the association between two positions independent of the distance, which makes the Transformer's path length constant (Chomomsky et al., 2005; Touvron et al., 2017).

The Transformer has been applied to air quality prediction (Zhu et al., 2022; Li et al., 2022). However, due to the limitations of traditional models in modeling long-term series and temporal dependencies, they fail to capture the complex patterns of air quality pollutants. Therefore, the Transformer can be used to predict air quality better.

Self-attention mechanism can capture different meteorological patterns simultaneously, and the head-attention mechanism in the model can make the model self-attention to recognize the dependencies (Shen et al., 2018; Wu et al., 2021). The Transformer models have been successfully applied to time series prediction, which we consider to use such models for atmospheric air quality prediction.

A model was developed for air quality prediction based on the distribution of meteorological factors and character strength of the pollution factors deployed. Unlike the traditional transformer, the Transformer was optimized to integrate spatial and temporal features into the encoder.
