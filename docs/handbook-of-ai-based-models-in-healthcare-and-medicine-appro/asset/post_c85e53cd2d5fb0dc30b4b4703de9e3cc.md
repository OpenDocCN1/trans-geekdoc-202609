
septic consequences. Therefore, in this chapter, dynamic Q-learning for the aseptic case and value approximation-based reinforcement learning for the septic case were designed.

### 17.4.1 Aseptic Death Case: Dynamic Q-Learning-Based Treatments

In simulations for the AIR model, the measured output states and the applied control dosages are assumed in discrete levels. If the inflammation dynamics exceed their limits, it is crucial to restore the patient to a healthy case using optimal treatment, or the immune system will be unable to counteract the increased pathogen attack. The initial conditions of these variables are taken as P =1.5, N* =0, D =0, C_A =0.125 , and k_pg =0.3, respectively. The numerical values related to dynamic Q-learning-based inflammation control for an aseptic case without disturbance and ineffective treatment samples have been illustrated in Figure 17.4. Figure 17.4a and Figure 17.4b show stabilized variables of the AIR for the aseptic scenario. u_a and u_p therapy signals obtained with no disturbance are shown in Figure 17.4c. The stabilization results for aseptic cases with disturbance and ineffective treatment samples have been illustrated in Figure 17.5. The stabilized dynamics of AIR have been given in Figure 17.5a and Figure 17.5b, respectively. Drug dosage inputs are illustrated in Figure 17.5c. Total reward values for the aseptic death case are given in Figure 17.4d and Figure 17.5d, respectively.

![](img/a2fc2296b12812e9151e817bff1de16d_359_0.png)
(a) Pathogen and Tissue Damage.

![](img/a2fc2296b12812e9151e817bff1de16d_359_1.png)
(b) Activated Phagocytes and Anti-inflammatory Mediator.

![](img/a2fc2296b12812e9151e817bff1de16d_359_2.png)
(c) Drug dosages.

![](img/a2fc2296b12812e9151e817bff1de16d_359_3.png)
(d) Total rewards.

FIGURE 17.4 Aseptic death case without disturbance and ineffective treatment samples: dynamic Q-learning control.

![](img/a2fc2296b12812e9151e817bff1de16d_360_0.png)
![](img/a2fc2296b12812e9151e817bff1de16d_360_1.png)
![](img/a2fc2296b12812e9151e817bff1de16d_360_2.png)
![](img/a2fc2296b12812e9151e817bff1de16d_360_3.png)
(a) Pathogen and Tissue Damage.
(b) Activated Phagocytes and Anti-inflammatory Mediator.
(c) Drug dosages.
(d) Total rewards.

FIGURE 17.5 Aseptic death case with disturbance and ineffective treatment samples: dynamic Q-learning control.

### 17.4.2 Septic Death Case: RBF Value Approximation-Based Treatments

Value approximation-based RL is preferred when there are infinite states of continuous time systems. When the inflammation dynamics exceed their limits in the septic case, value approximation-based RL aims to minimize P and D levels by using the lowest drug doses. The initial conditions are chosen as P = 1, N* = 0, D = 0, C_A = 0.125 , k_pg = 0.6 for the septic scenario parameters of the AIR model. The value approximation-based reinforcement learning inflammation control results for the septic

## ML Decision Support System to Treat the Acute Inflammation Response

case without disturbance and ineffective treatment samples have been illustrated in Figure 17.6. For the septic case, the dynamics of the AIR obtained are illustrated in Figure 17.6a and Figure 17.6b, respectively. u_a and u_p therapy signals obtained with no disturbance in value approximation-based control are shown in Figure 17.6c. Like the tabular reinforcement learning approach, disturbances were taken into account for a therapy plan compatible with clinical data in value approximation-based reinforcement learning control. The simulation results for the septic case with disturbance and ineffective treatment samples have been illustrated in Figure 17.7. The dynamics of the AIR have been given in Figure 17.7a and Figure 17.7b, respectively. Anti-inflammatory and pro-inflammatory therapy signals are shown in Figure 17.7c. The aim here is to ensure that the P and D disappear as quickly as possible by using these therapies. Total reward values for the septic death case are given in Figure 17.6d and Figure 17.7d.

- (a) Pathogen and Tissue Damage.
- (b) Activated Phagocytes and Anti-inflammatory Mediator.
- (c) Drug dosages.
- (d) Total rewards.

