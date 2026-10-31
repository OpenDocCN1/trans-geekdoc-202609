
Any finite set of eigenfunctions of the Koopman operator will span an invariant subspace. Discovering these eigenfunction coordinates is, therefore, a central challenge, as they provide intrinsic coordinates along which the dynamics behave linearly. In practice, it is more likely that we will identify an *approximately* invariant subspace, given by a set of functions $\{g_j\}_{j=0}^P$, where each of the functions $g_j$ is well approximated by a finite sum of eigenfunctions: $g_j \approx \sum_{k=0}^P \alpha_k \varphi_k$.

## 11.4.3 Examples of Koopman Embeddings

### Nonlinear System with Single Fixed Point and a Slow Manifold

Here, we consider an example system with a single fixed point, given by

$$\dot{x}_1 = \mu x_1, \tag{11.36a}$$ $$\dot{x}_2 = \lambda(x_2 - x_1^2). \tag{11.36b}$$

For $\lambda < \mu < 0$, the system exhibits a slow attracting manifold given by $x_2 = x_1^2$. It is possible to augment the state $\mathbf{x}$ with the nonlinear measurement $g = x_1^2$, to define a three-dimensional Koopman invariant subspace. In these coordinates, the dynamics become linear:

$$\frac{d}{dt}\begin{bmatrix}y_1\\y_2\\y_3\end{bmatrix}= \begin{bmatrix}\mu & 0 & 0\\0 & \lambda & -\lambda\\0 & 0 & 2\mu\end{bmatrix}\begin{bmatrix}y_1\\y_2\\y_3\end{bmatrix}\quad\text{for}\quad \begin{bmatrix}y_1\\y_2\\y_3\end{bmatrix}= \begin{bmatrix}x_1\\x_2\\x_1^2\end{bmatrix}. \tag{11.37a}$$

The full three-dimensional Koopman observable vector space is visualized in Figure 11.7. Trajectories that start on the invariant manifold $y_3 = y_1^2$, visualized by the blue surface, are constrained to stay on this manifold. There is a *slow* subspace, spanned by the eigenvectors corresponding to the slow eigenvalues $\mu$ and $2\mu$; this subspace is visualized by the green surface. Finally, there is the original asymptotically attracting manifold of the original system, $y_2 = y_1^2$, which is visualized as the red surface. The blue and red parabolic surfaces always intersect in a parabola that is inclined at a $45^\circ$ angle in the $y_2$–$y_3$ direction. The green surface approaches this $45^\circ$ inclination as the ratio of fast to slow dynamics becomes increasingly large. In the full three-dimensional Koopman observable space, the dynamics produce a single stable node, with trajectories rapidly attracting onto the green subspace and then slowly approaching the fixed point.

### Intrinsic Coordinates Defined by Eigenfunctions of the Koopman Operator

The left eigenvectors of the Koopman operator yield Koopman eigenfunctions (i.e., eigenobservables). The Koopman eigenfunctions of (11.37a) corresponding to eigenvalues $\mu$ and $\lambda$ are

$$\varphi_\mu = x_1, \quad \text{and}\quad \varphi_\lambda = x_2 - b x_1^2 \quad \text{with}\quad b = \frac{\lambda}{\lambda - 2\mu}. \tag{11.38}$$

![](img/ddadb1d3eaa6f9576eea68f95d453bca_251_0.png)

Figure 11.7 Visualization of three-dimensional linear Koopman system from (11.37a) along with projection of dynamics onto the x1−x2 plane. The attracting slow manifold is shown in red, the constraint y3 = y1^2 is shown in blue, and the slow unstable subspace of (11.37a) is shown in green. Black trajectories of the linear Koopman system in y project onto trajectories of the full nonlinear system in x in the y1−y2 plane. Here, μ = −0.05 and λ = 1. Reproduced from Brunton et al. (2016b).

In this way, a set of intrinsic coordinates may be determined from the observable functions defined by the left eigenvectors of the Koopman operator on an invariant subspace. Explicitly,

φ_α(x) = ξ_α y(x),  where  ξ_α K = α ξ_α. (11.39)

These eigen-observables define observable subspaces that remain invariant under the Koopman operator, even after coordinate transformations. As such, they may be regarded as intrinsic coordinates (Williams et al. 2015) on the Koopman-invariant subspace.

## 12 Methods for System Identification

S. Brunton

