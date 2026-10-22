
a method to calculate the optimal cluster size filter for the 3-D characterization of drought. The effect of different drought indicator thresholds to calculate drought is also analyzed. The approach was tested in South America with data from the Latin American Flood and Drought Monitor for 1950–2017. Analysis of the spatial trajectories and characteristics of the most extreme droughts is also included. Calculated droughts are compared with information reported at a country scale and a reasonably good match is found.

## 11.1. Introduction

In recent decades, methods for drought calculation have increasingly treated this phenomenon as an event characterized in space and time (Andreadis et al., 2005; Corzo Perez et al., 2011; Diaz et al., 2020a, 2020b; Herrera-Estrada & Diffenbaugh, 2020; Lloyd-Hughes, 2012; Sheffield et al., 2009; van Huijgevoort et al., 2013; Vernieuwe et al., 2020). Each drought event is calculated considering different characteristics, such as duration, spatial extent, and location. A better characterization of drought improves the analysis of its behavior and its possible effects on different economic and environmental sectors (World Meteorological Organization (WMO), 2006). Treating drought as an event with spatial extent has also allowed new methods for its monitoring and prediction to be proposed (Diaz et al., 2018, 2020a).

The approach to calculating drought in three dimensions (longitude, latitude, and time) has followed a gradual process. One of the first works to consider drought with a spatial extent (area) was Yevjevich (1967). He used spatially distributed synthetic precipitation data to define the drought areas. The time series of drought areas allowed him to calculate the onset, end, duration, and magnitude of drought. Another key work that marked a before and after in calculating drought as a phenomenon with spatial extension was the research of Andreadis et al. (2005). They introduced a methodology for the calculation of drought clusters. In their methodology, the drought areas are contiguous in space. Over a given region, for example, a country, one or more areas of drought can be distinguished at the same time. The different areas (2-D clusters) are calculated using a clustering technique. Later, this 2-D clustering-based method was expanded to three dimensions (i.e., latitude, longitude, and time). The works of Corzo Perez et al. (2011) and Lloyd-Hughes (2012) are some of the first examples in which drought is calculated as a 3-D object (i.e., a contiguous group of voxels). A voxel is a cube that represents a value in the 3-D space similar to a pixel that is a cell in the 2-D space (Fig. 11.1). Corzo Perez et al. (2011) and Lloyd-Hughes (2012) include new features in the characterization of drought, such as volume (number of voxels) and location. The location is defined as the centroid of the 3-D cluster. Subsequently, the centroids of the drought were used to build the spatial trajectory (i.e., drought tracking). In works such as those of Diaz et al. (2020a, 2020b), Herrera-Estrada et al. (2017), and Herrera-Estrada and Diffenbaugh (2020), spatial trajectories of drought are calculated, serving to analyze the dynamics of drought. The 3-D characterization of drought opens up other possibilities for drought monitoring and prediction. In addition to predicting drought duration and magnitude, its spatial extent, location, and trajectory could also be predicted (Diaz et al., 2018, 2020a).

Research gaps remain in the topic of 3-D drought characterization. When calculating 3-D drought clusters, hereafter also only clusters, it is common practice to apply a cluster size filter to remove small clusters resulting from the methodology and not from the droughts themselves. In most cases, the cluster size filter is chosen arbitrarily, or such a choice is generally driven by past work or experience. Another parameter commonly chosen arbitrarily is the drought indicator threshold (section 11.2.1) (i.e., the value for which a value of the hydrometeorological variable is considered a drought). Although there is extensive research on the latter, its combined effect with the cluster size filter has not been fully analyzed.

This research proposes a method to calculate the optimal cluster size filter for the 3-D characterization of drought. Droughts are calculated with a 3-D clustering technique using different cluster size filters and drought indicator thresholds. The analysis of the most extreme droughts in the analysis period is also presented. The methodology was tested in South America, using data from the Latin American Flood and Drought Monitor (LAFDM) (Sheffield et al., 2014; Wood et al., 2016) for 1950–2017.

## 11.2. Methods and Data

### 11.2.1. Drought Calculation

In this methodology, drought is represented by a 3-D cluster. The data must be organized in a grid system where each voxel is geographically referenced (latitude and longitude). The arrangement of these geospatial data voxels can be schematized as a cube with latitude, longitude, and time as its sides (Fig. 11.1). Each 3-D drought cluster is made up of voxels that indicate drought (Fig. 11.1). The 3-D clustering-based methodology considers three main steps: (1) calculation of the drought indicator, (2) classification of the voxels in drought, and (3) calculation of the 3-D clusters (Fig. 11.1). After calculating the droughts, their characterization is carried out as described in section 11.2.2.

### Step 1
Drought indicator (DI) calculation

### Step 2
Classification

### Step 3
Clustering

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_337_0.png)

### Step 2
Cells indicating drought

### Step 3
Clusters

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_337_1.png)

### Step 2
Voxels indicating drought

### Step 3
3-D drought clusters

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_337_2.png)

Figure 11.1 Schematic overview of the methodology for 3-D drought clusters calculation: Drought indicator calculation (Step 1), classification of voxels in drought (Step 2), and 3-D clusters calculation (Step 3). The middle and bottom panels provide a 2-D and 3-D view in each time step (t). Note that when we refer to the 2-D space, we use the term cell, while in the 3-D space, we use voxel.

### Step 1. Drought Indicator Calculation

The drought indicator is calculated with the hydrometeorological data. This indicator makes it possible to define anomalies in the data by using a statistic (Fig. 11.1, top panel). The standardized drought indicators, for example, standardize the values of the hydrometeorological variable. Using these standardized values, the drought is identified by means of a threshold associated with a statistical value that defines an anomaly as drought. Values lower than the threshold are considered as drought. Other indicators use a threshold value directly applied to the hydrometeorological variable for the entire analysis period or a moving time window. In this second method, the values that are below the threshold are also considered as drought.

### Step 2. Classification of Voxels in Drought

After drought indicator calculation, the indication that a voxel is in drought is carried out with the drought indicator data. To indicate that a voxel is in drought, the binary classification is employed (i.e., the use of 1s and 0s; Fig. 11.1, top panel). In this way, drought is identified with 1s and nondrought with 0s, as indicated in equation (11.1). When the drought indicator (DI) is below a selected threshold (T), a cell is in drought. In equation (11.1), D_s stands for drought state (i.e., drought (1) or nondrought (0)).

$$D_S(t)=\begin{cases}1 & \text{if } DI(t)\leq T \\ 0 & \text{if } DI(t)>T\end{cases} \tag{11.1}$$

This research also analyzes the effect of the threshold (T) on the calculation of droughts (3-D clusters). The thresholds of 0, −1, −1.5, and −2 are tested. It is noted that, in standardized drought indices, the values equal to or below zero indicate “drought.” Equation (11.1) is applied in each voxel in each time step (t).

### Step 3. 3-D Clusters Calculation

The third step is the calculation of the 3-D clusters. A clustering method to extract the drought events is applied following Corzo Perez et al. (2011). The drought events correspond to the 3-D clusters calculated
