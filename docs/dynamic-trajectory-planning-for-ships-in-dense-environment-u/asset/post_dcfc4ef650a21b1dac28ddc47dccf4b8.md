
![](img/1449f405bc8501f365f83db0d9a0a33f_7_0.png)

Fig. 6. Schematic representation of the neural network architecture used to train the learning model. Two networks are employed for the PPO algorithm, with identical structures except for the output layer. The actor-network consists of 5 neurons that correspond to the actions available to the agent for modifying its trajectory, while the critic network has 1 neuron for estimating the value function.

squares in the horizon, resulting in an observation size of 208. To estimate the movement of moving obstacles without using a Recurrent Neural Network (RNN) (Salehinejad et al. 2018), we implement short-term memory by stacking the last 4 observations, resulting in 832 inputs. The actor-network has 5 outputs, and the critic-network has 1 output. Fig. 6 illustrates the structure of the two neural networks used in the agent's training with PPO. The experiment will be conducted using an AMD Ryzen 9 3900X and an NVIDIA GeForce RTX 3090 running on Ubuntu 18.04.6. The algorithms are implemented in Python 3.6.9, using Torch 1.10 and CUDA 11.1.

The agent is trajectory-free, meaning it can adapt its trajectory towards its objective by adjusting its rudder angle or speed. Therefore, it does not follow a predetermined or passive reward-influenced trajectory, but can adjust its behavior based on the encountered state. The agent can perform five possible discrete actions for the actor-network, which are “accelerate”, “decelerate”, “turn to port”, “turn to starboard”, or “do nothing”. When changing speed, the agent can modify its speed by ±0.5 m s⁻¹ within an interval of [1 – 5] m s⁻¹. We do not want the agent to maneuver while immobile, and the maximum speed is a constraint due to the limitation of its field of observation and therefore its reaction time. For the helm maneuverability, its amplitude is limited in the interval [−20°, +20°] and can only be changed by −5° or +5° at each time step to limit the possible reactions and physical constraints that the ship could have. The hyperparameters used for the PPO learning algorithm, which trains the neural networks, are summarized in Table 2, where the Adam optimizer with a beta of (0.9,0.999) is used.

## 5.2. Evaluation

Throughout the entire learning process, the type of collision, the duration of each episode (in time steps), and a binary value indicating the success or failure of each episode are saved. The analysis graphs presented in Fig. 7 are generated from this data and show the agent's learning progress over time. To enhance the readability of the different graphs, each displayed value for a given episode i is a rolling average calculated over the last 500 episodes, i.e., 1/500 Σ_{i-500}^{i} object_i, where object is the relevant information calculated for each graph. For example, steptime is used to plot the duration of each episode over time.

The upper part (TOP) of the figure presents the complete results of the experiment, while the lower part (BOT) displays only the evolution of the first 50,000 episodes. The first observation is that the agent has learned to reach its objective, and BOT shows that this learning was

Table 2
Hyperparameters utilized by the PPO algorithm to train the model. The table presents various hyperparameters, including the number of episodes, the batch size, the learning rate, the discount factor, and the value of the clipping parameter. These hyperparameters play a critical role in determining the convergence and stability of the PPO algorithm, and their values are typically set based on prior experience with similar problems rather than using an automated hyperparameter optimization tool.

| PPO Hyperparameters |  |  |
|---|---|---|
| Name | Symbol | Value |
| Number max of episode | K | 10⁶ |
| Batch size | T | 3 × 10⁴ |
| Learning rate | η | 0.0001 |
| Discount Factor | γ | 0.99 |
| Clipping parameter | ε | 0.1 |
| Number minibatch | N | 10 |
| Value function coefficient | c₁ | 0.5 |
| Entropy coefficient | c₂ | 0.01 |

achieved in less than 20,000 episodes. The graph in the middle shows that there is a rapid increase in success rate in the first 20,000 episodes, followed by a gradual increase until reaching a success threshold of approximately 80% after 30,000 episodes. The graph in the bottom right indicates that in the first 10,000 episodes, the average time step increases from 120 to 150, indicating that the agent learns to reach its objective but takes more time to do so. Subsequently, the average time step decreases to 80 as the agent learns to find a more optimal trajectory without increasing negative collisions with the environment. The graph in the BOT left shows that the number of negative collisions is rare, and the episodes ending in “none” are at zero, indicating that the agent always tries to achieve its objective. TOP demonstrates that this rapid learning is not lost over time, and there is even a slight increase in performance since the central graph's slope is not completely flat. The TOP graphs also show that there is no loss of learning over time, and the entropy coefficient stabilizes the results without allowing risky explorations.

A performance evaluation example is presented in Table 3. The environment settings are kept the same as the learning phase, and each evaluation is conducted with the same seed for comparison studies. The evaluations are performed at 1000, 10,000, 100,000, and 1 million episodes, with one evaluation representing the average performance of a run of 500 episodes. The table displays the accuracy rate, which is the percentage of successful episodes, the average duration of an episode measured in time steps, which refers to the average number of states observed by the agent before an episode ends, and the negative or zero collision rates, which represents the episodes where the maximum number of time steps has been reached without the agent reaching its goal or colliding with any obstacles.

