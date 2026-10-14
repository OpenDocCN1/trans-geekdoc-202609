
The effect of mode collapse can be seen in Figure 4-10.

![](img/f0f0f5d89818fdddf117bbe758ac8143_138_0.png)

Figure 4-10. Example of mode collapse when the generator overpowers the discriminator

If you find that your generator is suffering from mode collapse, you can try strengthening the discriminator using the opposite suggestions to those listed in the previous section. Also, you can try reducing the learning rate of both networks and increasing the batch size.

## Uninformative loss

Since the deep learning model is compiled to minimize the loss function, it would be natural to think that the smaller the loss function of the generator, the better the quality of the images produced. However, since the generator is only graded against the current discriminator and the discriminator is constantly improving, we cannot compare the loss function evaluated at different points in the training process. Indeed, in Figure 4-6, the loss function of the generator actually increases over time, even though the quality of the images is clearly improving. This lack of correlation between the generator loss and image quality sometimes makes GAN training difficult to monitor.

## Hyperparameters

As we have seen, even with simple GANs, there are a large number of hyperparameters to tune. As well as the overall architecture of both the discriminator and the generator, there are the parameters that govern batch normalization, dropout, learning rate, activation layers, convolutional filters, kernel size, striding, batch size, and latent space size to consider. GANs are highly sensitive to very slight changes in all of these parameters, and finding a set of parameters that works is often a case of educated trial and error, rather than following an established set of guidelines.

This is why it is important to understand the inner workings of the GAN and know how to interpret the loss function—so that you can identify sensible adjustments to the hyperparameters that might improve the stability of the model.

## Tackling GAN challenges

In recent years, several key advancements have drastically improved the overall stability of GAN models and diminished the likelihood of some of the problems listed earlier, such as mode collapse.

In the remainder of this chapter we shall examine the Wasserstein GAN with Gradient Penalty (WGAN-GP), which makes several key adjustments to the GAN framework we have explored thus far to improve the stability and quality of the image generation process.

## Wasserstein GAN with Gradient Penalty (WGAN-GP)

In this section we will build a WGAN-GP to generate faces from the CelebA dataset that we utilized in Chapter 3.

![](img/f0f0f5d89818fdddf117bbe758ac8143_139_0.png)

## Running the Code for This Example

The code for this example can be found in the Jupyter notebook located at notebooks/04_gan/02_wgan_gp/wgan_gp.ipynb in the book repository.

The code has been adapted from the excellent WGAN-GP tutorial created by Aakash Kumar Nain, available on the Keras website.

The Wasserstein GAN (WGAN), introduced in a 2017 paper by Arjovsky et al.,4 was one of the first big steps toward stabilizing GAN training. With a few changes, the authors were able to show how to train GANs that have the following two properties (quoted from the paper):

- A meaningful loss metric that correlates with the generator’s convergence and sample quality
- Improved stability of the optimization process

Specifically, the paper introduces the Wasserstein loss function for both the discriminator and the generator. Using this loss function instead of binary cross-entropy results in a more stable convergence of the GAN.

In this section we’ll define the Wasserstein loss function and then see what other changes we need to make to the model architecture and training process to incorporate our new loss function.

You can find the full model class in the Jupyter notebook located at chapter05/wgan-gp/faces/train.ipynb in the book repository.

## Wasserstein Loss

Let’s first remind ourselves of the definition of binary cross-entropy loss—the function that we are currently using to train the discriminator and generator of the GAN (Equation 4-1).

Equation 4-1. Binary cross-entropy loss
$$-\frac{1}{n}\sum_{i=1}^{n}\left(y_i\log(p_i)+(1-y_i)\log(1-p_i)\right)$$

To train the GAN discriminator D, we calculate the loss when comparing predictions for real images p_i = D(x_i) to the response y_i = 1 and predictions for generated images p_i = D(G(z_i)) to the response y_i = 0. Therefore, for the GAN discriminator, minimizing the loss function can be written as shown in Equation 4-2.

Equation 4-2. GAN discriminator loss minimization
$$\min_D -\left(\mathbb{E}_{x\sim p_X}[\log D(x)] + \mathbb{E}_{z\sim p_Z}[\log(1-D(G(z)))]\right)$$

To train the GAN generator G, we calculate the loss when comparing predictions for generated images p_i = D(G(z_i)) to the response y_i = 1. Therefore, for the GAN generator, minimizing the loss function can be written as shown in Equation 4-3.

