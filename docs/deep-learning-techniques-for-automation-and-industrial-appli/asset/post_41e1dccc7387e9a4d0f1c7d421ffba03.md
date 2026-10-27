
Groundwater storage level fluctuations are time-dependent [8]. Hence, knowing the water availability, extraction, and recharge throughout the year can help understand this variation year over year.

### 9.1.1 Why Is It Difficult to Measure Subsurface Groundwater?

Surface water measurement methods are easy to execute as they are in the visible range, and equipment or sensors can be implemented comparatively easily. Maps can be drawn, and reports can be generated. Groundwater-related studies require subsurface measurements with the help of test well drilling, *in situ* borehole lithology, and other data logging, etc. There are alternate approaches such as geophysical observation of parameters like density, resistivity, conductivity, electromagnetic, or radioactivity using various methods. These methods are time-consuming, costly, and require a plethora of equipment and skills to carry out a single aquifer region study.

Some of these approaches use refraction- and reflection-based seismic surveys, gravity-based surveying, induced rock-based geomagnetic surveying, electromagnetic field surveying with or without the use of ground penetrating radar, vertical electrical sounding (VES)-based electrical surveying, and borehole petrophysics studies involving well data logging [12].

### 9.1.2 What are High Level Tasks Involved in Groundwater Measurement?

Investigation of groundwater hydrology is a time-consuming and cumbersome process. It involves the following steps [9]:

- Site selection and selection of geophysical methods
- Study of the hydrological site characteristics
- Conduct of tests like slugging and pumping
- Well-placement monitoring
- Drilling and subsurface sampling
- Water well design, installation, and development
- Well and borehole maintenance, rehabilitation, and abandonment
- Well tests and aquifer tests
- Groundwater sampling and analysis
- Characterization of groundwater bodies
- Groundwater assessment, data analysis, and reporting
- Design framework of groundwater monitoring networks
- Statistics for groundwater quality comparison

But in the last few years, researchers have started using a range of data modeling such as statistical models, artificial intelligence and its extended data science-based techniques such as machine/deep learning (ML/DL) models, or algorithm-based artificial neural networks (ANNs), along with remote satellite imaging and geographic information system (GIS) [10, 11, 13].

Groundwater potential (GWP) has been termed differently by various researchers. Some aimed at determining storage, i.e., the aggregated volume of aquifer water [14, 15], while others looked at it as the aquifer yield which is the water quantity that can be extracted without breaching the perpetual aquifer recharge [16]. For our research purpose, we are looking at GWP as the combination of the above two which is the storage that can be safely and sustainably withdrawn without breaching the balance of the periodic recharge level.

A total of 135 papers published during 2010–2022 on the topic of groundwater research were analyzed, and it was observed that 39% of papers were about GWP prediction, 25% were about modeling, and 17% were about groundwater assessment. Authors [17] looked at 1,509 research papers on the topic of GWP produced from year 2010 up to 2020. They referenced the information from research publication indexing databases Scopus and Web of Science (WoS). They found that this research topic has attracted researchers from 87 countries, and most of the publications were from India, Iran, and African countries. Upon post-data cleaning, they picked up 91 papers for the detailed review.

This paper is a compilation of the systematic review of the groundwater research described above using different types of machine learning (ML) such as hybrid, ensemble, artificial neural network, random forest, multi-linear regression, logistic regression, statistical models, and remote sensing. Our paper mainly captures the following: (i) input parameters widely used in groundwater potential (GWP) research; (ii) popular GWP model techniques; (iii) its applications; and (iv) future research directions.

## 9.2 Determination of Groundwater Potential (GWP) Parameters

### 9.2.1 Groundwater Potential (GWP) Parameters

Various research questions related to the determination of the GWP driving factors could be grouped in three categories as given below:

- 1. How can the presence of any hydrological components and surface or subsurface water storage capacity be determined?
- 2. What are the factors (input parameters, drivers, environmental variables) that affect groundwater level (GWL) potential distribution, fluctuations, mapping, and forecast in different regions over time? What is their relative importance?
- 3. What are examples of GWL-influencing factors?

The details of the research questions are presented in Table 9.1. Analysis of the literature led to the identification of six types of parameters which govern the groundwater potential (GWP) [18]. These are

- aquifer-related parameters and physical characteristics related to groundwater formation,
- geological parameters, which control GW,
- hydrological parameters associated with the water cycle,
- topographical parameters, those describing the terrain,
- land cover and land use parameters, and
- climatic parameters, related to long-term weather.

Figure 9.1 lists various parameters from the above categories. It also highlights which parameters are used frequently by researchers in determining GWP. Eleven parameters, namely geology (lithology), drainage, soil, slope (degree/percentage), rainfall/precipitation, land use, lineament density (LD), drainage density (DD), lineament, altitude/elevation, and curvature, were used by 40% or more researchers. Of these, geology, drainage, and soil were used by almost all the researchers, which shows their significance in this type of research.

### 9.2.2 Analysis of the Key GWP Parameters

This analysis helps in answering the important research question of which parameters are key contributors to GWP storage and recharge. Hence, a geographical terrain will have good groundwater potential with high aquifer water yield and good storage, if it meets the given criteria:

- It is thicker and less permeable. Aquifer resistivity is low and artesian pressure is high. Groundwater level is deep.
- It is in a non-coastal area, and pumping is within the limit, if it is in the coastal area, to avoid seawater intrusion.
- It should be non-agricultural to avoid nitrate pollution.

**Table 9.1** Research questions associated with GWP parameters.

| Type | Objective | Research questions (for selected study area) |
|---|---|---|
| GWP parameters | Determine subsurface hydrological components | What is the hydrogeochemistry of the water for a given area?<br>What are the hydrological components and surface water storage capacities in the study area? |
| GWP parameters | What are the factors (input parameters, drivers, environmental variables) that affect groundwater level (GWL) potential distribution, fluctuations, mapping and forecast in different regions over time? What are their relative importance? | How can spatially homogeneous clusters of GWL data be identified?<br>What are the critical controlling factors for groundwater potential mapping in the study area?<br>What are the data needs for water resources management?<br>What are the driving factors of the deceleration of GWL decline?<br>What are the environmental variables that can be used for mapping groundwater distribution potential?<br>What are the factors that determine groundwater development in different regions over time?<br>What are the hydrological parameters that influence groundwater level fluctuations?<br>What are the input data considerations for GWL potential modeling and forecasting?<br>What are the most efficient data inputs for GWL estimation?<br>What is the relative importance of different drivers of groundwater level change? |
| GWP parameters | What are examples of GWL influencing factors? | How does the rotation and permeability of the porous bed affect the dynamic coupling between the two flows?<br>What is the relationship between rainfall and groundwater levels?<br>How can potential spatial dependencies be captured and long-term dependencies be extracted from spatial-temporal data?<br>What are the changes in land use/land cover (LU/LC) in the study area over the past few decades? |
