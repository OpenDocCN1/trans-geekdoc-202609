
considered microstructures. Hence, we also expect a transversely isotropic suspension viscosity $\bar{V}$ if the volume element size for the computational investigations was chosen sufficiently large.

![](img/283dee3537da34c9897f9777475c5d3d_77_0.png)

![](img/283dee3537da34c9897f9777475c5d3d_77_1.png)

(a) $f_1$ and $f_2$ for the Newtonian case

(b) $f_1$ and $f_2$ for the Cross-type case

Figure 3.11: Anisotropy fractions $f_1$ and $f_2$ (3.55) for the Newtonian and the Cross-type case, $c_F \in \{5, 10, 15, 20, 25\}\%$, $\dot{\gamma} \in [10, 10^5]\text{s}^{-1}$. Figure adapted from Sterr et al. (2023, Figure 11).

To test if the volume element size was chosen appropriately, we define the relative deviation

$e_{\text{dev}} = \frac{|f_1 - f_2|}{|f_1|}, \quad (3.56)$

and evaluate the relative deviation $e_{\text{dev}}$ for both the Newtonian and Cross-type case. For all considered shear rates $\dot{\gamma}$ and volume fractions $c_F$, the deviation $e_{\text{dev}}$ is smaller than 2% in both the Newtonian and the Cross-type case. Therefore, the values of the fractions $f_1$ and $f_2$ differ only slightly from each other, and the expected symmetry of the material is captured with an error that is sufficiently small for engineering purposes. The elongational viscosity $\eta_{app}$ in the $y-z$ plane, as shown in Figures 3.9b and 3.10b, illustrate the material symmetry further, since the polar plots of the elongational viscosity $\eta_{app}$ are circular for all fiber volume fractions $c_F$ and shear rates $\dot{\gamma}$. Since we consider the volume elements as representative, we will discuss the dependence of both fractions $f_1$ and $f_2$ on the fiber volume fraction $c_F$ and the shear rate $\dot{\gamma}$ as shown in Figure 3.11.

In the Newtonian case, both fractions $f_1$ and $f_2$ grow significantly from 1.45 at a volume fraction $c_F = 5\%$ to 2.19 at a volume fraction $c_F = 25\%$. Because the matrix behavior in the Cross-type case is approximately Newtonian for low shear rates $\dot{\gamma}$, the values of the fractions $f_1$ and $f_2$ in the Cross-type case for a shear rate $\dot{\gamma} = 10\ s^{-1}$ are similar to those in the Newtonian case. As the shear rate $\dot{\gamma}$ grows, the values of the fractions $f_1$ and $f_2$ decrease up to a shear rate $\dot{\gamma}_{min} \approx 10^3\ s^{-1}$, where they reach their respective minima. Because more fibers are likely to be packed close to each other for higher volume fractions $c_F$, higher velocity gradients occur at lower macroscopic shear rates $\dot{\gamma}$. This, in turn, decreases the local matrix viscosity. Consequently, the minimum of the fractions $f_1$ and $f_2$ occurs at lower shear rates as the fiber volume fraction grows. For a fiber volume fraction $c_F = 25\%$, the minimum of the fractions $f_1$ and $f_2$ is attained at a shear rate $\dot{\gamma} = 10^3\ s^{-1}$, whereas, for a fiber volume fraction $c_F = 5\%$, the minimum is attained at a shear rate $\dot{\gamma} = 2 \cdot 10^3\ s^{-1}$. Also, the maximum absolute changes

\(\Delta f(c_F) = f(c_F, 10\ s^{-1}) - f(c_F, \dot{\gamma}_{min})\) (3.57)

increase with the fiber volume fraction $c_F$, e.g., $\Delta f(c_F) = 17\%$ and $\Delta f(c_F) = 28\%$ for fiber volume fractions $c_F$ of 5% and 25%, respectively. In contrast, the maximum relative changes

\(\Delta f(c_{\mathrm{F}}) = \frac{f(c_{\mathrm{F}}, 10\ \mathrm{s}^{-1}) - f(c_{\mathrm{F}}, \dot{\gamma}_{\min})}{f(c_{\mathrm{F}}, 10\ \mathrm{s}^{-1})} \quad (3.58)\)

lie between 12% to 14% for all investigated fiber volume fractions.

### 3.4.3 Comparison to mean-field results

In the following, we compare the computational results with mean-field estimates. In the Newtonian and Cross-type cases, we use the Mori-Tanaka model (3.40) to calculate the apparent mean-field viscosity \(\eta_{\mathrm{app}}^{\mathrm{MF}}\). Then, we compare the apparent mean-field viscosity \(\eta_{\mathrm{app}}^{\mathrm{MF}}\) with the apparent computational viscosity \(\eta_{\mathrm{app}}^{\mathrm{FFT}}\) via the deviation

