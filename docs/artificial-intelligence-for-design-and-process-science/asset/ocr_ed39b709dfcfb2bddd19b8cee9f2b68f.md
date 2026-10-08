# R. Vadhura and M. Huber

| Feature Vector | Test NN1 | Test NN2 | Test NN3 | Test NN4 | Test NN5 | Test NN6 | Test NN7 | Test NN8 | Test NN9 | Test NN10 | Avg. | Std Deviation | Best Accuracy from Network | Best Accuracy (Ratio) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|n| FV1 | 0.722 | 0.7116 | 0.7038 | 0.7129 | 0.7290 | 0.7059 | 0.7176 | 0.7108 | 0.7169 | 0.7104 | 0.71419 | 0.005146 | 0.7209 | 0.8868687 |
| FV2 | 0.629 | 0.6057 | 0.6528 | 0.5514 | 0.5869 | 0.5869 | 0.5869 | 0.5171 | 0.5171 | 0.5514 | 0.599651 | 0.015136 | 0.58621 | 1.01764977 |
| FV3 | | | 1 | 0.19922 | 1 | | | | | 1 | 1.99955 | | 0.00047 | 0.027068 | 0.94160043 |
| FV4 | 0.9061 | 0.9131 | 0.9135 | 0.9147 | 0.9147 | 0.9140 | 0.9148 | 0.9132 | 0.9147 | 0.9153 | 0.915328 | 0.003047 | 0.027618 | 0.90001754 |
| FV5 | | | | | | | | | | | 1 | 1 | 1.9995448 | | 0.99955448 |
| FV6 | 0.6359 | 0.6689 | 0.6830 | 0.6839 | 0.6879 | 0.6986 | 0.7072 | 0.6782 | 0.6435 | | 0.668954 | 0.02626 | 0.74327 | 0.90001754 |
| FV7 | 0.8869 | 0.8319 | 0.8530 | 0.8839 | 0.8846 | 0.886 | 0.86 | 0.853 | 0.883 | 0.84198 | 0.999553 | 0.0099553 | 0.82333 | 1.01316229 |
| FV8 | 0.9844 | 0.9464 | 0.8840 | 0.8460 | 0.8460 | 0.8464 | 0.8188 | 0.8175 | 0.8888 | 0.888928 | 0.882767 | 0.1934122 | 0.944444 | 0.9941162 |
| FV9 | 0.7562 | 0.5934 | 0.8860 | 0.8472 | 0.9151 | 0.9016 | 0.8175 | 1.0122 | 0.64217 | 0.827267 | 0.193412 | 0.039817 | 0.82533 | 1.01601784 |
| FV10 | | 0.8229 | 0.8229 | 0.8823 | 0.8383 | 0.8380 | 0.8235 | 0.7946 | 0.8083 | 0.80085 | 0.836765 | 0.034218 | 0.82533 | 0.99896322 |
| FV11 | | 0.9597 | 0.9564 | 0.9558 | 0.9593 | 0.9738 | 0.9681 | | 0.9593 | | 0.962168 | 0.006023 | 0.841928 | 0.99826324 |
| FV12 | | | 0.8387 | 0.8876 | 0.8548 | 0.8706 | 0.9149 | | | | 0.881717 | 0.033108 | 0.87097 | 1.02342062 |

Fig. 16 performance accuracy achieve or between until network vs network's discovered by policy

learned optimization policy achieve better or equivalent answers for the never-before-seen test problems.

# 6 Conclusions

Finding network architecture is essential for the success of deep learning systems. This chapter presents a novel deep learning framework that uses reinforcement-learning to learn a network architecture policy that transfers across target problems the world without needing for significant retraining.

The proposed approach optimizes networks in a learned embedding space constructed using an autoencoder and Siamese network. Using this and a performance predictor, an actor-critic RL component is trained, which uses the embedding vector as network representation as well as specific features to learn a policy for network architecture optimization over the continuous action space of embedding spaces. Initial experiments using classification datasets from the UCI repository show that the proposed system is able to successfully learn an embedding space as well as a policy that derives network architectures are close to optimal even for not-before-seen test problems.