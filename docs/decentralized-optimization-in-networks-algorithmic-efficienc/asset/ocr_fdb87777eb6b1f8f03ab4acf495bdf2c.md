![](bbox=[0.235, 0.125, 0.835, 0.305])

# FIGURE 8.6

(a) The comparison where the x-axis is the iteration; (b) The comparison where the x-axis is the number of gradient evaluations.

algorithm requires fewer gradient computations (\nabla Q_i) than the decentralized method in [24], leading to a reduction in computational overhead.

# ## 8.5.2 Example 2: IEEE 118-bus system

In this scenario, the proposed algorithm is employed to solve the Economic Dispatch Problem (EDP) on the IEEE 118-bus system [46] to further assess its performance. The IEEE 118-bus system, depicted in Fig. 8.7 [46], comprises 54 generator buses, along with a segment of load buses and transmission lines. Each generator i’s local cost function is quadratic, represented by J_i(p_i) = c_i p_i^2 + b_i p_i + a_i, where the coefficients a_i range from 6.78 to 74.33, {b_i} between 8.3391 and 37.6968, and {c_i} spans 0.0024 to 0.0697, measured in $, $/MW, and $/MW^2, respectively [46]. It is important to note that the load buses generate zero power due to the absence of associated power generation units. The generation capacities of the generators are constrained within the interval [p_i^{min}, p_i^{max}], where p_i^{min} lies between 5 and 150 MW, and p_i^{max} falls within 150 to 400 MW. The total demand in this system amounts to 4242 MW. For this scenario, we set the local step-size \gamma_i' = 1 / \Gamma_i' and the bounds of the added conditional noises \hat{e}^i = 20/t^{2.1} for all i = 1, ..., 54, and t \ge 0. Additionally, for simplicity, the random sleep probability is set to 0.8, as in Example 1.

Subsequently, the simulation results for the IEEE 118-bus system are presented in Figs. 8.8 and 8.9, illustrating the convergence of the proposed algorithm. As indicated by Figs. 8.8 and 8.9, after several iterations, the proposed algorithm successfully identifies the optimal generation power for each generator while addressing the concerns of privacy protection and computational efficiency, thereby achieving the minimum total generation cost for the EDP.