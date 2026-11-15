
## Optimizing block morphology for reducing traffic pollutant concentration in adjacent external spaces of street canyons: A machine learning approach

Yunni Wu $^{a,b,c}$, Hong Chen $^{a,b,c,*}$

$^a$ School of Architecture and Urban Planning, Huazhong University of Science and Technology, Wuhan, 430074, China  
$^b$ Hubei Engineering and Technology Research Center of Urbanization, Wuhan, 430074, China  
$^c$ The Key Laboratory of Urban Simulation for Ministry of Natural Resources, Wuhan, 430074, China

### ARTICLE INFO

Keywords:
- Block morphology
- CFD
- Machine learning
- Optimizations
- Traffic pollutant

## ABSTRACT

Residential blocks located in near-road environments are exposed to traffic-related air pollution that adversely affects the health of residents. Pedestrian height areas in adjacent external spaces (AES) of street canyons are most severely affected by traffic pollutants. In order to find block morphological optimization strategies that can mitigate the concentration of pollutants in the area, machine learning (ML) regression models were investigated to replace the time-intensive computational fluid dynamics (CFD) model. Data from 1000 CFD simulation cases were used to train the ML models. The best surrogate model was selected and coupled with optimization algorithms. Both single-objective and multi-objective optimization problems based on regional concentration parameters were discussed. The results showed that the block's standard deviation of building height (BHsd) was an essential morphological parameter that can effectively impact the pollutant concentration. The effect mechanism of the building height at different locations in the block on the concentration of the pollutant in the different regions also varies. The optimum block configuration obtained from the optimizations coupled ML model can facilitate reducing pollutant concentrations. This study provides a framework for residential block design optimization that can help urban designers efficiently evaluate and select block layouts conducive to reducing the impact of traffic pollutants.

## 1. Introduction

One of the primary drivers of air pollution in cities, transportation emissions have increased as a result of urbanization. Particulate matter (PM), nitrogen oxides (NOx), and carbon monoxide (CO), all of which are caused by traffic, can be harmful to human health, the climate, and the environment [1]. Numerous epidemiological studies have shown that the incidence of morbidity and mortality due to lung function impairment, asthma, respiratory cancer, cardiovascular and cerebrovascular system diseases, breast cancer, and thyroid function deterioration is closely related to traffic-related air pollution [2–4]. According to estimates, there were 8379 and 1908 cases of early fatalities in Beijing, China, due to traffic pollution in 2014 and 2020, respectively [5]. Therefore, it is essential to discover practical measures to lessen traffic pollution and enhance urban livability.

Urban residents who live near street canyons are at risk of severe health problems due to traffic-related air pollution [6,7]. Street canyons are urban features where buildings resemble canyons, impacting how pollution from moving automobiles is dispersed. The extent of the effects of air pollutants caused by traffic on residential areas relies on a number of variables, including the wind direction, the kind of road, the shape of the block, the amount of traffic, etc. In general, secondary roads have a lesser impact range, which may be within 50 m, but motorways and main roads have a wider impact range, which may reach 300 m or farther [8]. Studies have shown that the farthest diffusion distance of CO from the road source is between 100 m and 200 m [9], which coincides with the range of residential areas near the road. A more effective way to reduce the impact of air pollutants in street canyons is to guide them into the urban canopy rather than diluting them with strong winds. This prevents pollutants from spreading to nearby blocks and enlarging the exposure area [10–12]. It also lowers the concentration in areas where pedestrians walk.

Previous studies have concentrated on the dispersion of traffic pollutants in street canyons and their effects on pedestrians [13–18]. However, these studies have overlooked how these pollutants spread to the surrounding blocks and how to reduce their impacts on the residents in the adjacent external spaces (AES) of the street. AES refers to the

| Term | Definition |
|---|---|
| AES | the adjacent external spaces of the street |
| ML | Machine Learning |
| CFD | Computational Fluid Dynamics |
| GA | Genetic Algorithm |
| NSGAII | non-dominated sorting genetic algorithm II |
| CO | carbon monoxide |
| BHstd | the standard deviation of building height |
| FAR | Floor area ratio |
| Rbc | Building coverage ratio |
| LHS | Latin hypercube sampling |
| RF | Random Forest |
| GB | Gradient Boost |
| XGB | eXtreme Gradient Boosting |
| LGBM | Light Gradient Boosting Machine |
| Cpod | the normalized concentration in the podium volume |
| Cped | the normalized concentration in the pedestrian volume |
| AQI | Air quality index |

