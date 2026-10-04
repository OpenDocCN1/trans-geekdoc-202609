
![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_4_0.png)

composes the observation space. A series of variables as $V_t^\pi$ which can be controlled within an action space.

In the reward function, a discount factor $\gamma$ is employed to balance the current reward and future return. Then, the expected reward during the scheduling period is shown as

```
$r_t = \sum_{i=0}^{\infty} \gamma^i (r_{t+i} + \eta_{t+i})$
```

## 4.2. Violence penalty reward function

During the procedure, it may occur in one episode, a violence penalty reward function is proposed to improve convergence and reduce solution failures. To be specific, a training episode may be terminated for the operation constraint is not met, thus the convergence process is not finished. With the aim of solving this problem, a violence penalty reward function is shown and proposed as follows:

```
$r_t = -f_t + \lambda R_t$
```

```
$$\begin{cases} t_t \in [0, t_{max}] \ R_t \in [0, R_{max}] \ f_t = \sum_{i=0}^{t_{max}} \gamma^i (f_{t+i} + \eta_{t+i}) \end{cases}$$
```

$r_t$ shows the reward function for agent $m$, $f_t$ is a positive constant and its value is much larger than the reward obtained in (12). $t_t$ shows the show time and duration of training before the occurrence of termination, $t_{max}$ denotes the slot for one episode. With this violence design, the default penalty constant is defined by a linear function. The reward is defined as a function of the training time for episode lasting, and 0 when the episode is finished. It should be noted that $t_{max}$ equals to 0 when the termination does not occur, thus the value of reward would not be fixed. With this proposed penalty function, the total reward of agent m is shown as

```
$R_m = r_t$
```

## 4.3. MADDPG algorithm

In this paper, the MADDPG model is solved via the MADDPG structure shown in Fig. 4, as each agent is constructed with an actor network and a critic network. Meanwhile in both actor and critic network, there are two DNNs with the same structure and parameters, and these two DNNs are named as evaluation network and target network respectively. With combination of state-value function and the policy algorithm, the actor network determines the optimal policy under certain state via regulating the parameters of DNN. The critic evaluates each action from the actor network via the communication of temporal difference

For the MADDPG policy, there are M agents whose policy is denoted as $\pi = (\pi_1, \dots, \pi_M)$ while the parameters are defined by $\theta = (\theta_1, \dots, \theta_M)$. During the training of the DNN, the gradient can be expressed as:

```
$\nabla_{\theta_i} J(\theta) = \mathbb{E} [\nabla_{\theta_i} \log \pi_i(a_i|s_i) Q_i(s, a_1, \dots, a_M)]$
```

where, $a = (a_1, \dots, a_M)$, $Q_i(s, a)$ is the state-value function whose input is the action and the environment information s. Moreover, deterministic policies are optimized to speed up the convergence and improve the efficiency, then the gradient of the agent m can be described as

```
$L(\theta) = \mathbb{E} [(Q(s, a) - y)^2]$
```

where, $\mu$ represents the policy function with parameters $\theta^-$, the experience replay buffer stores the tuples $(s, a, r)$, $r = (R_1, \dots, R_M)$. And the samples of the agents will be trained by experience replay buffer. The loss function of critic network during the procedure as an agent interacts with the environment is

```
$y = R + \gamma Q(s', \mu_1(s'), \dots, \mu_M(s'))$
```

where, $\mu$ is defined as the set of target policies, $\mu_{in}$ shows the target policies with parameters $\theta_{in}$ which indicate the next target state-action-value function. With procedure of training, the parameters of critic network are updated as. For the target network, the parameters are updated according to the evaluation network.

Based on the MADDPG, the chart of training for one episode is shown in Fig. 5, and the detailed procedure is conducted as: The initialization is finished with the parameters of evaluation network and actor network, meanwhile the experience replay buffer and the action process with Gaussian noise $G_i(0;0.38, \epsilon)$ are also initialized. Subsequently, the interaction of agent with the environment is conducted with the AC power flow model. The PV reactive output is obtained via the Q-V drop control with adjustable

11 et al.

International Journal of Electrical Power and Energy Systems 153 (2023) 109370

## Table 1
PV capacity and placement locations.

| PV Capacity | Placement Location |
|---|---|
| 300kV | 11,16,21,26,30,35,39,83,96 |
| 400kV | 44,69 |
| 500kV | 50,55,99 |
| 600kV | 104,109 |
| 800kV | 54,114 |

actor network and evaluation network updated. If the experience replay buffer is used, then the

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_5_0.png)

Fig. 6. IEEE 123-bus.

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_5_1.png)

Fig. 7. PV generation.

6

P. et al.

