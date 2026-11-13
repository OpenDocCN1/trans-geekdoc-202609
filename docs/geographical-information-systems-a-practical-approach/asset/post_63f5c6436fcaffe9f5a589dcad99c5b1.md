
![](img/8aad3fa01ca9db86bd50bb2edb9a3134_254_0.png)

Figure 5.1 Reclassification in vector.

## Practical 5.3 See the Support Material

In this practical, you are going to learn how to implement the reclassification operation in ArcGIS Pro or QGIS.

are useful parameters for characterising geographical phenomena and their spatial patterns. For example, landscape metrics, which are used to quantify the spatial configuration of landscape and investigate the interaction between spatial pattern and ecological process, are calculated based on geometric properties of landscape units and distances, such as patch size, edge diversity, contiguity, shape complexity, proximity and connectivity (Turner et al. 2001; see also Case Study 9 in Chapter 10). Geometric properties and distances are usually not encoded during spatial data input. GIS offers measurement functions to calculate them.

## 5.3.1 Geometric Measurement

### 5.3.1.1 Length

Spatial data are provided either in a projected coordinate system or in a geographical coordinate system. Length and area are calculated differently in the two types of geo-referencing systems.

In a projected coordinate system, the length of the shortest line between two points is a straight-line distance, calculated based on the Pythagorean theorem:

\( D = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2} \quad (5.1) \)

where \((x_1, y_1)\) and \((x_2, y_2)\) are the coordinates of the two points. It is called **Euclidean distance**.

In a geographical coordinate system, the length of the shortest line between two points is measured as the **great circle distance**. A great circle is a circle on the spherical surface of the Earth whose centre coincides with the centre of the Earth. The two points separate the great circle into two arcs. The length of the shorter arc is the great circle distance between the points, also called a **geodesic**. This distance is not straight-line distance but spherical distance, calculated as:

\( D_{geodesic} = r \cos^{-1}[\sin \varphi_1 \sin \varphi_2 + \cos \varphi_1 \cos \varphi_2 (\lambda_1 - \lambda_2)] \quad (5.2) \)

where \((\varphi_1, \lambda_1)\) and \((\varphi_2, \lambda_2)\) are latitude and longitude coordinates of two points, and \(r\) is the radius of the Earth. Some GIS systems can select an appropriate equation to calculate length or distance according to the projection applied. For example, in ArcGIS, planar is the default when working in a projected coordinate system, while geodesic is the default when working in a geographical coordinate system. Some systems provide options for users to specify which type of measurement is going to be made. It will produce wrong results when using geographical coordinates to calculate Euclidean distances. It will be equally wrong when using Cartesian coordinates to calculate geodesics.

In vector, the length of a line feature is simply the sum of the lengths of each straight-line segment measured using one of the distance equations, as the line feature is represented as a polyline (see Figure 2.14). It should be noted that the length of a line feature calculated in GIS is almost always shorter than its true length, as the real smoothly curved shape of the feature is replaced by straight-line segments.

Measuring the length of a line feature in raster involves calculating the number of grid cells representing the line and multiplying by the cell resolution. However, the length of a line segment on the diagonal is measured as the number of cells forming the line times the cell resolution times 1.414 (= \(\sqrt{1^2 + 1^2}\)), as shown in Figure 5.2.

### 5.3.1.2 Perimeter and Area

In vector, area features are represented as polygons. The perimeter of a polygon is the sum of the lengths of the line segments forming the polygon. The area of a polygon is calculated by summing the areas of a number of trapeziums formed by drawing perpendiculars to the x-axis (Longley et al. 2011, p. 382), which can be mathematically expressed as:

\( A = \frac{1}{2} \left| \sum_{i=1}^n (x_{i+1} - x_i)(y_{i+1} + y_i) \right| \quad (5.3) \)

where \(n\) is the number of vertices of the polygon, and \((x_1, y_1), (x_2, y_2), \dots, (x_n, y_n), (x_{n+1}, y_{n+1})\) are the coordinates of the \(n\) vertices, with \(x_{n+1} = x_1\) and \(y_{n+1} = y_1\). They are coordinates in a projected coordinate system. Most GIS systems do not provide a measurement function to calculate areas in geographic coordinates.

