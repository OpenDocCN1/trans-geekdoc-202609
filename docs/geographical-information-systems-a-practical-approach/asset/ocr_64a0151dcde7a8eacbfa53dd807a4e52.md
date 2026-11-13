Contemporary datums, based on increasingly accurate measurements of the shape of the Earth, are intended to best fit the entire Earth and do not favour any particular area on the Earth, such as the WGS84 datum, based on the WGS 1984 reference spheroid, and the GDA, based on the GRS80 reference spheroid. The study of the Earth's size, shape and geoid is the science of geodesy. A comprehensive introduction to geodesy can be found in Torge and Müller (2012). As users, we do not have to know much about geodesy in order to use GIS effectively. However, we must make sure that all our data are based on the same spheroid and datum so that geographical coordinates are measured in the same frame of reference. Thus, GIS users may need to convert between datums, and functions to do that are generally available in GIS software packages.

the Earth. While the Earth has a spherical surface, map sheets and computer screens are 2D flat surfaces. How can a flat map be used to describe locations on the Earth's surface? A common approach is to systematically transform the Earth's spherical surface to a 2D flat surface. Such a transformation is called a **map projection**. After the transformation, a **plane coordinate system** is established, which translates latitude and longitude (nonlinear measures) to orthogonal Cartesian (_x_, _y_) coordinates (linear measures). A plane coordinate system established based on a map projection is called a **projected coordinate system**, also called a **plane coordinate grid**.

# 2.2.3 Projected Coordinate Systems

Geographical coordinates are spherical coordinates. They provide a convenient reference system for describing locations on the approximately spherical surface of

# 2.2.3.1 Map Projections

Map projection involves mathematically projecting the surface of the Earth onto a flat surface or a surface that can be made flat by cutting. Such a surface is called a **developable surface**. The commonly used developable surfaces for map projection include cylinder, cone and plane, which lead to three families of map projection: cylindrical, conical and azimuthal (planar). Conceptually, a map projection is created by placing a light

> **Practical 2.1 See the Support Material**
> 
> _In this practical, you are going to learn how to obtain information about the geographical coordinate system and datum used with a particular spatial dataset, how to convert between geographical coordinate systems and how to assign a geographical coordinate system to a spatial dataset using ArcGIS Pro or QGIS._