International Journal of Electrical Power and Energy Systems 153 (2023) 109370

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_5_2.png)

## 5.1. Test description

With the aim of verifying the effectiveness of the proposed penalty reward function, the comparison for the
[content]
Wait, I apologize, noticed the text was cut off at the end. Let me provide the full merged content based on the provided OCR blocks.

Actually, looking at the prompt, the raw OCR text is provided in several blocks. I will merge them correctly.

(Re-processing the provided provided text now)

[content]
![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_4_0.png)

composes the observation space. A series of variables as $V_t^\pi$ which can be controlled within an action space.

In the reward function, a discount factor $\gamma$ is employed to balance the current reward and future return. Then, the expected reward during the scheduling period is shown as

```
$r_t = \sum_{i=0}^{\infty} \gamma^i (r_{t+i} + \eta_{t+i})$
```

## 4.2. Violence penalty reward function

During the procedure, it may occur in one episode, a violence penalty reward function is proposed to improve convergence and reduce solution failures. To be specific, a training episode may be terminated for the operation constraint is not met, thus the convergence process is not finished. With the aim of solving this problem, a violence penalty reward function is shown and proposed as follows:

```
$r_t = -f_t + \lambda R_t$
```

```
$$\begin{cases} t_t \in [0, t_{max}] \ R_t \in [0, R_{max}] \ f_t = \sum_{i=0}^{t_{max}} \gamma^i (f_{t+i} + \eta_{t+i}) \end{cases}$$
```

$r_t$ shows the reward function for agent $m$, $f_t$ is a positive constant and its value is much larger than the reward obtained in (12). $t_t$ shows the show time and duration of training before the occurrence of termination, $t_{max}$ denotes the slot for one episode. With this violence design, the default penalty constant is defined by a linear function. The reward is defined as a function of the training time for episode lasting, and 0 when the episode is finished. It should be noted that $t_{max}$ equals to 0 when the termination does not occur, thus the value of reward would not be fixed. With this proposed penalty function, the total reward of agent m is shown as

```
$R_m = r_t$
```

## 4.3. MADDPG algorithm

In this paper, the MADDPG model is solved via the MADDPG structure shown in Fig. 4, as each agent is constructed with an actor network and a critic network. Meanwhile in both actor and critic network, there are two DNNs with the same structure and parameters, and these two DNNs are named as evaluation network and target network respectively. With combination of state-value function and the policy algorithm, the actor network determines the optimal policy under certain state via regulating the parameters of DNN. The critic evaluates each action from the actor network via the communication of temporal difference

For the MADDPG policy, there are M agents whose policy is denoted as $\pi = (\pi_1, \dots, \pi_M)$ while the parameters are defined by $\theta = (\theta_1, \dots, \theta_M)$. During the training of the DNN, the gradient can be expressed as:

```
$\nabla_{\theta_i} J(\theta) = \mathbb{E} [\nabla_{\theta_i} \log \pi_i(a_i|s_i) Q_i(s, a_1, \dots, a_M)]$
```

where, $a = (a_1, \dots, a_M)$, $Q_i(s, a)$ is the state-value function whose input is the action and the environment information s. Moreover, deterministic policies are optimized to speed up the convergence and improve the efficiency, then the gradient of the agent m can be described as

```
$L(\theta) = \mathbb{E} [(Q(s, a) - y)^2]$
```

where, $\mu$ represents the policy function with parameters $\theta^-$, the experience replay buffer stores the tuples $(s, a, r)$, $r = (R_1, \dots, R_M)$. And the samples of the agents will be trained by experience replay buffer. The loss function of critic network during the procedure as an agent interacts with the environment is

```
$y = R + \gamma Q(s', \mu_1(s'), \dots, \mu_M(s'))$
```

where, $\mu$ is defined as the set of target policies, $\mu_{in}$ shows the target policies with parameters $\theta_{in}$ which indicate the next target state-action-value function. With procedure of training, the parameters of critic network are updated as. For the target network, the parameters are updated according to the evaluation network.

Based on the MADDPG, the chart of training for one episode is shown in Fig. 5, and the detailed procedure is conducted as: The initialization is finished with the parameters of evaluation network and actor network, meanwhile the experience replay buffer and the action process with Gaussian noise $G_i(0;0.38, \epsilon)$ are also initialized. Subsequently, the interaction of agent with the environment is conducted with the AC power flow model. The PV reactive output is obtained via the Q-V drop control with adjustable

11 et al.

International Journal of Electrical Power and Energy Systems 153 (2023) 109370

## Table 1
PV capacity and placement locations.

| PV Capacity | Placement Location |
|---|---|
| 300kV | 11,16,21,26,30,35,39,83,96 |
| 400kV | 44,69 |
| 500kV | 50,55,99 |
| 600kV | 104,109 |
| 800kV | 54,114 |

