# CHAPTER 15 NOT A CRYSTAL BALL: MACHINE LEARNING

are treated. At input, a sentence is converted to an embedding, which represents the semantics (meaning) of each word, and then each word is assigned a number representing its position in the sequence. There are some functions used that can discover relationships between the words. The network makes some adjustments to the layers and then works as a feedforward neural net. Transformers still require a lot of training, but they're more efficient than RNNs and run faster on new data.

The final type of neural nets I'll mention is the generative adversarial network (GAN), which is actually two neural nets that interact with each other in a prescribed way to generate output. You can see the overall structure in Figure 15-12. One of nets is called the generator, which generates data based on random data. The generator's main goal is to generate plausible output. This generated data is fed into the second net, the discriminator, as negative training examples. The discriminator is a classifier that also has real data coming in input, so its task is to learn tell what the real data is, as opposed to the fake data coming out of the generator. The outputs from the generator feed directly into the inputs of the discriminator.

![](bbox=[0.082, 0.563, 0.856, 0.731])

Figure 15-12. The generative adversarial network structure and training behavior

Backpropagation is used from the discriminator outputs all the way back to the generator and uses the calculation to adjust the generator weights (note that it's only the generator that's changed this way, for

536