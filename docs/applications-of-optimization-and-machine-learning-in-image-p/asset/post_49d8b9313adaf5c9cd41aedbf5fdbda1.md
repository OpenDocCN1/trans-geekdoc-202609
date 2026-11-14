

## 3.3.2.4 Random Mode

Due to the discrete nature of smell molecules, their concentrations and intensities can change over time if they are spread out over a vast area relative to the search space. As a result, trailing becomes more difficult, and the scent is lost, making it difficult for an agent to follow. The agent may be unable to continue trailing at this moment, resulting in a local minimum. When this occurs, the agent enters a random mode:

\( x_N^d \left( t+1 \right)=x_N^d \left( t \right)+r_4 * SL \) (3.22)

Random number \( r_4 \) penalizes the value of \( SL \) by stochastically increasing the step length of \( S \). The molecule performs a step at random using Eq. (3.22) if the agent loses its track or if the trailing mode is unable to obtain the best fitness or locate the source of the smell.

As a result, the molecule will always try to retain its position on the search path that has the most concentration of the smell molecules. As previously noted, this information is used when trailing in Eq. (3.21) as the agent keeps track of its current location, \( x_{gbest}^d \left( t \right) \) agent and worst positions \( x_{worst}^d \left( t \right) \) agent, although the agent is restricted to searching only within the viable region by the optimization problem.

## 3.4 RESULTS AND DISCUSSIONS

The transmission power of −30 [dBm] has been chosen as the minimum for the experiments. The maximum power is set to offer a connection across a distance of 28.284 [m] within the random distribution area, while the transmission frequency is set to give the lowest attenuation value in the 915 [MHz] range, which is generally utilized in WSN applications. Finally, the sensitivity, which is defined as the minimum received power necessary for information recovery, is set at −60 [dBm]. Table 3.1 lists all the parameter values used in this investigation. There are only 10 possible scenarios according to [14]. However, scenarios 1 and 3, scenarios 2 and 5, scenarios 4 and 6 and scenarios 7 and 9 are identical. As a result, in this paper total scenarios are reduced from 10 to 6. The experiments were carried out on the same platform. MATLAB® R2022a, running on Windows 10 (64-bit), with an Intel® Core® i5-5000 processor clocked at 2.9 GHz and 8 GB of RAM, was used to compare the output of each algorithm.

| Parameter | Value |
|---|---|
| Total number of sensor nodes | 20 |
| Power range of sensor transmission | −30 [dBm] |
| power frequency of sensor transmission (f) | 915 [MHz] |
| Sensor's random locations area (L×L) | 20 [m] × 20 [m] |
| Sensitivity of sensor (\( P_{th} \)) | −60 [dBm] |

The SOA and BOA methods have been developed and applied to the scenarios studied in [14]. There were six different scenarios in the paper, each with 20 sensors dispersed across a 20 m² area. Various well-known algorithms, such as Particle Swarm Optimization (PSO), Simple Method (SM), Electrostatic Static Discharge Algorithm (ESDA), Differential Evolution (DE), Genetic Algorithm (GA), Electromagnetism-like algorithm (EM), Black Hole (BH) algorithm, Sine Cosine Algorithm (SCA) and Salp Swarm Algorithm (SSA), have been examined for comparison purposes. However, it's worth noting that there are only ten possibilities in [14]. And it is observed that the power transmission range of deployed sensors by investigated methods is within the considered range of –30 [dBm]. In order to solve any optimization problem, it is essential to first set the algorithm's parameters. Parameter sensitivity analysis is done before the SOA and BOA algorithms are executed and then values are allocated, as shown in Table 3.2.

| Algorithm | Parameter | Description | Assigned Value |
|---|---|---|---|
| HCCPSOBOA | \(\Phi_1, \Phi_2\) | Control parameters | 2.05 |
| | \(N\) | Total number of agents | 50 |
| | \(d\) | Dimension | 20 |
| | Maxit | Total number of maximum iterations | 1000 |
| | \(c\) | Sensory modality index | 0.01 |
| | \(a\) | Power exponent | 0.1 |
| | \(p\) | Probability switch | 0.5 |
| | \(V_{max} V_{min}\) | Velocity limits for agents | 5, -5 |

For a fair comparison, each scenario has been run 20 times by SOA and BOA algorithms, and the best results were presented in Table 3.3. From Table 3.3, it is clear that the BOA results are marginally better than the ESDA results. But the results of SOA are magnificent when compared to BOA, ESDA, and all other existing results. The best results obtained by SOA for all scenarios are bolded in Table 3.3. The reason was very clear,

