![](bbox=[0.19, 0.09, 0.48, 0.36])

![](bbox=[0.52, 0.09, 0.84, 0.36])

| Symbol | Description | Symbol | Description | Symbol | Description |
|---|---|---|---|---|---|
| ▲ | Push red slow. | ● | Pull red slow. | ■ | Slide red slow. |
| ▲ | Push green slow. | ● | Pull green slow. | ■ | Slide green slow. |
| ▲ | Push yellow slow. | ● | Pull yellow slow. | ■ | Slide yellow slow. |
| △ | Push red fast. | ○ | Pull red fast. | □ | Slide red fast. |
| △ | Push green fast. | ○ | Pull green fast. | □ | Slide green fast. |
| △ | Push yellow fast. | ○ | Pull yellow fast. | □ | Slide yellow fast. |

Figure 9.3 Latent representations of language and robot behavior by the coupled RAEs. Source: Adapted from Yamada, Matsunaga, and Ogata 2018.

ing a reward function and in performing a massive amount of exploration (with real robots). In the context of (cognitive) robotics and robot learning, imitation learning includes the following two cases: 1) learning from sensorimotor experiences and 2) learning from sensorimotor experiences by observing another agent’s demonstrations. In both cases, it is necessary to provide demonstrations about robot performance during the learning process via kinesthetic teaching or teleoperation by a human demonstrator. The difference between them is whether or not the sensory (mainly visual) experiences include demonstrations about the performance of another agent, typically a human. Namely, in the second case robots are required not only to learn to generate their own actions but also to map an observed other’s actions to their own by inferring what to perform and how to perform. This is much closer to the original meaning of imitation by humans and animals in the context of cognitive science (Meltzoff and Moore 1977).

There are several machine-learning approaches for performing imitation learning, such as neural networks (e.g., CNNs and RNNs); probabilistic models such as the combination of a Gaussian mixture model and Gaussian mixture regression (e.g., Calinon, Guenter, and Billard 2007); hidden Markov models (e.g., Inamura et al. 2004); and dynamical systems (e.g., dynamic movement primitives in Ijspeert, Nakanishi, and Schaal [2002] and Ijspeert