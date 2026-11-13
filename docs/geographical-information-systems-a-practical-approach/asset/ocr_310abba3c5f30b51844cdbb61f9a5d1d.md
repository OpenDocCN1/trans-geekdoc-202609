Fengshan. In some areas, mosquito abundance and human population density could be significant predictors of dengue incidence. But in other areas, other environmental and social factors might have more effects on dengue transmission. The findings from the study provided policymakers with useful insights into spatial targeting of intervention against dengue epidemics.

Source: Lin and Wen (2011).

describe geographical events and phenomena at a particular location and during a certain period of time. Such data are called timestamped spatial data, or simply spacetime data. There are two types of spacetime data: tracking data and spatial panel data (An et al. 2015).

**Tracking data**, also called movement data, represent individual objects (such as people, wildlife animals and vehicles) and their movement in geographical space over time. They are usually georeferenced point feature data with timestamps. Generally, a tracking dataset, despite the forms of data collection (for example, travel diaries, GPS tracks and Wi-Fi probe requests), is composed of a sequence of track points: {$(x_i, y_i, t_i) | i = 1, 2, ..., n\}$, where $(x_i, y_i)$ are the geographical coordinates of the track point $i$, and $t_i$ is the timestamp of the track point $i$. This sequence of track points represents a movement trajectory, which can be visualised in a 3D geographical space, with the $X$ and $Y$ axes being the location and the $Z$ axis being the time (Figure 6.20). The movement trajectory is also known as the **space-time path** in time geography (Hägerstrand 1970). The track point with $i = 1$ represents the start point of the movement trajectory, and that with $i = n$ is the end point. The space-time path describes the location of the track point as well as the travel or stay

![](bbox=[0.49, 0.29, 0.85, 0.57])

between track points during the period of observation.

This type of data is mainly used to track movement of individual objects or events, create the trajectory in geographical space, calculate characteristics of motion such as speed and direction, understand characteristics and activities of the individual objects or events that move and their dynamics over time. They can also be used to understand current and historic movement patterns and predict outcomes for future events.

**Spatial panel data** comprise time series observations of a set of spatial units. The spatial units are usually location-specific and time-invariant. They can be (1) grid