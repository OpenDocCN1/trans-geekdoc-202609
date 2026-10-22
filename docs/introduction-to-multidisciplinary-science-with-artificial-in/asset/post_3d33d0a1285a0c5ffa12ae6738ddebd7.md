
Legendre functions (see Ikelle, 2020), we obtain $A_l^{m,o}$. In theory an infinite series is necessary to fully characterize the gravitational field, but practically the double sum is truncated to a maximum of about $n$ between 100 and 200.

## Gravitational gradiometry principle.

In addition (or as an alternative) to measuring the gravity vector from one accelerometer, we can measure the gradiometry tensor (or gradiometry matrix), which is defined as follows (e.g., Baur and Grafarend, 2006):

$\mathbf{\Gamma} = \begin{pmatrix} \frac{\partial g_x}{\partial x} & \frac{\partial g_x}{\partial y} & \frac{\partial g_x}{\partial z} \\ \frac{\partial g_y}{\partial x} & \frac{\partial g_y}{\partial y} & \frac{\partial g_y}{\partial z} \\ \frac{\partial g_z}{\partial x} & \frac{\partial g_z}{\partial y} & \frac{\partial g_z}{\partial z} \end{pmatrix} = - \begin{pmatrix} \frac{\partial^2 U}{\partial x^2} & \frac{\partial^2 U}{\partial y \partial x} & \frac{\partial^2 U}{\partial z \partial x} \\ \frac{\partial^2 U}{\partial x \partial y} & \frac{\partial^2 U}{\partial y^2} & \frac{\partial^2 U}{\partial z \partial y} \\ \frac{\partial^2 U}{\partial x \partial z} & \frac{\partial^2 U}{\partial y \partial z} & \frac{\partial^2 U}{\partial z^2} \end{pmatrix}, \tag{1.94}$

