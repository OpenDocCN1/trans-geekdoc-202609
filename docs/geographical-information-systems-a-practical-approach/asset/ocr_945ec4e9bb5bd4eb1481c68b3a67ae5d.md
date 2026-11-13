passes. Therefore, a TIN can incorporate discontinuities on the terrain surface. These discontinuities are represented by breaklines. Breaklines are line features or boundaries of area features with or without height measurements. They become sequences of one or more triangle edges in the network (Figure 8.1). There are two kinds of breaklines: hard and soft. Hard breaklines represent a discontinuity in the slope of the surface, capturing abrupt changes in the surface. For example, streams and road cuts could be included in a TIN as hard breaklines. Soft breaklines do not change the local slope of a terrain surface. For example, coastlines or study area boundaries could be included in a TIN as soft breaklines to capture their position without affecting the shape of the surface.

# 8.2 Hydrologically Correct DEMs

DEMs are used predominantly in environmental analysis and modelling, while TINs are employed mostly for visualisation and engineering applications (Hutchinson and Gallant 2005). DEMs can be readily integrated with remotely sensed environmental data. Well-established algorithms developed for digital image processing can be used to process DEMs. However, a DEM may contain erroneous sinks or depressions generated during the DEM's production and generalisation processes (for example, by incorrect or insufficient input data, interpolation defects during DEM generation, rounding elevation values to the nearest integer numbers or averaging elevation values within grid cells).

![](bbox=[0.15, 0.51, 0.74, 0.87])

Figure 8.1 TIN with hard and soft breaklines.