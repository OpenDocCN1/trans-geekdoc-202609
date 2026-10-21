
![](img/a682317eba97b725284edc1c3cd47b8a_9_0.png)

Figure 7: Flexibility prediction results for NYSERDA S44 dataset using indoor temperature threshold of 0.5°C (left) compared with adjustment strategy RMSE/2 (center) and increased temperature threshold of 1.0°C (right)

### Table 3: Total flexible energy (kWh) and EPFR percentage of best performing models

|  | NIST |  | NYSERDA S40 |  | NYSERDA S44 |  |
|---|---|---|---|---|---|---|
|  | mode = Off | mode = ForcedOn | mode = Off | mode = ForcedOn | mode = Off | mode = ForcedOn |
| Flexible Energy ($E_{mode}$) | 1166 kWh | 430 kWh | 1087 kWh | 714 kWh | 1855 kWh | 785 kWh |
| EPFR | 98.70% | 87.20% | 97.30% | 86.20% | 87.40% | 95.40% |

be used in cases where previous adjustment for error strategies do not yield satisfactory results. Widening the comfort bounds has a two-fold effect: it potentially reduces the flexibility prediction error and increases the total amount of potential heat pump flexibility. As seen in Figure 7, the widening of the user comfort bounds by 0.5°C decreased MAFE by 85% on average. The widening of bounds also yielded an over 41% increase in potential flexibility for modes Off and ForcedOn.

Evaluation of the amounts of predicted flexible energy. After all experiments were completed, flexibility prediction results were aggregated and the total amount of flexible energy was calculated. To calculate flexible energy for mode ∈ {ForcedOn, Off}, the average power consumptions of the heat pump were calculated in both normal operation P̅_normal and in the given mode P̅_mode and then the absolute difference was multiplied by the predicted flexibility amount F̂_mode divided by 4 to normalize to hours (one time step every 15 minutes).

```
E_mode = (P̅_mode - P̅_normal) * F̂_mode / 4  (15)
```

The comfort bound of 0.5°C was used across all datasets for flexibility prediction. As seen in Table 3 all of the heat pump deployments provide over 1.5MWh of combined flexible energy, with the NYSERDA S44 providing 2.64MWh. The results indicate that the majority (over 68%) of total potential flexible energy can be utilized with scenario Off. On average, the flexibility prediction models managed to predict over 90% of available flexibility (EPFR) from all three datasets between both modes. Notably, all of the monitored heat pumps used in this study were not configured to maximize flexible energy and were operating to maintain a set temperature.

## 9 CONCLUSIONS AND FUTURE WORK

This paper proposes HeatFlex, a novel data-driven method for predicting flexibility from smart heat pumps. HeatFlex, utilizing modern machine learning models, LSTM and GRU recurrent neural networks, can accurately predict flexibility from heat pump devices without requiring knowledge about deployed heat pump parameters, building layout or environment details or manual development of physical models. Furthermore, HeatFlex only uses three, widely available monitored variables, making it applicable in a majority of use cases. The paper also proposes new metrics for heat pump flexibility, enabling quantitative evaluation of flexibility prediction performance. Conducted experiments on 3 open access datasets show that machine learning based indoor temperature forecasting models can be trained in a scalable, data-driven way and be effective at predicting energy flexibility from individual smart heat pump devices. Quantitative and qualitative performance evaluation shows that HeatFlex, utilizing recurrent neural networks, has over 32% lower indoor temperature forecasting error than the model baselines linear regression and SARIMAX, while also having more consistent performance throughout different seasons. Experimental results show that HeatFlex can be effective in different deployments, with different building sizes and heat pump types, predicting over 90% of potential heat pump flexibility.

In future work, we will develop data-driven predictive models that could predict flexibility from other types of devices (e.g. air conditioners, electric vehicle chargers). We will perform experiments using additional data from real smart heat pump deployments as well as simulations to verify HeatFlex robustness in various flexible operation conditions. Additionally, we will explore developing predictive models that optimize directly on flexibility prediction error, thus maximizing utility. Finally, we will develop novel probabilistic models which will enable evaluating potential prediction accuracy during inference.

## ACKNOWLEDGMENTS

