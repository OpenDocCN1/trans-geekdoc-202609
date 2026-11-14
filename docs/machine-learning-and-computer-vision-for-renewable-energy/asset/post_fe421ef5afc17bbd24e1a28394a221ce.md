
## A Deep Learning Framework for Modeling Temporal Dependencies

### Table 4. Spearman rank correlation

| | Hour | Day | Week | Month | Quarter | Half_year | Year |
|---|---|---|---|---|---|---|---|
| Hour | 1.00 | | | | | | |
| Day | 0.00 | 1.00 | | | | | |
| Week | 0.00 | 0.06 | 1.00 | | | | |
| Month | 0.00 | 0.00 | 0.97 | 1.00 | | | |
| Quarter | 0.00 | 0.00 | 0.94 | 0.97 | 1.00 | | |
| Half_year | 0.00 | -0.01 | -0.84 | -0.86 | -0.89 | 1.00 | |
| Year | 0.00 | -0.01 | -0.20 | -0.20 | -0.20 | 0.14 | 1.00 |

Score is 0.7284 (high), showing well-separated clusters. However, the Davies-Bouldin Index is 1.0289 (moderate), showing moderate cluster separation, and the Mini-Batch K-Means, Silhouette Score is determined to be 0.3805 (moderate), indicating moderate cluster separation as well.

Finally, with Fuzzy C-Means we found that Silhouette Score was found to be 0.3734 (moderate), indicating moderate cluster separation while Davies-Bouldin Index is given as 1.0554 (moderate), suggesting moderate cluster separation. All in all, K-Means appears to have the best performance among the three, with a higher Silhouette Score and lower Davies-Boulden Index values. While Mini-Batch K-Means and Fuzzy C-Means show similar, moderate performance based on these metrics. Finally, our temporal dependencies for hierarchy in each cluster using k-means are given in Figure 10.

### CONCLUSION AND FUTURE DIRECTION

Although accurate and reliable estimation of electricity/power consumption is extremely important, the field has despondently attracted less attention than other fields. But in the last few years, researchers have made some major strides and developed forecast models that are reliable, accurate, and effective by utilizing deep learning (DL) and artificial intelligence (AI). Due to their features and significance, these techniques—AI and DL—performed well and efficiently in handling non-linear problems with time-series data. In this chapter, we present a deep-learning ensemble method that uses chronological dependencies to anticipate and predict the hourly load of electricity demand. To guarantee model performance, our system first processes the data cleaning, normalizing, and transforming it.

Furthermore, the preprocessed data is fed into an ensemble model to extract hybrid discriminative features by using RNN, LSTM, CNN and, stacking ensemble architectures. This will enable the utilities to plan resources and balance supply-demand, thereby ensuring stability and security of the power grid and reliability of service provisions. Using an hourly electrical demand load, we assessed the suggested system and compared the outcomes, which are displayed in Table 3. Targeting future effort, a variety of non-linear exogenous data structures, such as variables, monetary features, and weather/climate conditions or changes, can be investigated for the tendency analysis of power loading patterns. Furthermore, a number of optimization techniques can be thought of and developed to raise the recommended system’s forecast accuracy.

### Table 5. Performance of clustering algorithms

| | Silhouette Score | Davies-Bouldin Index |
|---|---|---|
| K-means | 0.728393737 | 0.501091441 |
| Mini-Batch K-Means | 0.380461786 | 1.028941784 |
| Fuzzy C-Means | 0.373376881 | 1.055433432 |

### Figure 10. Clustering of electricity demand hierarchies

![](img/2e8f3dfd000fbfaa074ac5bc7a8b2717_78_0.png)

### REFERENCES