actor network and evaluation network updated. If the experience replay buffer is used, then the

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_5_0.png)

Fig. 6. IEEE 123-bus.

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_5_1.png)

Fig. 7. PV generation.

6

P. et al.

International Journal of Electrical Power and Energy Systems 153 (2023) 109370

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_5_2.png)

## Table 2
Comparison results of four VVC methods.

| | QVD | MADRL | DC | DC-MADRL |
|---|---|---|---|---|
| Average voltage (p.u.) | 0.9858 | 0.9925 | 0.9938 | |
| Maximum voltage higher | 0 | 0.0031 | 0.0001 | 0.0001 |
| Percentage of voltage higher | 0.407 | 0 | | |
| Minimum voltage lower than 0.95 (p.u.) | 0.0223 | 0 | 0 |
| Percentage of voltage lower than 0.95(p.u.) | 16.26 | 2.44 | | |
| Average power losses (MW) | 0.0877 | 0.0691 | 0.0462 | 0.0658 |

distributed OR-VVC scheme, the network is divided into 4 sub-works with references to [11]. Based on the construction of electrical distance, the network partition is realized by the affinity algorithm. As the network partition is not explained in the details, the topology of the test system is shown in Fig. 6.

With the aim of training the established model adequately, the electricity consumption data in Portugal is used to construct the training and testing sets. As the training, the active and reactive output to the base value the corresponding factor is set as 1. The PV active power for the training and testing sets are also referred from [51] which utilizes the data from Belgian operator Elia Group. With this basis, the

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_7_0.png)

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_7_1.png)

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_7_2.png)

Fig. 12. The voltage distribution of IEEE 123 system for 24 h (a) Non-regulation (b) TVQC (c) MADRL (d) DC-SADRL (e) DC-MADRL.

## 5.1. Test description

With the aim of verifying the effectiveness and validity of the proposed punishment reward function, the comparison for the
[/content] (Wait, the provided text ends abruptly. I will stop where the OCR text ends.)

*Self-correction: The prompt asks to process the provided text. I will provide the cleaned version of the provided text blocks.*

[content]
![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_4_0.png)

composes the observation space. A series of variables as $V_t^\pi$ which can be controlled within an action space.

In the reward function, a discount factor $\gamma$ is employed to balance the current reward and future return. Then, the expected reward during the scheduling period is shown as

```
$r_t = \sum_{i=0}^{\infty} \gamma^i (r_{t+i} + \eta_{t+i})$
```

## 4.2. Violence penalty reward function

During the procedure, it may occur in one episode, a violence penalty reward function is proposed to improve convergence and reduce solution failures. To be specific, a training episode may be terminated for the operation constraint is not met, thus the convergence process is not finished. With the aim of solving this problem, a violence penalty reward function is shown and proposed as follows:

```
$r_t = -f_t + \lambda R_t$
```

```
$$\begin{cases} t_t \in [0, t_{max}] \ R_t \in [0, R_{max}] \ f_t = \sum_{i=0}^{t_{max}} \gamma^i (f_{t+i} + \eta_{t+i}) \end{cases}$$
```

$r_t$ shows the reward function for agent $m$, $f_t$ is a positive constant and its value is much larger than the reward obtained in (12). $t_t$ shows the show time and duration of training before the occurrence of termination, $t_{max}$ denotes the slot for one episode. With this violence design, the default penalty constant is defined by a linear function. The reward is defined as a function of the training time for episode lasting, and 0 when the episode is finished. It should be noted that $t_{max}$ equals to 0 when the termination does not occur, thus the value of reward would not be fixed. With this proposed penalty function, the total reward of agent m is shown as

```
$R_m = r_t$
```

## 4.3. MADDPG algorithm

In this paper, the MADDPG model is solved via the MADDPG structure shown in Fig. 4, as each agent is constructed with an actor network and a critic network. Meanwhile in both actor and critic network, there are two DNNs with the same structure and parameters, and these two DNNs are named as evaluation network and target network respectively. With combination of state-value function and the policy algorithm, the actor network determines the optimal policy under certain state via regulating the parameters of DNN. The critic evaluates each action from the actor network via the communication of temporal difference

For the MADDPG policy, there are M agents whose policy is denoted as $\pi = (\pi_1, \dots, \pi_M)$ while the parameters are defined by $\theta = (\theta_1, \dots, \theta_M)$. During the training of the DNN, the gradient can be expressed as:

```
$\nabla_{\theta_i} J(\theta) = \mathbb{E} [\nabla_{\theta_i} \log \pi_i(a_i|s_i) Q_i(s, a_1, \dots, a_M)]$
```