### TABLE 3.3 Results Comparison Using Different Algorithms.

| Scenario | SOA | BOA | ESDA | PSO | SM | DE | GA | BH | EM | SSA | SCA |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Scenario 1 | -5.866 | -5.184 | -5.044 | -3.624 | 2.827 | -4.026 | -0.343 | Inf | Inf | -4.074 | 4.353 |
| Scenario 2 | -8.613 | -7.857 | -7.683 | -6.669 | -2.699 | -6.758 | -1.090 | -6.798 | 7.214 | -5.841 | 7.636 |
| Scenario 3 | -6.947 | -6.504 | -6.260 | -3.353 | 2.827 | -5.725 | -2.499 | -5.112 | 5.878 | -5.161 | 7.610 |
| Scenario 4 | -5.949 | -5.415 | -5.044 | -5.113 | 3.842 | -4.014 | -0.529 | -4.281 | Inf | -3.389 | 8.473 |
| Scenario 5 | -7.973 | -7.458 | -7.288 | -6.669 | -2.744 | -6.475 | -1.639 | -6.031 | 3.445 | -3.400 | 5.682 |
| Scenario 6 | -5.390 | -4.763 | -4.507 | -5.226 | 3.865 | -3.363 | -1.766 | Inf | Inf | -0.541 | 6.532 |

except that, for SOA, all other experimented algorithms were performed alone according to their evolution strategy. The best values marked by SOA are –5.866 [dBm], -8.613 [dBm], -6.947 [dBm], -5.949 [dBm], -7.973 [dBm] and -5.390 [dBm] for scenarios 1 to 6, respectively, and among all algorithms BH and EM are poorly performed. The main reason is the SOA algorithm that takes advantage of the different phases during convergence for solving high-dimensional optimization problems.

Sketches of convergence curves obtained from the implemented SOA and BOA algorithms for six scenarios are shown in Figure 3.2. The number of iterations and the objective function value are shown on the x- and y-axes respectively. The following observations can be drawn from Figure 3.2. For scenario 1, the SOA algorithm converged the best solution at the 728th iteration, while BOA converged at 466. For scenario 2, SOA and BOA are converged at 755 and 527; for scenario 3, SOA and BOA are converged at 707 and 509; for scenario 4, SOA and BOA are converged at 730 and 649; for scenario 5, SOA and BOA are converged at 860 and 781; and for scenario 6, SOA and BOA are converged at 870 and 395, respectively. The average convergences for SOA and BOA are at 775 and 554 iterations, respectively. The average convergence time for BOA is 5.22 s, whereas SOA is 10.54 s because of the strong evolutionary process. Table 3.4 summarizes the SOA- and BOA-derived sensor transmission powers for the various scenarios under consideration. Each sensor has a different transmission power than the other sensors. The transmission power varies from scenario 1 to scenario 6 depending on the scenario. The average minimum and maximum sensor transmission power from scenarios 1–6 are –20.5 dBm and –23.9 dBm for SOA, –20.1 dBm and –23.8 dBm for BOA algorithms.

### Scenario-1

### Scenario-2

### Scenario-3

### Scenario-4

### Scenario-5

### Scenario-6

### FIGURE 3.2 Comparison of convergence characteristics of investigated algorithms for the scenarios 1–6.

### TABLE 3.4 Each Sensor Transmission Power for Six Different Scenarios Obtained by BOA and SOA