- Adhikari, R. J. N. (2015). A neural network based linear ensemble framework for time series forecasting. Academic Press.
- Ahmadi, A., Daccache, A., Sadegh, M., & Snyder, R. L. (2023), Statistical and deep learning models for reference evapotranspiration time series forecasting: A comparison of accuracy, complexity, and data efficiency. Computers and Electronics in Agriculture, 215. doi:10.1016/j.compag.2023.108424
- Aldhsan, S. R. S., Abdul Maulud, K. N., Wan Mohd Jaafar, W. S. Karim, O. A., & Pradhan, B. (2021). Energy Consumption and Spatial Assessment of Renewable Energy Penetration and Building Energy Efficiency in Malaysia: A Review. Sustainability (Basel), 13(16), 9244. doi:10.3390/su13169244
- Bagnall, A., Lines, J., Hills, J., & Bostrom, A. (2015). Time-series classification with COTE: The collective of transformation-based ensembles. IEEE Transactions on Knowledge and Data Engineering, 27(9), 2522–2535. doi:10.1109/TKDE.2015.2416723
- Bandara, K., Bergmeir, C., & Smyl, S. (2020). Forecasting across time series databases using recurrent neural networks on groups of similar series: A clustering approach. Expert Systems with Applications, 140, 112896. doi:10.1016/j.eswa.2019.112896
- Cordeiro-Costas, M., Villanueva, D., Eguía-Oller, P., Martínez-Comesaña, M., & Ramos, S. (2023). Load Forecasting with Machine Learning and Deep Learning Methods. Applied Sciences (Basel, Switzerland), 13(13), 7933. doi:10.3390/app13137933
- Ensafi, Y., Amin, S. H., Zhang, G., & Shah, B. (2022). Time-series forecasting of seasonal items sales using machine learning–a comparative analysis. International Journal of Information Management Data Insights, 2(1), 100058. doi:10.1016/j.jjimei.2022.100058
- Hagenau, M., Liebmann, M., & Neumann, D. (2013). Automated news reading: Stock price prediction based on financial news using context-capturing features. Decision Support Systems, 55(3), 685–697. doi:10.1016/j.dss.2013.02.006
- Hamed, M. M., Ali, H., & Abdelal, Q. (2022). Forecasting annual electric power consumption using a random parameters model with heterogeneity in means and variances. Energy, 255, 124510. doi:10.1016/j.energy.2022.124510
- Hochreiter S, & Schmidhuber J (1997). Long Short-Term Memory. Neural Comput, 9(8), 1735–1780. doi:10.1162/neco.1997.9.8.1735
- Huang, S.-H., & Pan, Y.-C. (2014). Ergonomic job rotation strategy based on an automated RGB-D anthropometric measuring system. Journal of Manufacturing Systems, 33(4), 699–710. doi:10.1016/j.jmsy.2014.02.005
- Huang, S.-H., & Pan, Y.-C. (2015). Automated visual inspection in the semiconductor industry: A survey. Computers in Industry, 66, 1–10. doi:10.1016/j.compind.2014.10.006
- Jin, L., & Dong, J. (2016). Ensemble deep learning for biomedical time series classification. Computational Intelligence and Neuroscience. doi:10.1155/2016/6212684 PMID:27725828
- Jogonula, O., Adebisi, B., Hoang, K. V., Tsado, Y., Popoola, S. I., Hammoudeh, M., & Nawaz, R. (2022). CBLSTM-AE: A Hybrid Deep Learning Framework for Predicting Energy Consumption. Energies, 15(3), 810. doi:10.3390/en15030810
- Kamal-Chaoui, L., & Robert, A. (2009). Competitive cities and climate change. Academic Press.
- Kohzadi, N., Boyd, M. S., Kermanshahi, B., & Kaastra, I. (1996). A comparison of artificial neural network and time series models for forecasting commodity prices. Neurocomputing, 10(2), 169–181. doi:10.1016/0925-2312(95)00020-8
- Kranjc, J., Smailović, J., Podpečan, V., Grčar, M., Žnidaršič, M., & Lavrač, N. (2015). Active learning for sentiment analysis on data streams: Methodology and workflow implementation in the CloudFlows platform. Information Processing & Management, 51(2), 187–203. doi:10.1016/j.ipm.2014.04.001
- Le, T., Vo, M. T., Vo, B., Hwang, E., Rho, S., & Baik, S. W. (2019). Improving electric energy consumption prediction using CNN and Bi-LSTM. Applied Sciences (Basel, Switzerland), 9(20), 4237. doi:10.3390/app9204237
- Liu, T., Tan, Z., Xu, C., Chen, H., & Li, Z. (2020). Study on deep reinforcement learning techniques for building energy consumption forecasting. Energy and Building, 208, 109675. doi:10.1016/j.enbuild.2019.109675
- Lotfipoor, A., Patidar, S., & Jenkins, D. P. (2024). ‘Deep neural network with empirical mode decomposition and Bayesian optimisation for residential load forecasting’, Expert Systems with Applications, vol. 237, 121355. Advance online publication. doi:10.1016/j.eswa.2023.121355
- Mariano-Hernández, D., Hernández-Callejo, L., García, F. S., Duque-Perez, O., & Zorita-Lanandrid, A. L. (2020). A Review of Energy Consumption Forecasting in Smart Buildings: Methods, Input Variables, Forecasting Horizon and Metrics. Applied Sciences (Basel, Switzerland), 10(23), 8323. doi:10.3390/app10238323
- Rahman, M. M., Shakeri, M., Tiong, S. K., Khatun, F., Amin, N., Pasupuleti, J., & Hasan, M. K. (2021). Prospective methodologies in hybrid renewable energy systems for energy prediction using artificial neural networks. Sustainability (Basel), 13(4), 2393. doi:10.3390/su13042393
- Razavi, R., Gharipour, A., Fleury, M., & Akpan, I. J. (2019). Occupancy detection of residential buildings using smart meter data: A large-scale study. Energy and Building, 183, 195–208. doi:10.1016/j.enbuild.2018.11.025
- Sharma, N., Jain, V., & Mishra, A. (2018). An analysis of convolutional neural networks for image classification. Procedia Computer Science, 132, 377–384. doi:10.1016/j.procs.2018.05.198
- Shiri, Perumal, Mustapha, & Mohamed. (n.d.). A Comprehensive Overview and Comparative Analysis on DeepLearningModels: CNN, RNN, LSTM, GRU. https://arxiv.org/ftp/arxiv/papers/2305/2305.17473.pdf
- Singaravel, S., Suykens, J., & Geyer, P. (2018). Deep-learning neural-network architectures and methods: Using component-based models in building-design energy prediction. Advanced Engineering Informatics, 38, 81–90. doi:10.1016/j.aei.2018.06.004
- Slater, L. J., Arnal, L., Boucher, M., Chang, A., Moulds, S., Murphy, C., Nearing, G., Shalev, G., Shen, C., Speight, L., Villarrini, G., Wilby, R. L., Wood, A., & Zappa, M. (2022). Hybrid forecasting: Using statistics and machine learning to integrate predictions from dynamical models. Hydrology and Earth System Sciences. Advance online publication. doi:10.5194/hess-2022-334
- Somu, N., Raman, M. R. G., & Ramamritham, K. (2021). A deep learning framework for building energy consumption forecast. Renewable & Sustainable Energy Reviews, 137, 110591. doi:10.1016/j.rser.2020.110591
- Wang, Z., & Oates, T. (2015). Imaging time-series to improve classification and imputation. arXiv preprint arXiv:00327.