This work was supported by the FEVER (Flexible Energy Production, Demand and Storage-based Virtual Power Plants for Electricity Markets and Resilient DSO Operation) project under the Horizon 2020 programme.

## REFERENCES

[1] Alessandro Aliberti, Francesca Maria Ugliotti, Lorenzo Bottaccioli, Giansalvo Cirrincione, Anna Osello, Enrico Macii, Edoardo Patti, and Andrea Acquaviva. 2018. Indoor Air-Temperature Forecast for Energy-Efficient Management in Smart Buildings. Proceedings - 2018 IEEE International Conference on Environment and Electrical Engineering and 2018 IEEE Industrial and Commercial Power Systems Europe, EEIC/I and CPS Europe 2018 (2018). https://doi.org/10.1109/EEIC.2018.8494382

[2] Abdulaziz Almalaq and George Edwards. 2017. A review of deep learning methods applied on load forecasting. Proceedings - 16th IEEE International Conference on Machine Learning and Applications, ICMLA 2017 2017-December (2017), 511-516. https://doi.org/10.1109/ICMLA.2017.0-110

[3] Yoshua Bengio, Patrice Simard, and Paolo Frasconi. 1994. Learning Long-Term Dependencies with Gradient Descent is Difficult. IEEE Transactions on Neural Networks 5, 2 (1994), 157-166. https://doi.org/10.1109/72.279181

[4] Matthias Boehm, Lars Dannecker, Andreas Doms, Erik Dovgan, Bogdan Filipič, Ulrike Fischer, Wolfgang Lehner, Torben Bach Pedersen, Yoann Pitarch, Laurynas Sikšnys, and Tea Tüsar. 2012. Data management in the MIRABEL smart grid system. ACM International Conference Proceeding Series (2012), 95-102. https://doi.org/10.1145/2320765.2320797

[5] George Edward Pelham Box and Gwilym Jenkins. 1990. Time Series Analysis, Forecasting and Control. Holden-Day, Inc., USA.

[6] P. Carroll, M. Chesser, and P. Lyons. 2020. Air Source Heat Pumps field studies: A systematic literature review. Renewable and Sustainable Energy Reviews 134, August (2020). https://doi.org/10.1016/j.rser.2020.110275

[7] T. Chai and R. R. Draxler. 2014. Root mean square error (RMSE) or mean absolute error (MAE)? -Arguments against avoiding RMSE in the literature. Geoscience Model Development 7, 3 (2014), 1247-1250. https://doi.org/10.5194/gmd-7-1247-2014

[8] Kyunghyun Cho, Bart van Merriënboer, Dzmitry Bahdanau, and Yoshua Bengio. 2015. On the Properties of Neural Machine Translation: Encoder-Decoder Approaches. (2015), 103-111. https://doi.org/10.3115/v1/w14-4012 arXiv:1409.1259

[9] Junyoung Chung, Caglar Gulcehre, KyungHyun Cho, and Yoshua Bengio. 2014. Empirical Evaluation of Gated Recurrent Neural Networks on Sequence Modeling. (dec 2014). arXiv:1412.3555 http://arxiv.org/abs/1412.3555

[10] Tingting Fang and Risto Lahdelma. 2016. Evaluation of a multiple linear regression model and SARIMA model in forecasting heat demand for district heating system. Applied Energy 179 (2016), 544-552. https://doi.org/10.1016/j.apenergy.2016.06.133

[11] David Fischer, Marc Andre Triebel, and Oliver Selinger-Lutz. 2018. A Concept for Controlling Heat Pump Pools Using the Smart Grid Ready Interface. Proceedings - 2018 IEEE PES Innovative Smart Grid Technologies Conference Europe, ISGT-Europe 2018 (2018). https://doi.org/10.1109/ISGTEurope.2018.8571870

[12] Benedikt Heidrich, Marian Turoowski, Nicole Ludwig, Ralf Mikul, and Veit Hagenmeyer. 2020. Forecasting energy time series with profile neural networks. In e-Energy 2020 - Proceedings of the 11th ACM International Conference on Future Energy Systems. Association for Computing Machinery, Inc, New York, NY, USA, 220-230. https://doi.org/10.1145/3396851.3397683

