# Inversion of Complex Surface Heat Flux Based on ConvLSTM

![](bbox=[0.313, 0.187, 0.686, 0.403])

FIGURE 3.2
Utilizing the ANN to reconstruct the heat flux.

For example, in 2019, Huang et al. [21] used ANN to replace the traditional finite element algorithm. They combined the adaptive sequential Tikhonov regulation to achieve heat flux prediction. Although this problem solves the scene of the 3D complex surface, its heat flow is only time-dependent (evenly distributed in aspect), in practical scenarios, it is unrealistic to regard the fully connected network entirely as a pure black box since the number of parameters to be trained are too large.

Although predecessors have made endeavors to combine machine learning with IHCP, there are still unknowns waiting to be explored in this realm. For example, in practical industrial, it is a hard to reconstruct the surface heat flux using transient temperature. This is because:

+   1. The geometric shape of the actual workpiece is usually a three-dimensional irregular object with curved surface structure. Therefore, common approximation methods that can only deal with one or two dimensions often introduce unbearable errors.

+   2. The heat conduction model is usually nonlinear because the physical parameters often change with temperature. In addition, the radiation boundary conditions related to the fourth power of temperature will also introduce nonlinearity.

+   3. The calculation of heat flow should be efficient and real-time, especially when working for a long time.

In fact, these existing methods are hard to cover all aspects. They are more or less difficult to obtain satisfactory results in some points, so that is greatly