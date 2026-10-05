allows for a physical interpretation of the obtained stochastic dynamics$^{41}$ that generates Rouse-like motion of the chains$^{12}$ in the simulation of dense polymer melts.

# SIMULATION METHODS

The simulation methods most commonly used for atomistic or coarse-grained molecular models are MD simulations and MC simulations. In MD simulations, Newton's equations of motion are integrated to generate a trajectory (a history) of the model system. The method can capture all vibrational and relaxational processes contained in the chosen model Hamiltonian. MC is a stochastic simulation method that can capture relaxational and diffusive processes. MC is commonly used to generate equilibrium configurations for either sampling of thermodynamic and structural properties or to provide starting configurations for ensuring MD runs are used to evaluate the dynamics of the model system. In the following discussion, we will examine the two methods with regard to their two main applications—equilibration and generation of trajectories for dynamic measurements, respectively.

# Monte Carlo Method

The MC method denotes the configuration space of a model and generates a discrete-time random walk through configuration space following a master equation$^{41,51}$

```
$P(x,t_n) = P(x,t_{n-1}) + \sum_{x'} W(x 	o x')P(x',t_{n-1}) - \sum_{x'} W(x 	o x')P(x,t_{n-1})$
```

Here $x,x'$ denote two configurations of the system (specified, for instance, by the set of coordinates of all atoms $\{\vec{r}_n\}$ or the position of one end for all chains and all bond lengths, bond angles, and torsion angles $\{\vec{r}_i, l_i, 	heta_i^\alpha, \phi_i^\alpha\}$, where $\alpha = 1, \dots, M$ runs over all chains and the indices $i, j, k$ run over all internal degrees of freedom of chain. The transition rates $W(x 	o x')$ are chosen to fulfill the detailed balance condition

```
$W(x 	o x')P_{eq}(x') = W(x 	o x)P_{eq}(x)$
```

which ensures an equal probability flow from $x$ to $x'$ as in the reverse direction in equilibrium. Here

```
$P_{eq}(x) = \frac{1}{Z}\exp\{-eta H(x)\}$
```