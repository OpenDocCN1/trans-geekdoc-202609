
![](img/dd2f1e467aed0a84f984e6e656b2cc0f_428_0.png)

Figure 15.1 Map of the Yuna River basin.

variation) ranges between 1,080 and 3,120 mm, with the area of greatest precipitation in the mountain region upstream of the reservoir. Most of the annual rainfall in the Dominican Republic occurs between the end of April and the end of October, with a bimodal trend that has peaks in May and around the end of August to October (CEPAL, 2020; Jury et al., 2007). Due to its geographical location, the country is exposed to extreme weather events such as hurricanes, cyclones, and tropical storms. The hurricane season begins in June and ends in November, with the months of August to the end of October the periods of greatest occurrence (Jesús Encarnación, 2019).

During periods of prolonged rain, floods occur frequently in the lower Yuna basin. The rains generate an increase in river flow that consequently overflows and affects low-lying populations downstream of the reservoir. The lower Yuna plain is subject to flooding in general, characterized by a terrain of low slopes, extensive plains, and a meandering river course.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_429_0.png)

Figure 15.2 Floodplain in the lower Yuna basin.

Several flood events have been reported, such as flooding in October of 2007 that occurred because of Tropical Storm Noel. The event affected the entire Dominican territory and resulted in losses exceeding 439 million U.S. dollars (CEPAL, 2008). Another more recent event was the flood season between November 2016 and April 2017, which generated losses of 862.37 million US dollars, affecting sectors of public works, water and sewerage, agriculture, and housing among others (MEPyD, 2017). On the other extreme, periods of long droughts also affect the area, reducing hydroelectric generation and putting at risk the water meant to supply the irrigation districts in the lower Yuna.

At present, only 26% of the basin area is regulated by reservoirs. Hatillo is the most representative, regulating 23% of the total area of the basin (1,192 km²). This reservoir is the largest body of surface water in the Dominican Republic, covering an average area of 27.4 km². The system has a dam built on a 50 m high embankment of earth and rock.

The reservoir has a total storage capacity of 441 million m³ with a maximum length of 15 km. The minimum operating level is 70 m above sea mean level (MAMSL). The elevation of the crest of the spillway is 86.5 MAMSL, which corresponds to the maximum operating level, while the extraordinary maximum level is 100.75 MAMSL. The main components of the dam are presented in Figure 15.3. The reservoir has an uncontrolled spillway (i.e., no gates, only free overflow) with a maximum capacity of 650 m³/s; there are two hollow jet valves for the bottom outlet, with a maximum capacity of 82 m³/s each. A powerhouse with a Francis turbine has an installed capacity of 8 MW and an annual energy generation of 40 GWh; the maximum flow capacity of the turbine is 30 m³/s. Hatillo’s installed capacity is low compared with other hydroelectric plants in the Dominican Republic. Examples of other plants include Tavera (96 MW), Valdesía (54 MW), and Aguacate (52 MW). Downstream of Hatillo, large areas of land are used for agriculture in the lower Yuna River basin, predominantly for rice cultivation, which is the main food crop in the Dominican Republic (Moquete, 2004). The reservoir supplies water for the irrigation of approximately 27,000 ha of crops.

The dam is operated by Empresa de Generación Hidroeléctrica Dominicana (EGEHID) and the Dominican Institute of Water Resources (INDRHI). The reservoir operation under normal conditions consists of discharging 26 m³/s through the turbine throughout the day; this water returns to the Yuna River and it is used for irrigation. However, in emergency scenarios, such as in heavy rainy seasons or hurricane seasons, the National Dam Committee (COPRE) defines the actions for the operation of the reservoir. Releases through hollow jet valves occur when more water needs to be released due to flood control strategies or irrigation demands. Unfortunately, the information about operating rules of the reservoir were not available, as well as target levels, power production targets, and irrigation discharges. Nevertheless, daily data of inflows, spills, turbine discharges, valve outlets, and total outflows for the period 2009–2019 were provided by EGEHID. From these data, it was observed that 54% of the reservoir outlets are through spill, 45% are through the turbine, and 1% are through the bottom valves. The fact that most of the reservoir releases have not been controlled (i.e., through spillway) allows us to hypothesize that the flood control objective can be improved.

It is important to mention that given the lack of reservoir operation rules, this study sought to emulate the real operation (2009–2019) using machine learning (ML) models, which is described in section 15.3. Additionally, due to the lack of target levels, power production targets, irrigation demands, and specific objectives of the reservoir, an operating model has been proposed (see section 15.2.3) to be optimized by applying three objectives with which it seeks to emulate the interests in the operation of the reservoir.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_431_0.png)

