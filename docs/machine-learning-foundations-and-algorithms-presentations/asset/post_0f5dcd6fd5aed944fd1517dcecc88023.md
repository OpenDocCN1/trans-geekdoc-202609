
# SDEdit

# Stroke Painting to Image

![](img/f01928df50903c99ce023dd3c527a33d_745_0.png)

Input

Output

# Stroke-based Editing

![](img/f01928df50903c99ce023dd3c527a33d_746_0.png)

# Prompt-to-Prompt

“A basket full of apples.”

![](img/f01928df50903c99ce023dd3c527a33d_747_0.png)
![](img/f01928df50903c99ce023dd3c527a33d_747_1.png)
![](img/f01928df50903c99ce023dd3c527a33d_747_2.png)
![](img/f01928df50903c99ce023dd3c527a33d_747_3.png)
![](img/f01928df50903c99ce023dd3c527a33d_747_4.png)
![](img/f01928df50903c99ce023dd3c527a33d_747_5.png)
![](img/f01928df50903c99ce023dd3c527a33d_747_6.png)
![](img/f01928df50903c99ce023dd3c527a33d_747_7.png)

Source image

- apples → cookies
- basket → bowl
- basket → box
- basket → nest
- apples → oranges
- apples → chocolates
- apples → kittens

# Prompt-to-Prompt

> "A photo of a butterfly on a flower."

![](img/f01928df50903c99ce023dd3c527a33d_748_0.png)

Source image

![](img/f01928df50903c99ce023dd3c527a33d_748_1.png)

- flower → bread
![](img/f01928df50903c99ce023dd3c527a33d_748_2.png)

- flower → mug
![](img/f01928df50903c99ce023dd3c527a33d_748_3.png)

- flower → computer
![](img/f01928df50903c99ce023dd3c527a33d_748_4.png)

- flower → mirror
![](img/f01928df50903c99ce023dd3c527a33d_748_5.png)

- butterfly → bird
![](img/f01928df50903c99ce023dd3c527a33d_748_6.png)

- butterfly → snail
![](img/f01928df50903c99ce023dd3c527a33d_748_7.png)

- butterfly → drone

# Prompt-to-Prompt

# (High Level) Idea: Features inside diffusion models encode very high level information such as: style, content, and structure

![](img/f01928df50903c99ce023dd3c527a33d_749_0.png)

Reuse (copy and paste) the features from the previous prompt

# Generative Adverserialial Networks (GANs) and Normalizing Flows

# Machine Learning SS2024

Prof. Gerhard Neumann

KIT, Institut für Anthropik und Robotik

Slides based on Priyank Jaini (University of Waterloo) and Abuzar Khan (CMU)

# What we have seen: VAE

![](img/f01928df50903c99ce023dd3c527a33d_751_0.png)

- The decoder of a VAE is a generator!
- Trained by maximizing the likelihood of the data
  - Likelihood maximization does not actually relate to whether the output actually looks like a face
  $$\theta^* = \arg\max_{\theta} \log P(X;\theta)$$
- Can we make the training criteria a little more direct?

# How do faces look like?

![](img/f01928df50903c99ce023dd3c527a33d_752_0.png)

What’s the easiest way to check if the produced output looks like a face or not?

- You could just eyeball 👀 the results and use your understanding of what faces look like to evaluate what is generated.
- Unfortunately, you are not a differentiable function 😊
- But what if we could, find a differentiable proxy for you and your non-differentiable-ness?

# Can we find a more relevant loss?

![](img/f01928df50903c99ce023dd3c527a33d_753_0.png)

# What are GANs?

![](img/f01928df50903c99ce023dd3c527a33d_754_0.png)

**Generative Models** which generate data similar to the training data. 
e.g. Variational Autoencoders (VAE)

Neural Networks

**Adversarial Training**
GANs are made up of two competing networks (adversaries) that are trying to beat each other. A "game" is being played between the two.

# What are GANs?

![](img/f01928df50903c99ce023dd3c527a33d_755_0.png)

# The Generator

![](img/f01928df50903c99ce023dd3c527a33d_756_0.png)

- The generator produces realistic looking $X = G(z)$ from a latent vector $Z$
- Generator input $Z$ can be sampled from a known prior, e.g. standard Gaussian
- Goal: generated distribution $P_G(X)$ matches the true distribution $P_X(X)$

# The Discriminator

![](img/f01928df50903c99ce023dd3c527a33d_757_0.png)

