
The detection results obtained from RNN-RBM-based clustering approaches are summarized as radar chart in Fig. 7.17. The detection approach based on RNN-RBM-based OCSVM method can adequately detect the abnormal conditions by achieving an AUC of 0.98 (Fig. 7.17). This result indicates that RNN-RBM-based OCSVM uncovers almost all abnormal events in IM measurements declared by the operator KAUST WRRF. In addition, the results show that OCSVM outperforms the other methods (Fig. 7.17). This is mainly due to the flexible capacity of RNN-RBM to model time-series data and the ability of OCSVM to detect small deviations in the features.

![](img/aa2f42c739937b682075082233e335bb_255_0.png)

FIGURE 7.17 Detection efficiency of RNN-RBM-based clustering approaches based on testing data.

We then compared the detection results of the hybrid RNN-RBM-based clustering algorithms to other deep models, RNN, RBM, and DBM. In RNN, RBM, and DBM-based approaches, the binary clustering schemes (i.e., OCSVM, K-means, BIRCH, mean-shift, maximum expectation, and spectral clustering) are applied to the output features of the RNN, RBM, and DBM models. A summary of the performance of RNN, RBM, and DBM-based clustering schemes are respectively presented in Figs. 7.18, 7.19 and 7.20.

From Figs. 7.17, 7.18, 7.19, and 7.20, we can see that the RNN-RBM-based approaches have a better detection performance compared to RNN, RBM, and DBM-based techniques. In fact, RBM and DBM models do not capture time dependence in modeling time-series data, which misses important features, and the pattern might be due to unsuitable detection performance when they are used as features extractors (RNN and DBM) for anomaly detection. RNN-RBM model is a powerful hybrid neural architecture able to model temporal correlation across large time steps in the multivariate data and thus leads to a more representative model. The results demonstrate that the RNN-RBM-based approach offers enhanced performance compared to RNN, RBM, and DBM-based approaches in monitoring ICs of KAUST WRRF. We believe this is because RNN-RBM model is appropriate for approximating a complicated distribution for each time step.

EM KM MS OCSVM SC AGC

![](img/aa2f42c739937b682075082233e335bb_256_0.png)

FIGURE 7.18 Detection efficiency of RNN-based clustering approaches based on testing data.

EM KM MS OCSVM SC AGC

![](img/aa2f42c739937b682075082233e335bb_256_1.png)

FIGURE 7.19 Detection efficiency of RBM-based clustering approaches based on testing data.

EM KM MS OCSVM SC AGC

![](img/aa2f42c739937b682075082233e335bb_256_2.png)

FIGURE 7.20 Detection efficiency of DBM-based clustering approaches based on testing data.

In addition, we also compared the efficiency of the proposed approach with stand-alone clustering techniques in detecting abnormalities in IC data. Fig. 7.21 presents the results obtained when applying stand-alone clustering techniques to IC data. One can see that the achieved monitoring results by the stand-alone clustering methods to monitor IC data are unsatisfactory. Experimental results on IC data show that RNN-RBM-based OCSVM outperforms the baseline competitors by a large margin (Fig. 7.21).

![](img/aa2f42c739937b682075082233e335bb_257_0.png)

FIGURE 7.21 Detection performances of stand-alone clustering detectors.

Furthermore, to make the comparison of the results easier, Fig. 7.22 displays the AUC comparison between the studied algorithms. The results indicate that the RNN-RBM-based OCSVM is better at detecting anomalies in comparison to the other methods presented in this study.

![](img/aa2f42c739937b682075082233e335bb_257_1.png)

FIGURE 7.22 AUC metric of RNN-RBM, RBM, and DBM.

In summary, the results indicate that the hybrid RNN-RBM model is an intuitive choice for modeling IMs multivariate time-series data. The RNN-RBM modeling approach has been combined with binary clustering algorithms to monitor IMs data of KAUST WWTP. RNN-RBM with OCSVM can adequately distinguish normal observations from abnormal IMs observations. This study shows that the combination of RNN-RBM and OCSVM results in better detection. RNN-RBM are designed to handle multivariate time series data and OCSVM is efficient in separating normal from abnormal features. From the results above, we can summarize that the RNN-RBM-based OCSVM are more appropriate and efficient than the stand-alone clustering schemes, and the RBM and DBM-based and RNN-based clustering approaches, which justifies the superior feature extraction of the RNN-RBM model. Furthermore, OCSVM, which is trained in an unsupervised way, can accurately distinguish the normal from abnormal conditions compared to other studied binary clustering algorithms. The power of OCSVM consists of that it is a nonlinear kernel-based classifier, which defines hyperplane separating anomaly-free samples and abnormal samples by means of the projection in features space. The OCSVM demonstrated its highest performance by dominating the other competitors in all cases presented in this study.

### 7.6 Discussion

Anomaly detection has applications in various domains, such as air quality monitoring, intrusion detection, product quality monitoring, and system health monitoring. Recurrent deep learning models present new ways to model complex time series data due to their extended capability to capture nonlinear interdependencies, which goes beyond a traditional mindset. As discussed in this chapter, recurrent models such as RNN, LSTM, GRU are becoming well-reputed with the recent breakthrough in deep learning and they are very efficient in describing temporal dependencies in multivariate time series data. It should be noted that RNN units are subjected to the vanishing/exploding gradient issue, which degrades the model's capacity to capture long-term dependencies. To alleviate these problems, LSTM and GRU units have been designed and yield improved results as described in Sects. 7.2 and 7.3.

