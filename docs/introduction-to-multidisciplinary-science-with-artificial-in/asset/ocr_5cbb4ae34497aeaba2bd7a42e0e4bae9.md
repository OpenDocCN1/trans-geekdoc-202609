Legendre functions (see Ikelle, 2020), we obtain $A_l^{m,o}$. In theory an infinite series is necessary to fully characterize the gravitational field, but practically the double sum is truncated to a maximum of about $n$ between 100 and 200.

# Gravitational gradiometry principle.

In addition (or as an alternative) to measuring the gravity vector from one accelerometer, we can measure the gradiometry tensor (or gradiometry matrix), which is defined as follows (e.g., Baur and Grafarend, 2006):

$\mathbf{\Gamma} = \begin{pmatrix} \frac{\partial g_x}{\partial x} & \frac{\partial g_x}{\partial y} & \frac{\partial g_x}{\partial z} \\ \frac{\partial g_y}{\partial x} & \frac{\partial g_y}{\partial y} & \frac{\partial g_y}{\partial z} \\ \frac{\partial g_z}{\partial x} & \frac{\partial g_z}{\partial y} & \frac{\partial g_z}{\partial z} \end{pmatrix} = - \begin{pmatrix} \frac{\partial^2 U}{\partial x^2} & \frac{\partial^2 U}{\partial y \partial x} & \frac{\partial^2 U}{\partial z \partial x} \\ \frac{\partial^2 U}{\partial x \partial y} & \frac{\partial^2 U}{\partial y^2} & \frac{\partial^2 U}{\partial z \partial y} \\ \frac{\partial^2 U}{\partial x \partial z} & \frac{\partial^2 U}{\partial y \partial z} & \frac{\partial^2 U}{\partial z^2} \end{pmatrix}, \tag{1.94}$

from an array of accelerometers, especially when taking measurements using satellites or airplanes. This tensor is a symmetric tensor because the order of differentiation of a scalar quantity is irrelevant and it has only five independent components because the sum of the diagonal components is zero (Laplace's equation in free space); i.e.,

$\nabla^2 U(\mathbf{x}) = \frac{\partial^2 U}{\partial x^2} + \frac{\partial^2 U}{\partial y^2} + \frac{\partial^2 U}{\partial z^2} = - \left( \frac{\partial g_x}{\partial x} + \frac{\partial g_y}{\partial y} + \frac{\partial g_z}{\partial z} \right) = 0.$

These five components can, for example, be $(\partial g_x/\partial x, \partial g_x/\partial y, \partial g_x/\partial z, \partial g_z/\partial y, \partial g_z/\partial z)$. The practical implementation of the gradiometry tensor consists of taking differences of the accelerometers as follows:

$\Gamma_{jk} = \frac{g_j(x_k + \Delta x_k) - g_j(x_k)}{\Delta x_k}, \tag{1.95}$

where $j,k \in \{x_1,x_2,x_3\} = \{x,y,z\}$ and $\Delta x_k$ is the short distance between accelerometers in the $x_k$-direction. By measuring higher derivatives of gravity, small scale features can be accurately determined.

# Geoid.³

There is an infinite number of equipotential surfaces and a particular equipotential surface of the Earth known as geoid. It coincides with the mean sea level (ignoring tides and other dynamical effects in oceans); that is, the geoid is the equipotential surface that best fits the mean sea level. Geoid would be the Earth's surface if the oceans were to flow freely and cover the entire solid Earth's surface (in the absence of winds, tides and currents). The surface of the oceans would align with the surface of the geoid, so the geoid is a theoretical shape of the Earth. The choice of mean sea level is totally arbitrary but it makes sense because the surface of a fluid in equilibrium must follow an equipotential surface. So over the oceans, the geoid is the ocean surface. Over the continents, the geoid is not the topographic surface (its location can be calculated from gravity measurements). The geoid is

³Representing the shape of the Earth with all the variation of its complex surface topography (e.g. mountains and valleys) would be an impossible task. An entire branch of science, called geodesy, is dedicated to the study of the shape and size of the Earth. Geodesists have defined two main models or reference surfaces, namely geoid and ellipsoid, to approximate the Earth's shape.