# Table 8.2 Algorithmic and ML packages for causal discovery (full description of each package and incorporate algorithms can be found in its original source).

| Packages for causal discovery | |
|---|---|
| **CausalNex** | [https://causalnex.readthedocs.io/en/latest/index.html]
A Python library that combines ML and domain expertise for causal reasoning. |
| **Pcalg** | [https://cran.r-project.org/web/packages/pcalg/index.html]
An R package for causal discovery that includes:
Constraint-based structure learning algorithms:
• PC
• FCI
• Really fast causal inference (RFCI)
• Greedy interventional equivalence search (GIES)
Score-based structure learning algorithms:
• GES
• Greedy interventional equivalence search (GIES)
Hybrid structure learning algorithms:Adaptively restricted GES (ARGES) |
| **bnlearn** | [https://www.bnlearn.com]
• A Python package for causal discovery that includes:
Constraint-based structure learning algorithms:
• PC (the stable version)
• Grow-Shrink (GS)
• Incremental Association Markov Blanket (IAMB)
• Fast Incremental Association (Fast-IAMB)
Score-based structure learning algorithms:
• Hill Climbing (HC)
• Tabu Search (Tabu)
Hybrid structure learning algorithms:
• Max-Min Hill Climbing (MMHC)
• Hybrid HPC (H2PC)
• General 2-Phase Restricted Maximization (RSMAX2)
Local discovery algorithms:
• Chow-Liu
• ARACNE
Bayesian network classifiers:
• Naive Bayes
• Tree-Augmented naive Bayes (TAN) |
| **Tetrad**
**Py-causal**
**R-causal** | [https://www.ccd.pitt.edu/data-science]
Software, Python, and R packages created by the Center for Causal Discovery at Pittsburgh University. |
| **Causal discovery toolbox** | [https://fentechsolutions.github.io/CausalDiscoveryToolbox/html/data.html]
Python and R packages for causal discovery. |
| **TIGRAMITE** | [https://github.com/jakobrunge/tigramite]
A Python package for causal discovery for time series datasets. |

The simplest approach is to average the results of the flexural capacities of _Group A_ and do the same for _Group B_ and compare the average (or expectation (_E_)) from each group. Mathematically, this results in the following:
The difference in average (expectation) between

Group A and Group B = _E_ [ Y<sub>1</sub> -Y<sub>0</sub> ] (8.4)
Similarly, one can use the Pearlian approach (i.e., _do_-calculus) by applying the do-operator (see Equation 8.5).<sup>88</sup>

[ Y | do (T =1)] - _E_ [ Y | do (T = 0 ) ] (8.5)

Both Equations 8.4 and 8.5 estimate the Average Treatment Effect (ATE).