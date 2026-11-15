# Optimizing block morphology for reducing traffic pollutant concentration in adjacent external spaces of street canyons: A machine learning approach

Yunni Wu $^{a,b,c}$, Hong Chen $^{a,b,c,*}$

$^a$ School of Architecture and Urban Planning, Huazhong University of Science and Technology, Wuhan, 430074, China
$^b$ Hubei Engineering and Technology Research Center of Urbanization, Wuhan, 430074, China
$^c$ The Key Laboratory of Urban Simulation for Ministry of Natural Resources, Wuhan, 430074, China

+   **ARTICLE INFO**
+   
+   Keywords:
+   * Block morphology
+   * CFD
+   * Machine learning
+   * Optimizations
+   * Traffic pollutant

# ABSTRACT

Residential blocks located in near-road environments are exposed to traffic-related air pollution that adversely affects the health of residents. Pedestrian height areas in adjacent external spaces (AES) of street canyons are most severely affected by traffic pollutants. In order to find block morphological optimization strategies that can mitigate the concentration of pollutants in the area, machine learning (ML) regression models were investigated to replace the time-intensive computer fluid dynamic (CFD) model. Data from 1000 CFD simulation cases were used to train the ML models. The best surrogate model was selected and coupled with optimization algorithms. Both single-objective and multi-objective optimization problems based on regional concentration parameters were discussed. The results showed that the block's standard deviation of building height (BHsd) was an essential morphological parameter that can effectively impact the pollutant concentration. The effect mechanism of the building height at different locations in the block on the concentration of the pollutant in the different regions also varies. The optimum block configuration obtained from the optimizations coupled ML model can facilitate reducing pollutant concentrations. This study provides a framework for residential block design optimization that can help urban designers efficiently evaluate and select block layouts conducive to reducing the impact of traffic pollutants.

# 1. Introduction

One of the primary drivers of air pollution in cities, transportation emissions have increased as a result of urbanization. Particulate matter (PM), nitrogen oxides (NOx), and carbon monoxide (CO), all of which are caused by traffic, can be harmful to human health, the climate, and the environment [1]. Numerous epidemiological studies have shown that the incidence of morbidity and mortality due to lung function impairment, asthma, respiratory cancer, cardiovascular and cerebrovascular system diseases, breast cancer, and thyroid function deterioration is closely related to traffic-related air pollution [2–4]. According to estimates, there were 8379 and 1908 cases of early fatalities in Beijing, China, due to traffic pollution in 2014 and 2020, respectively [5]. Therefore, it is essential to discover practical measures to lessen traffic pollution and enhance urban livability.

Urban residents who live near street canyons are at risk of severe health problems due to traffic-related air pollution [6,7]. Street canyons are urban features where buildings resemble canyons, impacting how

pollution from moving automobiles is dispersed. The extent of the effects of air pollutants caused by traffic on residential areas relies on a number of variables, including the wind direction, the kind of road, the shape of the block, the amount of traffic, etc. In general, secondary roads have a lesser impact range, which may be within 50 m, but motorways and main roads have a wider impact range, which may reach 300 m or farther [8]. Studies have shown that the farthest diffusion distance of CO from the road source is between 100 m and 200 m [9], which coincides with the range of residential areas near the road. A more effective way to reduce the impact of air pollutants in street canyons is to guide them into the urban canopy rather than diluting them with strong winds. This prevents pollutants from spreading to nearby blocks and enlarging the exposure area [10–12]. It also lowers the concentration in areas where pedestrians walk.

Previous studies have concentrated on the dispersion of traffic pollutants in street canyons and their effects on pedestrians [13–18]. However, these studies have overlooked how these pollutants spread to the surrounding blocks and how to reduce their impacts on the residents in the adjacent external spaces (AES) of the street. AES refers to the