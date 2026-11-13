
cells (regular squares or hexagons), (2) polygons (for example, land use boundaries, neighbourhoods, property boundaries, political or administrative boundaries, which may sometimes be subject to changes in shape and size), or (3) data collection or observation sites (for example, buildings, meteorological stations and gauging stations). Figure 6.21 provides a time series of maps from a spatial panel dataset, which represent the violent crime rates (the number of violent crimes per 100,000 population, including murder, rape, robbery and aggravated assault) of each county in Florida, USA, from 2013 to 2020. In this example, the spatial units are counties.

Spatial panel data comprise information gathered at specific time intervals on the same spatial units. They allow organisations or researchers to examine how geographical variables, events or phenomena are changing over time and how they could affect trends in the future. For instance, the criminal activities can be reduced by a distribution of patrol officers according to the crime rate. By referencing spatial panel data on county-specific crime rates from the past 20 years, crime investigators may be able to trace the change in the spatial pattern of crimes, assess the efficacy of crime prevention measures and the safety of societies and predict future patterns and trends of the crime rate in order to facilitate practical crime prevention solutions and make better use of the confined resources.

## 6.7.2 Space-Time Cubes

Space-time data are often structured, represented and visualised using **space-time cubes**. The concept of the space-time cube originates from time geography (Hägerstrand 1970), where it refers to a 3D Euclidean space consisting of two horizontal dimensions of space (geographical plane) and one vertical dimension of time, as shown in Figure 6.20. There are various ways in which space-time cubes are built or visualised for a given timestamped spatial dataset. Bach et al. (2017) described some forms of the space-time cube and a range of space-time cube operations. This section introduces the grid-structured space-time cube, simply called grid cube, popularised by ESRI (Environmental Systems Research Institute).

A grid cube is structured in terms of rows, columns and time-steps. As shown in Figure 6.22, the basic unit of such a space-time cube is a bin. Every bin has a fixed position in space (x, y) and in time (t). All the bins at the same time-step form a time slice for that time-step. All the bins at the same location are grouped as a bin time series for that location. The rows and columns determine the spatial extent of the space-time cube, and the time-steps determine the temporal extent. Each bin has a count of geographical events occurring in the bin, or values for particular variables or geographical features within the bin.

The time-step interval can be the number of seconds, minutes, hours, days, weeks or years that will represent a single time-step, depending on how often the data are collected or at what time interval the user wants to conduct the analysis. For example, if the data are collected every year, the time-step interval can be set as 1 year. If the data such as moisture readings are recorded every five minutes, they can be aggregated temporally into hourly averages for analysis. In this case, the time-step interval is 1 hour.

Bins are typically cubes, but they can be hexbins that form a hexagonal grid cube. The idea with hexagons is to reduce sampling bias from edge effects of the square shape, which is related to high perimeter/area ratios. A circle has the lowest ratio but cannot form a continuous grid, and hexagons are the closest shape to a circle that can still form a grid. Hence, if working over a large area, a square grid will suffer more from distortion due to curvature than shapes like hexagons. Hexagonal grids and hexbins are preferable when issues of connectivity, nearest neighbourhood or movement paths are crucial aspects to be considered in the analysis. Bins can also be any other shapes of polygons, which represent defined or fixed locations with associated attributes that have been collected over time.

Grid cubes show how geographical events or phenomena change over time within geographical space by generating bins with either aggregated incident points or defined features with associated spatiotemporal attributes. For example, if you have a point feature dataset representing crime locations, you may aggregate points by counting how many points fall into each bin at each time-step in terms of their locations and timestamps. If the time-step interval is set to one month, the number of crimes is aggregated for each month. Sequentially, every other month is stacked above using their respective values. By looking at the bin time series for a particular location from bottom to top, you can observe how crime changes over time at that location.

Grid cubes can be used to represent any phenomena that have time and geography associated with them, such as vegetation health over time, poverty change rates, bacteria outbreaks, observations of rare plants or animals, changes in land use and the incidence rate of heart disease over a specified timeframe. As an example, Figure 6.23 shows part of a grid cube representing the global monthly total rainfall in 2010, constructed from the 2010 gridded monthly terrestrial precipitation time series data provided by the NOAA Physical Sciences Laboratory. Each bin is a cube with the side length of 0.5° latitude × 0.5° longitude in the X and Y dimensions (called bin distance or distance interval). The time-step interval of the grid cube is one month.

Grid cubes are not only a visualisation tool but also provide an effective tool for representing, structuring and storing space-time data. They have been used as a data model for space-time data structuring and analysis in ArcGIS and other software packages such as R.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_341_0.png)
![](img/8aad3fa01ca9db86bd50bb2edb9a3134_341_1.png)
![](img/8aad3fa01ca9db86bd50bb2edb9a3134_341_2.png)
![](img/8aad3fa01ca9db86bd50bb2edb9a3134_341_3.png)
![](img/8aad3fa01ca9db86bd50bb2edb9a3134_341_4.png)
![](img/8aad3fa01ca9db86bd50bb2edb9a3134_341_5.png)
![](img/8aad3fa01ca9db86bd50bb2edb9a3134_341_6.png)
![](img/8aad3fa01ca9db86bd50bb2edb9a3134_341_7.png)

Figure 6.21 A time series of maps of violent crime rates in Florida, USA, from 2013 to 2020.

Source: Data from Florida Department of Law Enforcement, USA.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_342_0.png)

## 6.7.3 Space-Time Analysis Methods

A number of methods have been developed for space–time analysis based on space–time cubes. This section focuses on three methods: time series clustering, local outlier analysis and emerging hotspot analysis, and introduces the techniques used in ArcGIS.

### 6.7.3.1 Time Series Clustering

Time series clustering is a technique for partitioning the locations in a space-time cube into distinct clusters based upon similarity of time series characteristics such as temporal patterns and trends. Member locations of each cluster may have similar values across time, or their values tend to increase and decrease at the same time or have similar repeating patterns. The objective is to maximise data similarity within clusters and minimise it across clusters. The technique can be used for various purposes, such as anomaly detection and pattern discovery.

There are many time series clustering methods available (Belhadi et al. 2020). For any time series clustering approach, the main points to be considered are what is meant by similarity between bin time series, how to measure the similarity

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_343_0.png)

Figure 6.23 Part of a grid cube of the global monthly total rainfall in 2010.

Source: Data from Terrestrial Air Temperature and Precipitation: 1900–2014 Gridded Monthly Time Series. Data provided by the NOAA PSL, Boulder, Colorado, USA, from their website at https://psl.noaa.gov.