resolution (Bogaert et al. 2000). Figure 5.2 provides an example.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_256_0.png)

The length of line AB
= 8 cells × (50m / cell)
= 400m

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_256_1.png)

The length of line CD
= 8 cells × (50m × 1.414 / cell)
= 565.6m

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_256_2.png)

The area of polygon E
= 21 cells × (50m × 50m / cell) =
52500m²

The perimeter of E
= (4 × 21 cells – 2 × 30 sides) × 50m
= 1200m

Figure 5.2 Measuring length, perimeter and area in raster (the cell resolution is 50 m).

In raster, area features are represented as groups of contiguous grid cells with a common attribute value. The area of an area feature is simply calculated as the number of cells it is composed of times the cell resolution. The perimeter of an area is computed as:

\( P = (4n_a - 2n_i)r \quad (5.4) \)

where \(n_a\) is the total number of cells the area is composed of, \(n_i\) is the number of shared cell sides in the area and \(r\) is the cell resolution

### 5.3.1.3 Shape

Shape describes the geometric form of individual features. It is considered a critical factor in defining and analysing habitat regions, assessing species richness, studying the effects of urban growth, determining the impact of deforestation, measuring the parameters of drainage basins and examining the patterns of geological formations (Wentz 2000). There are numerous measures that have been developed for describing and representing shapes. Wentz (2000)

**Practical 5.4 See the Support Material**

In this practical, you are going to learn how to measure length and area in ArcGIS Pro or QGIS.

groups these measures into four categories: compactness, boundary, form and multiple-parameter measures.

Compactness measures quantify how far a feature deviates from a standard shape, which is the most compact. A standard shape is usually a circle or square. An example of the shape compactness measure is given as:

\( SI_c = \begin{cases} \frac{P}{2\sqrt{\pi A}} \quad \text{for vector data} \\ \frac{P}{4\sqrt{\pi A}} \quad \text{for raster data} \end{cases} \)

where P is the perimeter and A is the area of the feature (Bogaert et al. 2000). When the feature is a circle (in vector) or a square (in raster), SI_c = 1. For shapes different from the standard shape, SI_c > 1. Higher values mean greater departure from the standard shape and less compactness.

Boundary measures quantitatively describe the roughness or the smoothness of a feature's outer edge. A more uneven boundary has more edges. A boundary measure is an indicator of shape complexity. A useful boundary measure is the fractal dimension of an area, expressed as follows (Moser et al. 2002):

\( SI_f = \frac{2 \ln P}{\ln A} \quad (5.7) \)

SI_f is 1 for shapes with very simple edges, such as circles and squares, and approaches 2 when shapes become more complex.

Form measures quantify the overall geometric configuration of a feature by comparing it to a standard shape, such as a circle. One example is the Boyce-Clark Index (Boyce and Clark 1964), which

involves drawing a set of equally spaced radials from a reference point within a shape to its perimeter. For example, for a circle with the centre as the reference point, all radials would be of equal length. Its mathematical form is:

\( \left| \sum_{i=1}^n \left| \frac{r_i}{\sum_{k=1}^n r_k} \times 100 - \frac{100}{n} \right| \right| \quad (5.8) \)

where r_i is the length of radial i from a reference point, and n is the number of radials.

Multiple-parameter measures combine measurements of several shape properties, such as compactness, jaggedness, elongation and fragmentation, and involve multivariate analysis. Most of the shape measures are based on length, perimeter and area. Although shape measures are not readily implemented in GIS, they can be calculated by using the basic geometric measurement and attribute calculation functions.

## 5.3.2 Buffering

Buffering is a distance measurement tool for vector data commonly available in GIS. It creates a zone around a feature or a set of features with a specific width. This zone is called a buffer. As shown in Figure 5.3, a buffer around a point feature is a circle with the buffer width as its radius, a buffer around a line feature is a band with a specific distance (buffer width) on both sides of the line conforming to its curve and a buffer around an area feature is a zone of a specific distance from the edge of the area conforming to its shape. Any point in a buffer around a feature is within the distance of the buffer width from the feature.
