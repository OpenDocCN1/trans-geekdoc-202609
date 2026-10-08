# Encoder and Decoder Model

| Task Features (13) | NN (Layers, Nodes in each Layer) | NN (Layers, Nodes in each Layer) | Task Features (13) |
|---|---|---|---|n| Gaussian Noise | Encoder | | Gaussian Noise |
| Transformed Feature Vector | | Sister Networks | | Transformed Feature Vector |
| Concatenate | | | Concatenate | |
| | Decoder | | |
| Accuracy | | (Euclidean_Distance (embedding 1, embedding 2) Legal Network's Consensus) | Accuracy | Actor |
| | Siamese Networks | | Critical | Policy |
| Accuracy & Legal/illegal | NN (Layers, Nodes in Layers) | Distance | NN (Layers, Nodes in Layers) | Accuracy & Legal/illegal | Critical State & Critical Advantage Policy

**Fig. 4** Architecture overview

The “encoder” model transforms the network description into an embedding space, with the problem description, serves as input to the “accuracy” prediction, “actor,” and “critic” networks. The “decoder” model is used to translate the embedding back to a corresponding network architecture for the target task. To improve the organization of the embedding space, a Siamese network [30] was also used encapsulating the encoder-decoder and action prediction networks as indicated as a dashed box in Fig. 4, where an embedding space is derived using an encoder-decoder and Siamese to focus on learning embeddings to place legal networks together and augmented with prediction features to form the state. On this, an accuracy and legal embedding prediction network (center) predicts reward, and an actor-critic pair (right) learns the value function and network modification policy.

The encoder learns to transform the “network architecture description” into a continuous embedding space. The decoder performs the reverse, translating an embedding point back into a network description as shown in Fig. 5.
To organize the embedding space, this autoencoder is augmented with lost terms from the “accuracy prediction” network and arranged in a Siamese network to co-locate embeddings that decode into legal network descriptions. The effect of this is an embedding space that is easy to traverse by the actor as shown in the embedding space image in Fig. 6, where blue regions correspond to legally decodable network architectures, while red regions decode to illegal descriptions.