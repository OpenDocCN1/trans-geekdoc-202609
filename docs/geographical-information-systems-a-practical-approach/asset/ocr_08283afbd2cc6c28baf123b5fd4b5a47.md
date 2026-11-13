coordinates that make up a line segment as represented in the input raster layer. The preceding two processes may produce spikes and gaps due to inaccuracies either present in the input raster data or induced by the specific algorithms used in the processes. After the spikes and gaps are removed, the extracted lines are smoothed. Then the topology is constructed by determining the adjacency relationships among all the lines. The individual line segments may be joined into whole lines or into polygons, depending on the types of geographical features represented in the original raster data.

The resolution of the input raster data is very important for raster-to-vector conversion, as it determines how well the line or area shapes are defined. At a higher resolution, the cells are smaller, and the results of vectorisation will approximate the real shapes more closely. As the resolution gets lower, the cells become larger, which leads to poorer representation of shapes after vectorisation and may even result in a completely false representation of the original shapes. Figure 3.7 shows an example where the raster produced in Figure 3.6 is converted back to the vector representation. When the result of this vectorisation is compared with

the original vector map, it is obvious that the vectorised polygons have distorted shapes. Therefore, for raster-to-vector conversion, we have to make sure that the resolution of the raster data is high enough to adequately represent the essential shapes of the features. Box 3.3 and Box 3.4 describe several tools available in ArcGIS Pro and QGIS for data structure conversion.

# ## 3.3.2 Geometric Transformation

Geometric transformation in GIS is used to adjust a data layer to correct geometric distortions, to register a data layer to a coordinate system (for example, converting a data layer created in digitiser units into real-world units represented on a map) or to transform a data layer by shifting, rotating, scaling or skewing its coordinate system. Transformations are applied uniformly to all features in a data layer.

# ## 3.3.2.1 Rubber Sheeting

Rubber sheeting is a GIS operation for correcting geometric distortions in a data layer. Geometric distortions often occur in source maps, due to low position accuracy (such as

![](bbox=[0.093, 0.666, 0.853, 0.846])

Figure 3.7 Vectorisation and distortion.