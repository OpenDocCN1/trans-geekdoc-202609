
## Data Preparation

The GIS data used include land use, digital elevation models (DEM), surface hydrological features (rivers and streams) and septic tanks. The land use layer was created from satellite images through image classification. It contains six broad types of land use: urban-residential, pasture, arable land, water, forest and others (Figure 5.9). The DEM was generated from 2002 1:25,000 topographic data with a 20 m grid resolution, which was used for visualisation purposes only. The surface hydrological feature layer was also generated from 2002 Victorian 1:25,000 Topographic Map Series. The DEM and surface hydrological feature layers were both acquired from the Victorian state government. The distribution of septic tanks in the catchment was identified using the house point data.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_267_0.png)

Figure 5.9 Land uses in the Woori Yallock catchment.

## Delineation of Riparian Buffers

Different management objectives may require different widths of riparian vegetation buffer. This study applied 50 m buffers along the rivers and 30 m buffers along the streams. It is based on the recommendations from the Victorian state government and the septic tank code of practice in the Woori Yallock catchment, which requires that each septic tank be located at least 50 m from a waterway. The 50 m and 30 m riparian buffer zones of the catchment were delineated based on the surface hydrological feature layer using the buffer function of ArcGIS Desktop (Figure 5.10).

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_268_0.png)

**Figure 5.10** The 50 m and 30 m riparian buffer zones in the Woori Yallock catchment.

## Identification of Critical Areas

Riparian buffer zones, land use and septic tank information were integrated to identify critical areas. Once the riparian buffer zones were created, the land use and septic tanks information within these zones was extracted through overlay analysis in ArcGIS Desktop. The extracted information was then used to identify those areas where there is a need for revegetation and restoration in order to reduce the threat of pollution. Two steps were involved in identifying critical areas. Firstly, agriculture and urban settlement areas within the riparian buffer zones were identified. And secondly, because the septic tanks may contaminate their surrounding areas, a 100 m area centred in every septic tank was delineated. The overlapped areas of the 100 m buffers around the septic tanks with the riparian buffer zones were considered as critical areas which are subject to pollution from the septic tanks. After these two steps, the critical areas in relation to land use and septic tanks were identified. Figure 5.11 shows the distribution of the critical areas.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_269_0.png)

Figure 5.11 Critical areas in relation to land use and septic tanks in the Woori Yallock catchment.

It can be found that most of the critical areas are located in the western, southern and south-eastern reaches of the river system. There are also a few critical areas scattering in the north-east and south-west of the catchment. Distribution of the critical areas mostly aligns with arable land. Only a few critical areas are urban settlements, which are concentrated in the south-west of the catchment. Therefore, urban activities have less impact on the hydrological system than agriculture in the Woori Yallock catchment. Agriculture is the biggest non-point source of pollution. The distribution of the critical areas caused by agriculture along the rivers and streams highlights the importance of agricultural activities to water pollution. More importantly, the affected areas are spread along the first-order streams, which have significant impacts on the water quality of the lower reaches of the river and stream system, although their areas are not large compared with the total area of the riparian buffers. The study concluded that although green footprints covered most of the Woori Yallock catchment, the water quality had degraded. More measures needed to be taken to protect the riparian zones of this catchment.

Source: Li et al. (2007).

input layer contains point features, and the other represents polygon features. The result is a point layer representing the same set of point features with additional attributes transferred from the polygon layer. Figure 5.12 illustrates the process.

**Line-in-polygon overlay** determines which areas a line feature is crossing. One input layer represents line features, and the other represents polygon features. It calculates the geometric intersection of the line features with the polygon features and splits the line features at polygon boundaries. Each of the resulting line features is assigned the attributes of the polygon it fell within, along with the original attributes from the input line feature layer. The result

is a line feature layer composed of the split line features (Figure 5.13).

Polygon-on-polygon overlay combines two polygon layers. It involves calculating the geometric intersection of the polygon features from the two input layers, creating a new set of polygons with the polygon boundaries from the original features split at the intersections and writing these new polygons as features to the output layer (Figure 5.14). Each new polygon is assigned the attributes from the two input layers.

