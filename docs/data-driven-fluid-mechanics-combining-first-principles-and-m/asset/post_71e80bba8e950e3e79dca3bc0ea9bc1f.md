
conditions within a δ-neighborhood of the equilibrium point, we require that the equilibrium point **q**ₑ is approached exponentially according to ||**q**(t) − **q**ₑ|| < α||**q**₀ − **q**ₑ|| exp(−βt) for all times, with α and β as positive constants. Systems of this type are referred to as **exponentially stable** and return to the equilibrium state within monotonically decreasing bounds when started in a δ-neighborhood of **q**ₑ.

Figure 13.2 illustrates the concept of Lyapunov, asymptotic and exponential stability schematically for a dynamical system with two dependent variables.

## For Hydrodynamic Applications

The definitions of Lyapunov have been adopted for hydrodynamic stability calculations; only minor modifications have been added to quantify concepts observed in fluid systems. We will follow Joseph (1976) and introduce four variants of hydrodynamic stability. These definitions require the introduction of a disturbance measure, which we take as the perturbation kinetic energy E.

The first definition (**asymptotic stability**) states that an equilibrium solution is asymptotically stable, if the perturbation energy satisfies

$$\lim_{t\to\infty} \frac{E(t)}{E(0)} \to 0.\tag{13.1}$$

This definition coincides with Lyapunov’s asymptotic stability definition, where the distance to the equilibrium state is measured by the kinetic energy of the perturbation. This definition, however, does not specify an ε-neighborhood bounding the distance from equilibrium as the equilibrium state is approached.

The second definition (**conditional stability**) accounts for the fact that an initial energy threshold value has to be respected for asymptotic stability. It states that an equilibrium is conditionally stable, if there exists a positive energy level δ such that asymptotic stability is observed as long as the initial energy of the perturbation falls below δ, that is, E(0) < δ.

A further restriction on this concept yields the third definition (**global stability**): for an infinite threshold value δ, the equilibrium is said to be globally stable. In other words, the equilibrium state is attracting trajectories, no matter how far we start from the equilibrium point.

Finally, even further constraints lead to the fourth definition (**monotonic stability**). We state that an equilibrium is monotonically stable, if the energy of the perturbation decreases monotonically for all times. Mathematically, this condition requires

$$\frac{dE}{dt} < 0 \qquad \text{for all} \quad t > 0.\tag{13.2}$$

## The Role of Time

It is interesting to note that none of the previous definitions, whether set forth by Lyapunov or proposed by Joseph (1976), contains a characteristic timescale. Instead, time is either absent in the definition, or an infinite time horizon is envisioned. This lack of restriction on the time it takes to return to the equilibrium point and thus to confirm stability, suggests that such-defined stability measures (such as growth rates,

![](img/ddadb1d3eaa6f9576eea68f95d453bca_281_0.png)

Figure 13.3 Bifurcation behavior, illustrated in the amplitude-parameter plane. In the supercritical bifurcation scenario (a), finite-amplitude states exist only for parameter values p larger than the critical one, p_crit. In the subcritical bifurcation scenario (b), finite-amplitude states exist at parameter values p where the base state has not yet gone unstable to infinitesimal perturbations, that is, for p < p_crit.

frequencies, modal shapes) may misrepresent the dynamic features of a flow that is characterized and dominated by fluid processes on finite timescales.

## Critical Parameters

The equations governing the temporal evolution of the state variable, denoted symbolically by the function f, commonly contain a variety of physical parameters often expressed as nondimensional numbers (such as the Reynolds number, Rayleigh number, Mach number, etc.) or parameters linked to the shape of the disturbances (such as their wavenumbers in homogeneous coordinate directions). The stability properties thus depend on these parameters as well, and a specific perturbation may be stable at one parameter setting, but become unstable at another. The parameter value(s) at which this transition from stability to instability occurs are known as critical parameters. Different critical parameters can be computed, depending on the chosen definition of stability; for example, the critical Reynolds number for monotonic stability of plane channel flow is Re_c = 49.6, while the critical Reynolds number for asymptotic stability of the same flow is Re_c = 5772.2, where the Reynolds number is based on the centerline base velocity and the half-channel height (Joseph & Carmi 1969, Orszag 1971).

## Bifurcation Behavior

Once we surpass the critical parameter, an instability ensues and the disturbance grows in amplitude/energy until nonlinearities saturate the growth and establish a new, nonlinear equilibrium state of finite amplitude. Finite-amplitude states, however, can also exist (due to a conditional stability; see the earlier definition) at parameter values below the critical one.

The existence of these finite-amplitude states determines the bifurcation behavior of the flow (see also Chapter 10 for a discussion of bifurcations in dynamical systems). Two cases have to be distinguished: supercritical and subcritical bifurcation behavior. In the supercritical case, finite-amplitude states exist only past the point (in parameter space) where the equilibrium state has gone asymptotically unstable to infinitesimal perturbations. This situation is illustrated in Figure 13.3(a). Infinitesimal perturbations below p_crit are asymptotically stable; for p > p_crit, finite-amplitude states exist owing to an asymptotic instability of the infinitesimal state (dashed line). In the subcritical case (see Figure 13.3(b)), we have a parameter regime where finite-amplitude states coexist with asymptotically stable infinitesimal states. In this regime, the infinitesimal state is conditionally stable: for an initial energy below a critical value, the perturbation returns to the infinitesimal state (open circle); while for an initial energy surpassing a threshold value (indicated by the dashed blue curve), a higher-energy state is approached at the same parameter value p (closed circle). After passing p_crit, this threshold value is zero, indicating that infinitesimal energy is necessary to approach the higher-energy state via an asymptotic instability.

Examples of supercritical bifurcation behavior in fluid systems include Rayleigh-Bénard convection and Taylor–Couette flow (flow between two differentially rotating coaxial cylinders) within certain parameter regimes, while wall-bounded shear flows such as plane Poiseuille, plane Couette, or pipe flow are governed by subcritical bifurcations.

## Temporal, Spatial, Spatio-temporal Evolution

While many stability calculations use time as the evolution coordinate and treat disturbances as temporally evolving entities, there are configurations where a different description is more appropriate. For example, disturbance evolution in flow past a roughness element is more aptly described as a spatial problem. In this case, the proper mathematical formulation is a signaling problem, rather than a temporal initial-value problem. In a signaling problem, a harmonic or steady point source drives the flow perpetually, and the instability manifests itself as amplitude growth as we move downstream from the disturbance source. The evolution direction is the spatial direction given by a representative streamline of the base flow. In this case, the time coordinate is often taken as harmonic and can be Fourier transformed.

Besides the purely temporal and the purely spatial approach, we can also formulate a general spatio-temporal approach, where we postulate a spatially and temporally localized initial condition and track its development in space and time, without assumptions on either evolution direction. Figure 13.4 illustrates the three concepts of perturbation evolution: temporal, spatial, and spatio-temporal. Each concept has to be motivated by the specific flow configuration and requires corresponding mathematical tools for its analysis.

## 13.3 General Formulation

Most treatises on hydrodynamic stability theory start with many simplifying assumptions about the flow (steady, parallel, unidirectional, incompressible base flow of Newtonian fluid), guiding the reader toward a set of mathematical techniques for the solution of the resulting stability equations. Only in a second step are some of the initial assumptions relaxed or eliminated, leading to additional mathematical complications. This simple-to-complex route has also been the historic route: simplifications