external area of the block adjacent to the street canyon, generally the sub-street area between the adjacent row and the second row of buildings within the block. These spaces have their own microclimate, which is sometimes remarkably different from the surrounding climate [19]. AES can make a place more inhabitable by allowing more activities to take place outdoors over longer periods (Fig. 1). The milder microclimate of the AES in the block enables increased use of the outside space while spending more time outdoors supports a sense of ownership and control over space, as well as increasing the likelihood of encounters with other people, which promotes community. Additionally, the spatial clarity of the contained space makes for a clearer sense of identity and ownership, which can also result in it being used more. Since these areas are often used for outdoor activities, it is essential to monitor the concentration of traffic pollutants there [20].

Urban morphology, which refers to the shape and arrangement of buildings and streets, is one factor that influences the dispersion and concentration of traffic pollutants. Urban morphology can affect the airflow patterns, turbulence intensity, and ventilation performance in urban blocks and street canyons. The previous papers summarize the influence of many block morphological parameters on the diffusion of traffic pollutants, such as floor area ratio (FAR) [21–23], building coverage ratio (Rbc) [24,25], building height [26,27], etc. Compared with the ideal block models commonly used in wind environments and pollutant dispersion simulation research, the actual blocks have more diverse and complex layouts [28]. For example, the standard deviation of building height (BHstd), a morphological indicator that characterizes the difference in building height in actual blocks, is often ignored in idealized block studies. It has been proven to significantly impact traffic pollution dispersion in many field studies [25,29]. Building height deviation affects the mean flows in horizontal and vertical directions, thus changing the pathways and rates of pollutant transport [30]. However, there is little research on how this parameter interacts with block building layout to affect pollutant diffusion.

Previous studies have simulated various combinations of morphological parameters to examine their effects on the wind environment and neighborhood pollutant concentration [31,32]. The results have analyzed how pollutant concentration distribution varied with block layouts and explained how block morphology impacted pollutant dispersion [15,24]. However, it is difficult to comprehensively cover the diverse neighborhood forms by cross-combining multiple morphological parameters [33]. The same morphological index can correspond to a variety of block configurations. Therefore, it is worth optimizing and discussing what kind of layout is more conducive to reducing the concentration of traffic pollutants in the block.

Optimization algorithms are methods that aim to find the best solution for a problem by minimizing or maximizing a function that measures the quality of the solution. Complex urban block models can be iterated with optimization algorithms multiple times to produce better design results that meet expectations [34–37]. Optimization algorithms usually have three elements: decision variables, constraints, and objective function. The choice of optimization objective needs to be considered carefully. It can be single-objective or multi-objective and can focus on the global or local level. These choices can lead to different optimization results [38–40].

In traditional urban block environment optimization problems, researchers are limited by the time-consuming nature of simulation data acquisition [41]. As a result, the number of optimization iterations is still limited, and the solution space is difficult to search globally [42,43]. To overcome this challenge, surrogate models replace computational fluid dynamics (CFD) simulation data that are time-consuming or difficult to obtain. A surrogate model is an approximate mathematical model of an outcome of interest that cannot be easily measured or computed. Surrogate models can help reduce the computational cost and complexity of optimization problems involving expensive or complex simulations [44]. Surrogate models applied to CFD include the response surface method [45], the kriging method [34], polynomial regression [40], and machine learning [46–49]. Machine learning (ML) is a branch of artificial intelligence that enables computers to learn from data and improve their performance without explicit programming. ML can enhance CFD by accelerating the computation, improving the accuracy, reducing the complexity, and enabling new applications [50]. Optimization algorithms based on ML models can greatly improve computational efficiency, and the solution set space can be explored in more detail.

This study aims to fill the literature gap regarding the impact of traffic pollutants on residents in the AES. AES is often overlooked despite being more exposed to pollutants than other areas. This study also examines how block morphology, especially BHstd, and block layouts affect pollutant dispersion in different areas. BHstd is an important morphological parameter frequently ignored in previous simulation studies. To achieve this goal, this study uses ML to create a regression model of block pollutant concentration as a surrogate model for CFD. Then, it combines the ML model with an optimization algorithm to explore the optimal block design strategy that can reduce pollutant concentration in the AES. The paper is structured as follows: Chapter 2 outlines the research framework of this study; Chapter 3 describes the case conditions, CFD, ML, and optimization settings used in this study; Chapters 4 and 5 present and discuss the main findings of this study; Chapter 6 concludes the paper with some implications.

![](img/3dfc16e89d69a1b97a2f485b1851c7d6_1_0.png)

Fig. 1. Residents engage in outdoor activities in block [19].