[13] Sepp Hochreiter and Jürgen Schmidhuber. 1997. Long Short-Term Memory. Neural Computation 9, 8 (1997), 1735-1780. https://doi.org/10.1162/neco.1997.9.8.1735

[14] Chiou Jye Huang and Ping Huan Kuo. 2019. Multiple-Input Deep Convolutional Neural Network Model for Short-Term Photovoltaic Power Forecasting. IEEE Access 7 (2019), 74822-74834. https://doi.org/10.1109/ACCESS.2019.2921238

[15] Konstantinos Kouzelis, Zheng H. Tan, Birgitte Bak-Jensen, Jayakrishnan Radhakrishna Pillai, and Ewen Ritchie. 2015. Estimation of Residential Heat Pump Consumption for Flexibility Market Applications. IEEE Transactions on Smart Grid 6, 4 (2015), 1852-1864. https://doi.org/10.1109/TSG.2015.2414490

[16] Guokun Lai, Wei Cheng Chang, Yiming Yang, and Hanxiao Liu. 2018. Modeling long- and short-term temporal patterns with deep neural networks. 41st International ACM SIGIR Conference on Research and Development in Information Retrieval, SIGIR 2018 July (2018), 95-104. https://doi.org/10.1145/3209978.3210006 arXiv:1703.07015v3

[17] Ming Li, Yijun Li, and Xinli Min. 2020. Practice and Application of LSTM in Temperature Prediction of HVAC System. Proceedings of 2020 IEEE 5th Information Technology and Mechatronics Engineering Conference, ITOEC 2020 Itoec (2020), 1000-1004. https://doi.org/10.1109/ITOEC49072.2020.9149190

[18] Junyu Liu, Xiao Wang, Yan Zhao, Bin Dong, Kuan Lu, and Ranran Wang. 2020. Heating Load Forecasting for Combined Heat and Power Plants Via Strand-Based LSTM. IEEE Access 8 (2020), 33360-33369. https://doi.org/10.1109/ACCESS.2020.2972303

[19] Fernando Mateo, Juan José Carrasco, Abderrahim Sellami, Mónica Millán-Giraldo, Manuel Domínguez, and Emilio Soria-Olivas. 2013. Machine learning methods to forecast temperature in buildings. Expert Systems with Applications 40, 4 (2013), 1061-1068. https://doi.org/10.1016/j.eswa.2012.08.030

[20] Bijay Neupane, Torben Bach Pedersen, and Bo Thieson. 2018. Utilizing device-level demand forecasting for flexibility markets. e-Energy 2018 - Proceedings of the 9th ACM International Conference on Future Energy Systems (2018), 108-118. https://doi.org/10.1145/3208903.3208922

[21] Bijay Neupane, Laurynas Sikšnys, and Torben Bach Pedersen. 2017. Generation and evaluation of flex-offers from flexible electrical devices. In e-Energy 2017 - Proceedings of the 8th International Conference on Future Energy Systems. Association for Computing Machinery, Inc, 143-156. https://doi.org/10.1145/3077839.3077850

[22] Thomas Nowak and Pascal Westring. 2017. Growing for good ? The European Heat Pump Market - Status and outlook. 12th IEA Heat Pump Conference 2017 (2017), 1-10.

[23] Dimitrios Papadaskalopoulos, Goran Strbac, Pierluigi Mancarella, Marko Aunedi, and Vladimir Stanojevic. 2013. Decentralized participation of flexible demand in electricity markets - Part II: Application with electric vehicles and heat pump systems. IEEE Transactions on Power Systems 28, 4 (2013), 3667-3674. https://doi.org/10.1109/TPWRS.2013.2245687

[24] Debayan Paul, Tanmay Chakraborty, Soumya Kanti Datta, and Debolina Paul. 2018. IoT and Machine Learning Based Prediction of Smart Building Indoor Temperature. 2018 4th International Conference on Computer and Information Sciences: Revolutionising Digital Landscape for Sustainable Smart Society, ICCOINS 2018 - Proceedings (2018), 1-6. https://doi.org/10.1109/ICCOINS.2018.8510597