- Discriminator $D(X)$ is trained to tell the difference between real and generated (fake) data
- Specifically, data produced by the generator
- If a perfect discriminator is fooled, the generated data cannot be distinguished from real data

# Training a GAN

![](img/f01928df50903c99ce023dd3c527a33d_758_0.png)

- Both, the generator and discriminator must be trained

# Training the discriminator

![](img/f01928df50903c99ce023dd3c527a33d_759_0.png)

- The discriminator:
- The discriminator is provided examples of real and synthetic faces
- The discriminator is trained to minimize its classification loss
- Minimize error between actual and predicted labels
- Discriminator parameters are trained such that
  - $D(X) = 1$ for real faces
  - $D(X) = 0$ for synthetic faces (i.e $1 - D(X) = 1$)

**Bernoulli Log-Likelihood:** $LL = \sum_{x_i \in D_{real}} \log D(X_i) + \sum_{\hat{x}_i \in D_{fake}} \log(1 - D(\hat{X}_i))$

# Training the generator

![](img/f01928df50903c99ce023dd3c527a33d_760_0.png)

- Training the generator:
- The discriminator’s loss is backpropagated to the generator
- The generator is trained to maximize the discriminator loss
- It is trained to “fool” the discriminator
- Generator parameters are trained such that
  - $D(G(Z)) = 1$ (i.e. $1 - D(G(Z)) = 0$)

# Training the generator

![](img/f01928df50903c99ce023dd3c527a33d_761_0.png)

- Training the generator:
- The discriminator’s loss is backpropagated to the generator
- The generator is trained to *maximize* the discriminator loss
- It is trained to “fool” the discriminator
- Generator parameters are trained such that:
  - Minimize $\log(1 - D(G(Z))

# The GAN formulation

![](img/f01928df50903c99ce023dd3c527a33d_762_0.png)

- Discriminator:
  - For real data $X$, Maximize $\log(D(X))$
  - For synthetic data, Maximize $\log(1 - D(\hat{X}))$
- Generator:
  - Minimize $\log(1 - D(\hat{X}))$

# The GAN formulation

![](img/f01928df50903c99ce023dd3c527a33d_763_0.png)

- The original GAN formulation is the following min-max optimization:
$$\min_G \max_D E_X \log D(X) + E_Z \log(1 - D(G(Z)))$$
- Objective of $D$: $D(X) = 1$ and $D(G(Z)) = 0$
- Objective of $G$: $D(G(Z)) = 1$

# How to Train a GAN?

![](img/f01928df50903c99ce023dd3c527a33d_764_0.png)

Step 1: Train the Discriminator using the current Generator

Step 2: Train the Generator to beat the Discriminator

> **Optimize:** min max $E_X \log D(X) + E_Z \log(1 - D(G(Z)))$

The discriminator is not needed after convergence

# Analysing GANs

![](img/f01928df50903c99ce023dd3c527a33d_765_0.png)

- So how does this behave when each component is optimized...

# The perfect discriminator

Consider a binary classification problem

![](img/f01928df50903c99ce023dd3c527a33d_766_0.png)

- The a posteriori probability of the classes for any instance $x = X$ is:
$$P(y_i|X) = \frac{P(X,y_i)}{P(X,y_1) + P(X,y_2)}$$

# The perfect discriminator

Consider a binary classification problem

![](img/f01928df50903c99ce023dd3c527a33d_767_0.png)

- The a posteriori probability of the classes for any instance $x = X$ is:
$$P(y_i|X) = \frac{P(X,y_i)}{P(X,y_1) + P(X,y_2)}$$

# The optimal discriminator

![](img/f01928df50903c99ce023dd3c527a33d_768_0.png)

- The **optimal discriminator** would be a Bayesian classifier:
$D(X) = \frac{P_X(X)}{P_X(X) + P_G(X)}$
- Assuming uniform prior

# Updating the Generator

# Fooling the perfect discriminator

![](img/f01928df50903c99ce023dd3c527a33d_769_0.png)

- Relearn generator parameters so that the new distribution of generated data “fools” the discriminator
- By moving it into the region assigned to the other class by the (perfect) discriminator

# Iterated Learning

![](img/f01928df50903c99ce023dd3c527a33d_770_0.png)

- Discriminator learns perfect boundary

# # Iterated Learning

![](img/f01928df50903c99ce023dd3c527a33d_771_0.png)

- Discriminator learns perfect boundary
- Generator moves its distribution past the boundary “into” the real distribution
