conditions within a δ-neighborhood of the equilibrium point, we require that the equilibrium point **q**ₑ is approached exponentially according to ||**q**(t) − **q**ₑ|| < α||**q**₀ − **q**ₑ|| exp(−βt) for all times, with α and β as positive constants. Systems of this type are referred to as **exponentially stable** and return to the equilibrium state within monotonically decreasing bounds when started in a δ-neighborhood of **q**ₑ.

Figure 13.2 illustrates the concept of Lyapunov, asymptotic and exponential stability schematically for a dynamical system with two dependent variables.

# For Hydrodynamic Applications

The definitions of Lyapunov have been adopted for hydrodynamic stability calculations; only minor modifications have been added to quantify concepts observed in fluid systems. We will follow Joseph (1976) and introduce four variants of hydrodynamic stability. These definitions require the introduction of a disturbance measure, which we take as the perturbation kinetic energy E.

The first definition (**asymptotic stability**) states that an equilibrium solution is asymptotically stable, if the perturbation energy satisfies

$$\lim_{t\to\infty} \frac{E(t)}{E(0)} \to 0.\tag{13.1}$$

This definition coincides with Lyapunov’s asymptotic stability definition, where the distance to the equilibrium state is measured by the kinetic energy of the perturbation. This definition, however, does not specify an ε-neighborhood bounding the distance from equilibrium as the equilibrium state is approached.

The second definition (**conditional stability**) accounts for the fact that an initial energy threshold value has to be respected for asymptotic stability. It states that an equilibrium is conditionally stable, if there exists a positive energy level δ such that asymptotic stability is observed as long as the initial energy of the perturbation falls below δ, that is, E(0) < δ.

A further restriction on this concept yields the third definition (**global stability**): for an infinite threshold value δ, the equilibrium is said to be globally stable. In other words, the equilibrium state is attracting trajectories, no matter how far we start from the equilibrium point.

Finally, even further constraints lead to the fourth definition (**monotonic stability**). We state that an equilibrium is monotonically stable, if the energy of the perturbation decreases monotonically for all times. Mathematically, this condition requires

$$\frac{dE}{dt} < 0 \qquad \text{for all} \quad t > 0.\tag{13.2}$$

# The Role of Time

It is interesting to note that none of the previous definitions, whether set forth by Lyapunov or proposed by Joseph (1976), contains a characteristic timescale. Instead, time is either absent in the definition, or an infinite time horizon is envisioned. This lack of restriction on the time it takes to return to the equilibrium point and thus to confirm stability, suggests that such-defined stability measures (such as growth rates,