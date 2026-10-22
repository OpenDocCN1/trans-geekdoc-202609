
## 1.4.5. Recurrent Neural Networks (RNNs) and LSTM

### RNN

RNNs are designed to automatically learn and understand the mutual relationship between inputs, which are provided in sequential order. RNNs are often applied to NLP and speech recognition, since they have sequential structure fit to process long time series (Fig. 1.11). In a typical RNN, the output becomes a variable of state (h) used as input into the same network for the following time step in the sequence.

### Long Short-Term Memory (LSTM) Networks

Traditional RNNs face difficulties in training models with long sequences, especially vanishing or exploding gradient problem. This problem was addressed in many studies, and one of the most popular techniques nowadays is the long short-term memory (LSTM) network, which was introduced by Hochreiter and Schmidhuber (1997). This and later developments allowed for much wider adoption of deep learning in time series forecasting.

Learning of such long-term dependencies between inputs and outputs is vital in hydrological modeling, because the lag time between hydrological processes may vary from days to years. For instance, the long lag time can be seen in the cases of glaciers, snow, and groundwater processes (Kratzert et al., 2019). Due to developments of new DL algorithms in the last several years, there has been clear revival of interest in using ML in water-related problems. These have demonstrated high accuracy, for example, in flood forecasting (e.g., Kratzert et al., 2019; Kao et al., 2020; Arsenault et al., 2023) and drought forecasting (Brust et al., 2021; Dikshit & Pradhan, 2021).

Kratzert et al. (2019) investigated the use of LSTM in rainfall runoff hydrology using Catchment Attributes and Meteorology for Large-Sample Studies (CAMELS) data sets for numerous catchments. The authors also studied the extent to which a single LSTM model could be regionalized, that is, applied to other catchments. As a result, the LSTMs predicted discharge with good accuracy compared with the reference model. The final conclusion claims that by using LSTM, the problem that is generally related to ML models of being black box models could be overcome, and the explanation is in the following. In LSTM the cell state's behavior in response to the hydrological trends and patterns can be physically interpreted, for instance, by analyzing the melting state of the cell state in comparison with the change in temperature. Consequently, with low temperatures, there is a

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_47_0.png)

Figure 1.11 Recurrent neural network. Inputs from a time series (X) are fed into processing nodes, producing output (Y) at each time step. The state or memory variable h_t is equal to Y_t in the basic algorithm.

certain increase in the cell state, and when the temperature exceeds certain degrees, the cell state starts to decrease (this imitates the snow accumulation and melting processes).

Examples of recent applications of DL in hydrometeorological problems, which are characterized by very large data sets, can be mentioned also. Schultz et al. (2021) evaluated numerical weather prediction models, which are quite important for analyzing all types of water resources problems. In this work, it is highlighted that DL is not yet widely used within the numerical weather prediction (NWP) context, mainly due to the lack of both the interpretability of the neural networks and the physical constraints. They mention also that many of the early experiments using simple neural networks did not capture the complexity of weather processes. Although these limitations are important, there are three main reasons for considering DL for weather prediction problems. First, large amounts of data are currently available. Second, new architectures of the neural networks have been developed that can capture well the time dependencies (RNNs), as well as spatial distributions and imagery, such as the convolutional neural network (CNN). Third, the computational power capacity needed for training such networks (graphical and specialized processors available on the cloud) has become easily available. All this brings the latest advanced ML techniques at the disposal of modelers and forecasters in water resources, leading thus to optimal water management.

For further information on the use of AI and ML in Earth system sciences, the reader is directed, for example, to the recorded lectures at the Summer School “Artificial Intelligence for Earth System Science” (AI4ESS, 2020), where some of the methods and impressive applications are presented.

## 1.5. Future Directions and Challenges

Use of modeling and forecasting tools is indispensable for effective water management. Traditionally, such models belonged to the class of the process-based (physically based) models, typically based on numerical solutions of differential equations of water motion. During the last three decades advances in machine learning techniques, increased computing power and data availability have led to changes in this landscape. Hydroinformatics is seen as the major area where machine learning, such algorithms, have been tested and applied to a large variety of water-related

problems, and have proven to be tools effectively complementing, and sometimes replacing physically based models. An improved physical representation does not necessarily guarantee an increased accuracy and utility of traditional models, so alternative ways are sought. This chapter presented an overview of the main approach in ML, relevant for this volume, in most cases with references to the authors’ own experience, and to the sources for further reading.

There is currently a serious change in the attitude toward the data-driven models within the practicing modelers community, and the current discussions in the hydrological literature is an indicator of this (see, e.g., Nearing et al., 2021; Beven, 2020). ML not only provides techniques for modeling, but also enhances ability of citizens to get access and better understand the modeling results via the natural language processing (NLP) and intelligent chatbots.

