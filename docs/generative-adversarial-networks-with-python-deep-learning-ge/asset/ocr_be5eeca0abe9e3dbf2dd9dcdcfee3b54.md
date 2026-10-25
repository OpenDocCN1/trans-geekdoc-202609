# 13.2 What Is the Frechet Inception Distance?

The Frechet Inception Distance, or FID for short, is a metric for evaluating the quality of generated images and specifically developed to evaluate the performance of generative adversarial networks. The FID score was proposed and used by Martin Heusel, et al. in their 2017 paper titled GANs Trained by a Two Time-Scale Update Rule Converge to a Local Nash Equilibrium. The score was proposed as an improvement over the existing Inception Score, or IS.

> For the evaluation of the performance of GANs at image generation, we introduce the “Frechet Inception Distance” (FID) which captures the similarity of generated images to real ones better than the Inception Score.
> 
> — GANs Trained by a Two Time-Scale Update Rule Converge to a Local Nash Equilibrium, 2017.

The inception score estimates the quality of a collection of synthetic images based on how well the top-performing image classification model Inception v3 classifies them as one of 1,000 known objects. The scores combine both the confidence of the conditional class predictions for each synthetic image (quality) and the integral of the marginal probability of the predicted classes (diversity). The inception score does not capture how synthetic images compare to real images. The goal in developing the FID score was to evaluate synthetic images based on the statistics of a collection of synthetic images compared to the statistics of a collection of real images from the target domain.

> Drawback of the Inception Score is that the statistics of real world samples are not used and compared to the statistics of synthetic samples.
> 
> — GANs Trained by a Two Time-Scale Update Rule Converge to a Local Nash Equilibrium, 2017.

Like the inception score, the FID score uses the inception v3 model. Specifically, the coding layer of the model (the last pooling layer prior to the output classification of images) is used to capture computer-vision-specific features of an input image. These activations are calculated for a collection of real and generated images. The activations are summarized as a multivariate Gaussian by calculating the mean and covariance of the images. These statistics are then calculated for the activations across the collection of real and generated images. The distance between these two distributions is then calculated using the Frechet distance, also called the Wasserstein-2 distance.

> The difference of two Gaussians (synthetic and real-world images) is measured by the Frechet distance also known as Wasserstein-2 distance.
> 
> — GANs Trained by a Two Time-Scale Update Rule Converge to a Local Nash Equilibrium, 2017.

The use of activations from the Inception v3 model to summarize each image gives the score its name of Frechet Inception Distance. A lower FID indicates better-quality images; conversely, a higher score indicates a lower-quality image and the relationship may be linear. The authors