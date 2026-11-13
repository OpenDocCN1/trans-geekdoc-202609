or modify it to measure network distances and find the shortest paths in a network. It also provides a basis for other network analysis operations in GIS, including finding the closest facilities and delineating service areas.

each location can be analysed. It is the most common GIS operation for comparing and analysing multiple data layers simultaneously. As a tool for describing spatial correspondence of different geographical phenomena, overlay analysis has been used in a wide range of applications, such as examining the relationship between rainfall distribution and elevation; calculating the number of properties within a 100-year floodplain; evaluating environmental sensitivity based on slope, surface drainage, bedrock foundation, soil erosion and other environmental factors and establishing spatial associations between wildlife occurrence and habitat conditions. The case study in Box 5.1 provides an example of the application of overlay analysis together with buffering for identifying the critical areas of riparian zones in a catchment. Overlay analysis can be conducted in both vector and raster.

However, network distance measurement in GIS requires preparation of a network dataset, which consists of three topologically structured elements: edges (links), junctions (nodes) and, optionally, turns (a transition from one link to another at a node). The network characteristics are recorded as attribute data linked with edges, junctions and turns. Examples of network attributes include link impedance, link demand, flow direction, speed limit, turn restriction and turn impedance. Link impedance is the cost involved in traversing a link, which may be measured as travel time, distance and fuel cost. Turn impedance is usually referred to as the time it takes to complete a turn.

# 5.4 Overlay Analysis and Map Algebra

# 5.4.1 Vector Overlay

Overlay analysis is a process of stacking multiple data layers registered to a common georeferencing system on top of each other so that the relationships between features at

Vector overlay involves combining geometries and attributes from the input vector layers into a single vector layer. There are three types of vector overlay: point-in-polygon, line-in-polygon and polygon-on-polygon.

Point-in-polygon overlay identifies in which area a point feature is located. One

# Practical 5.8 See the Support Material

In this practical, you are going to learn how to create a network dataset and measure network distances in ArcGIS Pro or QGIS.