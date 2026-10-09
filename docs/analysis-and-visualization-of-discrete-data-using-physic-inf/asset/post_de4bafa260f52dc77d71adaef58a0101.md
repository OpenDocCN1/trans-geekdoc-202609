
## 4.2. Use of visual analysis techniques

This book has so far described methods for deriving PDEs and solving them from physical data using NNs. As discussed earlier, this book assumes that physical data consist of the space-time coordinates in which the data are defined and the physical data associated with those coordinates. In NN, the space-time coordinates are used as input and the physical data as output, and the function that approximates the physical data is regressed. Yet, the following two aspects are largely left to humans:

- (1) What kind of NN to build
- (2) How to construct a partial differential term library

Therefore, it is desirable to develop visual analytics (VA) methods that emphasize the importance of visual exploration alongside the process that automatically constructs models.

As for the accuracy of the results, a relationship with the NN hyper-parameters was observed. However, increasing the complexity of the NN (number of layers, number of neurons per layer, etc.) does not necessarily increase the accuracy. Therefore, it is an important issue for the future to optimize NN hyperparameters. It is important to build hyperparameter visualization infrastructure that can utilize the judgment of users, in addition to simply using automation techniques.

In NN, the number of units per layer is variable. For example, AutoEncoders, the algorithm for dimensionality reduction using NN, is structured in such a way that the number of units is first gradually reduced from the input layer and then increased. As a visualization method to represent such parameters naturally, NN is represented by multidimensional coordinate points with an upper limit on the number of layers (dimensions). What is expected is the visualization method that performs dimensional reduction and maps error values in two- or three-dimensional space (Figure 4.35).

![](img/fa57e7010b16a211d5cf69ebb17e416e_180_0.png)

Figure 4.35. Visualization of NN hyperparameters.

The number of units per layer is entered in each row of the cell matrix (error value in the last cell) in the bottom row of Figure 4.35. In the first line, the NN consists of two layers, indicating that 80 units are allocated in each layer. The user interactively selects point groups with low errors on the scatterplot (nine in Figure 4.35), which are visualized in parallel coordinates. Parallel coordinates assign each dimension of multidimensional data to a parallel coordinate axis and represent it as a polyline connecting values for each dimension. The rightmost coordinate axis represents the error. This polyline is a coordinate point in a multidimensional space. The NN label and its simplified representation are shown to the left of the left end of the cell matrix. In the example shown in Figure 4.35, NN7 corresponding to the red point is selected. It indicates that for NN2 and NN6, the errors are larger despite having the same pattern of the number of units and the larger number of layers.

## 4.3. Methods for solving a given PDE

This book has so far described methods for deriving PDEs from physical data using NN models. As discussed earlier, this book assumes that physical data consist of the space-time coordinates at which the data are defined and the physical data associated with those coordinates. In NN, the space-time coordinates are used as input and the physical data as output, and the function that approximates the physical data is regressed. This book assumes PDEs with an exact solution and regards the exact solution data of the PDE at multiple discrete space-time points as pseudo-measurement data. As an application example, for a PDE with an exact solution, this book discussed a method to find the original PDE with high accuracy by considering the results computed by randomly changing the space-time coordinates in the exact solution as the pseudo-measurement data. The relationship between the NN hyperparameters (number of layers and neurons) and the accuracy was then visualized.

This section discusses a method for solving a given PDE using NN with boundary conditions (Dirichlet or Neumann type) described by space-time discrete points. The Dirichlet boundary condition is a type of boundary condition in PDE used when the value of a variable is given on the boundary. For example, it is used to describe temperature distributions, potential distributions, and fluid velocity distributions.

The Dirichlet boundary condition is mathematically expressed as follows: When a function $u(x)$ is given on the boundary $\partial\Omega$ of some domain $\Omega$, it is expressed as

$$u(x)=g(x), \quad x \in \partial \Omega, \quad (4.31)$$

where $g(x)$ represents the value on the boundary, and $u(x)$ the solution inside the domain $\Omega$.

For example, considering the two-dimensional heat conduction equation

$$\frac{\partial u}{\partial t} = \alpha \left(\frac{\partial^{2} u}{\partial x^{2}} + \frac{\partial^{2} u}{\partial y^{2}}\right), \tag{4.32}$$

when a temperature is given on a boundary within a rectangular region $\Omega$ using the Dirichlet boundary condition, it is expressed as follows:

$$u(x, y, t) = g(x, y),\ (x, y) \in \partial \Omega \tag{4.33}$$

where $g(x, y)$ represents the temperature on the boundary of region $\Omega$ and $u(x, y, t)$ represents the temperature within region $\Omega$.

The Neumann boundary condition is a type of boundary condition in PDE used when the normal gradient of a variable is given on a boundary. For example, it is used to describe the thermal conductivity of an object surface or the flow rate of a fluid.

The Neumann boundary condition is mathematically expressed as follows: When a gradient in the normal direction of a function $u(x)$ is given on the boundary $\partial \Omega$ of a region $\Omega$, it is expressed as

$$\left(\frac{\partial u}{\partial n}\right)(x) = g(x),\quad x \in \partial \Omega \tag{4.34}$$

where $\partial u / \partial n$ represents the gradient in the normal direction $u$ and $g(x)$ the value on the boundary.

For example, considering the two-dimensional heat conduction equation

$$\frac{\partial u}{\partial t} = \alpha \left(\frac{\partial^{2} u}{\partial x^{2}} + \frac{\partial^{2} u}{\partial y^{2}}\right), \tag{4.35}$$

when a heat flux is given on the upper boundary of a rectangular region $\Omega$ using the Neumann boundary condition, it is expressed as follows:

$$\frac{\partial u}{\partial y}(x, y, t) = g(x, y),\ (x, y) \in \partial \Omega \tag{4.36}$$

where $g(x, y)$ represents the heat flux on the upper boundary of the region $\Omega$, and $\partial u / \partial y$ represents the gradient of the temperature $u(x, y, t)$ in the region $\Omega$ in the $y$ direction.

As physical data, they are defined at the boundaries and inside the region of interest, from which NN model errors and PDE errors are computed to obtain a solution of a PDE (Figure 4.37). NN model errors were explained in the previous section, and PDE errors will be explained later. As an application example, this section introduces a program that utilizes this method to find solutions for PDEs with known exact solutions and compares them with the exact results. Additionally, for PDEs lacking exact solutions, we compare them with conventional PDE approximation solutions.

![](img/fa57e7010b16a211d5cf69ebb17e416e_183_0.png)

Figure 4.36. Detail of PINN processing and the user interface.

### 4.3.1. How to solve PDEs using the Fourier transform

Before describing how to solve PDEs using NNs, this section introduces how to solve PDEs using the Fourier transform [42]. The following equation is used as a definition. Here, $k$ is any real number.

$$f(x)=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^{\infty} F(k)e^{ikx}dk \tag{4.36}$$

If the explanatory variable $x$ in the function of interest $f(x)$ is a physical quantity, the Fourier transform transfers the dimension of the explanatory variable to its original reciprocal. For example, when the explanatory variable $x$ in the function before the transformation has the dimension of time, the explanatory variable $k$ after the transformation has the dimension of frequency. Alternatively, when the explanatory variable $x$ before the transformation has a length dimension, the explanatory variable $k$ after the transformation has a wavenumber dimension. Based on the definition, this
