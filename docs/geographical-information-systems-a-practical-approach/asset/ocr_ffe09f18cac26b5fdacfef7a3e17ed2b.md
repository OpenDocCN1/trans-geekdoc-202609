# Box 2.4 Types of Spatial Databases in ArcGIS

ArcGIS supports four types of spatial databases: georelational databases, file geodatabases, mobile geodatabases and enterprise geodatabases. Figure 2.36 provides a folder-tree view of examples of the first three types of spatial databases in an ArcGIS Pro project.

Georeational database
  Shapefiles
    landslides.shp < Point feature class
    sampledArea.shp < Polygon feature class
    transect.shp < line feature class
File geodatabase
  FileDB.gdb
    Climate < File geodatabase feature dataset
    Geology < File geodatabase feature dataset
    Hydrology < File geodatabase feature dataset
      gauges < File geodatabase feature class - points
      lakes < File geodatabase feature class - polygons
      rivers < File geodatabase feature class - lines
    Socio_economic < File geodatabase feature dataset
    Topography < File geodatabase feature dataset
Mobile geodatabase
  MobileDB.geodatabase
    main.parcels < Mobile geodatabase feature class - polygons
    main_road_junctions < Mobile geodatabase feature class - points
    main.roads < Mobile geodatabase feature class - lines

Figure 2.36 A folder-tree view of spatial databases.

# Georelational Databases

A georelational database in ArcGIS is a workspace containing Arclnfo coverage (including TIN) and grid files, or a collection of shapefiles held in a file system folder. A shapefile contains a single feature class, and a coverage may contain multiple feature classes. All the files are managed by the computer's file management system, but some file management functions, including deleting, renaming, copying, pasting and creating a shapefile or coverage, should be conducted in Catalog. The locational or geometric data and attribute tables of a shapefile or a coverage or a grid are linked, related or joined in ArcGIS via its data management software