Fluid dynamics are characterized by high-dimensional, nonlinear dynamical systems that exhibit multiple scales in space and time. Simulating these equations is currently too expensive for real-time optimization and control (Bagheri et al. 2009, Fabbiane et al. 2014, Brunton & Noack 2015), and there are efforts to obtain reduced-order models (ROMs) that capture the salient dynamics with a lower-dimensional system. There are two broad approaches to obtain ROMs: first, it is possible to start with a high-dimensional system, such as the discretized Navier–Stokes equations, and project the dynamics onto a low-dimensional subspace identified, for example, using proper orthogonal decomposition (POD; Berkooz et al. 1993, Holmes et al. 2012) and Galerkin projection (Quarteroni & Rozza 2013, Benner et al. 2015). The second approach is to collect data from a simulation or an experiment and identify a low-rank model using data-driven techniques. This approach is typically called system identification, and is often preferred for control design because of the relative ease of implementation. The dynamic mode decomposition (DMD) from Chapter 7 is an example of system identification that is widely used in fluid mechanics.

Most of the system identification techniques discussed here, including DMD from Chapter 7, result in linear models (see Chapter 10). Even for nonlinear systems, such as the Navier–Stokes equations, it is often possible to use linear approaches for closed-loop control. There are numerous examples of successful linear model-based flow control (Bagheri et al. 2009, Fabbiane et al. 2014, Brunton & Noack 2015). Control generally relies on fast, low-latency models for robust real-time performance, especially for fluids where the dynamics often evolve on fast timescales. Therefore, system identification also relies on dimensionality reduction to obtain low-dimensional approximations of the system for use in real-time feedback control.

This chapter explores several system identification techniques. First, we introduce balanced truncation and balanced POD (BPOD), which have been used extensively to obtain linear ROMs in fluid systems. Next, we develop the eigensystem realization algorithm (ERA), which has deep connections to both balanced POD and DMD. Finally, we introduce the sparse identification of the nonlinear dynamics (SINDy) algorithm.

### 12.1 Balanced Model Reduction

Balanced model reduction refers to an alternative *control-oriented* procedure that results in low-dimensional models for input–output systems. POD is the most common low-dimensional basis used for model reduction, and it orders modes based on the kinetic energy content of the approximated state. Instead of energy, balanced modes are ordered by how much input–output energy they capture, making them useful for feedback control. This section will explore balanced model reduction in the broader context of reduced-order modeling and system identification. Balanced modeling of fluids is based on both data and equations, and is typically used to reduce high-dimensional fluid systems. As with POD-based modeling, the general idea is to determine a hierarchical modal decomposition of the system state that may be truncated at some model order, only keeping the coherent structures that are most important for control.

### 12.1.1 The Goal of Model Reduction

Consider a high-dimensional system, depicted schematically in Figure 12.1,

$$\frac{d}{dt} \mathbf{x} = \mathbf{A}\mathbf{x} + \mathbf{B}\mathbf{u}, \tag{12.1a}$$ $$\mathbf{y} = \mathbf{C}\mathbf{x} + \mathbf{D}\mathbf{u}, \tag{12.1b}$$

for example from a spatially discretized simulation of a PDE. The primary goal of model reduction is to find a coordinate transformation $\mathbf{x} = \mathbf{\Psi}\tilde{\mathbf{x}}$ giving rise to a related system $(\tilde{\mathbf{A}},\tilde{\mathbf{B}},\tilde{\mathbf{C}},\tilde{\mathbf{D}})$ with similar input–output characteristics,

$$\frac{d}{dt}\tilde{\mathbf{x}} = \tilde{\mathbf{A}}\tilde{\mathbf{x}} + \tilde{\mathbf{B}}\mathbf{u}, \tag{12.2a}$$ $$\mathbf{y} = \tilde{\mathbf{C}}\tilde{\mathbf{x}} + \tilde{\mathbf{D}}\mathbf{u}, \tag{12.2b}$$

in terms of a state $\tilde{\mathbf{x}} \in \mathbb{R}^r$ with reduced dimension, $r \ll n$. Note that $\mathbf{u}$ and $\mathbf{y}$ are the same in (12.1) and (12.2) even though the system states are different. Obtaining the projection operator $\mathbf{\Psi}$ will be the focus of this section.

As a motivating example, consider the following simplified model:

$$\frac{d}{dt}\begin{bmatrix}x_1\\x_2\end{bmatrix}=\begin{bmatrix}-2 & 0\\0 & -1\end{bmatrix}\begin{bmatrix}x_1\\x_2\end{bmatrix}+\begin{bmatrix}1\\10^{-10}\end{bmatrix}u, \tag{12.3a}$$ $$y=\begin{bmatrix}1 & 10^{-10}\end{bmatrix}\begin{bmatrix}x_1\\x_2\end{bmatrix}. \tag{12.3b}$$

In this case, the state $x_2$ is barely controllable and barely observable. Simply choosing $\tilde{x}=x_1$ will result in a ROM that faithfully captures the input–output dynamics. Although the choice $\tilde{x}=x_1$ seems intuitive in this extreme case, many model reduction techniques would erroneously favor the state $\tilde{x}=x_2$, since it is more lightly damped. Throughout this section, we will investigate how to accurately and efficiently find the transformation matrix $\mathbf{\Psi}$ that best captures the input–output dynamics.
