# 182 Deep Neural Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

respectively. After the above operations, each image will be regarded as a state observation for the classification agent.

# Agent Architecture Design

Considering that the planetary gearbox's fault diagnosis has been converted as a "guessing game" and defined in the CMDP framework as described in Section 10.2, a fault recognition agent based on DQN is presented further in this section. After SET preprocessing to 2D TF maps, these TF maps will be regarded as the agent’s observations for when the agent is playing the guessing game. In this game, the agent will gradually learn the optimal recognition by interacting with the environment, realizing fault recognition accurately. The diagnostic framework is depicted in Figure 10.3.

In the method of this chapter, the recognition agent possesses two CNNs with the same structure, where a primary network (Eval-Net) is used to update the Q value, and another target network (Target-Net) is used to calculate fixed Q value. The designed CNN structure in Figure 10.3 is described as follows. This CNN has 3 convolutional layers (C-layer), and each C-layer has 8, 12, and 16 filters. The filter kernel size of the first two C-layer is 3 × 3, and the final padding manner in each C-layer is the "same", and the kernel initializer is "he_normal". The pool size and stride in MaxPooling2D operation are all set to 2. The activation function of each C-layer and the first fully connected layer (FC1) is a rectified linear unit (ReLU). The second fully connected layer (FC2) corresponds to the output of the model’s Q value, and its activation function is linear. The model’s state is the observed TF map with size of 128 × 128×1 obtained by SET. The output of the model is an approximated state-action value Q(s,a;θ) with K dimensions, and the optimal action corresponds to argmaxQ(s,a;θ).

To accelerate the agent’s exploration of the environment in the initial learning stage, a dynamic ε-greedy algorithm is used to generate the distribution of actions, thereby causing

![](bbox=[0.108, 0.653, 0.892, 0.873])

Figure 10.3 TFR- and DRL-based intelligent fault diagnosis framework for the planetary gearbox.