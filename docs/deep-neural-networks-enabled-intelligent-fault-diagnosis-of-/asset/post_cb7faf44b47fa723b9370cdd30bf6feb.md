
# Reinforcement Learning for Intelligent Fault Diagnosis ■ 181

Consequently, the mean-square error (MSE) is served as the objective function to update the model’s parameters

```
$L(\theta) = \mathbb{E}\left[(y-Q(s,a;\theta))^2\right]$
```

where $y$ is the target Q value and is obtained by:

```
$y = r + \gamma \max_{a'} Q(s',a';\theta)$
```

Finally, the gradient descent algorithm is used to update the objective function in (12) to obtain the optimal $Q(s,a;\theta)$, thereby inferring the optimal policy $\pi^* = \arg\max_a Q(s,a;\theta)$. Accordingly, the gradient updating is calculated by:

```
nabla_\theta L(\theta) = \mathbb{E}_{e\sim U(B)}[(y-Q(s,a;\theta))\nabla_\theta Q(s,a;\theta)]$
```

where $e \sim U(B)$ denotes the random uniform sampling from ER buffer B. Based on the above DQN, the guessing game defined in Section 10.2 can be solved in the framework of DRL.

## DQN-BASED INTELLIGENT FAULT DIAGNOSIS

In this section, a new diagnostic framework integrating SET and DRL is presented in detail, which is mainly composed of data preprocessing, autonomous learning stage, and diagnostic testing. Accordingly, data preprocessing using SET is first introduced. The strategy of the designed DQN is described and the diagnostic flowchart is shown.

## Data Preprocessing

Raw vibration signals from the planetary gearbox are divided into training data and testing data in appropriate proportions. Samples are obtained in an overlapping way from the above training or testing data, respectively. The data splitting way is depicted in Figure 10.2. To utilize time and frequency-domain information synchronously, this chapter adopts SET to convert 1D vibration signal to 2D TF map, which carries more potential fault information and enhances the robustness than raw signal. According to (10.4) and (10.5), SET,$ \tau,w)$ of each vibration sample is obtained and resized to SET, with a size of $128 \times 128 \times 1$, and it is mapped to a TF image (double type):

```
$P(m,n) = \frac{SET,(m,m) - min(SET)}{max(SET)-min(SET)}$
```

where $P(m,n) \in[0,1]$ is the value at the coordinate point $(m,n)$ of TF image, $m$ and $n$ are all equal to $\{0,1,2,...,127\}$, max and min denote taking maximum and minimum operation, respectively.

![](img/f29bba55de4872c43f26af4667e705f2_191_0.png)

FIGURE 10.2 Data splitting way.

After the above operations, each image will be regarded as a state observation for the classification agent.

## 182 Deep Neural Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

## Agent Architecture Design

Considering that the planetary gearbox's fault diagnosis has been converted as a "guessing game" and defined in the CMDP framework as described in Section 10.2, a fault recognition agent based on DQN is presented further in this section. After SET preprocessing to 2D TF maps, these TF maps will be regarded as the agent’s observations for when the agent is playing the guessing game. In this game, the agent will gradually learn the optimal recognition by interacting with the environment, realizing fault recognition accurately. The diagnostic framework is depicted in Figure 10.3.

In the method of this chapter, the recognition agent possesses two CNNs with the same structure, where a primary network (Eval-Net) is used to update the Q value, and another target network (Target-Net) is used to calculate fixed Q value. The designed CNN structure in Figure 10.3 is described as follows. This CNN has 3 convolutional layers (C-layer), and each C-layer has 8, 12, and 16 filters. The filter kernel size of the first two C-layer is 3 × 3, and the final padding manner in each C-layer is the "same", and the kernel initializer is "he_normal". The pool size and stride in MaxPooling2D operation are all set to 2. The activation function of each C-layer and the first fully connected layer (FC1) is a rectified linear unit (ReLU). The second fully connected layer (FC2) corresponds to the output of the model’s Q value, and its activation function is linear. The model’s state is the observed TF map with size of 128 × 128×1 obtained by SET. The output of the model is an approximated state-action value $Q(s,a;θ)$ with K dimensions, and the optimal action corresponds to $argmaxQ(s,a;θ)$.

