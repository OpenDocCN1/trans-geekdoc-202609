![](bbox=[0.146, 0.103, 0.477, 0.295])

![](bbox=[0.516, 0.103, 0.854, 0.295])

![](bbox=[0.146, 0.305, 0.477, 0.495])

![](bbox=[0.516, 0.305, 0.854, 0.495])

Figure 7.15 Learning data set of semi-supervised models

Figure 7.15(a) shows some labeled data and supervised learning involves finding a boundary between different types of labeled data (Figure 7.15(b)). On the contrary, for the case of semi-supervised learning, there are both labeled and unlabeled data (Figure 7.15(c)). But the amount of unleveled data is quite high than the leveled data. Training is performed in such a way that the model could divide them into similar parts (Figure 7.15(d)). In this case, the division is done taking the consideration of leveled data with the availability of unlabeled data.

A popular semi-supervised learning algorithm is described below:

Generative Adversarial Networks: A common training method used in medical software diagnostic with a very small set of labeled data is Generative Adversarial Networks (GAN) which is a type of semi-supervised learning method. From Figure 7.16, it is seen that real samples contain real images that are mixed with some latent space which generates noise. This data is fed into the Generator that generates some fake samples with fake images. Both the real sample and the output of the generator are mixed and compared in Discriminator. The Discriminator passes all the images and fine-tunes and