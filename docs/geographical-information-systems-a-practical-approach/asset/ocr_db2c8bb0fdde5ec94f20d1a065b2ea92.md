to the output layer. In a similar way, calculate the accumulative costs to move into the neighbouring cells from \(R_{2,1}\). Delete \((R_{2,1}, 2)\) from \(A\), and update \(A\). Now, \(A = \{(R_{1,1}, 4.5), (R_{2,2}, 4.2), (R_{2,3}, 5.04), (R_{3,3}, 5.5), (R_{3,2}, 7.86), (R_{3,3}, 4.95), (R_{3,4}, 3.5), (R_{4,4}, 4)\}\).

+   4 Select the lowest-cost cell from \(A\), which is \(R_{3,4}\) and assign its cost value to the output layer. Calculate the accumulative costs to move into the neighbouring cells from \(R_{3,4}\). Delete \((R_{3,4}, 3.5)\) from \(A\), and update \(A\). Now, \(A = \{(R_{1,1}, 4.5), (R_{2,2}, 4.2), (R_{2,3}, 5.04), (R_{2,4}, 9.5), (R_{3,1}, 5.5), (R_{3,2}, 7.86), (R_{3,3}, 4.95), (R_{4,4}, 4)\}\).

+   5 Select the lowest-cost cell from \(A\), which is \(R_{4,2}\) and assign its cost value to the output layer. Calculate the accumulative costs to move into the neighbouring cells from \(R_{4,2}\). Delete \((R_{4,2}, 4)\) from \(A\), and update \(A\). Now, \(A = \{(R_{1,1}, 4.5), (R_{2,2}, 4.2), (R_{2,3}, 5.04), (R_{2,4}, 9.5), (R_{3,1}, 5.5), (R_{3,2}, 7.86), (R_{3,3}, 4.95), (R_{4,4}, 9.5)\}\).

+   6 Select the lowest-cost cell from \(A\), which is \(R_{2,2}\) and assign its cost value to the output layer. Calculate the accumulative costs to move into the neighbouring cells from \(R_{2,2}\). Delete \((R_{2,2}, 4.2)\) from \(A\), and update \(A\). Now, \(A = \{(R_{1,1}, 4.5), (R_{2,3}, 5.04), (R_{2,4}, 9.5),\)

+   \((R_{3,1}, 5.5), (R_{3,2}, 7.86), (R_{3,3}, 4.95), (R_{3,4}, 9.5)\}\).

+   7 Select the lowest-cost cell from \(A\), which is \(R_{1,3}\) and assign its cost value to the output layer. Calculate the accumulative costs to move into the neighbouring cells from \(R_{1,3}\). Delete \((R_{1,3}, 4.5)\) from \(A\), and update \(A\). Now, \(A = \{(R_{2,3}, 5.04), (R_{2,4}, 9.5), (R_{3,1}, 5.5), (R_{3,2}, 7.86), (R_{3,3}, 4.95), (R_{4,4}, 9.5)\}\).

+   8 The process continues to select the lowest-cost cell from \(A\), assign the lowest-cost value to the output layer and update \(A\) until \(A\) becomes empty or the maximum distance is reached.

# 5.3.4 Least-Cost Path

Cost distance provides a basis for determining the least-cost path from a destination to a source location. As discussed earlier, a cell value on a cost distance surface represents the least accumulative cost of returning to the source locations from the cell. Based on the least accumulative cost values, the neighbour that is the next cell on the least accumulative cost path to the nearest source, also known as a backlink, can be tracked. A cost distance function in GIS typically outputs a cost distance surface as well as a direction or backlink raster that records the sequence of movements that

# Practical 5.6 See the Support Material

![](bbox=[0.8, 0.75, 0.9, 0.8])

In this practical, you are going to learn how to produce distance surfaces in ArcGIS Pro or QGIS.