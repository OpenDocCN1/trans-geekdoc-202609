
![](img/ddadb1d3eaa6f9576eea68f95d453bca_211_0.png)

![](img/ddadb1d3eaa6f9576eea68f95d453bca_211_1.png)

![](img/ddadb1d3eaa6f9576eea68f95d453bca_211_2.png)

![](img/ddadb1d3eaa6f9576eea68f95d453bca_211_3.png)

![](img/ddadb1d3eaa6f9576eea68f95d453bca_211_4.png)

Figure 9.2 Instantaneous fluctuating vorticity (ω_z) field. (a) The DNS field used for this benchmark. Magnified view of the: (b) DNS field, (c) measured field, (d) field reconstructed with 1300 modes, (e) field reconstructed with 3000 modes. (From Raiola, Discetti & Ianiro (2015), reproduced by permission from Springer Nature.)

in the neighborhood of a circle if ψ₁(θ) and ψ₂(θ) are sinusoidal functions. Since temporal-mode vectors have a unitary norm and zero mean, the scatter plot will be in the neighborhood of a goniometric circle (with radius 1) if the temporal modes are multiplied by the factor √nₛ/2.

In general, the scatter plot of the time coefficients might unlock information on the phase and frequency relation between the first and other modes, often corresponding to higher-order harmonics, thus shedding light on the interconnection between the
different flow features highlighted by the modal analysis. Assuming that the ith POD mode is harmonically related and phase shifted with respect to the first mode, it is possible to write that

$\sqrt{n_s/2}\,\psi_i(\vartheta) = \sin(\alpha_i \vartheta + \delta_i),\qquad (9.12)$

where $\alpha_i$ is a positive integer and $\delta_i$ is the phase shift of the $i$th mode with respect to the first mode.

In order to ascertain these frequency relations, the scatter plot of the POD temporal modes $\psi_1$ and $\psi_i$ should be observed in search of Lissajous curves. A Lissajous curve is the graph of a system of parametric equations of the type $x = A \sin(\alpha t + \delta)$ and $y = B \sin(\beta t)$, which can describe even very complex harmonic motions. Visually, the ratio $\alpha / \beta$ determines the number of "lobes" of the figure. The procedure to identify the harmonic relation and the phase shift for higher order modes relies on the simplifying assumption that the first two modes are at the same frequency with a $\pi/2$ phase shift. It is possible to extract the period phase from the time coefficients of the first two modes, that is, for any snapshot $\tan(\vartheta) = \psi_1 / \psi_2$. Subsequently, the positive integer $\alpha_i$ and the phase shift $\delta_i$, which characterize the harmonic relation, can be extracted from the solution of the optimization problem

$\operatorname{argmin}_{\substack{\alpha_i \in \mathbb{N}\\ \delta_i \in \mathbb{R}}} \left( \sqrt{n_s/2}\,\psi_i - \sin(\alpha_i \vartheta + \delta_i) \right),\qquad (9.13)$

where $\alpha_i$ and the phase shift $\delta_i$ are the free parameters to identify. An example of this procedure is given in the following, where it is applied to the analysis of the flow features in the wake of two tandem cylinders located near a wall.

## 9.3.1 An Example: The Wake of Two Cylinders in Ground Effect

The work by Raiola et al. (2016) reports a PIV wind tunnel study in the wake of cylinders near a wall. The experimental arrangement is sketched in Figure 9.3. The cylinders had a diameter of 32 mm. The acquisition was performed with a 2Mpixels camera ($1600 \times 1200$ pixels array) with a spatial resolution of about 7.2 pixels/mm while the sampling frequency of the PIV measurements was 10 Hz and the Reynolds number was equal to $4.9 \times 10^3$, thus the sampling frequency was not sufficient to sample the characteristic frequencies involved in the problem. An ensemble of 2 000 image couples was acquired for each experiment, obtaining a total of 2 000 flow fields. The interrogation strategy was an iterative multistep image deformation algorithm, with final interrogation windows of $16 \times 16$ pixels with 50% overlap (i.e., final vector spacing of 8 pixels, corresponding to $0.035D$). The ensemble size both in terms of snapshots and number of points enables a sufficient convergence of the statistics (errors well below 1% of the variance both in time and space).

The results of the modal analysis are reported herein for the case of two cylinders with a relative distance $L = 1.5D$ and a gap from the wall $G = 1D$. Under these conditions the vortex shedding for the upstream cylinder is completely suppressed, and the two cylinders act as a single bluff body (Zdravkovich 1987). At the same time, the ground affects the pressure distributions, as well as the flow development.