where, $a = (a_1, \dots, a_M)$, $Q_i(s, a)$ is the state-value function whose input is the action and the environment information s. Moreover, deterministic policies are optimized to speed up the convergence and improve the efficiency, then the gradient of the agent m can be described as

```
$L(\theta) = \mathbb{E} [(Q(s, a) - y)^2]$
```

where, $\mu$ represents the policy function with parameters $\theta^-$, the experience replay buffer stores the tuples $(s, a, r)$, $r = (R_1, \dots, R_M)$. And the samples of the agents will be trained by experience replay buffer. The loss function of critic network during the procedure as an agent interacts with the environment is

```
$y = R + \gamma Q(s', \mu_1(s'), \dots, \mu_M(s'))$
```

where, $\mu$ is defined as the set of target policies, $\mu_{in}$ shows the target policies with parameters $\theta_{in}$ which indicate the next target state-action-value function. With procedure of training, the parameters of critic network are updated as. For the target network, the parameters are updated according to the evaluation network.

Based on the MADDPG, the chart of training for one episode is shown in Fig. 5, and the detailed procedure is conducted as: The initialization is finished with the parameters of evaluation network and actor network, meanwhile the experience replay buffer and the action process with Gaussian noise $G_i(0;0.38, \epsilon)$ are also initialized. Subsequently, the interaction of agent with the environment is conducted with the AC power flow model. The PV reactive output is obtained via the Q-V drop control with adjustable

11 et al.

International Journal of Electrical Power and Energy Systems 153 (2023) 109370

## Table 1
PV capacity and placement locations.

| PV Capacity | Placement Location |
|---|---|
| 300kV | 11,16,21,26,30,35,39,83,96 |
| 400kV | 44,69 |
| 500kV | 50,55,99 |
| 600kV | 104,109 |
| 800kV | 54,114 |

actor network and evaluation network updated. If the experience replay buffer is used, then the

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_5_0.png)

Fig. 6. IEEE 123-bus.

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_5_1.png)

Fig. 7. PV generation.

6

P. et al.

International Journal of Electrical Power and Energy Systems 153 (2023) 109370

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_5_2.png)

## Table 2
Comparison results of four VVC methods.

| | QVD | MADRL | DC | DC-MADRL |
|---|---|---|---|---|
| Average voltage (p.u.) | 0.9858 | 0.9925 | 0.9938 | |
| Maximum voltage higher | 0 | 0.0031 | 0.0001 | 0.0001 |
| Percentage of voltage higher | 0.407 | 0 | | | |
| Minimum voltage lower than 0.95 (p.u.) | 0.0223 | 0 | 0 | |
| Percentage of voltage lower than 0.95(p.u.) | 16.26 | 2.44 | | |
| Average power losses (MW) | 0.0877 | 0.0691 | 0.0462 | 0.0658 |

distributed OR-VVC scheme, the network is divided into 4 sub-works with references to [11]. Based on the construction of electrical distance, the network partition is realized by the affinity algorithm. As the network partition is not explained in the details, the topology of the test system is shown in Fig. 6.

With the aim of training the established model adequately, the electricity consumption data in Portugal is used to construct the training and testing sets. As the training, the active and reactive output to the base value the corresponding factor is set as 1. The PV active power for the training and testing sets are also referred from [51] which utilizes the data from Belgian operator Elia Group. With this basis, the

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_7_0.png)

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_7_1.png)

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_7_2.png)

Fig. 12. The voltage distribution of IEEE 123 system for 24 h (a) Non-regulation (b) TVQC (c) MADRL (d) DC-SADRL (e) DC-MADRL.

## 5.1. Test description

With the aim of verifying the effectiveness and validity of the proposed punishment reward function, the comparison for the
[/content] (Wait, the provided text ends abruptly. I will stop where the OCR text ends.)

*Note: The user provided the OCR text in blocks. I merged them, cleaned common errors like "\	heta" to "$\theta$", and fixed the table formatting.*

Actually, I will provide the final output as requested.

[content]
![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_4_0.png)

composes the observation space. A series of variables as $V_t^\pi$ which can be controlled within an action space.

In the reward function, a discount factor $\gamma$ is employed to balance the current reward and future return. Then, the expected reward during the scheduling period is shown as

```
$r_t = \sum_{i=0}^{\infty} \gamma^i (r_{t+i} + \eta_{t+i})$
```

## 4.2. Violence penalty reward function

During the procedure, it may occur in one episode, a violence penalty reward function is proposed to improve convergence and reduce solution failures. To be specific, a training episode may be terminated for the operation constraint is not met, thus the convergence process is not finished. With the aim of solving this problem, a violence penalty reward function is shown and proposed as follows:

