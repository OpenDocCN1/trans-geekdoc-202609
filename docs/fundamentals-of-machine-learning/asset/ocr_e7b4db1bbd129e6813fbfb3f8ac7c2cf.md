# Reinforcement learning in the brain | 231

![](bbox=[0.178, 0.093, 0.804, 0.447])

**Fig. 11** Deep Deterministic Actor-Critic (DDAC) network (from Lillicap, 2015).

reinforcement learning, behavioural cognitive science, and neuroscience is related to reinforcement learning. This brief section presents a brief outlook into this fascinating area.

We started this chapter by acknowledging classical animal learning experiments of conditioning. One of the most famous of these is the experiment by Ivan Pavlov at the turn of the 20th century showing a conditioned flex of salvation in dogs following tones. Such conditioning behaviour was modeled by Robert A. Rescorla and Allan R. Wagner in 1972. The base form of the Rescorla-Wagner model has a form of

> $$\Delta V = \alpha(\lambda - V)$$

where what is described here is the associative strength between a stimulus and reward prediction: $\alpha$ describes the salience of a stimulus, $\beta$ is some learning rate. The most interesting part is the expression in brackets that represents the difference between the real reward and expectation of reward. This model is a form of temporal difference model. Reinforcing learning to models of behavioral conditioning is already an interesting step. However, an even bigger step was made when Wolfram Schulz, Peter Dayan, and Montague related the neural signals found by Wolfram Schulz in dopaminergic neurons in specific areas of the midbrain.

The upper panel in Fig. 10.12 shows that these neurons become active if an unexpected reward is given. The lower example shows the activation of the same neurons when a predictor of a reward is given later in the trial. The experiment demonstrates the backpropagation of the reward prediction, and the experiments have been described successfully with TD learning. The midbrain collection of nuclei called