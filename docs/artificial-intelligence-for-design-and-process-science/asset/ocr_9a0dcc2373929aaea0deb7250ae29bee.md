# A Reinforcement Learning Framework for Transferable Neural... 135

![](bbox=[0.125, 0.096, 0.874, 0.212])

**Fig. 5** Encoder-decoder

![](bbox=[0.118, 0.266, 0.859, 0.566])

**Fig. 6** Co-located legal and illegal networks

# 4.2 Accuracy Model

As accuracy prediction is problem specific, the accuracy model’s input is comprised of the concatenation of the embedding and a “problem description” feature vector. Using this, it predicts a performance measure for the network for the target problem as well as whether the embedding space corresponds to a legal architecture. It serves to help organize the embedding space and to generate simulated rewards in order to minimize the amount of network training. The example layered architecture used in the experiments later is shown in Fig. 7.

During the first training phase encoder-decoder and accuracy models are trained together using a loss function that includes reconstruction loss as MSE, embedding consistency loss from the Siamese network, as well as accuracy prediction and legal network identification losses.