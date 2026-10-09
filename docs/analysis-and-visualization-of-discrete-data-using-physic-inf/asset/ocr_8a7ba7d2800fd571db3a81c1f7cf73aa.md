Lipschitz continuous functions play an important role in calculus, functional analysis, and other areas of mathematics. They are also used in various fields, such as physics, engineering, and economics.

As shown above, a neural network with one sigmoidal function approximates a Lipschitz continuous function, and a neural network with multiple sigmoidal functions can approximate any Lipschitz continuous function. Therefore, any continuous function can be approximated with any precision.

# **2.7.2. Regression analysis using NNs**

To explain the regression analysis using NNs, we use as discrete data the bivariate data described in Section 5, paragraph 2. These data are calculated from the bivariate function

$$y = x_{1}^{2} + x_{1} + x_{2}^{3} + x_{2}^{2}.$$ (2.26)

The mean squared error of the model

$$y = w_{0} + w_{1}x_{1} + w_{2}x_{2},$$ (2.27)

created by linear regression from 26 discrete data randomly selected from $\{(x_{1}, x_{2})|0 \leq x_{1} \leq 1, 0 \leq x_{2} \leq 1\}$, was $0.0402$. Using the coefficients $w_{0}w_{1}w_{2}$ as parameters, the parameters that minimize the mean square error between the spatiotemporal model and the given discrete data were calculated using the Excel Solver function.

In the previous section, we discussed specific ways to achieve regression analysis using the Solver. In this section, we will use the same data to explain how to achieve an NN model by using Solver. A simple NN model can be realized as an activation function connected to the output of this linear regression model. This time, we use the Sigmoid function

$$\sigma(x) = \frac{1}{1 + e^{-x}}$$ (2.28)

and assume that the output obtained using this function in the Excel sheet function is scale converted to

$$y = (y_{max} - y_{min})\frac{1}{1 + e^{-(w_{0} + w_{1}x_{1} + w_{2}x_{2})}} + y_{min}$$ (2.29)

$\Delta y = \frac{(y_{max} - y_{min})}{\Delta y}$ to calculate the mean squared error between $y = \frac{1}{1 + e^{-(w_{0} + w_{1}x_{1} + w_{2}x_{2})}} + y_{min}$ and the given discrete data $y_{i}.$

$$\sum_{i=1}^{26} \left(y_{i} - \frac{\Delta y}{1 + e^{-(w_{0} + w_{1}x_{1} + w_{2}x_{2})}} - y_{min}\right)^{2}$$ (2.30)