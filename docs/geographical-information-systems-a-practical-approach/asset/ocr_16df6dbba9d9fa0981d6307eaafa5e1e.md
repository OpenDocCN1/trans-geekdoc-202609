![](bbox=[0.102, 0.092, 0.83, 0.417])

Figure 8.23 Five individual catchments delineated from a DEM.

# Practical 8.4 See the Support Material

In this practical, you are going to learn how to delineate catchments and extract other hydrology-related terrain attributes from a DEM in ArcGIS Pro or QGIS.

# 8.4.2.1 Topographic Wetness Index

TWI quantifies the effect of topography on the location and size of areas of water accumulation in soils (Beven and Kirkby 1979). It is defined as:

```
$TWI = \ln\left(\frac{A_s}{\tan \theta}\right)$ (8.17)
```

where $A_s$ is the upstream catchment area per unit contour length, and $\theta$ is the local

slope angle. $A_s$ is referred to as the specific catchment area. When a DEM is used, $A_s$ can be estimated as the ratio of the upstream catchment area to the cell size ($d$) of the DEM, unless the DEM has a very high resolution (Chirico et al. 2005). The following procedure is generally used to estimate TWI from a depressionless DEM:

+   1 Derive the flow direction from the DEM.