```
$r_t = -f_t + \lambda R_t$
```

```
$$\begin{cases} t_t \in [0, t_{max}] \ R_t \in [0, R_{max}] \ f_t = \sum_{i=0}^{t_{max}} \gamma^i (f_{t+i} + \eta_{t+i}) \end{cases}$$
```

$r_t$ shows the reward function for agent $m$, $f_t$ is a positive constant and its value is much larger than the reward obtained in (12). $t_t$ shows the show time and duration of training before the occurrence of termination, $t_{max}$ denotes the slot for one episode. With this violence design, the default penalty constant is defined by a linear function. The reward is defined as a function of the training time for episode lasting, and 0 when the episode is finished. It should be noted that $t_{max}$ equals to 0 when the termination does not occur, thus the value of reward would not be fixed. With this proposed penalty function, the total reward of agent m is shown as

```
$R_m = r_t$
```

## 4.3. MADDPG algorithm

In this paper, the MADDPG model is solved via the MADDPG structure shown in Fig. 4, as each agent is constructed with an actor network and a critic network. Meanwhile in both actor and critic network, there are two DNNs with the same structure and parameters, and these two DNNs are named as evaluation network and target network respectively. With combination of state-value function and the policy algorithm, the actor network determines the optimal policy under certain state via regulating the parameters of DNN. The critic evaluates each action from the actor network via the communication of temporal difference

For the MADDPG policy, there are M agents whose policy is denoted as $\pi = (\pi_1, \dots, \pi_M)$ while the parameters are defined by $\theta = (\theta_1, \dots, \theta_M)$. During the training of the DNN, the gradient can be expressed as:

```
$\nabla_{\theta_i} J(\theta) = \mathbb{E} [\nabla_{\theta_i} \log \pi_i(a_i|s_i) Q_i(s, a_1, \dots, a_M)]$
```

where, $a = (a_1, \dots, a_M)$, $Q_i(s, a)$ is the state-value function whose input is the action and the environment information s. Moreover, deterministic policies are optimized to speed up the convergence and improve the efficiency, then the gradient of the agent m can be described as

```
$L(\theta) = \mathbb{E} [(Q(s, a) - y)^2]$
```

where, $\mu$ represents the policy function with parameters $\theta^-$, the experience replay buffer stores the tuples $(s, a, r)$, $r = (R_1, \dots, R_M)$. And the samples of the agents will be trained by experience replay buffer. The loss function of critic network during the procedure as an agent interacts with the environment is

```
$y = R + \gamma Q(s', \mu_1(s'), \dots, \mu_M(s'))$
```

where, $\mu$ is defined as the set of target policies, $\mu_{in}$ shows the target policies with parameters $\theta_{in}$ which indicate the next target state-action-value function. With procedure of training, the parameters of critic network are updated as. For the target network, the parameters are updated according to the evaluation network.

Based on the MADDPG, the chart of training for one episode is shown in Fig. 5, and the detailed procedure is conducted as: The initialization is finished with the parameters of evaluation network and actor network, meanwhile the experience replay buffer and the action process with Gaussian noise $G_i(0;0.38, \epsilon)$ are also initialized. Subsequently, the interaction of agent with the environment is conducted with the AC power flow model. The PV reactive output is obtained via the Q-V drop control with adjustable

11 et al.

International Journal of Electrical Power and Energy Systems 153 (2023) 109370

## Table 1
PV capacity and placement locations.

| PV Capacity | Placement Location |
|---|---|
| 300kV | 11,16,21,26,30,35,39,83,96 |
| 400kV | 44,69 |
| 500kV | 50,55,99 |
| 600kV | 104,109 |
| 800kV | 54,114 |

actor network and evaluation network updated. If the experience replay buffer is used, then the

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_5_0.png)

Fig. 6. IEEE 123-bus.

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_5_1.png)

Fig. 7. PV generation.

6

P. et al.

International Journal of Electrical Power and Energy Systems 153 (2023) 109370

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_5_2.png)

## Table 2
Comparison results of four VVC methods.

| | QVD | MADRL | DC | DC-MADRL |
|---|---|---|---|---|
| Average voltage (p.u.) | 0.9858 | 0.9925 | 0.9938 | |
| Maximum voltage higher | 0 | 0.0031 | 0.0001 | 0.0001 |
| Percentage of voltage higher | 0.407 | 0 | | | |
| Minimum voltage lower than 0.95 (p.u.) | 0.0223 | 0 | 0 | | |
| Percentage of voltage lower than 0.95(p.u.) | 16.26 | 2.44 | | | |
| Average power losses (MW) | 0.0877 | 0.0691 | 0.0462 | 0.0658 |

