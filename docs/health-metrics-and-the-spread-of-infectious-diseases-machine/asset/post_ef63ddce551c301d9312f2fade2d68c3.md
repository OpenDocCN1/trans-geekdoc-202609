
## 11.2 Summary

In this chapter, we have learned how to visualise the results of a model. There are several important considerations when visualising the results of a model, and differences might arise due to the type of model used. We have seen how to use several packages and functions, such as ggplot2, vip, pROC, and DALEX to visualise the results of a model. We have also seen how to interpret the results of a model and how to communicate them effectively. The examples provided in this chapter demonstrate how to use visualisation techniques to enhance decision-making and communicate findings to various stakeholders.

# Spatial Data Modelling and Visualisation

### Learning Objectives

- Learn how to model and visualise spatial data
- Understand the concepts of spatial data, spatial data models, and spatial models
- Create maps, simulate infections, and predict the spatial distribution of phenomena

In the previous chapters, we explored the fundamentals of data visualisation with various techniques for creating static and interactive plots. In this chapter, we will learn how to model and envisage spatial data, which involves analysing and representing data with spatial components. We will explore the concepts of spatial data, spatial data models, and learn how to create maps, simulate infections, and predict the spatial distribution of phenomena such as disease spread. By combining spatial data with machine learning techniques, we can model the spatial dynamics of disease transmission and assess the risks associated with the spread of infections. We will use various packages such as sf, ggplot2, and gstat to create spatial models and visualisations, and gain insights into the spatial distribution of infections in a specific region.

## 12.1 Spatial Data, Spatial Data Models, and Spatial Models

Understanding the spatial distribution of phenomena such as disease spread, land cover changes, or climate patterns requires the use of spatial data and spatial models. These tools are essential for analysing and predicting spatial processes and for informing data-driven decisions in public health, environmental management, and urban planning.

A notable example is the Ebola Virus outbreak in West Africa (2014–2016). The virus spread across countries like Guinea, Liberia, and Sierra Leone, driven by factors such as population density, healthcare infrastructure, and human mobility. By analysing spatial data on cases, fatalities, and healthcare facilities and applying spatial models to simulate the virus's spread, researchers gained valuable insights into the dynamics of the outbreak. This analysis helped identify high-risk areas for targeted interventions.¹¹

- **Spatial Data:** This refers to data that includes geographic coordinates, addresses, or boundaries, representing the physical location of objects or events. Spatial data can be stored in two formats: vector and raster. Vector data use geometric shapes (points, lines, polygons) to represent features such as roads, cities, and boundaries. Raster data models, on the other hand, use a grid of cells or pixels, with a value representing a variable like temperature, land cover, or elevation.

- **Spatial Data Models**: These are frameworks for organizing and representing spatial data. They provide the structure for connecting real-world phenomena with their digital representation through algorithms (like spatial relationships and topology). Spatial data models form the foundation for managing and processing spatial information, enabling meaningful analysis and visualization.

- **Spatial Models**: Unlike spatial data, which organize data, spatial models simulate dynamic spatial phenomena that change over time. Examples include the spread of infectious diseases, flood development, or land changes. Spatial models are crucial for understanding and forecasting the evolution of spatial phenomena, allowing researchers and decision-makers to plan interventions and management strategies effectively.

For further information on spatial data models and spatial process, refer to the **ArcGIS** documentation for guidance on solving spatial problems and the **Esri** blog for in-depth discussions on spatial analysis. **R-Spatial.org** offers a wealth of resources on spatial data analysis, including tutorials and the latest developments in the field.

## 2.2 Making a Map

To learn how to make a map we first need spatial data. There are various sources and packages that provide spatial data for different regions and purposes. One such package is `rnaturalearth`, this package contains various types of boundaries of countries in the world. For more information use `rnaturalearth`. In particular, we use the `ne_countries()` function to get the boundaries of Africa, with the option `returnclass = "sf"` to return the data as **simple features**.

```r
library(tidyverse)
library(sf)
library(rnaturalearth)
```

```r
africa <- ne_countries(continent = "Africa",
      returnclass = "sf")
```

