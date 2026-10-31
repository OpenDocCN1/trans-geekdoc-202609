
Note in particular that the eigenfunctions of this equation are now functions of both space and time, which we distinguish from the space-only modes that we have dealt with so far using a ~. Most typically, systems modeled using this approach are stationary in time, meaning that C(x,x′,t,t′)=C(x,x′,t−t′) is only a function of the difference in time τ=t−t′. Similar to the case of spatial homogeneity, this means that the temporal dependence on these modes becomes Fourier modes. This allows for a temporal Fourier transform of (6.31), giving

∫_{Ω_x} S(x,x′,f) \hat{φ}_j(x′,f) dx′ = σ_j(f)^2 \hat{φ}_j(x,f), (6.32)

where the cross-spectral density tensor S(x,x′,f) is obtained from the temporal Fourier transforms:

S(x,x′,f)=∫_{-∞}^{∞} C(x,x′,τ) exp(−i2πfτ) dτ. (6.33)

This space-time or spectral POD was, in fact, the original formulation of POD as described in Lumley (1967) and Lumley (1970). However, the “space-only” POD has been much more commonly used since then, likely due to two main reasons: it is easy to formulate and compute from data, and it is readily amenable for the construction of projection-based reduced-order models (e.g., Holmes et al. 2012), as will be discussed in Section 6.5. Indeed, the difference between the original and most commonly used formulations has perhaps been under appreciated in the community (including by the author). Recently, the work of Towne et al. (2018) has brought the “spectral” version of POD back to prominence, though an exposition of the method and its close connections to other modeling approaches, and in the development of practical algorithms for its implementation (Schmidt & Towne 2019).

## 6.5 The Proper Orthogonal Decomposition for Projection-Based Modeling

Perhaps the most common usage of the POD involves using a truncated basis of POD modes to obtain a subspace that differential equations describing the physics of a system may be projected onto. For example, if we consider the incompressible Navier-Stokes momentum equation

∂u/∂t = −(u·∇)u + Re^{−1}Δu − ∇p, (6.34)

then taking the spatial inner product of both sides of this equation with a POD mode φ_j(x) gives

⟨∂u/∂t, φ_j⟩_x = −⟨(u·∇)u, φ_j⟩_x + Re^{−1}⟨Δu, φ_j⟩_x − ⟨∇p, φ_j⟩_x. (6.35)

Approximating the full velocity field with a set of POD modes (as in (6.1)), we obtain

\dot{a} = L a + Q(a,a) + f, (6.36)

where L is a linear operator, Q is a bilinear operator, and f is a vector, each defined based on the identified spatial POD modes by

L_ij = ν ⟨Δφ_j, φ_i⟩_x,    Q_ijk = −⟨(φ_j · ∇)φ_k, φ_i⟩_x,    f = −⟨∇p, φ_i⟩_x.    (6.37)

This gives a means of approximating the Navier–Stokes equations by a set of nonlinear ordinary differential equations, which is typically of much lower dimension than the full discretized equations.

## 6.6 Extensions of the Proper Orthogonal Decomposition

There are many modifications and extensions of the basic POD definition and algorithm that can improve on its suitability, accuracy, and efficiency in various applications. If being used for reduced-order modeling as described in Section 6.5, a subspace based on POD modes is optimal from an energetic sense, but is not necessarily the best choice for retaining all features of dynamic importance. For the case of linear systems, one can seek to define the subspace and direction of projection such that they best preserve the system dynamics (quantified by the observability and controllability Gramians). This is known as balanced truncation (Moore 1981), and it was shown by Rowley (2005) that these subspaces can be identified from POD using inner products that are weighted by the observability and controllability Gramians (see also the similar method developed in Willcox and Peraire (2002)). Further discussion of notions of these concepts are given in Chapter 10.

Several other variants of POD account for other desired qualities in spatio-temporal decompositions, such as finding a balance between energetic optimality and frequency localization (Sieber et al. 2016), and seeking scale separation (Mendez et al. 2019). Additional variants aim to reparameterize the spatio-temporal domain with translations, rotations, and/or rescalings to make certain data/systems (often those dominated by convection) more amenable to low-dimensional approximation (Rowley & Marsden 2000, Rowley et al. 2003, Mojgani & Balajewicz 2017, Mowlavi & Sapsis 2018, Reiss et al. 2018, Black et al. 2019, Mendible et al. 2020).