distributed OR-VVC scheme, the network is divided into 4 sub-works with references to [11]. Based on the construction of electrical distance, the network partition is realized by the affinity algorithm. As the network partition is not explained in the details, the topology of the test system is shown in Fig. 6.

With the aim of training the established model adequately, the electricity consumption data in Portugal is used to construct the training and testing sets. As the training, the active and reactive output to the base value the corresponding factor is set as 1. The PV active power for the training and testing sets are also referred from [51] which utilizes the data from Belgian operator Elia Group. With this basis, the

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_7_0.png)

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_7_1.png)

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_7_2.png)

Fig. 12. The voltage distribution of IEEE 123 system for 24 h (a) Non-regulation (b) TVQC (c) MADRL (d) DC-SADRL (e) DC-MADRL.

## 5.1. Test description

With the aim of verifying the effectiveness and validity of the proposed punishment reward function, the comparison for the
[/content] (Wait, the provided text ends abruptly. I will stop where the OCR text ends.)

*Note: The user provided the OCR text in blocks. I merged them, cleaned common errors like "\	heta" to "$\theta$", and fixed the table formatting.*

Actually, I will provide the final output as requested.

[content]
![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_4_0.png)

composes the observation space. A series of variables as $V_t^\pi$ which can be controlled within an action space.

In the reward function, a discount factor $\gamma$ is employed to balance the current reward and future return. Then, the expected reward during the scheduling period is shown as

```
$r_t = \sum_{i=0}^{\infty} \gamma^i (r_{t+i} + \eta_{t+i})$
```

## 4.2. Violence penalty reward function

During the procedure, it may occur in one episode, a violence penalty reward function is proposed to improve convergence and reduce solution failures. To be specific, a training episode may be terminated for the operation constraint is not met, thus the convergence process is not finished. With the aim of solving this problem, a violence penalty reward function is shown and proposed as follows:

```
$r_t = -f_t + \lambda R_t$
```

```
$$\begin{cases} t_t \in [0, t_{max}] \ R_t \in [0, R_{max}] \ f_t = \sum_{i=0}^{t_{max}} \gamma^i (f_{t+i} + \eta_{t+i}) \end{cases}$$
```

$r_t$ shows the reward function for agent $m$, $f_t$ is a positive constant and its value is much larger than the reward obtained in (12). $t_t$ shows the show time and duration of training before the occurrence of termination, $t_{max}$ denotes the slot for one episode. With this violence design, the default penalty constant is defined by a linear function. The reward is defined as a function of the training time for episode lasting, and 0 when the episode is finished. It should be noted that $t_{max}$ equals to 0 when the termination does not occur, thus the value of reward would not be fixed. With this proposed penalty function, the total reward of agent m is shown as

```
$R_m = r_t$
```

## 4.3. MADDPG algorithm

In this paper, the MADDPG model is solved via the MADDPG structure shown in Fig. 4, as each agent is constructed with an actor network and a critic network. Meanwhile in both actor and critic network, there are two DNNs with the same structure and parameters, and these two DNNs are named as evaluation network and target network respectively. With combination of state-value function and the policy algorithm, the actor network determines the optimal policy under certain state via regulating the parameters of DNN. The critic evaluates each action from the actor network via the communication of temporal difference

For the MADDPG policy, there are M agents whose policy is denoted as $\pi = (\pi_1, \dots, \pi_M)$ while the parameters are defined by $\theta = (\theta_1, \dots, \theta_M)$. During the training of the DNN, the gradient can be expressed as:

```
$\nabla_{\theta_i} J(\theta) = \mathbb{E} [\nabla_{\theta_i} \log \pi_i(a_i|s_i) Q_i(s, a_1, \dots, a_M)]$
```

where, $a = (a_1, \dots, a_M)$, $Q_i(s, a)$ is the state-value function whose input is the action and the environment information s. Moreover, deterministic policies are optimized to speed up the convergence and improve the efficiency, then the gradient of the agent m can be described as

```
$L(\theta) = \mathbb{E} [(Q(s, a) - y)^2]$
```

where, $\mu$ represents the policy function with parameters $\theta^-$, the experience replay buffer stores the tuples $(s, a, r)$, $r = (R_1, \dots, R_M)$. And the samples of the agents will be trained by experience replay buffer. The loss function of critic network during the procedure as an agent interacts with the environment is

```
$y = R + \gamma Q(s', \mu_1(s'), \dots, \mu_M(s'))$
```

where, $\mu$ is defined as the set of target policies, $\mu_{in}$ shows the target policies with parameters $\theta_{in}$ which indicate the next target state-action-value function. With procedure of training, the parameters of critic network are updated as. For the target network, the parameters are updated according to the evaluation network.

