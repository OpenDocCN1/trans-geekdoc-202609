So we can conclude the following:

+   - In the case where $B$ is large enough to overpower the effects of inhibition $D$, both stability conditions are satisfied.
+   - The Lyapunov condition tends to be more forgiving than the non-divergence condition. It allows for local neuron activity levels to compensate for global inhibitory effects, especially when individual neuron activity \(x[n]\) is low relative to \(B\).
+   - However, if $D$ is large and $B$ is relatively small, or if the number of active neurons \(n\) grows large, the non-divergence condition is violated before the Lyapunov condition fails.

The fact that the Lyapunov stability condition can be satisfied while the non-divergence condition is not indicates the following:

+   - **Local Stability**: The Lyapunov condition reflects local stability based on the current state of neuron activities, while the non-divergence condition requires global stability that accounts for the entire network’s dynamics.
+   - **Potential for Transient Stability**: When the Lyapunov condition is satisfied but the non-divergence condition is not, the system may exhibit transient stability or short-term convergence to an equilibrium before eventually diverging.
+   - **Network Resilience to Noise**: The Lyapunov condition could suggest that the network can tolerate small disturbances or noise, as it reflects the system’s capacity to return to stability under certain circumstances.

The Lyapunov stability condition is more sensitive to the current state of neuron activities and can allow the network to remain stable in some situations where the non-divergence condition might indicate global instability. However, when the non-divergence condition is violated, the network is more likely to exhibit long-term instability, even if local stability conditions hold temporarily.

# 9.3 RESULTS

In this section, we present the algorithm used to simulate the dynamics of a shunting recurrent network. The pseudocode provided next outlines the steps for updating neuron activities, applying external inputs, and checking stability conditions over time.

# 9.3.1 SIMULATION FOR SIMULTANEOUS INPUTS TO THE NETWORK

```
Algorithm 1 Shunting Recurrent Neural Network Simulation
1: Input: Number of neurons \(N\), number of inputs \(num\_inputs\), parameters \(B\), \(D\), time step \(dt\), simulation duration \(l\_end\)
2: Output: Stability condition statuses
3: Initialize neuron activities \(x\) with random values
4: Initialize external inputs \(I\) as zeros
```