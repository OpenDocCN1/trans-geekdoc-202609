With this, we can define the delta as follows:

$$\delta_j := \frac{\partial E_n}{\partial a_j} = \sum_k \frac{\partial E_n}{\partial a_k}\frac{\partial a_k}{\partial a_j}$$

Here, $E_n$ denotes the evaluation function (these equations are the same as we mentioned in *Chapter 2, Algorithms for Machine Learning – Preparing for Deep Learning*).

We get the following equation:

$$a_k = \sum_j w_{kj}z_j + c_k$$
$$= \sum_j w_{kj}h(a_j)m_j + c_k$$

Here, the delta can be described as follows:

$$\delta_j = h'(a_j)m_j\sum_k \delta_k w_{kj}$$

Now we have all the equations necessary for implementation, let's dive into the implementation. The package structure is as follows:

![](bbox=[0.364, 0.537, 0.635, 0.812])