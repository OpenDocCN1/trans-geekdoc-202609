

- **Mode collapse**: In mode collapse, after the training process is over, the generator is unable to generate samples of some class (modes) or generates only samples belonging to a small subset (partial collapse) or, in worst cases, generates a single sample (complete collapse).
- **Over-generalization**: This problem occurs when the GAN over-learns things from the real dataset that it should not or that does not exist, like a dog with four heads or more than two eyes.
- **Diminished gradient**: The discriminator gets so successful that it does not provide enough information for the generator to learn or make progress. Thus, the generator training can fail due to diminishing gradients.
- **Evaluating generative models**: This is also one of the major concerns: how to measure the fidelity of the samples synthesized by GANs and how to compare the two GANs trained on the same problem but with different models.
- **Highly sensitive to the hyperparameter and evaluation metrics**: GANs are also highly sensitive to the selections of hyperparameter and evaluation matrices in the networks of GANs. So, choosing the right parameters is a time-consuming and tedious process.

## The GAN loss function

Training a GAN can be a challenging task; it requires time and effort in deciding the parameters, suitable optimizers, loss function, and so on for better training. The training of the GAN progresses in iterations, and so to estimate the current state of our model, we need some kind of function (error function) that can represent the current state to make some improvements in the next iteration or state of the model. This role is played by the loss function; it can measure the error or loss of the model, which can be used to update the weights of the model and minimize the loss in further iterations. But deciding GAN's loss function is one of the challenging issues in the training of GAN. In GANs, there are two neural networks, that is, the discriminator and the generator, trying to win over the other in a two-players game-like situation. So, the first thing to understand is that one’s gain is another’s loss. Therefore, in simple terms, we can write:

Generator’s Loss = - (Discriminator’s Loss)

## The standard loss function [min-max loss]

In a paper by Ian Goodfellow, he described the standard GAN's loss function, that is, the min-max loss function represented as follows:

$$ \min \max V(D, G) = \min \max (E_{x \sim p_{data}(x)}[\log D(x)] + E_{z \sim p_z(z)}[1 - \log D(G(z))]) \quad (8.1) $$

The discriminator is a binary classifier, and the generator network also depends upon the feedback of the discriminator. Thus, to understand this loss function, we start with the binary-cross entropy loss (loss function for binary classification problems) as follows:

$$ \text{Loss}(\hat{p}, a) = [a \cdot \log(\hat{p}) + (1 - a) \cdot \log(1 - \hat{p})] \quad (8.2) $$

Where $a$ = actual value, and $\hat{p}$ = predicted value

The discriminator is trained on both real datasets and generated samples, mapping from image to probability, and so it runs twice before it calculates its loss function. On the other hand, the generator network runs only once, mapping from the latent space to generated image sample, and computes its loss function based on the feedback from the discriminator. They take turns in computing their losses and updating, then updating their weights to reduce the loss (error).

### At Discriminator:

| log(D(x)) → | Range [0,1] | Aim is to maximize | Higher value represents the discriminator classified sample as real. |
|---|---|---|---|
| log(D(G(z))) → or log[1-D(G(z))] → | Range [0,1] | Aim is to minimize or maximize | Lower value represents that discriminator correctly identified the fake generated sample. |

### At Generator:

| log[1-D(G(z))] → | Range [0,1] | Aim is to minimize | Lower value represents that discriminator identified the fake generated sample as real. |

$D(z)$ = discriminator's function mapping from the image to the probability value.

$G(z)$ = Generator's function mapping from random vector space to generated sample.

The min-max loss function specifies minimizing the generator loss and maximizing the discriminator's loss. Figure 8.7 shows the output of the discriminator, so let us try to understand the meaning of those outputs first.

## The discriminator loss

During the training of the discriminator, it is trained on both the real and fake generated samples, with a label as $a = 1$ (real) and $a = 0$ (fake), respectively. While training on a real dataset, we have $a = 1$ (actual value) and $\hat{p} = D(x)$ (predicted value), the output of the discriminator. Substituting these values in equation (8.2), we get the following:

$\text{Loss real}(D(x), 1) = [\log(D(x))]$

And while training on generated samples, values are $a=0$ (actual value) and $\hat{p} = D(G(z))$ (predicted value). Substitute these values in equation (8.2), and we get the following:

$\text{Loss fake}(D(G(z)), 0) = [\log(1 - D(G(z)))]$

The total loss at discriminator is the combined loss, that is:

$D \text{ Loss} = \text{Loss real} + \text{Loss fake}$

So, combining equations (8.3) and (8.4), we get the following:

$D \text{ Loss} = [\log(D(x)) + \log(1 - D(G(z)))]$

## The generator loss

Similarly, for the generator, the label for an actual value is zero and $\hat{p} = D(G(z))$. Substituting these values into equation (8.2), we get the following:

## Combined loss

Both the loss equations of the discriminator and generator are combined to formulate a general equation, to maximize the discriminator loss and minimize the generator loss:

$\text{Loss} = D.\text{Loss} + G.\text{Loss}$

$\text{Loss} = \min\max[\log D(x) + \log(1 - D(G(z)))]$

$G \to D$

Or

$\text{Minmax } V(G, D) = \min\max[\log D(x) + \log(1 - D(G(z)))]$

$G \to D$

Note that the generator loss is independent of the term $\log(D(x))$; it is mentioned just to make a general expression. The preceding expression is valid for one sample only. Expectation ($E$) is taken over the preceding equation considering the loss over the entire dataset, and therefore, the final min-max loss function is as follows:

$$ \min\max V(D, G) = \min\max(E_{x \sim p_{data}(x)}[\log D(x)] + E_{z \sim p_z(z)}[1 - \log D(G(z))]) \quad (8.9) $$

## Non-saturating loss (NS-loss)

The NS-loss function is the solution to the generator’s saturation issue faced in the case of the min-max loss function. It results from a small modification in the generator’s loss function. Instead of minimizing $[\log(1 - D(G(z)))]$ for generator, NS-loss function maximizes $[\log(D(G(z)))]$. So, it is only the perspective change, which means the generator’s focus is on maximizing the probability of generated samples being recognized as real instead of focusing on minimizing the probability of the image being recognized as fake. This small change results in better and more stable training with stronger gradient information passed backward to update the generator’s weight and better training.

At generator:

| log[D(G(z))] → | Range [0,1] | Aim is to maximize | Higher value represents that discriminator identified the fake generated sample as real. |
|---|---|---|---|

$D(z) = \text{discriminator's function mapping from the image to the probability value.}$

$G(z) = \text{Generator's function mapping from random vector space to generated sample.}$

## Wasserstein GAN loss

This is one of the most popular loss functions used in various successful GAN models. It uses Earth-Mover’s distance (or Wasserstein-1 distance) for measuring the gap between the real and generated probability distributions. This loss function is considered as $meaningful\ loss$ because the discriminator network acts as a $critic$ here, and instead of giving just binary probabilities as output, it provides the appropriate $distance\ score$. This score represents the distance between two probability distributions and helps to further minimize this distance by moving one probability distribution towards another. This is our main goal in GAN, that is, transforming latent space with normal probability distribution to the real dataset probability distribution. This loss function showed tremendous results in the training of GAN models. It