As reported in Figure 9.4, the first two modes account for almost 60% of the variance, and the scatter plots of the temporal modes (multiplied by √n_s/2) return a perfect goniometric circle confirming that these two modes are representative of a traveling pattern. The asymmetry of the first POD mode highlights the strong interaction of the wall boundary layer with the shedding in the wake, evident from the presence of near-wall vorticity visualized in the first (and second mode, not reported here for brevity). Higher-order modes are mostly characterized by intermittent release of vorticity at a spatial and temporal frequency that is a multiple of the principal shedding frequency as shown from the contour plot of the fourth spatial mode and outlined from the Lissajous curves in the scatter plot of the fourth modes against the first one. This is an asymmetric mode that models the cross-wise oscillation of the shedding wake.

![](img/ddadb1d3eaa6f9576eea68f95d453bca_213_0.png)

Figure 9.3 Experimental setup for PIV measurements in the wake of two tandem cylinders in ground effect. (Reprinted from Raiola, Ianiro & Discetti (2016), copyright 2016, with permission from Elsevier.)

## 9.4 Extended Proper Orthogonal Decomposition

Until this point, this chapter has been centered on the analysis of a given data set A. However, the availability of multiple data sets, for example, A and B, are rather frequent. Subtracting the base conditions y0,A to A and y0,B to B, it is possible to obtain YA and YB. Given these two data sets, the most straightforward task would be to perform two separate modal analyses, as for instance performed by Mallor et al. (2019). However, if the measured quantities are synchronized, it is tempting to perform a combined analysis to extract information not only about the modes of a certain data set, for example, A, but also about the features of the second data set (B) that correlates with these modes.

To this purpose, the reader must remember that the POD spatial modes can be obtained from a projection of the snapshot matrix onto the temporal-mode matrix as in (9.3). This projection approach can be used to extend the POD to other quantities, in a generalized approach named Extended POD (Borée 2003). The columns of ΨA, that is, the POD temporal modes, form a basis in the ℝ^{n_s} vector space; thus, it is possible to use ΨA as a basis for the projection also of the matrix YB, provided that

![](img/ddadb1d3eaa6f9576eea68f95d453bca_214_0.png)

Figure 9.4 Modal analysis results for two tandem cylinders with L/D = 1.5 and G/D = 1. On the top, the correlation matrix eigenvalues are reported along with the scatter plots of the first temporal mode against the second and the fourth modes (temporal modes are multiplied by sqrt(n_s/2)). At the bottom of the figure, the spatial modes 1 and 4 are reported, highlighting the fact that the first and the fourth modes have an even spatial frequency ratio with a phase shift of π/4. (Adapted from Raiola, Ianiro & Discetti (2016), copyright 2016, with permission from Elsevier.)

the available number of snapshots of A and B is the same. Consequently, while in (9.3) the projection was used to estimate the spatial modes Φ_A of A, it is possible to define the EPOD modes of B as

Y_B = Φ_{B_A} Σ_{B_A} Ψ_A^* → Φ_{B_A} Σ_{B_A} = Y_B Ψ_A, (9.14)

where the subscripts A and B refer to the quantities A and B, respectively. The columns of Φ_{B_A} are thus the spatial modes of Y_B obtained from the projection on the temporal modes of Y_A. The data sets A and B have to be captured/generated in the same time reference frame; however, they might represent different physical quantities, and the snapshots of A and B can have different numbers of elements.

While the POD temporal modes ψ_{A_i} are estimated from the solution of the eigenvalue problem of the correlation matrix Y_A^* Y_A and are optimal for Y_A, the extended spatial modes φ_{B_A,i} are not optimal nor are necessarily ordered by their variance content σ_{B_i}^2. The value of σ_{B_i}^2 can be computed as the square root of the variance of the columns of Φ_{B_A} Σ_{B_A} in order to obtain φ_{B_A,i} vectors of unitary norm.

It has to be remarked that the projection of the snapshot matrix B on the temporal mode matrix Ψ_A is energy preserving since Ψ_A is a basis in the R^{n_s} vector space. Due to the orthogonality of the temporal modes ψ_{A_i} this has the consequence that EPOD decomposition, although not being optimal, is orthogonal. The orthogonality principle has the advantage to guarantee that each EPOD mode σ_{B_A,i} φ_{B_A,i} contains
