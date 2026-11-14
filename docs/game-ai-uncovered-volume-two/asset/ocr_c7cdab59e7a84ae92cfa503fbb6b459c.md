check was done to determine if the spline intersected the circle (Image 23.5). Finding the closest point on a spline (or Bezier curve) is non-trivial, iterative and involves complex maths, so instead, the generated cubic Bezier curve was converted into a series of points along the curve, and each individual point was tested against the circle. Calculating the points was required for converting the Bezier curve to the Catmull-Rom spline, so if no intersection was found then the converted spline could then be used for the path following.

![](bbox=[0.112, 0.23, 0.85, 0.4])

IMAGE 23.5 The initially generated spline (P_car to P_target) intersects the circle (centre C, radius r). The entry and exit intersection points are P_i1 and P_i2.

However, what if an intersection had been found? In this case, you want to push the spline so that it is outside of the circle, so the entry and exit intersection points need to be found. Using the first and last points that were found inside the circle from the simple circle point test, a proper line-segment circle calculation can be done to calculate a more accurate intersection point on the circle’s edge. Once the two intersection points are found, you can calculate the new point that you want the spline to pass through. This new point (M) is the midpoint between the two intersection points. As shown in Image 23.6, the new point (P_new) is along the vector from the circle centre (C) through the Midpoint (M) with a distance of circle radius (r) and buffer distance (b) from the centre.

![](bbox=[0.112, 0.65, 0.85, 0.86])

IMAGE 23.6 The two new curves created that no longer intersect the obstacle. M is the midpoint between the two intersection points, and b is the buffer distance that you want to move the new point to (outside the obstacle).