To uncover anomalies in time series data, recurrent models are used to extract relevant information from massive data and generate residuals which are then evaluated by existing monitoring tools (e.g., statistical monitoring schemes and clustering algorithms) that are proven effective. One of the major advantages of using these unsupervised deep recurrent models to detect anomalies is that they do not need hand-coded features and prior knowledge of anomalies to work. For the purpose of anomaly detection, residuals generated by the reference recurrent models can be checked by the statistical monitoring schemes such as univariate and multivariate CUSUM and EWMA or by using binary clustering algorithms. In this chapter, we discussed the general framework of recurrent deep learning based anomaly detection in Sect. 7.4.

In this chapter, to improve process monitoring in case of high-dimensional data, we have described some hybrid models integrating the benefits of recurrent models and energy-based models such as RBM and DBN. These recurrent hybrid models enjoy certain desirable properties when modeling high-dimensional time-series datasets. Here, three flexible hybrid models to capture temporal dependencies in a multivariate setting were discussed: RNN-RBM, LSTM-RBM, and LSTM-DBN architectures. In this chapter, deep hybrid recurrent models were coupled with binary clustering algorithms for anomaly detection in multivariate time series data.

The efficacy of RNN, RBM, and RNN-RBM based methods, or stand-alone binary clustering methods, has been verified by using seven years ICs data from an actual WWTP where more than 150 anomalies happened. Results show that RNN-RBM-based OCSVM outperformed the state-of-the-art competitors by a large margin. As a perspective, other powerful architectures that help learn temporal dependencies in data can be explored by merging recurrent models and energy-based models and autoencoders.

## References

- [1] H. Lütkepohl, New Introduction to Multiple Time Series Analysis, Springer Science & Business Media, 2005.
- [2] J.D. Hamilton, Time series analysis, in: Economic Theory. II, Princeton University Press, USA, 1995, pp. 625–630.
- [3] I. Melnyk, A. Banerjee, Estimating structured vector autoregressive models, in: International Conference on Machine Learning, 2016, pp. 830–839.
- [4] J. Li, W. Chen, Forecasting macroeconomic time series: lasso-based approaches and their forecast combinations with dynamic factor models, International Journal of Forecasting 30 (4) (2014) 996–1015.
- [5] R. Frigola, F. Lindsten, T.B. Schön, C.E. Rasmussen, Bayesian inference and learning in Gaussian process state-space models with particle MCMC, in: Advances in Neural Information Processing Systems, 2013, pp. 3156–3164.
- [6] Z. Chen, Y. Chen, L. Wu, S. Cheng, P. Lin, L. You, Accurate modeling of photovoltaic modules using a 1-D deep residual network based on IV characteristics, Energy Conversion and Management 186 (2019) 168–187.
- [7] F. Harrou, A. Dairi, Y. Sun, F. Kadri, Detecting abnormal ozone measurements with a deep learning-based strategy, IEEE Sensors Journal 18 (17) (2018) 7222–7232.
- [8] F. Harrou, A. Dairi, Y. Sun, M. Senouci, Statistical monitoring of a wastewater treatment plant: a case study, Journal of Environmental Management 223 (2018) 807–814.
- [9] K. Cho, B. Van Merriënboer, C. Gulcehre, D. Bahdanau, F. Bougares, H. Schwenk, Y. Bengio, Learning phrase representations using RNN encoder–decoder for statistical machine translation, preprint, arXiv:1406.1078, 2014.
- [10] J. Chung, C. Gulcehre, K. Cho, Y. Bengio, Empirical evaluation of gated recurrent neural networks on sequence modeling, preprint, arXiv:1412.3555, 2014.
- [11] G.-B. Zhou, J. Wu, C.-L. Zhang, Z.-H. Zhou, Minimal gated unit for recurrent neural networks, International Journal of Automation and Computing 13 (3) (2016) 226–234.
- [12] T. Mikolov, A. Joulin, S. Chopra, M. Mathieu, M. Ranzato, Learning longer memory in recurrent neural networks, preprint, arXiv:1412.7753, 2014.
- [13] Q.V. Le, N. Jaitly, G.E. Hinton, A simple way to initialize recurrent networks of rectified linear units, preprint, arXiv:1504.00941, 2015.
- [14] Y. LeCun, Y. Bengio, G. Hinton, Deep learning, Nature 521 (7553) (2015) 436.
- [15] S. Hochreiter, J. Schmidhuber, Long short-term memory, Neural Computation 9 (8) (1997) 1735–1780.
- [16] A. Graves, M. Liwicki, S. Fernández, R. Bertolami, H. Bunke, J. Schmidhuber, A novel connectionist system for unconstrained handwriting recognition, IEEE Transactions on Pattern Analysis and Machine Intelligence 31 (5) (2009) 855–868.
- [17] W. Zaremba, I. Sutskever, O. Vinyals, Recurrent neural network regularization, preprint, arXiv: 1409.2329, 2014.
