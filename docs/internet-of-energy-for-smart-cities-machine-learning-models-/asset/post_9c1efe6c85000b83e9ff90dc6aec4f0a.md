
either to calculate or estimate the solar radiation received by PV panel during the daylight or, for panels with sun tracking system, to compute the tilt angle of the panel in order to receive the highest level of radiation possible. Studies show that even for fixed PV panels, the selection of optimum tilt angle for different periods of the year can result in important increase in energy output [30].

There are different available sun position calculators available on Internet, the most used being SunCalc.org (www.suncalc.org), NOAA Solar Position Calculator (https://www.esrl.noaa.gov/gmd/grad/solcalc), SunCalc.net (www.suncalc.net), SunEarthTools (www.sunearthtools.com). Besides knowing the sun position, it is important also to know the sunrise and sunset. With this information we can select the intervals of time where data are relevant to solar power conversion or when energy used in a PV based system is taken from storage batteries of from the grid.

Figure 9.5 shows data displayed at the location of PV park (selected for the use case) situated in the proximity of the Faculty of Electrical Engineering. The application programming interface (API) of the site can be used to obtain data at any location in the world at any date and hour by accessing a link with the following structure:

https://suncalc.org/#/lat,lon,zoom/date/time/objectlevel/maptype

where lat = latitude, lon = longitude, zoom = map zoom, date = date, time = time, objectlevel = object height for shadow calculation, maptype = type of map (0 = OpenStreet Map, 1 = Esri-Satellite, 2 = Esri-Topo, 3 = Esri-Street).

![](img/617e854c2620a5a4bed0116cef33155a_260_0.png)

Figure 9.5 Sun position calculator (www.suncalc.org) providing data for PV park near the Faculty of Electrical Engineering Iasi

## 9.5.1.4 Cloud Services

Possessing accurate weather information at the right time has become a necessity for many businesses that get impacted more frequently by the recent climate changes and increase in the extreme meteorological phenomena [1]. Energy generation is one of the sectors that can be affected by weather events and renewable systems are among the most sensitive part of the energy segment.

The increasing amount of collected meteorological data and better accuracy of weather forecasts based on this data has increased users confidence in using this kind of data for analysis and making predictions important for different activities.

In the case of monitoring PV parks operation, meteorological data can be used to prevent damages of PV panels due to extreme phenomena, identification of long periods of non friendly conditions of operation, identification of disturbing transitory conditions, all that can result in a degrading capacity of PV panels operation.

Meteorological data are available now via different services, many of them accessible via Internet. From the existent sources, we have considered the ones that are freely available and those which provide an easy access to the data via a dedicated API.

Among the services we have analyzed we can mention AccuWeather, OpenWeatherMap (openweathermap.org), DarkSky (darksky.net), Troposphere (troposphere.io). The free versions of data access are limited to a certain number of data per day, the frequency of the data and the length of historical data that can be retrieved from their databases.

## 9.5.1.5 Alerting Systems

As presented in section 1, PV can be damaged by extreme weather events. Therefore, in their monitoring process it is useful to take into account this type of events that may take place in the area where these panels are located, to be predicted, to be detected and to take appropriate measures.

These kinds of events are requiring special attention not only because they can cause material damages to the PV panels, but in some cases they can result also in loss of human lives.

Alerting systems have been developed by many countries and they provide useful information to administration bodies at different territorial levels, to state or private companies and even to individual persons. In recent years, there have been put into action programs such as the Severe Weather Information Centre of World Meteorological Organization, World Meteorological Organization’s World Weather & Climate Extremes Archive from Arizona State University and others that integrate national or regional systems at a continental or even a global level. These systems allow the identification of extreme phenomena and their global alertness, because their effects can span (directly or indirectly) over large geographical areas, exceeding the borders of a single country.

European National Meteorological Services have grouped together in the EU-METNET network which aims to provide a functional structure that can organize in

![](img/617e854c2620a5a4bed0116cef33155a_262_0.png)

a)

![](img/617e854c2620a5a4bed0116cef33155a_262_1.png)

b)

Figure 9.6 Awareness types a) and levels b)

a co-operative approach EU Member states’ activities in the meteorological area. This framework includes data gathering and processing systems, forecasts, reports, together with activities oriented to research, system development and training programs. The meteorological information issued by EUMETNET is made available to the European user through the dedicated website Meteoalarm.eu.

We focused on the Meteoalarm system because of the location of our study case. Other alert systems provide similar product and services via their associated websites.

The Meteoalarm system can alert for possible occurrence of severe weather.

Figure 9.6 shows the available awareness types and levels with their associated icons and colors that can be displayed in maps associated to region of interest. The use of these symbols can quickly provide an overview of the existing weather situation in that region, highlighting on the map the points where extreme events occur or may occur.

From this set, we will look for the occurrence events that can impact PV panel operation such as severe thunderstorms, gale-force winds, heavy rain with risk of hail, heat waves, fog, snow or extreme cold conditions.

Figure 9.7 shows an alert for atmospheric instability that will result in heavy rain with hail and thunder storms in the region of Iasi County.

This information can be integrated with other information collected from weather stations which can include also storm detectors and meteorological services. The overall information can then be used for taking immediate decisions regarding preventive actions to avoid or reduce damages of the PV park or as a notification that at the end of the event, an inspection or an evaluation of the PV park status will be mandatory.

![](img/617e854c2620a5a4bed0116cef33155a_263_0.png)

Figure 9.7 Alert of heavy rain with hail for Iasi County

## 9.6 MACHINE LEARNING TECHNIQUES IN PV PANEL OPERATION MONITORING

The increase of data available from energy source generation systems allows us to use machine learning techniques in order to find hidden although natural patterns in data that can provide a better insight of systems and processes helping one in making better decisions and predictions.

The use of machine learning algorithms is based on availability of data from which, by using different computational methods we can learn relevant information about a process directly from data. There is no need to have a mathematical model or a set of equations from which to extract the information. The model is obtained by learning which subsequently is used for making predictions for newly incoming data.

Based on different learning styles, machine learning algorithms can be divided in four different categories:

Supervised learning: this method is based on a training process for obtaining the model. The training process uses data sets including both correct and wrong predictions. Corrections are applied to the model when those predictions are wrong. The training is an iteration process that ends when the model, using the training data, reaches an expected level of accuracy.

Unsupervised learning: in this method datasets are not labeled, therefore, the model is obtained by first identifying existing patterns or structures in the input data. This can be obtained by reducing redundancy, by organizing data by similarity and extracting non visible rules.

Semi-Supervised Learning: in this method models are obtained based on datasets that contain both labeled and non labeled data. Therefore, algorithms must correct the model based on good and wrong predictions but also must identify structures in the labeled and non labeled data.

Reinforcement Learning: in this type of learning the machine is trained to make specific decisions. The training is based on a trial and error process in which data is feed continuously to the model. The machine is learning from the past datasets (experience) and adds knowledge that is used in making the best predictions in order to take the next best decisions.

Another classification of machine learning techniques can be obtained based on the method used for solving the problem.

A summary of machine learning techniques applied in PV system application found in literature is given in Table 9.2.

Applying machine learning technologies can bring a lot of benefits if the techniques are well implemented. There are some steps that one can take in order to develop a correctly machine learning approach:

- 1. Gathering data. This is the step of acquiring data or identifying already
