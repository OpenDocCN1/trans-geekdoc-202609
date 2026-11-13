
![](img/8aad3fa01ca9db86bd50bb2edb9a3134_258_0.png)

### Figure 5.3 Buffers.

The buffer width is a user-specified distance. For neighbouring or connected features, their buffers tend to overlap, as shown in Figure 5.3. Usually, the boundaries of overlapping buffers are dissolved so that a single coherent zone is created around the features. Buffers may be generated with a fixed width or variable widths according to the types or attributes of features. In the example shown in Figure 5.4, buffers of 500 m were drawn around roads, and buffers of 200 m around tracks. When working in a projected coordinate system, Euclidean buffers are produced, which measure straight-line distance in a two-dimensional Cartesian plane. When working in a geographical coordinate system, geodesic buffers are created, which accounts for the actual shape of the Earth. Some GIS systems, such as ArcGIS, allow users to produce either Euclidean or geodesic buffers. Buffering has a wide range of applications – for example, defining riparian zones to protect riparian vegetation or creating buffers around a power station to assess environmental and social impacts.

## 5.3.3 Distance Surface

Distance measurement in raster calculates the shortest distances from the location(s) representing the source(s) or origin(s) to every other location and creates a **distance surface** in raster, which shows a series of concentric rings of equal distance around the source location(s), as shown in Figure 5.5. Distance in raster may be measured based on absolute physical distance between places, or costs incurred while traversing the physical distance. The distance measured by taking into account costs is called **cost distance** or **weighted distance**. Here, the cost can be travel time, energy consumption or other costs or the sum of them, which may be affected by topography, such as slope, land cover and other factors. For example, the cost for constructing a highway may include construction costs, land costs and potential costs of environmental and social impacts.

Cost distance is measured as a function of physical distance and costs. Typically, a cost distance measurement tool in GIS uses a source raster layer representing the source locations and a cost raster layer with the same resolution containing the costs associated with each cell to calculate an accumulated cost surface. The value associated with each cell on the cost layer represents the cost per unit distance for moving through the cell. For example, if a cost layer represents travel time, which is in minutes, a cost value will be minutes per metre. Suppose the cost layer has a cell resolution of 50 m and a particular cell has a cost value of 0.01 minutes per metre: the time for travelling through the cell is 0.01 x 50 = 0.5 minutes. That is, the total cost per cell is the cost value times the cell resolution. Cost is calculated from cell centre to cell centre. Therefore, the cost to move from one cell to its adjacent cell in the cardinal directions is the sum of the cost of each multiplied by half the cell size. If the movement is diagonal, the cost is increased by multiplying the cell size by 1.414. Using the cost layer, cost distance is calculated by totalling the cost while traversing each cell from the source, assigning a least accumulative cost of getting back to the source locations to each cell in a new layer it creates. A number of algorithms have been developed for calculating cost distance, for example, the spreading algorithm (Douglas 1994) and the pushbroom algorithm (Eastman 1989). Figure 5.6 illustrates the spreading algorithm.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_259_0.png)

### Figure 5.4 Variable buffers.

## Practical 5.5 See the Support Material

In this practical, you are going to learn how to generate buffers in ArcGIS Pro or QGIS.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_260_0.png)
![](img/8aad3fa01ca9db86bd50bb2edb9a3134_260_1.png)

### Figure 5.5 Distance surfaces: (a) physical distance and (b) cost distance.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_261_0.png)

### Figure 5.6 Cost distance calculation.

Let \( R_{ij} \) be the cell at row \( i \) and column \( j \), \( c_{ij} \) be the accumulative cost value of \( R_{ij} \) and \( A \) be the accumulative cost cell list.

(except \( R_{i,1} \) and \( R_{i,4} \)) from \( R_{i,2} \) and \( R_{i,3} \) like so:

- 1 Assign 0 to the cells representing the source locations (labelled 1 and 2 in the source layer), as there is no accumulative cost to return to them, and then calculate the accumulative costs of their adjacent cells like so:

\( c_{i,2} = 0 + (1 + 2) / 2 = 1.5 \)  
\( c_{2,1} = 0 + (1 + 3) / 2 = 2 \)  
\( c_{2,2} = 0 + [(1 + 5) / 2] \times 1.414 = 4.24 \)

\( c_{i,3} = c_{i,2} + (2 + 4) / 2 = 1.5 + 3 = 4.5 \)  
\( c_{2,1} = c_{i,2} + [(2 + 3) / 2] \times 1.414 = 1.5 + 3.535 = 5.04 \)  
\( c_{2,2} = c_{i,2} + (2 + 5) / 2 = 5 \)  
\( c_{2,3} = c_{i,2} + [(2 + 3) / 2] \times 1.414 = 5.04 \)

Similarly, calculate \( c_{3,3} \), \( c_{3,4} \) and \( c_{4,3} \). Add all the accumulative cost values to \( A = \{(R_{i,2}, 1.5), (R_{2,1}, 2), (R_{2,2}, 4.24), (R_{3,3}, 4.95), (R_{3,4}, 3.5), (R_{4,3}, 1.5)\} \).