FIGURE 17.6 Septic death case without disturbance and ineffective treatment samples: RBF value approximation control.

![](img/a2fc2296b12812e9151e817bff1de16d_362_0.png)
(a) Pathogen and Tissue Damage.

![](img/a2fc2296b12812e9151e817bff1de16d_362_1.png)
(b) Activated Phagocytes and Anti-inflammatory Mediator.

![](img/a2fc2296b12812e9151e817bff1de16d_362_2.png)
(c) Drug dosages.

![](img/a2fc2296b12812e9151e817bff1de16d_362_3.png)
(d) Total rewards.

FIGURE 17.7 Septic death case with disturbance and ineffective treatment samples: RBF value approximation control.

## 17.5 DISCUSSION AND COMPARISON

The immune response to pathogenic infection or trauma both attempts to eliminate the invasive pathogen threat and promote tissue repair. It is very important to plan patient-specific treatment for rapidly progressing medical conditions such as acute inflammation, as mortality rates may increase when treatment with broad-spectrum drugs is used instead of specific treatment. In this chapter, reinforcement learning-based treatment of acute inflammatory conditions under external disturbances and ineffective treatments has been performed to calculate the optimum drug dose and timing of the treatment, which will strengthen the immune system to prevent possible damage to tissues and lead the patient to a healthy case. The pro-inflammatory mediator and anti-inflammatory mediator reference points are assumed to be around zero for healthy patients. Computational results can be evaluated as follows: it was observed that a large N* value destroys the pathogen level faster by causing tissue damage. This result activates the anti-inflammatory response ($C_A$) while reducing the value of $N^*$. The anti-inflammatory mediator directly abates inflammation by preventing tissue damage produced by inflammation. In this process, the anti-inflammatory therapy signal ($u_a$) can increase the $C_A$ value and minimize tissue damage while causing pathogen growth. On the other hand, if the pro-inflammatory therapy signal ($u_p$) rapidly decreases the pathogen while increasing the $N^*$ value, irreparable risks to the organs can occur.

Remember that the rewarding functions are constructed based on the negative power of the stabilization errors for designed reinforcement learning models. In the learning period, maximization of the reward value implies the minimization of the inflammation states or stabilization error. If the reinforcement models are compared in terms of stabilization speed, value approximation models are found to be much faster than the tabular reinforcement models, even though septic dynamics are stabilized. When the disturbance and ineffective treatment periods are added to the damaged state and anti-inflammatory drug dosage, respectively, then the total rewards of both reinforcement models oscillate, since the manifolds corresponding to disturbed states change unexpectedly and new state-action pairs are rewarded, which means that the reinforcement models can sweep larger state-action spaces so that they are ready to make better decisions in large spaces for future patients.

In the stabilization dynamics, the drugs ($u_a$ and $u_p$) are applied to the $N^*$ and $C_A$ states to compensate the $P$ and $D$ dynamics. Therefore, it is assured that the $N^*$ and $C_A$ converge to zero, but that does not mean that the $N^*$ and $C_A$ stabilized; true control dosages must be chosen. In the results, the $P$ and $D$ states are specially checked for stability. According to Table 17.1, the reward value functions are compared for the maximum state values of the AIR model. The polynomial and Gaussian reward functions provided smaller $P$ and $D$ values, which is important for sensitive patients. For the mean return values of the treatments, the root-mean-squared values of the states and control dosages are shown in Table 17.2.

For the lower amounts of drug dosages, parabolic reward values are suitable for treatment. The triangular reward value is preferable for the smaller stabilization error. Note that these results are to emphasize the details when different dosages are applied and the consequences obtained from sensitive patients. In a general sense, it

### TABLE 17.1
Maximum Values of States

| Reward Value Functions | P | N* | D | C_A |
|---|---|---|---|---|
| Parabolic | 1.6853 | 0.5097 | 3.9420 | 0.7533 |
| Polynomial | 1.8529 | 0.8896 | 5.7766 | 0.8034 |
| Barrier Lyapunov | 1.6853 | 0.3470 | 5.3475 | 0.6613 |
| Gaussian | 1.6853 | 0.4357 | 3.7150 | 0.7523 |
| Triangular | 1.6853 | 0.4561 | 3.9830 | 0.7533 |
