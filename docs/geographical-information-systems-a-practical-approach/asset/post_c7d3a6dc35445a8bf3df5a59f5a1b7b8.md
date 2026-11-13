
recorded in spatial data are defined according to a particular georeferencing (coordinate) system that has a fixed relationship to the Earth's surface and takes the Earth's shape into account.

- Geographical space can be conceptualised in the object or field view. In the object view, the geographical space consists of a collection of discrete objects or entities. Each object can be accurately located and has a well-defined boundary. In the field view, the geographical space constitutes continuous surfaces representing variables whose values change continuously across the space.

- Map scale determines the amount of detail about geographical features captured and represented in spatial data.

- Geographical features represented in spatial data are selected and generalised through cartographic generalisation. The methods of cartographic generalisation include selection, simplification, exaggeration, combination, displacement, and classification.

- Geographical coordinate systems uniquely define locations of geographical features on the surface of the Earth using latitude and longitude. They are based on a specific datum.

- Map projections transform the Earth's spherical surface to a flat surface, which converts the latitudes and longitudes of locations on the Earth's surface into locations on a plane. This process always produces some distortions in shape, distance, direction, scale and area. There are three families of map projection: conic, cylindrical and azimuthal.

- Projected coordinate systems are plane coordinate systems established based on a particular map projection. The UTM system, based on the cylindrical transverse Mercator projection, is a popular projected coordinate system widely used for large-scale topographic maps, remote sensing images and GIS databases.

- A spatial data model defines how spatial data represent geographical features, and how spatial data are structured, connected, organised and stored inside a GIS system. Three types of spatial data models have evolved: vector, raster and object-oriented. The majority of the existing GIS systems are based on either vector or raster models or both. The vector and object-oriented models conform to the object view of geographical space, while the raster model is based on the field view.

- A spatial database is a shared collection of logically related spatial data structured and organised based on one or several spatial data models. Georelational and object-relational databases are two typical types of spatial databases. A spatial database is designed to meet the information needs of an organisation.

## Key Terms

- arc–node topology
- area feature
- azimuthal projection
- cartographic generalisation
- cartographic spaghetti
- cell–by–cell encoding
- cell size
- cell value
- centre location rule
- central meridian
- conformal projection
- conic projection
- cylindrical projection
- datum
- Delaunay triangulation
- developable surface
- distortion ellipse
- domain
- easting
- ellipsoid
- equidistant projection
- equivalent projection
- false easting
- false northing
- false origin
- feature class
- feature attribute table
- field view
- foreign key
- geocode
- geocoding
- geodesy
- geographical coordinate
- geographical coordinate system
- geoid
- georeference
- georeferencing
- georeferencing system
- georelational database
- latitude
- left-right topology
- line feature
- local scale
- longitude
- map projection
- map scale
- maximum area rule
- meridian
- metric georeferencing system
- nominal scale
- normal projection
- non-topological data structure
- northing
- object view
- object-oriented data model
- object-relational database
- oblique projection
- parallel
- plane coordinate grid
- plane coordinate system
- point feature
- polygon–arc topology
- primary key
- prime meridian
- principal scale
- projected coordinate system
- raster
- raster data model
- raster pyramid
- relation
- relational database
- representative fraction
- run-length encoding
- scale factor
- secant projection
- shapefile
- spatial data
- spatial data model
- spatial database
- spatial distortion
- spatial measurement framework
- spatial resolution
- spheroid
- standard line
- standard parallel
- standard point
- tangent projection
- topological data structure
- topological relationship
- transverse projection
- triangle-node topology
- triangulated irregular network (TIN)
- value attribute table
- vector data model
- Voronoi polygon
- zero meridian

## References

- Allen, D.W. (2019) Focus on Geodatabases in ArcGIS Pro, Redlands, CA: ESRI Press.
- Corbett, J.P. (1979) Topological Principles in Cartography, Technical Paper 48, Washington, DC: United States Department of Commerce, Bureau of the Census.
- de Berg, M., Cheong, O., van Kreveld, M. and Overmars, M. (2008) Computational Geometry: Algorithms and Applications, 3rd edition, Berlin: Springer.
- Ebdon, D. (1992) 'SPANS – A quadtree-based GIS', Computers & Geosciences, 18(4): 471–475.
- ESRI (1998) ESRI Shapefile Technical Description – An ESRI White Paper, Redlands, CA: ESRI Press.
- ESRI (1999) Understanding GIS – The ARC/INFO method, Redlands, CA: ESRI Press.
- Gillenson, M.L. (2012) Fundamentals of Database Management Systems, 2nd edition, Hoboken, NJ: Wiley.
- Haining, R. (2009) 'The special nature of spatial data', in A. Fotheringham and P. Rogerson (eds.) The SAGE Handbook of Spatial Analysis, Los Angeles: Sage, 5–23.
- Lo, C.P. and Yeung, A.K.W. (2007) Concepts and Techniques in Geographic Information Systems, 2nd edition, Upper Saddle River, NJ: Pearson Prentice Hall.
- Marx, R.W. (1990) 'The TIGER system: Automating the geographic structure of the United States census', in D.J. Pequet and D.F. Marble (eds.) Introductory Readings in Geographic Information Systems, London: Taylor and Francis, 120–141.
- Pequet, D.J. (1984) 'A conceptual framework and comparison of spatial data models', Cartographica, 21: 66–113.

## Review Questions

1. Discuss the nature of spatial data.
2. What is the object view of geographical space? How does vector representation construct point, line and area features in the computer?
3. What is the field view of geographical space? How does raster representation represent geographical phenomena?
4. Why do all spatial data in a project have to be georeferenced?
5. What is map scale? What impact does map scale have on how we model geographical space using maps?
6. Discuss why spatial data cannot perfectly represent geographical features and what implications this has for users of spatial data.
7. What is a map projection? Describe the characteristics of the three families of map projection.
8. What are eastings and northings?
9. Describe the UTM zoning system.
10. What is a spatial data model? Outline the importance of spatial data models in GIS.
11. What are vector and raster data models? Discuss their advantages and disadvantages.
12. Discuss the main characteristics of the georelational and object-relational databases.

- Peucker, T.K. and Chrisman, N. (1975) ‘Cartographic data structure’, The American Cartographer, 2(1): 55–69.
- Robinson, A.H., Morrison, J.L., Muehrcke, P.C., Kimmerling, A.J. and Guptill, S.C. (1995) Elements of Cartography, Sixth Edition, New York: Wiley.
- Samet, H. (1990a) Applications of Spatial Data Structures: Computer Graphics, Image Processing and Geographical Information Systems. Reading, MA: Addison-Wesley.
- Samet, H. (1990b) Design and Analysis of Spatial Data Structures. Reading, MA: Addison-Wesley.
- Shekhar, S. and Chawla, S. (2003) Spatial Databases: A Tour, Upper Saddle River, NJ: Prentice Hall.
- Theobald, D.M. (2001) ‘Topology revisited: Representing spatial relations’, International Journal of Geographical Information Science, 15(8): 689–705.
- Torge, W. and Müller, J. (2012) Geodesy, 4th edition, Berlin: De Gruyter.
- Yeung, A.K.W. and Hall, G.B. (2007) Spatial Database Systems: Design, Implementation and Project Management, Dordrecht: Springer.

## See the Support Material

Practicals 2.1 and 2.2 worksheets (of both ArcGIS Pro and QGIS versions) are available in the Practicals section of the website.
The datasets for the two practicals are available in the Data section.
A quiz for Chapter 2 is available in the Quiz section to help you review the information and knowledge learned from the chapter.
