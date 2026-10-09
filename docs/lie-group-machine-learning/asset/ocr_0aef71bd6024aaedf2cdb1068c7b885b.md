(a) A point $v_i$ in the original sample with Gaussian noise is represented by the Lie group $M_i$ via a reference vector $rv$, (b) The method of (a) is used for each point in the sample to extract the Lie group characteristic feature $T$ from a complete sample $X$.

The construction of the sample set is based on the method of [10], because the point cloud that makes up the sample is in $R^2$, and any point in the connection origin and point cloud can form a two-dimensional vector $v_i$. Transform this vector into a specified reference vector $rv$. Without loss of generality, we can make $rv = (1, \, 1)$. For each vector, we use two parameters, namely vector length and vector direction, to express $v_i = (r_i n_i)^T$, where $r_i$ represents the length $\|v_i\|$ of vector $v_i$, $n_i$ is the direction of $v_i$, and $\|n_i\|=1$. Then, the vector $v_i$ is transformed into vector $rv$, which can be realised by scaling the length of $M_i$ and rotating the direction $v_i = M_i \cdot rv$, where $M_i = \left(\begin{array}{cc} e^{\alpha_i} & 0 \\ 0 & R_i \end{array}\right)$, $\alpha_i = \|v_i\|/\|rv\|$ is the scaling factor of $M_i$, and $R_i$ is a rotation matrix in $R^2$ space, i.e., SO(2). Since $rv$ is fixed, $v_i$ and $M_i$ determine a one-to-one relationship, i.e., each point $v_i$ can be represented by $M_i$. The sample construction process is shown in Figure 9.10. For a sample of $k$ points, we can construct

$X = \left(\begin{array}{c} v_1 \\ v_2 \\ \vdots \\ v_k \end{array}\right) = T \cdot \left(\begin{array}{c} rv \\ rv \\ \vdots \\ rv \end{array}\right), T = \left(\begin{array}{ccc} M_1 & \cdots & 0 \\ \vdots & \ddots & \vdots \\ 0 & \cdots & M_k \end{array}\right).$

Now, sample $X$ is represented by $T$. Since each $M_i$ is a Lie group of structure $R \times \mathrm{SO}(2)$, $T$ is the direct product form of $k\ M$; hence, $T$ forms a $2k$-dimensional Lie group. Find Lie algebra elements in Lie group $T$ and obtain

$\log(T) = \left(\begin{array}{ccc} \log(M_1) & \cdots & 0 \\ \vdots & \ddots & \vdots \\ 0 & \cdots & \log(M_k) \end{array}\right), \quad \text{where}, \quad \log(M_i) = \alpha_i \left(\begin{array}{cc} 1 & 0 \\ 0 & 1 \end{array}\right) + \theta_i \left(\begin{array}{cc} 0 & -1 \\ 1 & 0 \end{array}\right)$

where $\alpha_i$ is given above and $\theta_i = \arccos(v_i \cdot rv/\|v_i\| \cdot \|rv\|)$ is the angle between the vector $v_i$ and the reference vector $rv$.

![](bbox=[0.18, 0.72, 0.48, 0.88])

![](bbox=[0.5, 0.72, 0.88, 0.88])

**Fig. 9.10:** Construction process of samples.