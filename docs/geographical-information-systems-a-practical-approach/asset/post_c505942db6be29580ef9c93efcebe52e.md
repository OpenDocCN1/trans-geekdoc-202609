

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_194_0.png)

| Elevation (m) |
| --- |
| 1,160 - 1,811.61 |
| 1,811.62 - 2,249.25 |
| 2,249.26 - 2,618.82 |
| 2,618.83 - 2,988.39 |
| 2,988.4 - 3,640 |

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_194_1.png)

| Hillshade Value |
| --- |
| High: 254 |
| Low: 0 |

Figure 4.7 2D surface maps: (a) hypsometric map and (b) hill-shaded map.

while a slope opposite to the light source appears dark. It provides a bird's-eye view of the terrain, as shown in Figure 2.2a

By tradition, hill-shaded maps are shaded as though they are illuminated from the north-west. In GIS, hill-shaded maps can be created by setting different sun altitudes and azimuths, simulating the sun's relative position at different times during a day or different seasons. The sun's altitude is the angle of the incoming light measured above the horizon. It ranges from 0° to 90°, with 0° indicating that the sun is on the horizon, and 90° indicating that the sun is directly overhead. The sun's azimuth is the direction of the incoming light relative to the north, ranging from 0 to 360° in a clockwise direction. An azimuth of 0° indicates north, east is 90°, south is 180° and west is 270°. Figure 4.7b shows a hill-shaded map produced with the sun's altitude as 45° and the sun's azimuth as 135°.

Hill shading adds to the visual quality of the map and makes the shape of terrain features more discernible. But by itself, it does not really add to the information provided by the map. It is particularly useful for depicting mountainous areas. Some maps combine hill shading and contour lines or hypsometric tinting to produce maps which are easy to interpret due to the hill shading and provide actual elevation information from the contour lines or elevation zoning. Hill shading also provides a useful background or base map for thematic mapping.

## 4.2 Map Design

As discussed in the previous section, maps symbolise geographical features according to their dimensionality (point, line, area or surface) and the level of measurement (qualitative or quantitative) of their attributes. What geographical features are to be presented, how they are to be classified, what symbols are to be used, how texts are to be placed and how cartographic elements are to be laid out are the major issues in map design. In general, map design involves selection, classification, symbolisation and layout design.

### 4.2.1 Selection

Map design depends on the purpose of the map. Once the purpose has been decided, the geographical area to be included on the map must be determined. This may be a city, a catchment, a region or the entire world. The larger the area covered, the greater the Earth's curvature involved in the map. Therefore, selection may involve making a choice of map projections, particularly for small-scale mapping over a large region or when detailed measurements need to be made from the map.

### Practical 4.3 See the Support Material

In this practical, you are going to learn how to make 2D surface maps in ArcGIS Pro or QGIS.

All projected maps are distorted in some way (see Section 2.2). A map projection should be chosen so that it does not distort the spatial pattern or to relegate the distortions away from the area of main interest on the map. Equal area or equivalent projections are generally best for thematic mapping of data distributions. For example, for correct interpretation of point patterns and densities, an equivalent projection is required. Equidistant map projections should be used when measuring distances from a point. Conformal projections are often used for large-scale reference maps and for maps showing routes or shapes, as they preserve angles rather than areas. Shape, size and location of the mapped area are also important determinants in making decisions about map projections. Table 2.2 provides some useful recommendations.

The most important task in the selection stage is cartographic abstraction and generalisation. Not all geographical features and their properties can be represented in a map. The selection process aims to identify what is relevant, given the purpose of the map, and select and organise information to help users interpret spatial patterns and processes. Section 2.1 discussed the principles and methods of cartographic abstraction and generalisation.

### 4.2.2 Classification

For most maps, it is necessary to classify data before mapping them. It is not usually practical to have a unique symbol for each data record for every feature, because the human eye only has a limited ability to discriminate a large number of different symbols or colour shades. **Data classification** is a means of generalising thematic maps. Generalisation helps make sense of complex data. Classification involves grouping similar features into classes to reduce complexity and organise data. It is mainly based on the attribute values associated with geographical features. Qualitative attribute data are often organised into classes (categories) and subclasses. For example, production from relatively natural environments is a class of land use. It can be divided into two subclasses: grazing natural vegetation and production forestry. Production forestry can be further divided into two subclasses: wood production and other forest production. When qualitative attribute values of geographical features are mapped, they are grouped into classes or subclasses. Each class or subclass is symbolised using a distinct colour or pattern.