It is important to note that some episodes are excluded from the performance calculation. Specifically, any episode lasting less than 20 time steps is removed from the calculations during evaluation. This is because it is believed that it takes at least 20 time steps at the beginning of an episode to start maneuvering if an obstacle is close to the agent. However, this estimate is highly dependent on the maneuverability capabilities of the agent, and the value would likely be much higher if the agent was less maneuverable. Episodes lasting less than 20 time steps leading to the goal are also ignored for consistency. The evaluation demonstrates that the agent continues to improve its behavior over time, and all cues are enhanced during the learning process. The summary Table 3 indicates that at the end of training, the agent shows an average performance of 94.69%. This means that only 5.31% of the 500 episodes tested, and exceeding the evaluation threshold of 20 time steps, resulted in negative collisions. The 500 evaluation scenarios are randomly generated and independent of those used during training. Accuracy is calculated as the number of episodes that have reached the objective divided by the total number of tested episodes, and the same method is used for calculating collision rates with fixed obstacles, ships, or walls. The evaluations are carried out using an environment set up in the same way as during learning, as summarized in Table 1. The 500 evaluation scenarios were generated in a total of 26.58 s, using the same setup as the learning phase.

![](img/1449f405bc8501f365f83db0d9a0a33f_8_0.png)

Fig. 7. Graphs depicting the evolution of the agent's learning over time. The left graph shows the distribution of collision types encountered by the agent, while the center graph displays the average number of episodes where the agent successfully reaches the objective. The right graph illustrates the average duration of each episode in terms of time steps. The top row of graphs represents the complete learning process, while the bottom row focuses on the first 50,000 episodes. These graphs provide valuable insights into the learning dynamics of the agent and the effectiveness of the training procedure.

## Table 3

Analysis of the model's performance at different learning checkpoints, defined as a number of episodes during the training process. The table displays the average collision rates of the model over 500 episodes, with the performance being evaluated on the same seed. By using various learning checkpoints and systematically evaluating the model's performance at different stages of the training process, the table shows how the collision rates of the model evolve over time.

| Performance evaluation | Number of episodes |  |  |  |
|---|---|---|---|---|
| | 10³ | 10⁴ | 10⁵ | 10⁶ |
| Accuracy (%) | 5.4 | 38.3 | 90.1 | 94.69 |
| Mean time step | 169 | 247 | 83 | 55 |
| Ships collision (%) | 30.3 | 21.3 | 2.5 | 2.5 |
| Static obstacle collision (%) | 14.5 | 18.9 | 7.1 | 2.8 |
| Walls collision (%) | 8.9 | 20.3 | 0.2 | 0 |
| Zero collision (%) | 40.9 | 1.2 | 0.3 | 0 |

## Table 4

Evaluation of the model's performance at the end of the training process by varying the density of the environment, where a density of k means having k obstacles of each type. The table displays the average collision rates of the model over 500 episodes for different densities, allowing for a comprehensive analysis of the impact of environmental complexity on the model's performance. By systematically varying the density of obstacles and measuring the corresponding collision rates, the table provides insights into the robustness of the model to changing environmental conditions.

| Performance based on density | Density |  |  |  |  |
|---|---|---|---|---|---|
| | 1 | 2 | 3 | 4 | 5 |
| Accuracy (%) | 98.6 | 96.8 | 94.69 | 88.9 | 83.89 |
| Mean time step | 45 | 54 | 55 | 63 | 71 |
| Ships collision (%) | 0.5 | 1.4 | 2.5 | 4.3 | 7.6 |
| Static obstacle collision (%) | 1 | 1.8 | 2.8 | 6.8 | 8.3 |

Table 4 displays the progress of an agent's performance using the same policy while altering the obstacle density in the environment. The density refers to the number of obstacles for each type. To ensure comparability, the various tests conducted on different densities were carried out on identical environment dimensions, i.e., 350×350 m. These assessments were performed on the same model trained previously, with only the agent's ability to navigate in environments of different densities being tested, considering that it was trained in a density 3 environment. The number of fixed and mobile obstacles was kept the same. The results show that the overall performance of the agent deteriorates with an increase in density, and too many obstacles hinder the agent's ability to navigate.

We can demonstrate the agent's learned behavior through two scenarios detailed in Fig. 8. These scenarios provide a visual overview of the agent's behavior in the environment. The environment used in the demonstration scenarios has been enlarged to a square of size 800×800 m, with ten obstacles of each type. The ships' dynamics, hitboxes, appearance modes, and behaviors of the different objects are the same as those used during training. The two episodes presented

above one another show the scenario's progression divided into four frames, each frame containing the same number of time steps, except the last one, which contains slightly more to display the entire episode. In each frame, the starting point is the large red dot, and the agent's last position in each image is the small red dot. Its previous positions are in yellow, and its objective is in green. We can also see the trajectories of mobile obstacles in blue and fixed obstacles in light blue. The two examples presented were selected based on their interest in analyzing the agent's behavior in only four frames. Sometimes the path to the objective is too short, making it interesting to analyze, or it enters a dense area where it is difficult to analyze its maneuvers with just one image.

In the first scenario, one can observe in frame 1 that the agent is already headed in the right direction at the start, and it moves straight towards its objective, making minor adjustments to stay on course. In frame 2, the agent tries to avoid a stationary and a moving obstacle by turning to port in a spiral, and then returning to its objective. In frame 3, a moving obstacle approaches the agent head-on, so the agent tries to dodge it by turning to port. We can see that the agent has turned almost 90° to avoid a collision, as a COLREG was activated, but it was forced to tack. Therefore, it chose to move far away from the ship to
