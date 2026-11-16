
the most common phenomena of this kind we mention:

- hail storms;
- dust storms;
- ice storms;
- strong winds;
- tornados;
- storms with electrical discharges.

Heavy rain with hail can result in broken glass modules which evidently have important loss in power and yield. The problem is that modules that seem to look good, often have small damages most of the time invisible to the human eye, which cause them also significant loss in power.

PV panels and parks that face the power of tornados are usually severely damaged at panel, panel support, and even PV park infrastructure level. Because these are evidently highly impacting phenomena, inspection and evaluation of the damages are mandatory.

Lightning strikes, whether direct or indirect, can result in both down time and expenses in identifying and replacing damaged parts [7].

Direct strikes (rare) would destroy (melt) panels, inverters, etc.

If panels are not protected, lightning can produce damages whether it strikes directly the PV panels or nearby [7]. Such an event can produce damages both in the electrical circuit of PV system and in its structure. Any of this kind of damage will affect PV system operation generating losses due to down time needed to identify and fix the problem and replacement costs of damaged parts or entire PV panel.

## 9.4 PREVENTING MEASURES

In order to prevent or limit the effect of extreme events, it is important to obtain useful information about them (possibility of occurrence, moment of occurrence or impact, intensity, other characteristics) before their occurrence. This information may come from the park's own monitoring system or from other available sources of information.

Having such information available, various proactive measures can be taken to ensure the proper functioning of the system and the prevention of undesirable effects such as energy theft [23, 24].

## 9.5 REAL-TIME DATA ACQUISITION AND ANALYTICS

### 9.5.1 DATA SOURCES

Machine learning makes no exception when it comes to photovoltaic systems. In order to obtain the best possible models, a large volume of data is needed to be used for training the model and to validate it. With respect to PV systems, taking into account its high interaction with the environment, there are numerous sources that can be used. In our study we have identified different categories of data sources as we can see below:

- data received from sensors placed within the PV park. They can be mounted on the PV panels providing information on solar radiation, tilt angle, temperature, humidity, shocks, or they can be placed on other components of the photovoltaic park;
- data received from PV panels and their control devices such as inverters, storage battery packs, power distributors, power lines, grid connectors etc;
- data collected from small weather stations located in the PV park or in the region where the park is located;
- data published by meteorological services that can be accessed from internet using dedicated application programming interfaces (APIs);
- data from services computing or collecting astronomical data (in the case of PV parks we can be interested in data related to sun position, sunrise, sunset). More sophisticated studies can make use of data regarding cloud movement, storm or other extreme weather predictions;
- data from cloud services where historical data are stored, integrated, processed and where real-time data can be processed, displayed and stored for future use;
- data from geopositioning services that are useful for locating a specific PV park, PV panel or data sources (weather stations), for mapping them or for annotating data with geographic information;
- data from alert systems provide information not only about severe weather phenomena but also about events that can affect PV park operation or can put them in danger.

### 9.5.1.1 Local Data Acquisition Systems

Local data acquisition systems are relying on a set of sensors which are either embedded or mounted on the PV panel with the purpose of acquiring real-time local data to be used in controlling algorithms or monitoring system status. They are sometimes called weather stations because they measure temperature, pressure, dew point, wind direction and strength, level of illumination etc. They work in conjunction with gateways which allow them to connect to Internet and send acquired data to data centers or cloud services where data is analyzed, stored, processed and displayed in order to support decision elaboration.

Usually controlled by a microcontroller, these systems can be extended to also collect information related to panel orientation with respect to solar radiation (the case of PV panels which include tracking position systems), can perform detection of a storm in the near region of the station providing also an estimation of its distance, speed, direction of movement and its evolving strength.

### 9.5.1.2 Meteorological Mini Stations

With people's increasing awareness of the importance of preserving the environment and the effects that human activity has on it, through various programs or individual initiatives, mini-stations have been installed in different geographical locations. Many of them are connected in various networks that manage them and that offer, sometimes free of charge and using a standard interface, the data collected in real time or historical data sets of different parameters.

One of these networks is the Weather Underground global community network which brings together data about weather or about air quality in the region where they are located. The network is based on individual initiatives all over the world, therefore, there is no uniform geographical distribution of stations. Figure 9.4 shows two regions in Romania, close to two cities of comparable size and population but with different number of mini-stations in the vicinity.

![](img/617e854c2620a5a4bed0116cef33155a_258_0.png)

Figure 9.4 Number of weather stations in two different regions of Romania a) Iasi (5 stations) b) Cluj-Napoca (15 stations)

There is a standard set of parameters measured by mini-stations including temperature, humidity, Dew point, precipitation level and pressure. Other parameters (like solar radiation) are measured only by some stations and published by their webpage or through corresponding API.

If such stations are available in the vicinity of the PV park, they can be used as data sources to feed the training, validation and prediction process, part of the PV monitoring system to be discussed in the next section.

Table 9.1, extended from [17] with two new operating stations in the region of the use case, provides a summary of data available from these stations and their characteristics.

### 9.5.1.3 Astronomical Data

Because the amount of power generated by a solar panel depends directly on the incidence of solar radiation, it is important to know the sun position. This is useful

Table 9.1
Characteristics and Data Types Provided by Weather Stations Located in the Region of PV Platform Weather Stations

| Characteristics | IIAI19 | IIAI20 | IIAI22 | IIAI40 | IISVLADI2 |
|---|---|---|---|---|---|
| Measurement of Temperature, Humidity, Dew Point, Precipitation, Pressure | Yes | Yes | Yes | Yes | Yes |
| Measurement of Wind Direction, Speed and Gust | Yes | Yes | Yes | Yes | Yes |
| Measurement of Solar Radiation | No | No | No | Yes | Yes |
| Measurement period (min) | 5 | 15 | 15 | 5 | 5 |
| Distance from PV platform (km) | 1.64 | 2.82 | 0.53 | 1.31 | 4.55 |
| Weather History in Graphs and Tables | Yes | Yes | Yes | Yes | Yes |
| Webcam | No | No | No | No | No |
| Elevation (m) | 39 | 104 | 30 | 45 | 99 |
| Position | 47.149° N, 27.572° E | 47.175° N, 27.574° E | 47.156° N, 27.6° E | 47.144° N, 27.582° E | 47.124° N, 27.633° E |
| Hardware | La Crosse Technology | Davis Vantage View | RaspberryPi | Other | Other |
| Software | Cumulus | weatherlink.com | weatherlink.com | EasyWeather | EasyWeather |