from an array of accelerometers, especially when taking measurements using satellites or airplanes. This tensor is a symmetric tensor because the order of differentiation of a scalar quantity is irrelevant and it has only five independent components because the sum of the diagonal components is zero (Laplace's equation in free space); i.e.,

$\nabla^2 U(\mathbf{x}) = \frac{\partial^2 U}{\partial x^2} + \frac{\partial^2 U}{\partial y^2} + \frac{\partial^2 U}{\partial z^2} = - \left( \frac{\partial g_x}{\partial x} + \frac{\partial g_y}{\partial y} + \frac{\partial g_z}{\partial z} \right) = 0.$

These five components can, for example, be $(\partial g_x/\partial x, \partial g_x/\partial y, \partial g_x/\partial z, \partial g_z/\partial y, \partial g_z/\partial z)$. The practical implementation of the gradiometry tensor consists of taking differences of the accelerometers as follows:

$\Gamma_{jk} = \frac{g_j(x_k + \Delta x_k) - g_j(x_k)}{\Delta x_k}, \tag{1.95}$

where $j,k \in \{x_1,x_2,x_3\} = \{x,y,z\}$ and $\Delta x_k$ is the short distance between accelerometers in the $x_k$-direction. By measuring higher derivatives of gravity, small scale features can be accurately determined.

## Geoid.³

³Representing the shape of the Earth with all the variation of its complex surface topography (e.g. mountains and valleys) would be an impossible task. An entire branch of science, called geodesy, is dedicated to the study of the shape and size of the Earth. Geodesists have defined two main models or reference surfaces, namely geoid and ellipsoid, to approximate the Earth's shape.

There is an infinite number of equipotential surfaces and a particular equipotential surface of the Earth known as geoid. It coincides with the mean sea level (ignoring tides and other dynamical effects in oceans); that is, the geoid is the equipotential surface that best fits the mean sea level. Geoid would be the Earth's surface if the oceans were to flow freely and cover the entire solid Earth's surface (in the absence of winds, tides and currents). The surface of the oceans would align with the surface of the geoid, so the geoid is a theoretical shape of the Earth. The choice of mean sea level is totally arbitrary but it makes sense because the surface of a fluid in equilibrium must follow an equipotential surface. So over the oceans, the geoid is the ocean surface. Over the continents, the geoid is not the topographic surface (its location can be calculated from gravity measurements). The geoid is recorded by satellites that use radar technology to measure the elevation of the sea surface. As illustrated in Figure 1.19, the geoid is fatter at the equator and thinner at the Poles. Remember that the geoid is an equipotential surface therefore it must remain perpendicular to the direction of the gravity field. The bumps and hollows of geoid inform us of the submarine topography and the composition of the subsurface.

![](img/f5b5b8709fc3a81631262f22d3552c5e_59_0.png)

The reference ellipsoid is another (theoretical) shape of the Earth. It is the ellipsoid that most closely fits the geoid. It can be shown (Clairaut and Colson, 1739; and Blakely, 1995) that the (theoretical) value of gravity on this reference ellipsoid is:

g(θ) = g_eq (1 + k sin²θ) / sqrt(1 - e² sin²θ)
≈ g_eq (1 + k sin²θ) (1 + ½ e² sin²θ + ⅜ e⁴ sin⁴θ)
= g_eq (1 + k1 sin²θ + k2 sin⁴θ)
= g_eq [1 + (k1 + k2) sin²θ - k2/4 sin²(2θ)] , (1.96)

where θ is the latitude, g_eq is the gravity at the equator, e² = (a² - b²)/a² (a is the semi-major axis and b is the semi-minor axis) is the eccentricity of the ellipsoid, k = (b g_pole - a g_eq)/(a g_eq) is a constant that depends on the shape and the rotation of the Earth, and g_pole is the gravity at the poles. The other two parameters in the last equality are related to k and e as follows: k₁ = k + ½ e² and k₂ = ½ k e² + ⅜ e⁴. The typical values of g_eq, k, and e are g_eq = 978031.846 mGal, k = 0.001931851, and e² = 0.006694379 and we can deduce k₁ = 0.005278895 and k₂ = 0.000023462. These values are more accurately determined by the increasing amounts of satellite data. We used Taylor’s expansion in (1.96) and limited the calculations to the third term of the Taylor’s series to obtain the final equality. So if the Earth were a homogeneous ellipsoid, the value of gravity at the Earth’s surface would be given by (1.96).

> Quiz: What is the farthest location on the Earth’s surface from the center of the Earth?

Geoids are used in oceanography to determine (mean) sea surface topography. In polar regions where oceans are partly covered by sea ice, icebergs, or ice shelves, the geoid also provides a link between the surface ellipsoidal height and the freeboard height, which in turn, can be used to infer the thickness of the floating ice, including Antarctic subglacial lakes (Ewert et al., 2012). In geophysics, analysis of gravitational anomalies yields insight into the thicknesses of the lithosphere and into the tectonic and geodynamic processes that shape the continents and surrounding oceans.

Again, note that we cannot directly see the geoid surface and reference ellipsoid; therefore, we cannot actually measure the heights above or below the geoid surface. We must infer where the geoid surface is by making gravity measurements and where the reference ellipsoid is by modeling it mathematically or numerically.

Geoid undulations are differences, in meters, between the geoid and the reference ellipsoid. Geoid undulations are also known as geoid height anomalies. They are caused by the distribution of mass in the solid Earth, the topography of the seafloor and the Earth’s surface, and mantle processes. They are generally denoted by N which is the ellipsoidal height with respect to the geoid (see Figure 1.20). In absolute values, N, is less than 100 m always everywhere—that is, about 10^{-5} × r_e, where r_e is the Earth radius. A map of global geoid height anomalies is shown in Figure 1.21. The width of the geoid height anomalies indicates the depth of the density anomalies that cause them. When underground density anomalies are near the surface, the geoid height anomalies are narrow. When density anomalies are very deep, the geoid height anomalies are very broad, sometimes thousands of kilometers across. These large-scale geoid height anomalies are a result of the large upwellings (light color) and downwellings (dark color) of mantle convection, which we will discuss in later chapters. As illustrated in Figure 1.21, there are significant geoid height anomalies over the ocean due to bathymetry (i.e., the topography of the ocean floor). For example, over the oceans, there are seamounts, which lead to water being replaced by rock. The rock increases the gravitational pull in that area and consequently changes the
