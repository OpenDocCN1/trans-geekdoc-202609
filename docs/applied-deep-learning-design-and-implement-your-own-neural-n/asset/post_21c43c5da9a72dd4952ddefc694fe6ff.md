
Figure 8.2 depicts the basic architecture of GAN:

![](img/7e519fee1b702b91799cdf1664598392_566_0.png)

Figure 8.2: Basic architecture of GAN showing with generator and the discriminator networks.

**Real dataset**: It contains the real samples that are given as input (x) to the discriminator. The generator is trained to produce new samples that appear to belong to this original dataset.

**Random noise vector**: It is the input (z) given to the generator, which it learns to transform into fake samples. It acts as the initial seed or starting point for the generator.

- **Generator**: It is a neural network that takes a random noise vector as a starting point and generates new samples (x*) as output.

- **Discriminator**: It is another neural network that takes as input real images (x) and fake images (x*) and identifies them as real (1) or fake (0).

Here, the generator network uses the random noise vector to produce fake samples and passes them to the discriminator network. Discriminator, which is a trained network on a real data set, identifies it as real (from the real dataset) or a fake sample (generated image). So, when the discriminator identifies it as a fake image, the generator knows that it needs improvement. On the other hand, if the discriminator gets confused and classifies it as a real image, which means that the generator learned very well. As the generator improves, the discriminator also improves itself from the feedback. Each time it recognizes an image as fake, it also learns and improves in identifying fake images. So, we can say that both generator and the discriminator improve themselves from this setup continuously. This learning is an iterative process, which requires moving back and forth to reach a level of expertise for both the generator and discriminator. Table 8.1 explains the inputs, outputs, and aims of the generator and discriminator networks of GAN.

| | Generator | Discriminator |
|---|---|---|
| Input | Random Noise Vector(z). | Both Real(x) and Fake(x*) Samples. |
| Output | New generated fake (x*) samples. | Classifying input as real(1) or fake(0). |
| Aim | Generating samples that appear to belong to the original dataset. | Correctly identifying real and fake without confusion. |

Table 8.1: Inputs, outputs, and aim of generator and discriminator networks of GAN

## Training a GAN

The training of a GAN requires individual training of both generator (G) and discriminator (D) networks in a particular order, as follows:

- *First of all, the discriminator is trained on the real dataset while keeping the training of the generator network frozen (which means setting the training of the generator to false).
- *Now, the generator network is trained with the help of feedback from our trained discriminator. This time, the training of the discriminator is frozen.

## Training algorithm for GAN

These two steps further consist of some actions taken in order to train both the discriminator and the generator. All these steps are explained in the form of an algorithm as follows:

Repeat Step 1 and Step 2 for every iteration.

- 1. **Training the discriminator**
   - a. Two inputs, one from the real dataset (x) and another synthesized by the generator (x*) are given to the discriminator.
   - b. Discriminator networks try to classify them as real (1) or fake (0).
   - c. A loss function or classification error is calculated and backpropagated to update the trainable parameters of the discriminator in order to minimize the error.

### 2. Training the generator

- a. Using a random noise vector (z) as input, the generator network synthesizes a fake sample (x*).
- b. This generated fake sample (x*) is given to the discriminator for classification.
- c. The classification error is computed and backpropagated through the generator network to update the trainable parameters and to maximize the discriminator error (so that the discriminator classifies the fake sample as a real one).

The steps discussed previously are described in detail as follows:

### Step 1: Training the discriminator

According to the algorithm discussed earlier, the first step is to train the discriminator (D) network. Figure 8.3 helps us to visualize the training process by highlighting the order of steps in an orange box and numbering them. There are two inputs given to the discriminator:

- 1. A sample from the real dataset (x)
- 2. A fake sample from generator (x*)

![](img/7e519fee1b702b91799cdf1664598392_568_0.png)

Figure 8.3: Training of discriminator network on both real and generated samples.

The discriminator is a binary classifier that takes the inputs and tries to classify them as real (1) or fake (0) samples. Initially, the generator produces anything random as it is not trained yet, and so the discriminator learns the features from real data samples. During the training of the discriminator, the generator network’s training is set to false. The given inputs are passed through the neural network of the discriminator, and a prediction value of real (1) or fake (0) is produced as the output.

A loss function (classification error or discriminator error) is calculated and back-propagated to update the weights and the trainable parameters of the neural network to minimize the error and achieve better classification prediction. Any of the well deep learning neural network and backpropagation methods can be used that are appropriate for a specific type of problem.

### Step 2: Training the generator

Training the generator is the second step of the algorithm. Figure 8.4 shows the basic steps involved in the training process. The process starts with the input to the generator in the form of a random noise vector (z). It represents no meaning to it, as it is noise, and it acts as a starting seed for the generator to work on.

![](img/7e519fee1b702b91799cdf1664598392_569_0.png)

Figure 8.4: Training of generator network based on the feedback from the discriminator network using the backpropagation method.

The generator network transforms the input vector to a fake sample (x*) and passes this output further to the trained discriminator for predicting its plausibility. A loss function (generator loss) or classification error is calculated and backpropagated through the discriminator network to the generator network, and weights and parameters of the network are updated accordingly to minimize its loss or maximize the discriminator loss so that the fake sample is classified as a real one. This time, the training discriminator is set to false.

Thus, it is clear that generator training is tightly integrated with the discriminator. Indirectly, the discriminator is helping the generator network to learn better. It can be said that the better the discriminator, the better the generator comes out to be. After training, we have the trained generator that can generate to produce new plausible samples. The generator model is kept, which is the actual aim of the whole training process.

## When to stop the training?

We have previously discussed that for every iteration, the discriminator network and the generator network are trained simultaneously. The goal of the discriminator is to minimize its loss function (or to penalize the generator) by correctly identifying between the fake and real samples. On the other hand, the generator's aim is to minimize its loss function (or maximize the discriminator's loss) by generating a plausible sample that makes the discriminator classify it as a real sample.

The situation here is like when one network succeeds in its own goal, and the other one is penalized. These two networks are competing with each other to try to improve. So, now the question that arises is when to stop this process? This situation is similar to the concept of a zero-sum game in game theory of Game Theory. It is the situation in which the gain/loss of one participant balances out or cancels out the loss/gain of another participant in the game. Therefore, the total sum of zero is achieved. Now, there is a state for all zero-sum games called Nash-equilibrium, in which the player reaches a point where no one gains or losses by using any strategy. In GANs, this state is reached:

- *When the generator can generate plausible new samples indistinguishable from a real sample.
- *When the discriminator gets confused between fake and real samples with 50% probability.

At this stage, GAN is considered to be converged. But in actual practice, reaching this state is very difficult or, in other words, nearly impossible to achieve. It is considered as one of the research issues among others of GANs.