There are basically three methods for vector overlay: union, intersect and identity (Figure 5.15). The **union** method performs polygon-on-polygon overlay and keeps all

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_271_0.png)

| ID | Vegetation Type |
|---|---|
| 1 | Pine |
| 2 | Oak |
| 3 | Spruce |
| 4 | Spruce |
| 5 | Pine |

Figure 5.12 Point-in-polygon overlay.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_271_1.png)

| Old ID | New ID | Soil Type |
|---|---|---|
| 1 | 1 | Loam |
| 1 | 2 | Sandy |
| 3 | 3 | Sandy |
| 3 | 4 | Clay |
| 2 | 5 | Sandy |
| 2 | 6 | Sandy-Loam |

Figure 5.13 Line-in-polygon overlay.

the features from the two input layers. The intersect method performs point-in-polygon, line-in-polygon or polygon-on-polygon overlay and preserves the features or portion of the features that fall within the common area of all inputs. The identity

method performs point-in-polygon, line-in-polygon or polygon-on-polygon overlay but keeps all the features in the first input layer and deletes the portions of the second layer features which cross the boundary of the first input layer.

| ID | Land Use | Soil Type |
|---|---|---|
| 1 | Agriculture | Loam |
| 2 | Urban | Loam |
| 3 | Urban | Clay |
| 4 | Agriculture | Sandy |
| 5 | Agriculture | Loam |
| 6 | Forest | Loam |
| 7 | Forest | Sandy |
| 8 | Forest | Sandy-Loam |
| 9 | Agriculture | Sandy-Loam |
| 10 | Urban | Sandy-Loam |
| 11 | Urban | Sandy |

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_272_0.png)

Figure 5.14 Polygon-on-polygon overlay.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_272_1.png)

Figure 5.15 Three basic methods for vector overlay.

In some GIS systems such as ArcGIS, the intersect method can be used with inputs with any combination of feature types (point, line and polygon). The output feature type will be of the same type or a type of the input features with the lowest dimension geometry. For example, if all the inputs are polygons, the output type

will be polygon. If one of the inputs is line and none are points, the output type will be line. If any of the inputs are point, the output type will be point. The intersect method can also run with a single input. In this case, it will identify the intersections between features within the single input, which can be useful to find polygon overlap and line intersections.

### 5.4.2 Raster Overlay

Raster overlay combines multiple raster layers into a single raster, in which every cell of each raster references the same geographical location. Therefore, raster overlay does not involve geometric intersection as vector overlay does. It involves operations on individual values of corresponding cells in the input layers to create a new raster layer with new cell values. A value can be assigned to each cell in the output raster based

on unique combinations of values from several input rasters. Usually, raster overlay is used to mathematically combine the rasters assigned with numerical cell values to calculate a new value for each cell in the output raster. Figure 5.16 shows an example of raster overlay by addition. Two input rasters are added together to create an output raster, with the values for each cell summed.

Raster overlay can be used to perform arithmetical, logical, relational, conditional and statistical operations on the input rasters (see Table 5.5). When applying logical operators in raster overlay, we often first re-classify the input rasters into binary rasters with cell values of either 1 or 0, then perform overlay operations, as shown in Figure 5.17.

### 5.4.3 Map Algebra

Raster overlay with mathematical operators is one of the map algebra tools

**Practical 5.9 See the Support Material**

In this practical, you are going to implement vector overlay in ArcGIS Pro or QGIS.

| 5 | 8 | 3 | 6 |
|---|---|---|---|
| 7 | 4 | 2 | 8 |
| 7 | 8 | 9 | 4 |
| 6 | 7 | 4 | 2 |

| 12 | 6 | 45 | 23 |
|---|---|---|---|
| 20 | 11 | 28 | 9 |
| 6 | 7 | 3 | 10 |
| 21 | 15 | 12 | 8 |

| 17 | 14 | 48 | 29 |
|---|---|---|---|
| 27 | 15 | 30 | 17 |
| 13 | 15 | 12 | 14 |
| 27 | 22 | 16 | 10 |

Figure 5.16 Raster overlay by addition.
