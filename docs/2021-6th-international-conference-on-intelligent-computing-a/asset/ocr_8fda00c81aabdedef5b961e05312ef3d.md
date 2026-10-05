# C. Experimental process establishment

For the geological features that have been extracted, multiple kernel learning can be used as a regression method to predict the features. After the kernel learning training is completed, the well observation data can be the metric value of the model. The error of the model results on the target can be used to optimize parameters in the multiple kernel learning process.

Multiple kernel learning has a higher degree of freedom in selecting input features. The X and Y coordinates are associated with a kernel as an input feature, all input features correspond to other kernel features. The multiple kernel learning formula corresponds to the model is shown below:

```
$K(\	ilde{x},\tilde{y}) = \mathbf{d} \cdot \mathbf{d} + e^{-\frac{(\tilde{x}-\tilde{y})^2}{2\sigma_1^2}} + \sum_{m=1}^{M} w_m e^{-\frac{(\tilde{x}-\tilde{y})^2}{2\sigma_m^2}}$
```

With the parameters ai on the X, Y coordinates (x1 and x2), all input features correspond to other kernel features. The multiple kernel learning is automatically updated by the MKL rule. They are used to find a measure of porosity at the well.

With the multi-scale kernel method, when the input data is not uniformly distributed or the model has a multi-scale structure the constant value makes the model fitting more flexible, making the multi-scale kernel has a wide range of applications.

After determining the synthetic kernel learning method, the next problem is to optimize the parameters of the synthetic kernel. Usually, the synthetic kernel is combined with the support vector method to project the objectives into different optimization problems for solving, such as Boosting, semi-definite programming, quadratic programming and other methods. In order to quickly obtain the optimal weights, these algorithms have been effectively solved the multiple kernel learning process.

This paper uses a multi-scale kernel learning algorithm [10], which is a two-optimization method. The first layer optimizes the weight of the multiple kernel function, and the second layer solves the problem of support vector regression. In the weight space, gradient descent can be used

# III. EXTRACT GEOLOGICAL FEATURES AND MULTIPLE KERNELS

# A. Geological feature extraction

The multiple kernel learning model applies processing and feature extraction techniques [6] [11] to seismic data to extract the relevance of the noise of seismic data and obtain feature information.

# B. Seismic vector characteristics

For the overall first-order gradient z=f(x,y), the gradient means thatthat derivative of the function at a certain point can achieve the maximum value along the direction, which can be represented as a two-dimensional direction. Generally, the derivative of it at a pixel point can be approximated by the difference between adjacent pixels.

The gradient of each pixel is generally defined as the maximum value of the gradient of the pixel and its neighbors. Using the first-order or second-order operator (convolution method) to get the character neighborhood of the pixel in the original image, and then use the gradient operator to convolve each pixel thereafter. Multiple gradient operators can be obtained. Sobel, Robson and Laplace gradient are also used

In petroleum and gas exploration, the location of the river channel and the edge area are important geological features [2]. The boundary of seismic attributes can highlight the severely changing local area in the seismic data and determine the boundary of the main sedimentary bodies buried in this area. Laplace gradient operator is used to detect the edge of seismic attributes.

# D. Porosity prediction of geophysical parameters

This experiment uses a variety of combination features to build a multiple kernel learning model to predict porosity, including multiple kernel learning using different input methods and a single support vector regression kernel model. The internal parameters of the model are updated according to the history of seismic data values and porosity values.

At first, we use seismic data (wave impedance) and coordinate (X, Y), the two input features to build a multiple kernel learning model, and then use this model to predict porosity. It can be seen that although the porosity predicted by the multiple kernel learning using seismic data and coordinate distribution has some abnormal points in the well, and there are many abnormal values in some local areas, which are not reproduced by the geological structures and porosity values.

All input features to build a single support vector regression model. These features, geological features other than coordinates are extracted from seismic data and represent the static geological interpretation of the area. It is seen from above that the multiple kernel model remains consistent with the buried rock structure of this small layer, there are many small areas with similar porosity values. This does not conform to the heterogeneity of actual reservoir physical parameters and violates the natural law of spatial