Equation 4-3. GAN generator loss minimization
$$\min_G -\left(\mathbb{E}_{z\sim p_Z}[\log D(G(z))]\right)$$

Now let’s compare this to the Wasserstein loss function.

First, the Wasserstein loss requires that we use y_i = 1 and y_i = -1 as labels, rather than 1 and 0. We also remove the sigmoid activation from the final layer of the discriminator, so that predictions p_i are no longer constrained to fall in the range [0, 1] but instead can now be any number in the range (-∞, ∞). For this reason, the discriminator in a WGAN is usually referred to as a critic that outputs a score rather than a probability.

The Wasserstein loss function is defined as follows:

$$-\frac{1}{n} \sum_{i=1}^{n} (y_i p_i)$$

To train the WGAN critic $D$, we calculate the loss when comparing predictions for real images $p_i = D(x_i)$ to the response $y_i = 1$ and predictions for generated images $p_i = D(G(z_i))$ to the response $y_i = -1$. Therefore, for the WGAN critic, minimizing the loss function can be written as follows:

$$\min_D -\left(\mathbb{E}_{x \sim p_X}[D(x)] - \mathbb{E}_{z \sim p_Z}[D(G(z))]\right)$$

In other words, the WGAN critic tries to maximize the difference between its predictions for real images and generated images.

To train the WGAN generator, we calculate the loss when comparing predictions for generated images $p_i = D(G(z_i))$ to the response $y_i = 1$. Therefore, for the WGAN generator, minimizing the loss function can be written as follows:

$$\min_G -\left(\mathbb{E}_{z \sim p_Z}[D(G(z))]\right)$$

In other words, the WGAN generator tries to produce images that are scored as highly as possible by the critic (i.e., the critic is fooled into thinking they are real).

## The Lipschitz Constraint

It may surprise you that we are now allowing the critic to output any number in the range $(-\infty, \infty)$, rather than applying a sigmoid function to restrict the output to the usual $[0, 1]$ range. The Wasserstein loss can therefore be very large, which is unsettling—usually, large numbers in neural networks are to be avoided!

In fact, the authors of the WGAN paper show that for the Wasserstein loss function to work, we also need to place an additional constraint on the critic. Specifically, it is required that the critic is a 1-Lipschitz continuous function. Let's pick this apart to understand what it means in more detail.

The critic is a function $D$ that converts an image into a prediction. We say that this function is 1-Lipschitz if it satisfies the following inequality for any two input images, $x_1$ and $x_2$:

$$\frac{|D(x_1) - D(x_2)|}{|x_1 - x_2|} \le 1$$

Here, |x₁ − x₂| is the average pixelwise absolute difference between two images and |D(x₁) − D(x₂)| is the absolute difference between the critic predictions. Essentially, we require a limit on the rate at which the predictions of the critic can change between two images (i.e., the absolute value of the gradient must be at most 1 everywhere). We can see this applied to a Lipschitz continuous 1D function in Figure 4-11 —at no point does the line enter the cone, wherever you place the cone on the line. In other words, there is a limit on the rate at which the line can rise or fall at any point.

![](img/f0f0f5d89818fdddf117bbe758ac8143_142_0.png)

Figure 4-11. A Lipschitz continuous function (source: Wikipedia)

![](img/f0f0f5d89818fdddf117bbe758ac8143_142_1.png)

For those who want to delve deeper into the mathematical rationale behind why the Wasserstein loss only works when this constraint is enforced, Jonathan Hui offers an excellent explanation.

## Enforcing the Lipschitz Constraint

In the original WGAN paper, the authors show how it is possible to enforce the Lipschitz constraint by clipping the weights of the critic to lie within a small range, [−0.01, 0.01], after each training batch.

One of the criticisms of this approach is that the capacity of the critic to learn is greatly diminished, since we are clipping its weights. In fact, even in the original WGAN paper the authors write, “Weight clipping is a clearly terrible way to enforce a Lipschitz constraint.” A strong critic is pivotal to the success of a WGAN, since without accurate gradients, the generator cannot learn how to adapt its weights to produce better samples.

Therefore, other researchers have looked for alternative ways to enforce the Lipschitz constraint and improve the capacity of the WGAN to learn complex features. One such method is the Wasserstein GAN with Gradient Penalty.

In the paper introducing this variant,5 the authors show how the Lipschitz constraint can be enforced directly by including a gradient penalty term in the loss function for