To accelerate the agent’s exploration of the environment in the initial learning stage, a dynamic ε-greedy algorithm is used to generate the distribution of actions, thereby causing

![](img/f29bba55de4872c43f26af4667e705f2_192_0.png)

Figure 10.3 TFR- and DRL-based intelligent fault diagnosis framework for the planetary gearbox.

# Reinforcement Learning for Intelligent Fault Diagnosis ■ 183

various experience samples $e_i = (s_i, a_i, r_i, s_{i})$, which are stored in ER buffer $B$. The change of $\epsilon$ is obtained by:

```
$\epsilon = \begin{cases} \epsilon \times \epsilon_{decay}, & \text{if } \epsilon \ge \epsilon_{\min} \\ \epsilon_{\min}, & \text{otherwise} \end{cases}$
```

where $\epsilon_{\min}$ denotes the minimum of $\epsilon$, $\epsilon_{decay}$ is the decay factor.

## DQN-Based Fault Recognition

Considering the planetary gearbox's fault diagnosis has been converted as a "guessing game" and defined in the CMDP framework as described in Section 10.2, a fault recognition agent based on DQN is presented further in this section. After SET preprocessing to 2D TF maps, these TF maps will be regarded as the agent’s observations for when the agent is playing the guessing game. In this game, the agent will gradually learn the optimal recognition by interacting with the environment, realizing fault recognition accurately. The diagnostic framework is depicted in Figure 10.3.

Specifically, the updating of Eva-Net is performed through the gradient descent to the MSE of the Q value and target value, as illustrated in (11), where $C$ is set to 4. In the method of this chapter, the recognition agent possesses two CNNs with the same structure, where a primary network (Eval-Net) is used to update the Q value, and another target network (Target-Net) is used to calculate fixed Q value. The designed CNN structure in Figure 10.3 is described as follows. This CNN has 3 convolutional layers (C-layer), and each C-layer has 8, 12, and 16 filters. The filter kernel size of the first two C-layer is 3 × 3, and the final padding manner in each C-layer is the "same", and the kernel initializer is "he_normal".

In the testing stage, the agent's observations from the guessing game are relatively independent, which means the agent needs to pay more attention to the current reward in answering a question. It will also be verified in the experiment sections. Also, according to the above settings and the definition of CMDP, we build a simulation environment for training the agent.

In this method, the Adam optimizer with the learning rate of 1e-3 and decay of 1e-4 is used to update the parameters of the agent; the training episode is set to 200; the mini-batch is updated by minibatch way, and the mini-batch size is set to 32; one round guessing games with $T=128$; the capacity of ER buffer $B$ is 1000. The discount factor $\gamma$ in (13) is 0.1 because the agent's observations are relatively independent, which means the agent needs to pay more attention to the current reward in answering a question.

Finally, the Target-Net is updated by copying parameters of Eva-Net every step $C$, where $C$ is set to 4.

## EXPERIMENTAL STUDIES

This section introduces the Spectra' drivetrain dynamics simulator (DDS) test bench, data description, evaluation indicator, and running system configuration. Finally, results compared with some existing methods are given in detail.

## Experimental Description

### DDS Testbed and Data Description

Testing Bed The experimental platform is used as the test object to collect various faulty signals under multiple speed-load scenarios, and thereby to verify the performance of the proposed method. This system is mainly composed of a two-stage parallel gearbox, motor, motor controller, brake device, and brake controller, as shown in Figure 10.5. In this chapter, experiments are conducted on the planetary gearbox, whose main parameters are listed in Table 10.1. When the planetary gearbox operates at different conditions, vibration signals are collected by using 608A11 sensors with 5210 Hz sampling frequency.

Generally, faults occur in the bearing or gear component. Thus, the experiment simulates nine planetary gearbox's states, including a health status (HEA), four bearing fault types (BWF: wall wear fault; CWF: combo wear fault occurred in an inner race and outer race; IWF: inner race-wear fault; OWF: outer race-wear fault) and four gear fault types