[25] Torben Bach Pedersen, Thibaut Le Gully, Per D. Pedersen, Luis J. Ferreira, Laurynas Sikšnys, Petr Sluka, Michele Albano, Arne Skou, and Petur Olsen. 2016. An Energy Flexibility Framework on the Internet of Things. 2 (2016), 17-37. https://doi.org/10.5220/0006163400170037

[26] Torben Bach Pedersen, Laurynas Sikšnys, and Bijay Neupane. 2018. Modeling and Managing Energy Flexibility Using FlexOffers. 2018 IEEE International Conference on Communications, Control, and Computing Technologies for Smart Grids, SmartGridComm 2018 (2018). https://doi.org/10.1109/SmartGridComm.2018.8587605

[27] Rob J Hyndman and Yeasmin Khandakar. 2008. Automatic Time Series Forecasting: The forecast Package for R. Journal of Statistical Software 27, 3 (2008), 22. http://www.jstatsoft.org/v27/i03/paper

[28] Olga Rybnytska, Laurynas Sikšnys, Torben Bach Pedersen, and Bijay Neupane. 2020. PGF MU: Integrating data management with physical system modelling. Advances in Database Technology - EDBT 2020-March (2020), 109-120.

[29] Laurynas Sikšnys, Emmanouil Valsomatiz, Katja Hose, and Torben Bach Pedersen. 2015. Aggregating and Disaggregating Flexibility Objects. IEEE Transactions on Knowledge and Data Engineering 27, 11 (2015), 2893-2906. https://doi.org/10.1109/TKDE.2015.2445755

[30] Jiancai Song, Guixiang Xue, Xuhua Pan, Yunpeng Ma, and Han Li. 2020. Hourly heat load prediction model based on temporal convolutional neural network. IEEE Access 8 (2020), 16726-16741. https://doi.org/10.1109/ACCESS.2020.2968536

[31] Hai Tao, Li Junjie, Shi Yu, Chen Yongjian, and Liu Zhenyu. 2020. Predictive analysis of outdoor temperature and humidity based on BP neural network single-step prediction method. Proceedings of 2020 IEEE 3rd International Conference on Information Systems and Computer Aided Education, ICISCAE 2020 (2020), 402-407. https://doi.org/10.1109/ICISCAE51034.2020.9236853

[32] Stylianos I. Vagropoulos, G. I. Chouliaras, E. G. Kardakos, C. K. Simoglou, and A. G. Bakirtzis. 2016. Comparison of SARIMAX, SARIMA, modified SARIMA and ANN-based models for short-term PV generation forecasting. 2016 IEEE International Energy Conference, ENERGYCON 2016 (2016), 0-5. https://doi.org/10.1109/ENERGYCON.2016.7514029

[33] Emmanouil Valsomatiz, Katja Hose, Torben Bach Pedersen, and Laurynas Sikšnys. 2015. Measuring and comparing energy flexibilities. CEUR Workshop Proceedings 1330, c (2015), 78-85.

[34] Emmanouil Valsomatiz, Torben Bach Pedersen, and Alberto Abelló. 2018. Day-ahead trading of aggregated energy flexibility. e-Energy 2018 - Proceedings of the 9th ACM International Conference on Future Energy Systems (2018), 134-138. https://doi.org/10.1145/3208903.3208936

[35] Inna Vorushylo, Patrick Keatley, Nikhilkumar Shah, Richard Green, and Neil Hewitt. 2018. How heat pumps and thermal energy storage can be used to manage wind power: A study of Ireland. Energy 157 (2018), 539-549. https://doi.org/10.1016/j.energy.2018.03.001

[36] Wei Wu, Harrison M. Skye, and Piotr A. Domanski. 2018. Selecting HVAC systems to achieve comfortable and cost-effective residential net-zero energy buildings. Applied Energy 212, October 2017 (2018), 577-591. https://doi.org/10.1016/j.apenergy.2017.12.046

[37] Keming Yan, Chris Diduch, and Mary E. Kaye. 2019. An improved temperature prediction technique for HVAC units using intelligent algorithms. 2019 IEEE Energy Conversion Congress and Exposition, ECCE 2019 (2019), 490-494. https://doi.org/10.1109/ECCE.2019.8912944
