# Evolution of a ship position with different K/T parameters

![](bbox=[0.07, 0.12, 0.45, 0.27])

Fig. 5. Evolution of the position of a ship over 100-time steps by applying Nomoto's 1st order model as a function of different T, K. The ship maintains a constant speed while keeping its rudder angle fixed at 5°.

obtained at the end of the episode is considered. Although it is common to apply a modified reward to all observed states to accelerate learning and to evaluate certain states more accurately, it is not advisable in this study. The trajectory (time, speed, etc.) is not intended to be constrained too much, as it may lead to convergence towards dangerous states. Instead, the agent is taught to develop collision avoidance strategies even if it means taking longer paths.

The first justification is that a collision grid is used to evaluate the states’ value, which clearly delimits the danger zones with negative weights and the interesting zones with positive or zero weights. This evaluation will be reflected in the network’s updates, and the discounted reward will still assess the relevance of each transition leading to either a successful or a failed episode, even in the absence of a passive reward. Thus, a correlation can be made between the grid, its weights, and a discounted reward. The second justification is the complexity of constructing a passive reward function. It is difficult and ambiguous to determine the impact of each part of this function on the agent’s convergence towards its goal. For instance, if the objective is too far away, a relative objective is displayed at 50% of the horizon, which further complicates the passive reward function. In the absence of obstacles, it is impossible to differentiate between a positive action towards the goal and a neutral or negative one when the grid remains unchanged. Thus, for such a transition, the reward becomes ambiguous, and providing a fixed reward would not align with the actual occurrence. Attempting to resolve this ambiguity by relying on the agent’s heading is also insufficient since the rate of turn may not change the relative objective from one box to another. Even if a good evaluation of goal achievement was determined, it would still be necessary to assess the distance, potential collisions, and any violation of COLREG to establish a global reward. Since this information has already been considered in the grid at each step, including it in the reward would be redundant. Moreover, the weighting of different components is a significant disadvantage of passive rewards, and it is challenging to determine the appropriate weight for each component. The process of weighting the reward can be difficult as it involves a significant amount of hyperparameterization. Additionally, it may only be applicable to the particular problem at hand, making it difficult to reproduce with any modifications to the environment or actions taken by the agent. As a result, the agent can only receive a reward that is a constant value among three possibilities, which is determined by the type of collision. For instance, if the agent collides with the goal, it receives a reward of +5. However, if it collides with an obstacle or border, it receives a reward of −1, and in all other situations, the reward is 0. The equation for the reward function is shown in Eq. (4), and at the end of each

# Table 1

Details of configuration of the environment used for training and evaluating the model.

| Environment specifications |  |
| Name | Value |
| Number of mobile obstacles | 3 |
| Number of static obstacles | 3 |
| Positive reward | 5 |
| Negative reward | -1 |
| Null reward | 0 |
| Horizon of main ship (m) | 120 |
| Size of a square (m) | 15 |
| Obstacles hitbox radius (m) | 15 |
| Objective hitbox radius (m) | 13 |

episode lasting t time steps, we compute the cumulative reward for each time step from i = t − 1 to i = 0 using the discount factor γ as rW_i = γ × rW_{i+1}. There is no penalty for the number of time steps taken during an episode, so the agent is not penalized for using longer or shorter trajectories to reach its goal. The primary objective is therefore to reach the goal without colliding with any obstacles, and the only non-zero rewards come from positive or negative collisions that end an episode.

rW_final = { 5 if collision=objective
-1 if collision=(ships or obstacles or walls)
0 otherwise } (4)

# 5. Model validation

# 5.1. Agent training

The generation of our model will occur in two phases. The first phase involves the training of our model, while the second phase involves the evaluation of its performance. The training process will comprise one million episodes, each with a maximum duration of 300 time steps. The total training time will be approximately 52 h, which primarily depends on the number of squares in the grid and the number of obstacles in the environment. At the start of each episode, the agent’s starting position, objective, and various obstacles in the environment will be randomly initialized. Thus, the learning environment will not remain static, and the parameters of the environment are summarized in Table 1. During both the learning and evaluation phases, at the start of each new episode, the position of all obstacles, as well as the rudder angle and direction for moving obstacles, are randomly reset, along with the position of the ship piloted by the agent and its target. This randomization of the environment allows us to observe the agent’s ability to generalize its policy and perform well in previously unseen scenarios. The size of the environment is limited to 350 × 350 meters, with a maximum of three obstacles of each type. This constraint is expected to accelerate the learning process by enabling faster convergence and shorter episode durations. Additionally, limiting the number of obstacles should help the agent learn to avoid them without solely focusing on obstacle avoidance. Finally, since the input data is limited to a grid with a horizon, the size of the environment does not significantly impact the model’s performance. While we can test the model on environments with varying sizes and obstacle densities, a restricted size during learning should result in faster convergence, albeit at the expense of partial observability of the environment by the agent.

To train the model using the PPO learning method, two neural networks need to be defined: the actor-network, which assigns weight to each action, and the critic-network, which evaluates the value of the agent’s actions. Both networks have the same internal structure and the same number of inputs, namely, 3 hidden layers of 512 fully connected neurons. The input size is determined by the number of