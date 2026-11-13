![](bbox=[0.219, 0.083, 0.814, 0.396])

Figure 6.5 Standard deviational ellipse.

Accordingly, the minimum standard deviation is calculated as:

$$\sigma_{min} = \sqrt{\frac{\sum_{i=1}^{n} \left( -x_i \sin(\theta + 90) + y_i \cos(\theta + 90) \right)^2}{n}}$$  
$$= \sqrt{\frac{\sum_{i=1}^{n} \left( -x_i \cos(\theta) + y_i \sin(\theta) \right)^2}{n}} \quad (6.11)$$

The standard deviational ellipse is defined by \(\sigma_{max}\) as the semi-major axis, \(\sigma_{min}\) as the semi-minor axis and \(\theta\) as the orientation of the major axis. For the full mathematical description, refer to Yuill (1971).

The standard deviational ellipse provides information about the dispersion of features and the orientation and core area of their distribution. For example, Figure 6.6 shows the dispersion patterns of

peasant observations in three different areas created in ArcGIS. It can be seen that the three ellipses are small compared with the entire area of the catchment. Obviously, peasant distributions are clustered, not widely distributed. Using some GIS measurement tools and spatial query functions, we can calculate the area and count of data points in each ellipse, then compute the densities of data points inside the ellipses. In this example, the density of peasant sightings for each ellipse is calculated. The ellipse in Area 1 has a density of 13.53 sightings/km\(^2\), the ellipse in Area 2 has a density of 16.88 sightings/km\(^2\) and the density for the ellipse in Area 3 is 9.14 sightings/km\(^2\). Therefore, peasants are more concentrated in Area 2. In addition, the orientations of these ellipses indicate that the distributions of peasant in the catchment are largely affected by the river courses.