\(e_{\mathrm{MF}} = \frac{\left| \eta_{\mathrm{app}}^{\mathrm{MF}} - \eta_{\mathrm{app}}^{\mathrm{FFT}} \right|}{\eta_{\mathrm{app}}^{\mathrm{FFT}}}. \quad (3.59)\)

To reduce dimensionality, and to avoid compromising the comparison with potential interpolation errors, as discussed in section 3.4.1, we focus our discussion on the two scalar quantities \(\eta_{\mathrm{app}}^{x}\) and \(\eta_{\mathrm{app}}^{y}\). The results for the Newtonian and the Cross-type case are shown in Figures 3.12 and 3.13, as well as Figure 3.14. In the Newtonian case, the elongational viscosities $\eta_{\mathrm{app}}^{x}$ and $\eta_{\mathrm{app}}^{y}$ obtained via the mean-field method are lower than the ones obtained via the FFT-based computational method. Also, for a fiber volume fraction $c_{\mathrm{F}} = 5\%$, the mean-field and FFT-based results for $\eta_{\mathrm{app}}^{x}$ and $\eta_{\mathrm{app}}^{y}$ can still be considered similar for engineering purposes, as the deviation $e_{\mathrm{MF}}$ is below 5.7%. However, for increasing fiber volume fractions $c_{\mathrm{F}}$, the deviation $e_{\mathrm{MF}}$ increases monotonically up to 26.8% for the elongational viscosity $\eta_{\mathrm{app}}^{x}$ and 23.5% for the elongational viscosity $\eta_{\mathrm{app}}^{y}$.

![](img/283dee3537da34c9897f9777475c5d3d_80_0.png)

(a) Apparent viscosities \(\eta_{app}^x\) and \(\eta_{app}^y\)

(b) Deviation \(e_{MF}\)

Figure 3.12: Apparent viscosities \(\eta_{app}^x\) and \(\eta_{app}^y\) for the mean-field model and the FFT-based computational method, and deviation \(e_{MF}\) (3.59) for fiber volume fractions \(c_F \in \{5, 10, 15, 20, 25\}\)% in the Newtonian case. Figure adapted from Sterr et al. (2023, Figure 12).

In the Cross-type case, for shear rates \(\dot{\gamma} \approx 10 \text{ s}^{-1}, \dot{\gamma} \approx 10^5 \text{ s}^{-1}\), we observe the same results for the deviation \(e_{MF}\) as in the Newtonian case. This is a direct result of the two Newtonian regions of the Cross-type matrix viscosity \(\eta\) at the shear rate limits \(\dot{\gamma} \to 0 \text{ s}^{-1}\) and \(\dot{\gamma} \to \infty \text{ s}^{-1}\). The largest deviation \(e_{MF}\) occurs for a shear rate \(\dot{\gamma} = 10^3 \text{ s}^{-1}\), where the matrix nonlinearity is highest. As we already observed for the anisotropy measures \(f_1\) and \(f_2\) in section 3.4.1, the fiber volume fraction \(c_F\) influences the shear rate \(\dot{\gamma}\) at which the maximum deviation \(e_{MF}\) occurs. In particular, for both elongational viscosities \(\eta_{app}^x\) and \(\eta_{app}^y\), the maximum observed deviation for a fiber volume fraction \(c_F = 25\%\) occurs at a lower shear rate \(\dot{\gamma} = 10^3 \text{ s}^{-1}\), whereas it occurs at a shear rate

\(\dot{\gamma} = 2 \cdot 10^3 \text{ s}^{-1}\) for a fiber volume fraction \(c_F = 5\%\).

![](img/283dee3537da34c9897f9777475c5d3d_81_0.png)

**Figure 3.13:** Apparent viscosities \(\eta_{app}^x\) and \(\eta_{app}^y\) for the mean-field model and the FFT-based computational method for fiber volume fractions \(c_F \in \{5, 25\}\%\) and shear rates \(\dot{\gamma} \in [10, 10^5] \text{ s}^{-1}\) in the Cross-type case. Figure adapted from Sterr et al. (2023, Figure 13).

As an additional consequence of the Cross-type material law (3.2), the curves of the elongational viscosities \(\eta_{app}^x\) and \(\eta_{app}^y\) for the two calculation methods intersect twice. For the fiber volume fractions \(c_F = 5\%\) and \(c_F = 25\%\), the first intersection occurs at shear rates \(\dot{\gamma} \approx 10^2 \text{ s}^{-1}\) while the second intersection occurs in the shear rate interval \([10^4, 5 \cdot 10^4] \text{ s}^{-1}\), depending on the fiber volume fraction \(c_F\). For higher fiber volume fractions \(c_F\) the second intersection occurs at lower macroscopic shear rates \(\dot{\gamma}\), because the decreased fiber to fiber distance leads to higher microscopic shear rates. Consequently, we observe an earlier transition into the second Newtonian regime at the shear