| | BOA | | | | | | SOA | | | | |
|---|---|---|---|---|---|---|---|---|---|---|---|
| | 1 | 2 | 3 | 4 | 5 | 6 | 1 | 2 | 3 | 4 | 5 | 6 |
| Sensor 1 | -17.6 | -18.7 | -21.8 | -26.3 | -25.7 | -14.7 | -17.9 | -19.2 | -21.9 | -26.7 | -25.9 | -15.1 |
| Sensor 2 | -21.7 | -25.7 | -28.8 | -15.7 | -28.7 | -16.4 | -22.0 | -26.2 | -28.9 | -16.1 | -28.9 | -16.8 |
| Sensor 3 | -16.7 | -21.7 | -28.8 | -28.6 | -22.7 | -25.7 | -17.0 | -22.2 | -28.9 | -29.0 | -22.9 | -26.1 |
| Sensor 4 | -28.7 | -16.7 | -28.8 | -28.2 | -18.7 | -19.2 | -29.0 | -17.2 | -28.9 | -28.6 | -18.9 | -19.6 |
| Sensor 5 | -25.7 | -19.7 | -21.8 | -15.7 | -22.6 | -19.2 | -26.0 | -20.2 | -21.9 | -16.1 | -22.8 | -19.6 |
| Sensor 6 | -13.0 | -25.7 | -22.8 | -16.4 | -17.6 | -22.7 | -13.3 | -26.2 | -22.9 | -16.8 | -17.8 | -23.1 |
| Sensor 7 | -18.7 | -21.7 | -28.8 | -16.7 | -16.1 | -25.7 | -19.0 | -22.2 | -28.9 | -17.1 | -16.3 | -26.1 |
| Sensor 8 | -16.7 | -16.4 | -14.9 | -28.7 | -28.7 | -22.7 | -17.0 | -16.9 | -15.0 | -29.1 | -28.9 | -23.1 |
| Sensor 9 | -21.7 | -19.2 | -28.8 | -16.7 | -28.7 | -28.7 | -22.0 | -19.7 | -28.9 | -17.1 | -28.9 | -29.1 |
| Sensor 10 | -21.7 | -22.7 | -25.8 | -14.7 | -28.7 | -13.7 | -22.0 | -23.2 | -25.9 | -15.1 | -28.9 | -14.1 |
| Sensor 11 | -28.7 | -28.6 | -28.8 | -17.6 | -25.7 | -21.4 | -29.0 | -29.1 | -28.9 | -18.0 | -25.9 | -21.8 |
| Sensor 12 | -28.7 | -28.7 | -28.8 | -28.7 | -25.7 | -28.5 | -29.0 | -29.2 | -28.9 | -29.1 | -25.9 | -28.9 |
| Sensor 13 | -21.7 | -16.2 | -9.7 | -28.2 | -28.7 | -19.7 | -22.0 | -16.7 | -9.8 | -28.6 | -28.9 | -20.1 |
| Sensor 14 | -21.7 | -25.7 | -28.8 | -18.7 | -16.2 | -22.7 | -22.0 | -26.2 | -28.9 | -19.1 | -16.4 | -23.1 |
| Sensor 15 | -28.7 | -22.7 | -25.8 | -22.7 | -16.2 | -22.7 | -29.0 | -23.2 | -25.9 | -23.1 | -16.4 | -23.1 |
| Sensor 16 | -10.7 | -28.7 | -21.8 | -22.7 | -19.2 | -19.7 | -11.0 | -29.2 | -21.9 | -23.1 | -19.4 | -20.1 |
| Sensor 17 | -21.7 | -22.7 | -28.8 | -19.2 | -28.7 | -19.6 | -22.0 | -23.2 | -28.9 | -19.6 | -28.9 | -20.0 |
| Sensor 18 | -28.7 | -28.7 | -22.8 | -15.7 | -19.2 | -22.7 | -29.0 | -29.2 | -22.9 | -16.1 | -19.4 | -23.1 |
| Sensor 19 | -16.7 | -22.7 | -17.7 | -16.4 | -18.7 | -19.2 | -17.0 | -23.2 | -17.8 | -16.8 | -18.9 | -19.6 |
| Sensor 20 | -21.7 | -8.1 | -6.8 | -5.4 | -25.7 | -17.6 | -22.0 | -8.6 | -6.9 | -5.8 | -25.9 | -18.0 |
| Avg. Trans. Power | -21.6 | -22.0 | -23.8 | -20.1 | -23.1 | -21.1 | -22.3 | -22.5 | -23.9 | -20.5 | -23.3 | -21.5 |

### 3.4.1 Computational Complexity

The complexity of computation of HCCPSOBOA is O(t(N × D)) where t denotes the quantity of iterations, D demonstrates the quantity of variables, and N indicates the number of solutions. This computation’s complexity is comparable to that of CCPSO, BOA, GA, DE, EM and SCA. However, the computational complexity of SSA is O(t(N × log(N))) in the average case and O(t(N^2)) in the worst case, and for BH is O(t(N^2 × D)). This indicates that the complexity of the computational SCA and BH is worse than that of other algorithms due to the sorting of solutions in every iteration.

## 3.5 CONCLUSIONS

The SOA and BOA approaches are presented in this paper to determine the transmission power of various sensor nodes to conserve sensor

