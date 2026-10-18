relaxations. This smoothing procedure can be done at test time. During training time, Zhang et al.’s goal is to keep small.

# 10.4.2 State-adversarial DRL for Q-Learning: DQN

Besides DDPG, Zhang et al. [19] also formulated the robust policy regularizer for DQN. Because the action space for DQN is finite, and Q-learning’s policy is to maximize Q-value, then the total variation distance between true state s and adversarial state in DQN is

A hinge-like robust policy regularizer is used, where and c is a small positive constant:

Zhang et al.[19] pointed out that, unlike DDPG, the regularized reward sum is similar to the robustness of classification tasks, if is treated as the “correct” label. The maximization can be solved using projected gradient descent (PGD) or convex relaxation of neural networks [19].

# 10.4.3 Experimental Results

Similar to certificated verification, Zhang et al. [19] also assumed the set of adversarial states. is a -norm ball around s with radius . is also referred to as the perturbation budget.

Zhang et al. ran SA_DDPG in five different environments (Ant, Hopper, Inverted Pendulum, Reacher, and Walker2d) to test the robustness of SA-DDPG. Zhang et al. evaluated SA-DDPG with SGLD and convex relaxation. They measured the median, minimum, 25%, and 75% rewards in each training. Their results showed that SA-DDPG is able to consistently improve robustness: the statics of SA-DDPG is higher or equal to DDPG in five environments.

SA-DQN was implemented on four Atari games and one control problem: Pong, Freeway, BankHeist, RoadRunner, and Acrobot. Zhang et al. included vanilla DQN and adversarially trained DQN with 50% adversary as baselines. They observed that SA-DQN achieves much higher rewards under adversarial attacks in most environments and that naïve adversarial training is mostly ineffective under strong attacks.