We see the future advances of modeling technologies in more effective combination of various types of models and their hybridization (e.g., in the line of physics-aware AI, see Jiang et al., 2020) and coevolution (as outlined by Razavi et al., 2022). Out of the experience of the authors, we see the following as the main future directions:

- 1. **Integration of AI and ML into operational water management:** Integrating AI and ML models into real-time decision support systems for efficient and adaptive water management is one potential approach. This entails creating models that can adapt to changing environmental circumstances in real time and improve water allocation and distribution.
- 2. **Improved data availability and quality:** ML models require access to high-quality, diversified data. Future work should concentrate on improving data-gathering methods, strengthening data-sharing channels, and creating approaches for dealing with missing or incomplete data. This will aid in the development of more accurate and robust ML models.
- 3. **Uncertainty quantification and risk assessment:** Addressing uncertainty and measuring risks associated with machine learning predictions are major problems. Future research should concentrate on creating approaches for quantifying uncertainties in ML-based predictions, as well as incorporating risk assessment frameworks for improved decision making under uncertainty.
- 4. **Explainability and interpretability of ML models:** ML models, particularly deep learning models, are often considered black boxes due to their complex structures. Enhancing the interpretability and explainability of ML models in water resource applications is an important

Abrahart, R. J., See, L. M., & Solomatine, D. P. (Eds.) (2008). Practical hydroinformatics: Computational intelligence and technological developments in water applications (Vol. 68). Springer Science & Business Media.

AI4ESS (2020). Artificial Intelligence for Earth System Science Summer School 2020. https://www2.cisl.ucar.edu/events/summer-school/ai4ess/2020

Arsenault, R., Martel, J.-L., Brunet, F., Brissette, F., & Mai, J. (2023). Continuous streamflow prediction in ungauged basins: Long short-term memory neural networks clearly outperform traditional hydrological models. Hydrology and Earth System Sciences, 27(1), 139–157.

Artificial intelligence (2022, December 2). In Wikipedia. https://en.wikipedia.org/wiki/Artificial_intelligence

Beven, K. (2020). Deep learning, hydrological processes and the uniqueness of place. Hydrological Processes, 34, 3608–3613.

Bhattacharya, B., & Solomatine, D. P. (2005). Neural networks and M5 model trees in modeling water level-discharge relationship. Neurocomputing, 63, 381–396.

Bowden, G. J., Dandy, G. C., & Maier, H. R. (2005a). Input determination for neural network models in water resources applications. Part 1, Background and methodology. Journal of Hydrology, 301, 75–92.

Bowden, G. J., Dandy, G. C., & Maier, H. R. (2005b). Input determination for neural network models in water resources applications. Part 2, Case study: Forecasting salinity in a river. Journal of Hydrology, 301, 93–107.

Breiman, L. (1984). Classification and regression trees. Routledge. https://doi.org/10.1201/9781315139470

Breiman, L. (2001). Random forests. Machine Learning, 45, 5–32.

Brust, C., Kimball, J. S., Maneta, M. P., Jencso, K., & Reichle, R. H. (2021). Droughtcast: A machine learning forecast of the United States drought monitor. Frontiers in Big Data, 4. https://doi.org/10.3389/fdata.2021.773478

Corzo, G., & Solomatine, D. (2007a). Baseflow separation techniques for modular artificial neural network modelling in flow forecasting. Hydrological Science Journal, 52(3), 491–507.

Corzo, G., & Solomatine, D. (2007b). Knowledge-based modularization and global optimization of artificial neural network models in hydrological forecasting. Neural Networks, 20(4), 528–536.

Corzo, G. A., & Solomatine, D. P. (2006). Optimization of base flow separation algorithm for modular data-driven hydrologic models. Proceedings of the 7th International Conference on Hydroinformatics (HIC 2006). Nice, France.

Corzo, G. A., Diaz Mercado, V., & Laverde Barajas M. (2018). Spatiotemporal Hydrological Analysis. International Journal of Hydrology, 2(1), 25–26.

Corzo Perez, G. A. (2009). Hybrid models for hydrological forecasting: Integration of data-driven and conceptual modeling techniques. Taylor & Francis, CRC Press.

Diaz, V., Corzo Perez, G. A., van Lanen, H. A. J., Solomatine, D., & Varouchakis, E. A. (2020). An approach to characterize spatio-temporal drought dynamics. Advances in Water Resources.

Dikshit, A., & Pradhan, B. (2021). Explainable AI in drought forecasting. Machine Learning With Applications, 6, 100192.