Similarly, calculate \( c_{3,2} \), \( c_{3,3} \), \( c_{3,4} \) and \( c_{4,2} \). Delete \( (R_{i,2}, 1.5) \) and \( (R_{4,3}, 1.5) \) from \( A \), and add all the newly calculated accumulative cost values to \( A \). If the new accumulative cost for a cell in \( A \) is equal to or greater than the value the cell currently has, the value is ignored; otherwise, the old accumulative cost value for the cell is replaced in \( A \) with the new value. So \( c_{2,1} \), \( c_{2,2} \), \( c_{3,3} \) and \( c_{3,4} \) are not updated. Now, \( A = \{(R_{i,1}, 4.5), (R_{2,1}, 2), (R_{2,2}, 4.2), (R_{2,3}, 5.04), (R_{3,2}, 7.86), (R_{3,3}, 4.95), (R_{3,4}, 3.5), (R_{4,2}, 4)\} \).

- 2 Select the lowest-cost cells from \( A \), which are \( R_{i,2} \) and \( R_{4,3} \), and assign the cost values to the cells in the output layer. Calculate the accumulative costs to move into the neighbouring cells

- 3 Select the lowest-cost cell from \( A \), which is \( R_{2,1} \), and assign its cost value to the output layer. In a similar way, calculate the accumulative costs to move into the neighbouring cells from \(R_{2,1}\). Delete \((R_{2,1}, 2)\) from \(A\), and update \(A\). Now, \(A = \{(R_{1,1}, 4.5), (R_{2,2}, 4.2), (R_{2,3}, 5.04), (R_{3,3}, 5.5), (R_{3,2}, 7.86), (R_{3,3}, 4.95), (R_{3,4}, 3.5), (R_{4,4}, 4)\}\).

- 4 Select the lowest-cost cell from \(A\), which is \(R_{3,4}\) and assign its cost value to the output layer. Calculate the accumulative costs to move into the neighbouring cells from \(R_{3,4}\). Delete \((R_{3,4}, 3.5)\) from \(A\), and update \(A\). Now, \(A = \{(R_{1,1}, 4.5), (R_{2,2}, 4.2), (R_{2,3}, 5.04), (R_{2,4}, 9.5), (R_{3,1}, 5.5), (R_{3,2}, 7.86), (R_{3,3}, 4.95), (R_{4,4}, 4)\}\).

- 5 Select the lowest-cost cell from \(A\), which is \(R_{4,2}\) and assign its cost value to the output layer. Calculate the accumulative costs to move into the neighbouring cells from \(R_{4,2}\). Delete \((R_{4,2}, 4)\) from \(A\), and update \(A\). Now, \(A = \{(R_{1,1}, 4.5), (R_{2,2}, 4.2), (R_{2,3}, 5.04), (R_{2,4}, 9.5), (R_{3,1}, 5.5), (R_{3,2}, 7.86), (R_{3,3}, 4.95), (R_{4,4}, 9.5)\}\).

- 6 Select the lowest-cost cell from \(A\), which is \(R_{2,2}\) and assign its cost value to the output layer. Calculate the accumulative costs to move into the neighbouring cells from \(R_{2,2}\). Delete \((R_{2,2}, 4.2)\) from \(A\), and update \(A\). Now, \(A = \{(R_{1,1}, 4.5), (R_{2,3}, 5.04), (R_{2,4}, 9.5), (R_{3,1}, 5.5), (R_{3,2}, 7.86), (R_{3,3}, 4.95), (R_{3,4}, 9.5)\}\).

- 7 Select the lowest-cost cell from \(A\), which is \(R_{1,3}\) and assign its cost value to the output layer. Calculate the accumulative costs to move into the neighbouring cells from \(R_{1,3}\). Delete \((R_{1,3}, 4.5)\) from \(A\), and update \(A\). Now, \(A = \{(R_{2,3}, 5.04), (R_{2,4}, 9.5), (R_{3,1}, 5.5), (R_{3,2}, 7.86), (R_{3,3}, 4.95), (R_{4,4}, 9.5)\}\).

- 8 The process continues to select the lowest-cost cell from \(A\), assign the lowest-cost value to the output layer and update \(A\) until \(A\) becomes empty or the maximum distance is reached.

## 5.3.4 Least-Cost Path

Cost distance provides a basis for determining the least-cost path from a destination to a source location. As discussed earlier, a cell value on a cost distance surface represents the least accumulative cost of returning to the source locations from the cell. Based on the least accumulative cost values, the neighbour that is the next cell on the least accumulative cost path to the nearest source, also known as a backlink, can be tracked. A cost distance function in GIS typically outputs a cost distance surface as well as a direction or backlink raster that records the sequence of movements that

## Practical 5.6 See the Support Material

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_262_0.png)

In this practical, you are going to learn how to produce distance surfaces in ArcGIS Pro or QGIS.
