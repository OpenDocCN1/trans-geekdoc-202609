![](bbox=[0.28, 0.08, 0.88, 0.14])

where $m=1/s\sum_{i=1}^{s}m_{i}$, $N_{i}=\sum_{x^{j}\in C_{i}}1$, $m_{i}=1/N_{i}\sum_{x^{j}\in C_{i}}x^{j}$. The intra-class distance $S_{W}$ and inter-class distance $S_{B}$ after projection can be expressed as

![](bbox=[0.32, 0.22, 0.85, 0.3])

Then, we have

![](bbox=[0.4, 0.34, 0.85, 0.42])

To make the intra-class distance smaller and the inter-class distance as large as possible, we can maximise the following function:

![](bbox=[0.39, 0.47, 0.85, 0.52])

The projection vector $\boldsymbol{w}$ can be expressed as

![](bbox=[0.39, 0.56, 0.85, 0.6])

Therefore, $\boldsymbol{w}$ can be solved by solving the following characteristic equation:

![](bbox=[0.41, 0.63, 0.85, 0.66])

The characteristic vector corresponding to the largest eigenvalue of the equation is the solution. Hence, the Finsler metric formula can be written as

![](bbox=[0.39, 0.72, 0.85, 0.76])

Hence, the distance between two points in the data set can be defined as

![](bbox=[0.26, 0.79, 0.85, 0.84])

The basic flow of the Finsler metric KNN (FMKNN) algorithm is given below:

+   1.  Set neighbour parameter $K$.
2.  Find projection vector $w$ according to (13.18).
3.  Construct a neighbourhood graph according to the data set, where the nodes are all data samples. The distance between points can be obtained by (13.20).
4.  For each point $x_{q}$ in the test set, find the $K$ nearest neighbours in the training set.