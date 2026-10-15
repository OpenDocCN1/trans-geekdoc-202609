signals obtained with no disturbance are shown in Figure 17.4c. The stabilization results for aseptic cases with disturbance and ineffective treatment samples have been illustrated in Figure 17.5. The stabilized dynamics of AIR have been given in Figure 17.5a and Figure 17.5b, respectively. Drug dosage inputs are illustrated in Figure 17.5c. Total reward values for the aseptic death case are given in Figure 17.4d and Figure 17.5d, respectively.

# 17.4.2 Septic Death Case: RBF Value Approximation-Based Treatments

Value approximation-based RL is preferred when there are infinite states of continuous time systems. When the inflammation dynamics exceed their limits in the septic case, value approximation-based RL aims to minimize P and D levels by using the lowest drug doses. The initial conditions are chosen as P = 1, N* = 0, D = 0, C_A = 0.125 , k_pg = 0.6 for the septic scenario parameters of the AIR model. The value approximation-based reinforcement learning inflammation control results for the septic

![](bbox=[0.1, 0.45, 0.38, 0.68])

![](bbox=[0.48, 0.45, 0.78, 0.68])

![](bbox=[0.1, 0.7, 0.38, 0.9])

![](bbox=[0.48, 0.7, 0.78, 0.9])

(a) Pathogen and Tissue Damage.

(b) Activated Phagocytes and Anti-inflammatory Mediator.

(c) Drug dosages.

(d) Total rewards.

FIGURE 17.5 Aseptic death case with disturbance and ineffective treatment samples: dynamic Q-learning control.