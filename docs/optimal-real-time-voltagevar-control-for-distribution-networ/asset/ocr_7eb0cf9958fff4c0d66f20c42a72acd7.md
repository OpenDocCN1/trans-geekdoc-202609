J. Li et al.

International Journal of Electrical Power and Energy 155 (2023) 109370

![](bbox=[0.135, 0.068, 0.467, 0.233])

![](bbox=[0.532, 0.068, 0.903, 0.233])

Fig. 2. The Q-droop model (a)The traditional Q-droop control model; (b) The adjustable Q-droop control model.

![](bbox=[0.135, 0.297, 0.467, 0.362])

Fig. 3. Simplified network.

# 2. Real-time VVC scheme

The paper proposes a ORT-VVC scheme to reduce loss with mitigating voltage fluctuations for distribution network as shown in Fig. 1. The proposed scheme is superior in its real-time response and high global optimization ability, which is integrated in an “off-line training, online execution” process. Moreover, the proposed scheme is applicable to distribution network framework which can be decomposed into several sub-networks of which is ruled by an agent. Each agent can communicate with its adjacent agents and determine strategies for network stability.

With consideration of time, the ORT-VVC scheme is implemented by the hierarchical coordination system to operate the “minutes-level dispatch” strategy and the dynamic load procedure. For the static procedure, each agent collects the information of network topology, resources, device installations, etc., then then optimizes the controlling parameters of the Q-V droop group. For the dynamic procedure, the reactive output is determined based on the real-time operation status.

The scheme is realized via the MADPG method which the multiple agents are based on deep neural network (DNN). Moreover the DNN is trained through the offline training stage, and then employed in the online execution stage to determine the reactive power according to the real-time system constraints. During the procedure, the input includes the PV active power demand, load consumption, voltage within the network and also the load transmitted from its agents. For the executions, the optimized Q-droop control model and the system status variables, such as PV active power and the load, then the output is the reactive power setting.

At the start of the dispatch, such as 15 minutes, the one agent will control the parameters to each PV inverter and there find no more information communication between PVs and

# 3. Q-V droop control based ORT-VVC

# 3.1. Q-V droop model

The Q-droop control models are shown in Fig. 2 Fig(a) represents the proposed adjustable Q-V droop. As shown in Fig. (3)(a), the Q-droop curve is not activated and there exists a dead zone as $[V_l, V_h]$ where the reactive power is only generated when the voltage is beyond the dead zone $[V_l, V_h]$ in the traditional method. Moreover, the controlling parameters are shown in Fig. 2(b), where the Q-slope is set as 1.0, and would not be regulated during the operation period. Thus, a more flexible Q-V droop control method parameters are adjustable while the mathematical model is shown as:

```
$Q_{i}^{max} - \alpha_{i}(V_{i} - V_{ref}) \geq Q_{i} \geq Q_{i}^{min}$
$- \alpha_{i}(V_{i} - V_{ref}) \geq Q_{i}, \quad i \in N^{PV}$
```

$\alpha = \alpha_{i,s}$

```
$(V_{i})^{2} + (Q_{i})^{2} \leq (x_{i})^{2}, \quad i \in N^{PV}$
```

$N^{PV}$ is the set of buses equipped with PV for sub-networks. $V_{i}^{t}$ and $Q_{i}^{t}$ represent the active power, reactive power and capacity of PV at node $i$ at time $t$, respectively. $R_{i}^{max}$ and $Q_{i}^{max}$ are the maximal and minimal reactive power limits, respectively. $V_{i}^{t}$ is the voltage of the PV connecting to node $i$ at time $t$, i.e. the intersection of the Q-V curve and the x-axis, and $V^{opt}$ is the optimal droop point. $R_{i}$ is the sensitivity of voltage to reactive power.

Eq. implements the action rule of reactive power scheme, eq.(2) and the Q-V sensitivity is determined by the number of nodes and the Q-V sensitivity of the system. Then, it can be that the Q-V droop model contains the necessary and information for network operation. In this paper, an adjustable droop parameter to determine the position of the Q-V curve in the distribution network operation status. As shown in Fig. 2(b), multiple droop curves are determined by several candidate $V_{i}^{opt}$ collectively constitute the feasible baseline.

3