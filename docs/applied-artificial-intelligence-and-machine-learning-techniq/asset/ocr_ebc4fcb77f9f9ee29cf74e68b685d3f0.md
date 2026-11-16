+   5: Set transient input duration `transient_duration` and value `transient_value`
+   6: Set noise mean `noise_mean` and standard deviation `noise_stddev`
+   7: Compute number of simulation steps `num_steps` as `t end/dt`
+   8: `for t = 1 to num_steps do`
+   9: `if t <= transient_duration then`
+   10: Apply transient input: `I[1: num_inputs] = transient_value`
+   11: `else`
+   12: Set input to zero: `I[1: num_inputs] = 0`
+   13: `end if`
+   14: Initialize rate of change `dx_dt` to zeros
+   15: `for i = 1 to N do`
+   16: Compute self-excitatory term: `self_excitation = (B - x[i]) · f(x[i])`
+   17: Compute inhibitory term: `inhibition = (D + x[i]) · Σ_{k≠i} f(x[k])`
+   18: Compute external input term: `input_term = I[i]`
+   19: Update rate of change: `dx_dt[i] = -x[i] + self_excitation - inhibition + input_term`
+   20: `end for`
+   21: Add Gaussian noise to rate of change: `noise = noise_mean + noise_stddev · randn(N, 1)`
+   22: Update neuron activities with noise: `x = x + dt · (dx_dt + noise)`
+   23: `end for`

The following parameters were used in the simulation of the shunting network (Table 9.1). In addition to simulating the network, we assess its stability using two criteria given Equations 9.12 and 9.15.

The non-divergence condition ensures that the network's activity does not grow unbounded, indicating stability or poor network behavior. The Lyapunov stability condition assesses stability by examining whether small perturbations will lead to divergence or remain bounded. By evaluating these conditions, we can determine if the network operates within a stable regime or if its dynamics might lead to instability. Comparing these criteria helps in understanding the impact of different parameters and input values on the network's stability.

Simulation results for the network are shown in Figures 9.1 and 9.2, which show the dynamics of the network as well as compare the analytical steady-state prediction with the ones obtained from simulation, respectively.

# 9.3.2 SEQUENTIAL PRESENTATION

The simulation results, shown in Figure 9.3, highlight the network's dynamics under sequential input presentation with parameters `B = 2.2` and `D = 0.1`, and with eight sequential inputs. The figure demonstrates how the neuron activations evolve over time, reflecting the network's ability to process and retain information. Notably, the network