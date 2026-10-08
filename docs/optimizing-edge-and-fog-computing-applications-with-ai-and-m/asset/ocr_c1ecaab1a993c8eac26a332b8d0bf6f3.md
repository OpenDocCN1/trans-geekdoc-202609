![](bbox=[0.277, 0.118, 0.722, 0.453])

**Figure 2.1 Relationship between tasks and nodes (two levels).**

A new model for representation TransEC, which translates the EC tasks, nodes, and environment to various vector subspaces, is presented using the entities and relations previously mentioned.

In particular, the tasks and nodes are initially embedded into various sub-spaces using embedding layers. Then, the potential features of the environment are retrieved using linear transformations and convolution neural networks, and the knowledge is mapped to a dynamic sub-space. Lastly, our TransEC model is used to extract the relationships between second-level entities.

Scheduling decisions in a dynamic and large-scale EC environment can be resolved by DRL with the ability of the TransEC model, which effectively reduces the state dimension. The Deep Q-Learning (DQL) algorithm is selected among many RL algorithms due to its ability to facilitate quick decision-making.

Additionally, the TransEC-DQL algorithm’s training frequency is adjusted to account for both the state information surrounding this time slot as well as the knowledge of the present time slot, which involves the distributions of task and node resource situations. Also double Q-learning is used to enhance DQL performance over time [6]. Many similar solutions using hybrid solutions are proposed in references [7–12].

# **Literature survey:**

The paper “Workflow Makespan Minimization for Partially Connected Edge Network: A Deep Reinforcement Learning-Based Approach” [13] takes on the