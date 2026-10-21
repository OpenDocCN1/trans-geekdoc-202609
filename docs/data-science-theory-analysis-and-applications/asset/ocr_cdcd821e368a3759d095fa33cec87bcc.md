![](bbox=[0.25, 0.13, 0.78, 0.22])

∑ = F3
Γ_old = F3.oldvalue(-628.257)
Γ_new = F3.newvalue(-851.477)
T = time(1 min)
Transition Function(F) = F(q1 * ∑ * Γ_old * Γ_new * T) => q2
Present State(q1) = “Neutral” and Final State (q2) = “Depressed”

# FIGURE 10.11 State transition from neutral (starting) state to depressed (final) state with correct inputs.

![](bbox=[0.25, 0.48, 0.78, 0.57])

∑ = PO7
Γ_old = PO7.oldvalue(-861.501)
Γ_new = PO7.newvalue(-706.549)
T = time(1 min)
Transition Function(F) = F(q1 * ∑ * Γ_old * Γ_new * T) => q2
Present State(q1) = “Neutral” and Final State (q2) = “Harmony”

# FIGURE 10.12 State transition from neutral (starting) state to harmony (final) state with correct inputs.

![](bbox=[0.28, 0.83, 0.8, 0.93])

∑ = T7
Γ_old = T7.oldvalue(-861.501)
Γ_new = T7.newvalue(-706.549)
T = time(1 min)
Transition Function(F) = F(q1 * ∑ * Γ_old * Γ_new * T) => q2
Present State(q1) = “Neutral” and
Final State (q2) = “No Final State”

# FIGURE 10.13 State transition from neutral (starting) state to the same state with wrong inputs.

execute our transition function algorithm. The next state form of the finite machine is verified using the prediction of the classification algorithm. We describe the the state channels table using both initial and final values of the machine in Table 10.4 and illustrate the process of state transition in Figures 10.9–10.13. The state-transition machine (M) is described using six tuples mentioned in the proposed work section.