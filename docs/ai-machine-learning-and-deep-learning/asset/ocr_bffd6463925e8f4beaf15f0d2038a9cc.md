avoidance policy. In both cases, noise or adversarial attacks are added to the observations.

Nominal DQN policy is not robust against the perturbed inputs. Increasing the magnitude of adversarial or noise increases the average number of collisions and decreases the average reward.

Lutjens et al. ran the DQN with add-on defense, called certified adversarially robust reinforcement learning (CARR L). The results showed that, by adding certified defense to the DQL model, we can address existing misclassification under adversarial attacks and sensor noise. If the robustness parameter is increased, the number of collisions decrease when observations are corrupted. The reward increases with an increasing robustness parameter at . Also, the CARR L policy only marginally reduces the reward under no perturbation. It cannot significantly deteriorate the performance of DRL.

# 10.4 ROBUSTNESS ON ADVERSARIAL STATE OBSERVATIONS

Zhang et al. [19] also investigated the robust DRL algorithm under adversarial perturbation or noisy environment conditions (Figure 10.4). Zhang et al. [19] further demonstrated that the naïve adversarial training methods cannot improve DRL robustness significantly in noisy environment but instead make DRL training unstable and deteriorate agent performance. They concluded that naïvely applying techniques from supervised learning to RL is not appropriate since RL and supervised learning are two quite different problems.