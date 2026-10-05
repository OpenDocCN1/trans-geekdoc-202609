# APPENDIX: A RACE BETWEEN MEMORIZATION AND GENERALIZATION

![](bbox=[0.373, 0.085, 0.698, 0.196])

**Figure 66:** Frechet Inception Distance (FID) as a function of training step τ for a DDPM trained on 16,384 CIFAR-10 images. The FID initially decreases, reflecting improved generation quality and diversity, but begins to rise past τmem as the model starts copying training examples.

To quantify memorization, we follow the protocol of [Som+22] and compute a similarity score for each generated image based on the cosine similarity of SSCD (Self-Supervised Descriptor for Image Copy Detection) [Piz+22] features, extracted from ResNet-50 model. Each score is defined as the similarity between a generated image and its nearest neighbor in the training set.

Figure 64 plot the training and validation losses as a function of the training step τ. As observed in the main text, initially, both losses decrease, increasing generalization: the model output increases increasingly with the population size. At a critical time τmem, the validation loss diverges from the training loss, marking the onset of memorization. Early stopping at this point can prevent the model from entering the memorization phase.

In Figure 64, we report the similarity scores for 200 generated images at two checkpoints: early stopping (τ = 8,192) and the final training step (τ = 262,144). For reference, we also show the similarity score for real images from the full LAION-10 dataset (black dashed line). At the early stopping time, the generated images exhibit similarity to that of the dataset. In contrast, by the end of training, the similarity score increases by a factor of two, indicating memorization.

Finally, in Figure 65, we show representative examples of replicated samples (similarity score > 0.5) from the final checkpoint, confirming that Stable Diffusion memorized part of its training set.

# F.3 FURTHER RESULTS ON DDPMs

FID DYNAMICS Figure 66 reports the Frechet Inception Distance (FID) as a function of the training step τ for a DDPM trained on 16,384 CIFAR-10 images, consistent with the setup in Figure 22. At each checkpoint, we generate 32,768 samples and compute the FID against the union of CIFAR-10 standard train and test splits. The FID captures both the quality and diversity of the generated images. As training