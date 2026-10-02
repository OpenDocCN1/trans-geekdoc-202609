*Article*

# A Data-Driven Short-Term Forecasting Model for Offshore Wind Speed Prediction Based on Computational Intelligence

Ioannis P. Panapakidis 1,*, Constantine Michailides 2 and Demos C. Angelides 3

+   1. Department of Electrical Engineering, Technological Educational Institute of Thessaly, 41110 Larisa, Greece
2. Department of Civil Engineering and Geomatics, Cyprus University of Technology, 3036 Limassol, Cyprus; c.michailides@cut.ac.cy
3. Department of Civil Engineering, Aristotle University of Thessaloniki, 54124 Thessaloniki, Greece; dangelid@civil.auth.gr
* Correspondence: panap@teilar.gr; Tel.: +30-2410-684325

Received: 27 March 2019; Accepted: 6 April 2019; Published: 10 April 2019

**Abstract:** Wind speed forecasting is an important element for the further development of offshore wind turbines. Due to its importance, many researchers have proposed different models for wind speed forecasting that differ in terms of the time-horizon of the forecast, types and number of inputs, complexity, structure, and others. Wind speed series present high nonlinearity and volatilities, and thus an effective model should successfully deal with those features. An approach to deal with the nonlinearities and volatilities is to utilize a time series processing technique such as the wavelet transform. In the present paper, an ensemble data-driven short-term wind speed forecasting model is developed, tested and applied. The term “ensemble” refers to the combination of two different predictors that run in parallel and the prediction is obtained by the predictor that leads to the lowest error. The proposed model utilizes the wavelet transform and is compared with other models that have been presented in the related literature and outperforms their accuracy. The proposed forecasting model can be used effectively for 1 min and 10 min ahead horizon wind speed predictions.

**Keywords:** computational intelligence; offshore wind; forecasting; machine learning; neural networks; neuro-fuzzy systems

# 1. Introduction

# 1.1. Motivation and State-of-the-Art

The rapid implementation of wind turbines across the globe corresponds to a set of challenges during power systems operation and planning. This is due to intermittent nature of wind potential. By the end of 2018, the total European Union-installed offshore wind capacity reached 19 GW. Total investments in offshore wind in 2018 were more than 10.3 billion € (WindEurope [1], 2018). This includes investments in construction of projects, transmission assets, and refinancing. More than 91% of all offshore wind installations were located in shallow or intermediate water depths with a mean water depth equal to 27.1 m. The capacities span from few to hundred megawatts and the installations differ in terms of hub site, distance to shore, water depth and others (Snyder et al. [2], 2009). The reduction of installation and maintenance costs but also the reliable assessment of energy production of offshore wind parks will signify the next phase of their deployment.

Wind energy leads to disturbances of the balance between generation and demand sides. A wind speed prediction system is a potential solution to the aforementioned situation. Apart from the balance, accurate predictions can lead to lower costs during the installation in the offshore field of wind turbines and can strengthen their reliability during their operation (Soman et al. [3], 2010). A large