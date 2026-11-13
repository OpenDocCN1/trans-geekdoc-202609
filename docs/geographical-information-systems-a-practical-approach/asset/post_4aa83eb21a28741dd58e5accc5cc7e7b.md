
For example:
3x3 rectangle neighbourhood centred at Cell(3, 5):

| 4 | 3 | 2 |
| 4 | 2 | 2 |
| 3 | 3 | 2 |

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_279_0.png)

The output value of Cell(3, 5)
= (4+3+2+4+2+2+3+3+2) / 9 = 2.8

The output value of Cell(3, 5)
= 4 - 2 = 2

The output value of Cell(3, 5)
= 2

Figure 5.21 Examples of neighbourhood statistics.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_279_1.png)

Figure 5.22 Part of a DEM: (a) before and (b) after smoothing.

calculate the mean and maximum elevation in each type of forests. Some GIS packages have zonal geometry functions that can be used to calculate area, perimeter, thickness and other geometric characteristics for each zone in a raster. Practical 5.13 demonstrates how to access the zonal functions in ArcGIS Pro and QGIS.

## Practical 5.12 See the Support Material

In this practical, you are going to learn some uses of focal functions in ArcGIS Pro or QGIS.

| Forest |
|---|
| 11 | 11 | 12 | 13 | 13 | 13 |
| 11 | 11 | 12 | 13 | 13 | 13 |
| 12 | 11 | 12 | 13 | 13 | 13 |
| 12 | 12 | 12 | 11 | 13 | 13 |
| 11 | 12 | 12 | 11 | 11 | 12 |
| 11 | 11 | 11 | 11 | 11 | 12 |

| Elevation (m) |
|---|
| 1016 | 1023 | 1024 | 1030 | 1043 | 1050 |
| 1021 | 1023 | 1025 | 1038 | 1045 | 1055 |
| 1025 | 1026 | 1041 | 1044 | 1058 | 1068 |
| 1028 | 1030 | 1035 | 1052 | 1069 | 1072 |
| 1033 | 1045 | 1042 | 1055 | 1070 | 1078 |
| 1042 | 1048 | 1055 | 1058 | 1065 | 1080 |

| Output Rasters |
|---|
| 1041.9 | 1041.9 | 1041.2 | 1052 | 1052 | 1052 |
| 1041.9 | 1041.9 | 1041.2 | 1052 | 1052 | 1052 |
| 1041.2 | 1041.9 | 1041.2 | 1052 | 1052 | 1052 |
| 1041.2 | 1041.2 | 1041.2 | 1041.9 | 1052 | 1052 |
| 1041.9 | 1041.2 | 1041.2 | 1041.9 | 1041.9 | 1041.2 |
| 1041.9 | 1041.9 | 1041.9 | 1041.9 | 1041.9 | 1041.2 |

| | | | | | |
|---|---|---|---|---|---|
| 1070 | 1070 | 1080 | 1072 | 1072 | 1072 |
| 1070 | 1070 | 1080 | 1072 | 1072 | 1072 |
| 1080 | 1070 | 1080 | 1072 | 1072 | 1072 |
| 1080 | 1080 | 1080 | 1070 | 1072 | 1072 |
| 1070 | 1080 | 1080 | 1070 | 1070 | 1080 |
| 1070 | 1070 | 1070 | 1070 | 1070 | 1080 |

Figure 5.23 Examples of zonal statistics.

## Practical 5.13 See the Support Material

In this practical, you are going to learn some uses of zonal functions in ArcGIS Pro or QGIS.

Global functions calculate a new value for every cell in the output raster as a function of the existing values of all cells in the input raster. Distance surface and least-cost path functions, discussed earlier, and visibility analysis functions (see Section 8.5) are global functions.

current volume only introduces the most commonly used methods available in GIS. These include inverse distance weighted (IDW), natural neighbour, trend surface, spline and kriging.

## 5.5 Spatial Interpolation

Spatial interpolation is the procedure of estimating values of a variable at locations whose values are unknown based on a sample of locations with known values. Spatial data are often collected as discrete observations at points or along transects, such as soil cores, soil moisture, vegetation transects and meteorological station data. Through spatial interpolation, spatial distributions of the geographical phenomena can be approximated. This is an important technique in creating continuous spatial datasets from sampling networks of observation points. For example, it can be used to estimate rainfall based on the data recorded at a network of rain gauge stations; to estimate concentrations of air pollutants, such as CO₂, SO₂, NO₂ and particulate matter (PM) using samples from monitor stations; and to assess mining potentials based on drilling data.