Quantitative attribute data, describing counts, amounts, ratios or ranked values, are generally classified into a number of classes, each representing a range of numerical values. Many data classification methods exist. The classification methods most commonly available in GIS include equal interval, natural breaks, quantile and standard deviation.

#### 4.2.2.1 Equal Interval

This classification method divides the data into equal-sized ranges. For example, if features have values ranging from 0 to 1,000 and they are to be grouped into five classes, each class will have an interval of 200 and the five classes will be 0–200, 201–400, 401–600, 601–800 and 801–1,000. In general, the class interval is determined by dividing the whole range of all the data (the highest data value minus the lowest data value) by the number of classes. Figure 4.1 is a wealthy household map classified into six classes using the equal interval method, with a constant class interval of 300. It is reproduced in Figure 4.8a for comparison.

The equal interval method is easy to understand and most suitable for familiar data ranges, such as percentages. It is also useful for comparing the amount of a value with other values. For example, we can show that an agricultural production region is part of the group of agricultural production areas that made up the top one-fifth of the gross annual revenues of agricultural production. However, this classification method may create classes with unequal distribution of features and, in some cases, may produce classes containing no features. In the example shown in Figure 4.8a, the fifth class has no data (that is, no local government areas have a number of wealthy households within the range 1,201–1,500); therefore, it is not shown in the map.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_197_0.png)

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_197_1.png)

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_197_2.png)

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_197_3.png)

Figure 4.8 Data classification: (a) equal interval, (b) natural breaks, (c) quantile and (d) standard deviation.

#### 4.2.2.2 Natural Breaks

The natural breaks method is a variance-minimised (within classes) classification method. It is based on natural groupings of data values associated with geographical features. This method identifies natural breaks by identifying patterns inherent in the data. The data are divided into classes whose boundaries are set where there are relatively large changes in the data values so that the differences in data values between classes are maximised while the differences in data values in the same class are minimised. This method is carried out in GIS by using a specific algorithm, such as the Jenks algorithm (Jenks and Caspall 1971). The Jenks algorithm is based on minimising the sum of squared deviations of class members from the mean values. It starts with a random set of classes and adjusts the class boundaries to reduce the sum of squared deviations in each class in an iterative process (Slocum 2005). This method is used when natural breaks occur, but often, data are too scattered to provide clear breaks. It is generally good at revealing the patterns inherent in the data. However, class breaks are typically uneven, unusual and data-specific. Therefore, it is unsuitable for comparing maps based on different underlying information. Figure 4.8b shows the wealthy household map classified using the natural breaks method.

#### 4.2.2.3 Quantile

This method groups data so that each class contains an equal number of features. Each class is approximately equally represented on the map. It is well suited to linearly distributed data and very useful for ordinal data, as the class assignment of quantiles is based on ranked data. Class ranges are usually irregular, as features are grouped by the number in each class, as shown in Figure 4.8c. The method may produce a visually attractive but misleading map. This is because the classification may result in a situation where similar features are placed in adjacent classes, while features with widely different values are put in the same class. This distortion could be minimised by increasing the number of classes.

#### 4.2.2.4 Standard Deviation

This method classifies data according to their deviation from the mean of the data-set. It first calculates the mean value, then generates class breaks by successively adding or subtracting the standard deviation from the mean. Class intervals can be one standard deviation, 1/2 standard deviation, 1/3 standard deviation or 1/4 standard deviation. This often results in a central class defined as the mean value ± half a class interval. For example, if the class interval is one standard deviation, the central class will range from the mean minus 0.5 standard deviations to the mean plus 0.5 standard deviations, with additional classes at ± 1 standard deviation intervals beyond this central class. Figure 4.8d provides an example. This method is particularly useful when the purpose is to show deviation from the mean.

The maps shown in Figure 4.8 are classified using different data classification methods based on the same dataset. Obviously, different methods can lead to different representations of the same data, from which substantially different conclusions
