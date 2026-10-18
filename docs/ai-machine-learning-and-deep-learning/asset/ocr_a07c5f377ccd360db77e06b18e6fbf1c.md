and is neural network parameters for policy . The policy gradient is defined as [5]

2. Q-learning: This is an off-policy RL. The main aim of Q-learning is to maximize the Q-value, which is shown here. is the next state based on the action taken in previous state, and is a possible action in . is the learning rate, shows the iteration number, and is the discount factor:

This equation clearly demonstrates that Q-learning decides the next move and knows . It uses -greedy policy and finds the action with the highest Q-value increment.

# 10.2.2 Deep Reinforcement Learning

In real-world applications, the input cannot be as simple as discrete states and can be represented by a value. The input data may have high dimension, like images in an autonomous vehicle. One solution is to extract the features from high-dimensional data. But this relies on the researcher’s design. And it is intricate to extract the information of targets from the input images.

Another approach is to use a neural network to find the optimal policy value function or Q-function. This is the basic idea behind DRL. In 1992, Gerald Tesauro developed a computer backgammon program, called TD-Gammon, trained by neural network by using temporal-difference learning [6]. TD-Gammon is just slightly below the top human backgammon players of the time. It explores the strategies that no one has before and advances the theory of backgammon play.

When DL occurs, it behaves powerfully in image processing. DL can extract features from high-dimensional input images or videos, and those features are more generalized than artificial features.

There are three main approaches to solving RL by utilizing DL: methods based on Q-value, methods based on policy search, and a hybrid of both in actor-critic configurations.

Classic Q-networks have many problems when learning Q-values. First, the training data is not iid (independent and identically distributed) because successive samples are correlated [7]. Second, even slight changes to the Q-