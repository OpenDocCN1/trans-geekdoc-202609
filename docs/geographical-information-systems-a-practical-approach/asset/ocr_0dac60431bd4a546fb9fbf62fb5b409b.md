Table 5.5 Mathematical operators and functions in map algebra

| Type | Operators/functions |
|---|---|
| Arithmetic | +, -, x, /, power, square root, exponential, logarithm |
| Logical | AND, OR, NOT |
| Relational | =, >, >=, <, <= |
| Conditional | IF ... THEN ..., IF ... THEN ... ELSE |
| Trigonometric | (Inverse) cosine, (inverse) sine, (inverse) tangent |
| Statistical | Maximum, minimum, mean, range, standard deviation, sum, median, mode, majority, minority, variety |

In this algebraic equation, outlayer is the variable representing the output raster; inlayer1, inlayer2, inlayer3 and inlayer4 are variables representing four input rasters; +, – and * are mathematical operators; log10() is a mathematical function and slope() is a raster data analysis function for calculating slope for each cell in the input raster. Both operators and functions manipulate data items and return a result. Functions differ from operators in that they operate on arguments. The right side of the equation is called a map algebra expression.

Mathematical operators and functions in map algebra perform mathematical computations. They mainly include arithmetic, logical, relational/comparison operators, conditional, trigonometric and statistical functions. Some of the basic operators and functions are listed in Table 5.5.

There are four common types of raster data analysis functions that can be used in map algebra: local, focal/neighbourhood, zonal and global functions. **Local functions** perform cell-by-cell analysis. They compute a new value for every cell in the output raster as a function of one or more existing values of the cell at the same location on a single or multiple input rasters. Raster data reclassification and raster overlay operations, discussed earlier, are all local functions. Raster overlay operates on multiple rasters. Reclassification and many mathematical functions listed in Table 5.5 (such as power, logarithmic and trigonometric functions) operate on a single raster. Practical 5.11 provides some examples of local functions in ArcGIS Pro and QGIS.

**Focal functions** calculate a new value for every cell in the output raster as a function of the existing values, distances and/or directions of the cells in its neighbourhood on the input raster. The cell being processed currently is called the **focal cell**. The neighbourhood can be defined

> **Practical 5.11 See the Support Material**
> 
> In this practical, you are going to learn some local functions in ArcGIS Pro or QGIS.