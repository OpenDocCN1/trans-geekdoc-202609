# Table 3 Used parameters for DDRL.

| Parameter | Value | Explanation |
| :--- | :--- | :--- |
| env | LeaderFollower | |
| Env_type | OpenAI Environment | |
| Executed algorithm | PPO | |
| Stop condition | Time-steps = 300000 | |
| lambda | 1.0 | The GAE (generalized advantage estimation) parameter |
| train_batch_size | 400 | Size of each SGD (stochastic gradient descent) epoch |
| learning rate | 5e-5 | Learning rate for training |
| kl_coeff | 0.2 | Initial koefficient for KL divergence |
| Num_sgd_iter | 30 | Number of sgd iterations in each outer loop |
| Num_gpu | 0 | |
| worker | 0 | |

# Table 4 Comparison of existing papers on the study of UAV drone tracking.

| Paper | Algorithm | Performance values |
| :--- | :--- | :--- |
| [29] | CNN-LSTM (distributed) | The accuracy rate is ~%98 |
| [30] | DDPG | 35% of the successful tracking ratio |
| [31] | SAC | The average reward is 32 |
| [32] | UCT (distributed) | 75% of the successful tracking ratio |
| [33] | DRL | The cumulative total reward is 73.70 |
| [34] | CMDP | 28% searching time reduction |
| [35] | MDP | Control accuracy (m/s2) is 0.2691 |
| Our study | Distributed PPO | The average reward is -54.78 |

trained in a distributed manner. We can follow the experiments in three different axes. Accordingly, the follower drone performed the tracking function in the vertical plane for a period of 6 s. During this time, the second experiment was about ten times more successful than the first.

the follower drone performed the tracking function in the vertical plane for a period of 6 s. In Fig. 4 , drone tracking is simulated.

Table 4 shows the results of some special studies in the literature similar to the experiments conducted in this paper according to the environment and DRL algorithms used. When Table 4 is analyzed, it is seen that different effects, such as average reward or task success rate, are obtained according to the environment in which reinforcement learning is used. The fact that distributed systems have not been used much in the drone tracking problem makes it difficult to compare the results. In addition, since the approach proposed in our paper is to prove the success of the distributed system over the non-distributed system in drone tracking, it is impossible to compare it with similar problems.

The software is a piece of code that can be easily used and installed by the user without requiring anything other than some basic requirements. In particular, they can customize the artificial neural network and change the simulation environment. Therefore, it can be widely used in academic and scientific studies. The software also makes it easier for researchers to combine distributed architecture and reinforcement learning algorithms. Since the algorithm trained using Python code is open source, other users can easily update and improve it. This software is shipped fully open source using the MIT license and an explanatory user manual with links to all the libraries used.

# 4. Impact

This study addresses problems such as motion control, object tracking, and vertical elevation for a quadcopter. A gradient-based deep RL approach is used to establish a control strategy. This article presents two different approaches to training the DRL algorithm. The first approach trains the learning algorithm with a distributed architecture. The second is trained as non-distributed. The training was carried out using the CPU. To increase the success of the training and reduce the computational cost in such complex problems, we have shown with experiments that the CPU cannot be successful alone and can be more successful with more than one worker when trained in a distributed manner. We can follow the experiments on three different axes. Accordingly,

# 4.1. Experimental results

In both experiments, while 300000 time-step training was performed, the division-based average of the rewards received by the agent from the environment is shown in Fig. 5. While the agent was trained for a total of 700 episodes during the training phase in the first experiment, this value was approximately 500 episodes in the second experiment. The distributed-trained agent completes more Episodes in the same time slot. When Fig. 5 is examined, it is concluded that the mean reward value of the distributed PPO algorithm during the training is -54.78 and that the non-distributed PPO algorithm is -559.49. Comparing the results in this experiment, training time, rewards received in episodes, and solving the given task, It was found that the second experiment gave more successful results than the first. Training for the second experiment took approximately 1 h.