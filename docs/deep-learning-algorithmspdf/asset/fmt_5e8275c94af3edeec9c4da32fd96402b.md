
# Reinforcement Learning Algorithms

Reinforcement learning algorithms estimate the action value function by iteratively updating the Bellman equation. When value function \[1\]. If the optimal Q-function Qχ is known, the agent can select optimal actions by selecting the action with the maximal value in a state.

## Target Deep Q Learning

RL agents update their model parameters while they observe a stream of transitions like. They discard the incoming data after a single update. There are two issues with this method. The first one is that there are strong correlations among the incoming data, which may break the assumption of many popular stochastic gradient-based algorithms. Secondly, the minor changes in the Q function may result in a huge change in the policy, which makes the algorithm difficult to converge \[7, 9, 14, 15\].

As for the deep Q-networks algorithms proposed in (Mnih et al., 2013), two aspects are improved. On the one hand, the action value function is approximated by the DNN, DQN uses the DNN with a parameter to approximate the value function; on the other hand, the experience replay mechanism is adopted. The algorithm learns from sampled transitions from an experience buffer, rather than learning fully online. This mechanism makes it possible to break the temporal correlations by mixing more and less recent experience for updating and training. This model free reinforcement learning algorithm solves the problem of “model disaster” and uses the generalized approximation method of the value function to solve the problem of “dimension disaster. The convergence issue was mentioned in 2015 by Schaul et al. \[14\]. The above Q-learning update rules can be directly implemented in a neural network. DQN uses the DNN with parameters to approximate the value function. The parameter updates from transition are given by the following \[11\]:

(1)

with

The update targets for Sarsa can be described as follows: (2)

本书版权归Arcler所有

![Image 538](index-123_1.png)

![Image 539](index-123_2.png)

![Image 540](index-123_3.png)

![Image 541](index-123_4.png)

![Image 542](index-123_5.jpg)

![Image 543](index-123_6.jpg)

![Image 544](index-123_7.jpg)

![Image 545](index-123_8.jpg)

![Image 546](index-123_9.png)

![Image 547](index-123_10.png)

![Image 548](index-123_11.png)

![Image 549](index-123_12.png)

![Image 550](index-123_13.png)

## Ensemble Network Architecture for Deep Reinforcement Learning 97

where

is the scalar learning rate.

are target network parameters which are fixed to. In case the squared error is taken as a loss function.

In general, experience replay can reduce the amount of experience required to learn and replace it with more computation and more memory, which are often cheaper resources than the RL agent’s interactions with its environment \[14\].

## Double Deep Q Learning

In Q-learning and DQN, the max operator uses the same values to both select and evaluate an action. This can therefore lead to overoptimistic value estimates (van Hasselt, 2010). To mitigate this problem, the update targets value of double Q-learning error can then be written as follows: (3)

DDQN is the same as for DQN \[8\], but with the target replaced with.

## Ensemble Methods for Deep Reinforcement Learning

As DQN classes use DNNs to approximate the value function, it has strong generalization ability between similar state inputs. The generalization can cause divergence in the case of repeated bootstrapped temporal difference updates. So we can solve this issue by integrating different versions of the system have been shown to be more effective. They can lead to a higher accuracy. Bagging, boosting, and Ada Boosting are methods to train multiple learning the value function. They are combined by major voting, Rank Voting, Boltzmann Multiplication, mixture model, and other ensemble Temporal Ensemble

As described in Section 2.2, the DQN classes of deep reinforcement learning algorithms use a target network with parameters copied from every

本书版权归Arcler所有

![Image 551](index-124_1.png)

![Image 552](index-124_2.jpg)

![Image 553](index-124_3.jpg)

![Image 554](index-124_4.png)

![Image 555](index-124_5.jpg)

![Image 556](index-124_6.jpg)

![Image 557](index-124_7.jpg)

![Image 558](index-124_8.png)

![Image 559](index-124_9.jpg)

![Image 560](index-124_10.jpg)

![Image 561](index-124_11.png)

![Image 562](index-124_12.png)

![Image 563](index-124_13.png)

![Image 564](index-124_14.png)

## Deep Learning Algorithms 98

C steps. Temporal Ensemble method is suitable for the algorithms which use a target network for updating and training. Temporal ensemble uses the previous K learned networks to produce the value estimate and builds up N complete networks with K distinct memory buffers. The recent Q-value function is trained according to its own target network. So each one of Q-value functions represents temporally extended estimate of Q-value function.

Note that the more recent target network is likely to be more accurate at the beginning of the training and the accuracy of the target networks is increasing as the training goes on. So we denote a learning rate parameter here for target network. The weight of ith target network is.

So the learned Q-value function by temporal ensemble can be described as follows:

(4)

As lim, we can see that the target networks have the same weights when equals 1. This formula indicates that the closer the target networks are, the greater the target networks’ weight is. As target networks become more accurate, their weights become equal. The loss function remains the same as in DQN and so does the parameter update equation:

(5)

In every iteration, the parameters of the oldest ones are removed from the target network buffer and the newest ones are added to the buffer. Note that the Q-value functions are inaccurate at the beginning of training. So the parameter may be a function of time and even the state space.

## Ensemble of Target Values

The traditional ensemble reinforcement learning algorithms maintain multiple tabular algorithms in memory space \[4, 16\], and majority voting, rank voting, Boltzmann addition, and so forth are used to combine these

![Image 565](index-125_1.jpg)

![Image 566](index-125_2.jpg)

![Image 567](index-125_3.jpg)

![Image 568](index-125_4.png)

![Image 569](index-125_5.png)

![Image 570](index-125_6.png)

## Ensemble Network Architecture for Deep Reinforcement Learning 99

tabular algorithms. But deep reinforcement learning uses neutral networks as function approximators. Te use of multiple neural networks is very computationally expensive and inefficient. In contrast to previous researches, we combine diferent DRL algorithms that learn separate value functions and policies. Terefore in our ensemble approaches we combine the diferent policies derived from the update targets learned by deep Q-networks, deep Sarsa networks, double deep Q-networks, and other DRL algorithms as follows:

(6)

Besides these update targets formula, other algorithms based on value function approximators can be also used to combine. The update targets according to the algorithm k at time t will be denoted by.

The loss function remains the same as in DQN and so does the parameter update equation:

(7)

## The Ensemble Network Architecture

The temporal and target values ensemble algorithm (TEDQN) is an integrated architecture of the value-based DRL algorithms. As shown in Sections 3.1 and 3.2, the ensemble network architecture has two parts to avoid divergence and improve performance.

The architecture of our ensemble algorithm is shown in Figure 1; these two parts are combined together by evaluated network.
