# 21.3.2 Kernel Extreme Learning Machine

The estimation of \(\beta\) may be inaccurate and challenging because the matrix of \(HH^T\) can be singular. Therefore, a regularized version of the ELM algorithm should be considered that a small training error is allowed and the network output weight \(\beta\) can be determined based on the following optimization problem [34]:

\(Minimize : \text{Objective} = \frac{1}{2}\|\beta\|_F^2 + \frac{\lambda}{2} \sum_{i=1}^N \|\xi_i\|_2^2\)
\(Subject to: \beta^T t = t_i - \xi_i \ i = 1, ..., N\)
(21.13)

where \(\xi_i\) is the error vector corresponding to \(x_i\) and \(\lambda\) is a parameter that determines the importance of the training error in the optimization problem and should be more than zero. To determine the network output weights (\(\beta\)), the theory of Karush–Kuhn–Tucker (KKT) [40] can be employed to solve the following dual optimization problem:

\(\text{Objective}_{Dual} = \frac{1}{2}\|\beta\|_F^2 + \frac{\lambda}{2} \sum_{i=1}^N \|\xi_i\|_2^2 - \sum_{i=1}^N a_i(\beta^T t_i - t_i + \xi_i)\) (21.14)

The network output weights \(\beta\) can be obtained by calculating the derivatives of the above objective function with respect to \(\beta_i, \xi_i, \text{and } a_i\) and setting them equal to zero. After applying this approach, the \(\beta\) matrix can be expressed as:

\(\beta = \left(HH^T + \frac{1}{\lambda}I\right)^{-1} HT\)
\(or\)
\(\beta = H\left(H^T H + \frac{1}{\lambda}I\right)^{-1} T = H(K + \frac{1}{\lambda}I)^{-1}T\) (21.15)

where \(K\) is the ELM kernel matrix, and its element is equal to the elements of \([k]_{ij} = H_i^T H_j\) [41]. The network response for a given vector \(x_l\) is given by:

\(o_l = \beta t_l = T\left(K + \frac{1}{\lambda}I\right)^{-1} H^T H_l = T\left(K + \frac{1}{\lambda}I\right)^{-1} k_l\) (21.16)

where \(k_l\) is a vector in which its elements are equal to the elements of \(k_{l,i} = H_l^T H_l\), \(i = 1, ..., N\).