Figure 15.3 Dam components: (a) location of the dam, (b) operation levels, (c) schematic representation of the components of the dam.

## 15.2.2. Data

The period of analysis for the case study was defined from the information available on the reservoir’s operation; it corresponds to the period of 2009 to 2019, with daily time steps. These data consist of series of inflows, levels, and outflows of the reservoir (Fig. 15.4), in addition to storage elevation curve, area elevation curve, and evaporation losses. In machine learning models (which are developed in section 15.3), the normalization or standardization of data is often advisable. In this study, the data are standardized using the standard scoring method: $X_n = (X - \mu)/\sigma$, with $X$ being the value of the variable without standardization, $\sigma$ the standard deviation, and $\mu$ the average of the time series.

## 15.2.3. Reservoir Operation Model

A reservoir operation model was built from the data from the period of analysis. This model integrates water balances, physical characteristics of the dam components and a water release decision component that is integrated by machine learning models (which will be further discussed). The water balances determine the storage volume of the reservoir at each time step $t$, the level and the surface area are calculated by applying the storage-elevation curve and the area-elevation curve, respectively. The water balance equation is as follows:

$S_{t+1} = S_t + I_{N_t} - Q_{spill,t} - Q_{c,t} - EVP_t$  (15.1)

where $S_{t+1}$ (subject to $S_{t+1} \geq 0$) and $S_t$ correspond, respectively, to the storage volume of the reservoir for the next time step $(t+1)$ and the current time step $t$; $I_{N_t}$ corresponds to the inflows of the reservoir for the current time step $t$, taking the inflow time series; $EVP_t$ corresponds to the evaporation losses for the current time step $t$, which are calculated based on the surface area of the reservoir and the month of the year; $Q_{spill,t}$ corresponds to the spilled volume of the reservoir for the current time step $t$, which is calculated as a function of the height above the crest of the spillway; and $Q_{c,t}$ corresponds to the controlled outflows of the reservoir for the current time step $t$. At every time step (i.e., day), the model computes the water balance.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_433_0.png)

Figure 15.4 Real Data of the analysis period: (a) Inflows and outflows of the reservoir, (b) levels of the reservoir.

during dry periods, the turbine discharges a minimum flow during the day. Unfortunately, there is no information available on critical flow thresholds below which significant environmental impacts occur. Berge et al. (2003) proposed downstream of the dam a minimum flow of 3 m³/s to have the necessary recipient capacity for pollutants and to support aquatic life. However, in this study, the minimum flow is assumed based on the historical data of outflows from the reservoir taking the flow that is statistically exceeded 95% of the time (7.5 m³/s).

On the other hand, a maximum storage level value (87.5 m.a.s.l) is proposed from which the maximum flow capacity of the turbine can be released. So then:

$$Q_{c,t} = \begin{cases} Q_{cmin} & \text{if } S_t \le S_{min} \\ Q_{tbmax} & \text{if } S_t \ge S_{max} \\ Q_{ml,t} & \text{if } S_{min} < S_t < S_{max} \end{cases}\tag{15.2}$$

where $Q_{c,t}$ are the controlled discharges of the reservoir at $t$; $S_t$ is the storage in the reservoir at time $t$; $S_{min}$ is the proposed minimum threshold storage; $S_{max}$ is the proposed maximum threshold storage; $Q_{cmin}$ is the minimum discharge (7.5 m³/s); $Q_{tbmax}$ is the maximum discharge through the turbine (30 m³/s). When the level is within the defined storage threshold ($S_{min} < S_t < S_{max}$), the discharge is defined by the ML models $Q_{ml,t}$, which is described in section 15.3.

Once the controlled discharges have been defined, reservoir level is verified with respect to spillway crest level. If this is exceeded, the spillway release is calculated as a function of the height above the crest of the spillway. The specific rating curve of the spillway for Hatillo reservoir is available at Viparelli (1983). After all outflows (i.e., controlled and uncontrolled) are defined (including the evaporation losses $EVP_t$), reservoir storage volume for the next time step $S_{t+1}$ is obtained by means of water balance (equation (15.1)), starting the process again and so the cycle continues until the analysis period is completed. The route shaded in the flow diagram (Fig. 15.5) corresponds to the main operating route in this proposed model (i.e., when the storage levels are within the defined threshold), where the segmented rectangle highlights the component of ML models, which will be described in section 15.3.

## 15.3. Methodology

Initially, section 15.3.1 provides a brief overview of the ML models used. The proposed methodology is divided into two general parts. In