Aside from these variants, computation of POD can require overcoming several practical challenges involving the acquisition and processing of data of sufficient quantity and quality to ensure converged results. For further discussion of such practical considerations for experimental data in particular, see Chapter 9.

## 6.7 Examples

This section will present two simple examples to show how the POD can be applied, and its outputs interpreted. Both of these examples come with accompanying Python code, available on the book’s website.⁴ The example considered here is similar to an example considered in (Tu et al. 2014). We consider data that is sampled from the function

$$ y(x,t)=c_1 \exp\left[\frac{(x-x_1)^2}{2s_1^2}\right]\sin(2\pi f_1 t)+c_2 \exp\left[\frac{(x-x_2)^2}{2s_2^2}\right]\sin(2\pi f_2 t), \qquad (6.38) $$

where we choose the parameters $c_1 = 1$, $x_1 = 0.5$, $s_1 = 0.6$, $f_1 = 1.3$, $c_2 = 1.2$, $x_2 = -0.5$, $s_2 = 0.3$, and $f_2 = 4.1$. We collect data in the range $x \in [-2,2]$ and $t \in [0,50]$. A visualization of this function over four time units is shown in Figure 6.1.

![](img/ddadb1d3eaa6f9576eea68f95d453bca_148_0.png)

Figure 6.1 Surface plot of data from (6.38).

![](img/ddadb1d3eaa6f9576eea68f95d453bca_148_1.png)

Figure 6.2 Singular values corresponding to each POD mode for data from (6.38).

We perform POD by compiling the data in a matrix and performing a SVD, using the procedure discussed in Section 6.3. The resulting singular values, spatial POD modes, and corresponding temporal coefficients are shown in Figures 6.2 through 6.4, respectively. The leading two singular values are much larger than the rest (which are essentially zero), due to the fact that the data comes from a function that is the sum of two terms (with each the product of a spatial function and a temporal function).

![](img/ddadb1d3eaa6f9576eea68f95d453bca_149_0.png)

Figure 6.3 POD mode shapes computed from data from (6.38).

![](img/ddadb1d3eaa6f9576eea68f95d453bca_149_1.png)

Figure 6.4 POD mode coefficients for data from (6.38).

However, the leading two POD modes do not cleanly partition the two component functions, and instead each mode is a mix of the two. This is due to the fact that the SVD is “greedy” in the sense that the first set of singular vectors captures as much energy as possible, which in this case means taking part of each of the two terms in (6.38).

In Figure 6.5, we show the results of applying spectral POD to the same data set, which we see is able to distinguish between the two spatial functions corresponding to different temporal frequencies, both of which show up as peaks in the corresponding spectrum, shown in Figure 6.6. Note that here a simple Fourier transform in time would also suffice, since the data is entirely deterministic and free of noise. Here we could also separate out the frequency content using dynamic mode decomposition on appropriately arranged data.

The next example that we consider involves data from a fluid simulation, considering two-dimensional flow over a circular cylinder at a Reynolds number of 60.

![](img/ddadb1d3eaa6f9576eea68f95d453bca_150_0.png)

Figure 6.5 Spectral POD mode shapes computed from data generated from (6.38).

![](img/ddadb1d3eaa6f9576eea68f95d453bca_150_1.png)

Figure 6.6 Spectral POD energy content of data generated from (6.38).

A similar example has already been introduced and discussed in Chapter 1. We consider 41 snapshots of data collected over approximately eight convective times (being the time taken for fluid in the freestream to travel one cylinder diameter). The data is collected when the system is in a transient state, close to the unstable equilibrium solution, but with oscillations (corresponding to vortex shedding) that are slowly growing in time.

The accompanying Python code shows how the data for both the streamwise and transverse velocity components can be arranged as in (6.19); how POD can be performed via an SVD; and how the resulting modes and mode coefficients can be visualized. The first two modes are shown in Figures 6.7 and 6.8, with their accompanying time-varying coefficients shown in Figure 6.9. We see that these leading two modes are similar in structure, featuring oscillatory structures in the streamwise (horizontal) direction, which have a phase difference between modes 1 and 2 (with a similar phase difference observed for the mode coefficients in time).