A simple feature object is a type of spatial data that contains the geometry of the spatial features (e.g., points, lines, polygons) and additional attributes such as the name of the country, population, and other information.

This is a map of Africa, but we can make it more interesting by adding some colours to the book. A better resolution of the colored map can be found in the online version.

```r
ggplot(data = africa) +
geom_sf() +
coord_sf()
# Africa with colours
gplot(data = africa) +
aes(fill=name),
  color = "white",
```

```r
linewidth = 1,
show.legend = F) +
coord_sf()
```

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_209_0.png)

(a) Map of Africa (b) Map of Africa with colors

Figure 12.1 Map of Africa

## 12.3 Coordinate Reference System (CRS)

**A Coordinate Reference System (CRS)** is a standardized way of defining the spatial location of features on the Earth's surface. It uses a set of coordinates to represent the position of points, lines, and polygons in space. There are different types of CRS, such as **geographic** and **projected** CRS, which are used to represent the Earth's surface in different ways. Geographic CRS (**LatLong**) represents locations on a curved surface using latitude and longitude for global mapping, while projected CRS or **Universal Transverse Mercator (UTM)** projects the curved Earth onto a flat map, using metres for precise mapping. In particular, the UTM system provides the distance in metres from the equator and the central meridian of a specific zone.

We use the `sf` package to define and transform CRS. The `st_crs()` function allows you to retrieve the CRS of a spatial object, while the `st_transform()` function allows you to transform the coordinates of a spatial object to a different CRS.

```r
africa_crs <- st_crs(africa)
africa_crs
# Coordinate Reference System:
# User input: WGS 84
# wkt:
# GEOGCRS["WGS 84",
# DATUM["World Geodetic System 1984",
# ELLIPSID["WGS 84",6378137,298.25723563],
# LENGTHUNIT["metre",1]]
# PRIMEM["Greenwich",0,
# ANGLEUNIT["degree",0.0174532925199433],
# CS[ellipsoid,2],
# AXIS["latitude",north,
```

```r
# ORDER[1],
# ANGLEUNIT["degree",0.0174532925199433],
# AXIS["longitude",east,
# ORDER[2],
# ANGLEUNIT["degree",0.01745329251994333],
# ID["EPSG",4326]
```

For example, the CRS of the Africa map is WGS 84 or World Geodetic System 1984 is a reference system for the Earth's surface that defines origin and orientation of the coordinate axes, called a datum (a fact known from direct observation). The EPSG is a structured dataset of CRS and Coordinate Transformations, it was originally compiled by the now, defunct, European Petroleum Survey Group². The EPSG code for WGS 84 is 4326.

## 12.4 Example: Simulation of Infections in Central African Republic

Synthetic data are created for the Central African Republic. The simulation of the number of infected individuals, their location, and temperature levels are obtained with random numbers generating functions from the {stat} package, which is a base package.
The Central African Rep. is a landlocked country in Central Africa, with a population of approximately 5 million people. The country is known for its diverse wildlife and natural resources, has faced challenges such as political instability and armed conflict.

```r
ctr_africa <- africa%%%
filter(name == "Central African Rep.")
```

### 12.4.1 Bounding Box

We use the st_bbox() function to retrieve the bounding box of the ctr_africa object, as a matrix with minimum and maximum values of the coordinates. A bounding box is a rectangular area defined by two points: the lower-left corner (minimum values of the coordinates) and the upper-right corner (maximum values of the coordinates). It provides a quick way to determine the spatial extent of a region and is often used in spatial analysis to define the boundaries of a study area.

```r
bbox <- ctr_africa%%% st_bbox()
bbox
# xmin ymin xmax ymax
# 14.45941 2.26764 27.37423 11.14240
```

### 12.4.2 Spatial Coordinates

The st_coordinates() function allows to extract the coordinates from a geometry vector and release a matrix with 5 columns, where the first two columns are the longitude (X) and latitude (Y), and the other indexes to group the coordinates into polygons.

¹Null, "Ebola Virus Disease in West Africa — the First 9 Months of the Epidemic and Forward Projections," New England Journal of Medicine 371, no. 16 (October 16, 2014): 1481-95, doi:10.1056/NEJMoa1411100.