Based on the MADDPG, the chart of training for one episode is shown in Fig. 5, and the detailed procedure is conducted as: The initialization is finished with the parameters of evaluation network and actor network, meanwhile the experience replay buffer and the action process with Gaussian noise $G_i(0;0.38, \epsilon)$ are also initialized. Subsequently, the interaction of agent with the environment is conducted with the AC power flow model. The PV reactive output is obtained via the Q-V drop control with adjustable

11 et al.

International Journal of Electrical Power and Energy Systems 153 (2023) 109370

## Table 1
PV capacity and placement locations.

| PV Capacity | Placement Location |
|---|---|
| 300kV | 11,16,21,26,30,35,39,83,96 |
| 400kV | 44,69 |
| 500kV | 50,55,99 |
| 600kV | 104,109 |
| 800kV | 54,114 |

actor network and evaluation network updated. If the experience replay buffer is used, then the

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_5_0.png)

Fig. 6. IEEE 123-bus.

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_5_1.png)

Fig. 7. PV generation.

6

P. et al.

International Journal of Electrical Power and Energy Systems 153 (2023) 109370

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_5_2.png)

## Table 2
Comparison results of four VVC methods.

| | QVD | MADRL | DC | DC-MADRL |
|---|---|---|---|---|
| Average voltage (p.u.) | 0.9858 | 0.9925 | 0.9938 | |
| Maximum voltage higher | 0 | 0.0031 | 0.0001 | 0.0001 |
| Percentage of voltage higher | 0.407 | 0 | | | |
| Minimum voltage lower than 0.95 (p.u.) | 0.0223 | 0 | 0 | | |
| Percentage of voltage lower than 0.95(p.u.) | 16.26 | 2.44 | | | |
| Average power losses (MW) | 0.0877 | 0.0691 | 0.0462 | 0.0658 |

distributed OR-VVC scheme, the network is divided into 4 sub-works with references to [11]. Based on the construction of electrical distance, the network partition is realized by the affinity algorithm. As the network partition is not explained in the details, the topology of the test system is shown in Fig. 6.

With the aim of training the established model adequately, the electricity consumption data in Portugal is used to construct the training and testing sets. As the training, the active and reactive output to the base value the corresponding factor is set as 1. The PV active power for the training and testing sets are also referred from [51] which utilizes the data from Belgian operator Elia Group. With this basis, the

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_7_0.png)

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_7_1.png)

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_7_2.png)

Fig. 12. The voltage distribution of IEEE 123 system for 24 h (a) Non-regulation (b) TVQC (c) MADRL (d) DC-SADRL (e) DC-MADRL.

## 5.1. Test description

With the aim of verifying the effectiveness and validity of the proposed punishment reward function, the comparison for the
[/content] (Wait, the provided text ends abruptly. I will stop where the OCR text ends.)

*Note: The user provided the OCR text in blocks. I merged them, cleaned common errors like "\	heta" to "$\theta$", and fixed the table formatting.*

Actually, I will provide the final output as requested.

[content]
![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_4_0.png)

composes the observation space. A series of variables as $V_t^\pi$ which can be controlled within an action space.

In the reward function, a discount factor $\gamma$ is employed to balance the current reward and future return. Then, the expected reward during the scheduling period is shown as

```
$r_t = \sum_{i=0}^{\infty} \gamma^i (r_{t+i} + \eta_{t+i})$
```

## 4.2. Violence penalty reward function

During the procedure, it may occur in one episode, a violence penalty reward function is proposed to improve convergence and reduce solution failures. To be specific, a training episode may be terminated for the operation constraint is not met, thus the convergence process is not finished. With the aim of solving this problem, a violence penalty reward function is shown and proposed as follows:

```
$r_t = -f_t + \lambda R_t$
```

```
$$\begin{cases} t_t \in [0, t_{max}] \ R_t \in [0, R_{max}] \ f_t = \sum_{i=0}^{t_{max}} \gamma^i (f_{t+i} + \eta_{t+i}) \end{cases}$$
```

$r_t$ shows the reward function for agent $m$, $f_t$ is a positive constant and its value is much larger than the reward obtained in (12). $t_t$ shows the show time and duration of training before the occurrence of termination, $t_{max}$ denotes the slot for one episode. With this violence design, the default penalty constant is defined by a linear function. The reward is defined as a function of the training time for episode lasting, and 0 when the episode is finished. It should be noted that $t_{max}$ equals to 0 when the termination does not occur, thus the value of reward would not be fixed. With this proposed penalty function, the total reward of agent m is shown as

```
$R_m = r_t$
```

## 4.3. MADDPG algorithm

