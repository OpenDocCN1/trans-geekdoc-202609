
![](img/dd452eef0506ea820c436fef2f776436_149_0.png)

![](img/dd452eef0506ea820c436fef2f776436_149_1.png)

![](img/dd452eef0506ea820c436fef2f776436_149_2.png)

### Figure 9.5

Generative adversarial networks (GANs). The top panel illustrates a convolutional network used to generate a sample of images trained to fool the discriminative convolutional network. The input on the left are 100-dimensional continuously valued vectors that are chosen randomly to generate different images; the input vector then activates layers of filters with a larger and larger spatial scale. The lower panels display sample images produced by training a GAN on photos from single categories. Top: From A. Radford, L. Metz, and S. Chintala, “Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks,” figure 1, arXiv:1511.06434, https://arxiv.org/pdf/1511.06434.pdf. Courtesy of Soumith Chintala. Bottom: From A. Nguyen, J. Yosinski, Y. Bengio, A. Dosovitskiy, and J. Clune, “Plug & Play Generative Networks: Conditional Iterative Generation of Images in Latent Space,” figure 1, https://arxiv.org/pdf/1612.00005.pdf. Courtesy of Ahn Nguyen.

![](img/dd452eef0506ea820c436fef2f776436_150_0.png)

### Figure 9.6

Vector arithmetic in generative adversarial networks. Mixtures of inputs to a generative network trained on faces produced the outputs on the left, which were then used to create the blends on the right by adding and subtracting the chosen input vectors. Because the blends are done at the highest representational level, parts and poses are seamlessly combined, rather than averaged as occurs in morphing. Adapted from A. Radford, L. Metz, and S. Chintala, “Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks,” figure 7, arXiv:1511.06434, https://arxiv.org/pdf/1511.06434/.

![](img/dd452eef0506ea820c436fef2f776436_151_0.png)

### Figure 9.7

Spring/summer 2018 men's wear show for Giorgio Armani, in Milan.

The number of units and connections increased to match the complexity of real-world problems. Most algorithms in AI scale badly and never went beyond solving toy problems. We now know that neural network learning scales well and that performance continues to increase with the size of the network and the number of layers. Backprop, in particular, scales extremely well.

Should we be surprised? The cerebral cortex is a mammalian invention that mushroomed in primates and especially in humans. And as it expanded, more capacity became available and more layers were added in association areas for higher-order representations. There are few complex systems that scale this well. The Internet is one of the few engineered systems whose size has also been scaled up by a million times. The Internet evolved once the protocols were established for communicating packets, much like the genetic code for DNA made it possible for cells to evolve.

Training many deep learning networks with the same set of data results in a large number of different networks that have roughly the same average level of performance. What we would like to know is what all these equally good networks have in common, but analyzing a single network will not reveal this. Another approach to understanding the principles behind deep learning is to further explore the space of learning algorithms; we have only sampled a few locations in the space of all learning algorithms. What could emerge from a much broader exploration is a computational theory of learning as profound as theories in other areas of science,^27 one that could shed much welcome light on the learning algorithms discovered by nature.

Yoshua Bengio^28 (figure 9.8) at the University of Montreal and Yann LeCun succeeded Geoffrey Hinton as the directors of CIFAR’s Neural Computation and Adaptive Perception (NCAP) Program when it passed its ten-year review and was renamed “Learning in Machines and Brains.” Yoshua led a team at the University of Montreal that applied deep learning to natural language, which will be a new focus for the Learning in Machines and Brains program. In meetings over ten years, this small group of around two dozen faculty and fellows gave birth to deep learning. The substantial progress in the last five years in the application of deep learning to many problems that had previously been intractable can be traced to them, but of course they are a small part of a much larger community (one that will be explored in chapter 11).

Even though deep learning networks have proven themselves in many applications, they would never survive on their own in the real world.^29

![](img/dd452eef0506ea820c436fef2f776436_152_0.png)

### Figure 9.8

Yoshua Bengio is the codirector of the CIFAR Learning in Machines and Brains Program. A French-born Canadian computer scientist, Yoshua has been a leader in applying deep learning to problems in natural language. Advances made by Geoffrey Hinton, Yann LeCun, and Yoshua Bengio were seminal for the successes of deep learning. Courtesy of Yoshua Bengio.

They are coddled by researchers who feed them data, who tweak their hyperparameters like learning rate, number of layers, and number of units in each layer to improve convergence, and who provide them with vast computing resources. On the other hand, neither would the cerebral cortex survive in the real world without the rest of the brain and body to provide support and autonomy, which, in an uncertain world, is a much more difficult problem than pattern recognition. Chapter 10 will introduce an ancient learning algorithm that helped us survive in nature by motivating us to seek rewarding experiences.

## 10 Reward Learning

According to a story going back to the Middle Ages, the inventor of the game of chess was offered a field of wheat from a grateful ruler. The inventor instead requested one grain of wheat on the first square, two on the second, four on the third, and so on, doubling the number of grains on each successive square until all sixty-four squares of the chess board were covered with grains of wheat. Thinking this a modest request, the ruler readily agreed. In reality, however, to grant that request, he would have had to have given the inventor not just all the wheat in his kingdom, but all the wheat in the entire world for many centuries to come since the number of wheat grains on the sixty-fourth square would have been 2^64 (roughly 10^19).^1 This is called “exponential growth.” The number of board positions in games like chess and Go grows even faster than the number of wheat grains in our story. At every move, there are on average thirty-five possible moves in a chess game, and, for Go, the branching factor is 250. This makes the exponential growth much more rapid.

### Learning How to Play Backgammon

Games have the advantage that the rules are well defined, the players have perfect knowledge of the board and the decisions not as complex as those in the real world, but sufficiently complex to be challenging. In 1959, Arthur Samuel, a machine learning pioneer at IBM in the early days of commercial digital computers, wrote a program that could play checkers so successfully that on the day it was announced, IBM’s stock scored a major gain. Checkers is a relatively easy game, but Samuel’s program, based on a cost function to assess the strengths of different game positions, much like previous game programs, and run on IBM’s first commercial computer, the IBM 701, which used vacuum tubes, was impressive in one novel respect: it learned by playing itself.

Before moving on to IBM's Thomas J. Watson Research Center in Yorktown Heights, New York, Gerald Tesauro worked with me when he was at the Center for Complex Systems Research at the University of Illinois in Urbana-Champaign on the problem of teaching a neural network to play backgammon (figure 10.1).² Our approach used expert supervision to train networks with backprop to evaluate game positions and possible moves. The flaw in this approach was that the program could never get better than our experts, who were not at world-championship level. But, with self-play, it might be possible to do better. The problem with self-play at that time was that the only learning signal was win or lose at the end of the game. But when one side won, which of the many moves were responsible? This is called the “temporal credit assignment problem.”

A learning algorithm that can solve this temporal credit assignment problem was invented in 1988 by Richard Sutton,³ who had been working closely with Andrew Barto, his doctoral advisor, at the University of Massachusetts at Amherst, on difficult problems in reinforcement learning, a branch of machine learning inspired by associative learning in animal experiments (figure 10.2). Unlike a deep learning network, whose only job is to transform inputs into outputs, a reinforcement network interacts in a closed loop with the environment, receiving sensory input, making

![](img/dd452eef0506ea820c436fef2f776436_155_0.png)

### Figure 10.1

Backgammon board. Backgammon is a race to the finish, with the red pieces moving in the opposite direction of the black pieces (arrows). The starting position is shown. Two dice are rolled, and the two numbers indicate how far two pieces can be moved ahead.
