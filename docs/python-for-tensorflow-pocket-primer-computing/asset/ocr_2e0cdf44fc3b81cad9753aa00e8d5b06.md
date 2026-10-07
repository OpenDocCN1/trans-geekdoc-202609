observations, which is needed to calculate the median on a sample with an even number of values. As you can surmise, the NumPy functions min() and max() calculate the smallest and largest values in the data sample. The output from launching Listing 2.19 is here:

```
Minimum: 0.000
Q1 value: 0.237
Median: 0.500
Mean Val: 0.495
Std Dev: 0.295
Q3 value: 0.747
Maximum: 0.999
```

Chapter 4 contains more detailed information about matplotlib in order to plot various charts and graphs. However, the Python code samples in the next several sections contain some rudimentary APIs of matplotlib. The code samples start with simple examples of line segments, followed by an introduction to Linear Regression.

# WORKING WITH LINES IN THE PLANE (OPTIONAL)

This section contains a short review of lines in the Euclidean plane, so you can skip this section if you are comfortable with this topic. A minor point that is often overlooked is that lines in the Euclidean plane have infinite length. If you select two distinct points of a line, then all the points between those two selected points is a line segment. A ray is a “half infinite” line; when you select one point as an endpoint, then all the points on one side of the line constitute a ray.

For example, the points in the plane whose y-coordinate is 0 is a line and also the points (0,0) and (1,0) on the x-axis form a line segment. In addition, the points on the x-axis that are to the right of (0,0) form a ray, and the points on the x-axis that are to the left of (0,0) also form a ray.