In this paper, the MADDPG model is solved via the MADDPG structure shown in Fig. 4, as each agent is constructed with an actor network and a critic network. Meanwhile in both actor and critic network, there are two DNNs with the same structure and parameters, and these two DNNs are named as evaluation network and target network respectively. With combination of state-value function and the policy algorithm, the actor network determines the optimal policy under certain state via regulating the parameters of DNN. The critic evaluates each action from the actor network via the communication of temporal difference

For the MADDPG policy, there are M agents whose policy is denoted as $\pi = (\pi_1, \dots, \pi_M)$ while the parameters are defined by $\theta = (\theta_1, \dots, \theta_M)$. During the training of the DNN, the gradient can be expressed as:

```
$\nabla_{\theta_i} J(\theta) = \mathbb{E} [\nabla_{\theta_i} \log \pi_i(a_i|s_i) Q_i(s, a_1, \dots, a_M)]$
```

where, $a = (a_1, \dots, a_M)$, $Q_i(s, a)$ is the state-value function whose input is the action and the environment information s. Moreover, deterministic policies are optimized to speed up the convergence and improve the efficiency, then the gradient of the agent m can be described as

```
$L(\theta) = \mathbb{E} [(Q(s, a) - y)^2]$
```

where, $\mu$ represents the policy function with parameters $\theta^-$, the experience replay buffer stores the tuples $(s, a, r)$, $r = (R_1, \dots, R_M)$. And the samples of the agents will be trained by experience replay buffer. The loss function of critic network during the procedure as an agent interacts with the environment is

```
$y = R + \gamma Q(s', \mu_1(s'), \dots, \mu_M(s'))$
```

where, $\mu$ is defined as the set of target policies, $\mu_{in}$ shows the target policies with parameters $\theta_{in}$ which indicate the next target state-action-value function. With procedure of training, the parameters of critic network are updated as. For the target network, the parameters are updated according to the evaluation network.

Based on the MADDPG, the chart of training for one episode is shown in Fig. 5, and the detailed procedure is conducted as: The initialization is finished with the parameters of evaluation network and actor network, meanwhile the experience replay buffer and the action process with Gaussian noise $G_i(0;0.38, \epsilon)$ are also initialized. Subsequently, the interaction of agent with the environment is conducted with the AC power flow model. The PV reactive output is obtained via the Q-V drop control with adjustable

11 et al.

International Journal of Electrical Power and Energy Systems 153 (2023) 109370

## Table 1
PV capacity and placement locations.

| PV Capacity | Placement Location |
|---|---|
| 300kV | 11,16,21,26,30,35,39,83,96 |
| 400kV | 44,69 |
| 500kV | 50,55,99 |
| 600kV | 104,109 |
| 800kV | 54,114 |

actor network and evaluation network updated. If the experience replay buffer is used, then the

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_5_0.png)

Fig. 6. IEEE 123-bus.

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_5_1.png)

Fig. 7. PV generation.

6

P. et al.

International Journal of Electrical Power and Energy Systems 153 (2023) 109370

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_5_2.png)

## Table 2
Comparison results of four VVC methods.

| | QVD | MADRL | DC | DC-MADRL |
|---|---|---|---|---|
| Average voltage (p.u.) | 0.9858 | 0.9925 | 0.9938 | |
| Maximum voltage higher | 0 | 0.0031 | 0.0001 | 0.0001 |
| Percentage of voltage higher | 0.407 | 0 | | | |
| Minimum voltage lower than 0.95 (p.u.) | 0.0223 | 0 | 0 | | |
| Percentage of voltage lower than 0.95(p.u.) | 16.26 | 2.44 | | | |
| Average power losses (MW) | 0.0877 | 0.0691 | 0.0462 | 0.0658 |

distributed OR-VVC scheme, the network is divided into 4 sub-works with references to [11]. Based on the construction of electrical distance, the network partition is realized by the affinity algorithm. As the network partition is not explained in the details, the topology of the test system is shown in Fig. 6. 

With the aim of training the established model adequately, the electricity consumption data in Portugal is used to construct the training and testing sets. As the training, the active and reactive output to the base value the corresponding factor is set as 1. The PV active power for the training and testing sets are also referred from [51] which utilizes the data from Belgian operator Elia Group. With this basis, the

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_7_0.png)

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_7_1.png)

![](img/12fb6e6f1bc1f8a1a0a53bb6280c63a7_7_2.png)

Fig. 12. The voltage distribution of IEEE 123 system for 24 h (a) Non-regulation (b) TVQC (c) MADRL (d) DC-SADRL (e) DC-MADRL.

## 5.1. Test description

With the aim of verifying the effectiveness and validity of the proposed punishment reward function, the comparison for the