Basically, spatial interpolation involves applying an interpolation method to a set of points with known values to create a continuous surface. These points are also known as sample points or observations. They can be regularly or irregularly distributed. Many interpolation methods have been developed. Li and Heap (2008) provide a comprehensive review of more than 40 spatial interpolation methods. The

### 5.5.1 IDW

IDW estimates a value of each location by taking the distance-weighted average of the values of sample points in its neighbourhood (Figure 5.24). The closer a sample point is to the location being estimated, the more influence or weight it has in the averaging process. In other words, each sample point has a local influence that diminishes with distance. The rationale behind IDW is Tobler's first law of geography: ‘everything is related to everything else, but near things are more related than distant things’ (Tobler 1970, p. 236). Mathematically, IDW can be expressed as:

```
$Z_0 = \sum_{i=1}^{n} w_i Z_i \quad (5.10)$
$w_i = \frac{1/d_i^r}{\sum_{j=1}^{n} (1/d_j^r)} \quad (5.11)$
```

where $Z_0$ is the interpolated value of the point being estimated, $n$ is the number of sample points in the neighbourhood, $Z_i$ ($i = 1, \dots, n$) is the value of the $i$th sample point in the neighbourhood, $d_i$ ($i = 1, \dots, n$) is the distance from the point being estimated to the $i$th sample point in the neighbourhood and $r$ is the power.

The power parameter determines the significance of the sample points on the interpolated value. By defining a higher power, more emphasis is placed on the nearby points, producing a more varying and less smooth surface. Specifying a

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_282_0.png)

- The location with unknown value
- Sample point

```
Z_0 = \frac{\sum_{i=1}^5 Z_i / d_i^2}{\sum_{i=1}^5 1 / d_i^2}
```

where

d_1..., d_5 are distances
Z_1..., Z_5 are the values of Point 1, Point 2, ..., Point 5

Figure 5.24 Sample points and the circular neighbourhood used in IDW.

lower power will give more influence to the distant points, resulting in a smoother surface. A power of 2 is most commonly used with IDW. Figure 5.24 shows two surfaces interpolated using IDW with different r values, based on the same set of sample points. An optimal r value is considered to be where the minimum mean absolute error or RMSE is at its lowest. Some GIS systems offer tools to find the optimal r value.

The characteristics of the interpolated surface can also be controlled by the shape and size of neighbourhood. Usually, a neighbourhood is defined as a circle, with a fixed or variable radius, which limits the number of sample points that can be used for interpolation (see Figure 5.24).

IDW is easy to understand and use, which makes it a very popular method for interpolation in GIS. The interpolated surface passes through the sample points.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_283_0.png)

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_283_1.png)

Figure 5.25 Rainfall surfaces interpolated using IDW with different power values.

However, the interpolated values are always within the range of the measured values of sample points and will never be beyond the maximum and minimum values of the samples. If the original sample points do not capture the underlying true maximum and minimum surface values (for example, mountaintops and valley bottoms), they will be missing from the interpolated surface.

### 5.5.2 Natural Neighbour

**Natural neighbour** estimates the value of an unsampled location by finding the closest subset of sample points to the location being estimated, then applying weights to them based on proportionate areas (Sibson 1981). It is based on Voronoi (Thiessen) tessellation.

**Voronoi tessellation** builds a network of polygons based on a set of sample points, called Voronoi or **Thiessen polygons**. Each polygon contains only one sample point, and any location within a polygon is closer to the polygon's sample point than to any other sample point contained in other polygons (Figure 5.26). Voronoi tessellation was originally used for computing areal estimates from rainfall data. It now has ecological applications, such as determining territories and influence zones of wild animals, delineating spaces available for the roots of individual plants and spaces around flowering orchid stems, studying the growth patterns of forests and forest canopies and predicting forest fires.

For natural neighbour interpolation, initially, a network of Voronoi polygons is created of all the sample points. Then, a new Voronoi polygon network is constructed of all the sample points plus an unsampled point being estimated. The addition of the unsampled point changes the shape and size of Voronoi polygons of the surrounding sample points. For example, in Figure 5.26, the dashed lines represent the edges of the initial Voronoi network before the unsampled point $P_0$ is added, and the solid lines represent the edges of

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_284_0.png)

| Unsampled point | Sampled point |
|---|---|
| — Edge of a Voronoi polygon | --- Edge of an initial Voronoi polygon |

Figure 5.26 Voronoi tessellation (the shaded polygon containing the unsampled point).
