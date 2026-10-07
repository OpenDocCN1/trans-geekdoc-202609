# CONCLUSION | 91

need for end-to-end backpropagation. We found that our proposed method, GIM, outperforms its supervised end-to-end counterpart and enables training layers of a network in relative isolation. Future work can study the effectiveness of GIM in a true distributed setting; can we train a neural network efficiently using GIM by distributing the model over multiple computational nodes with little communication between the nodes?

Research Question 5: Can latent variable quantization enable more expressive approximate mean-field posterior distributions and yield improved confidence scores in DLVMs?

Finally, we explored the problem of calibrated uncertainty. We considered the hypothesis that variational inference infers from a too restrictive class of approximate posterior functions. Based on this, we proposed a novel mean-field approximate posterior based based on quantizing latent variables called SQUAD. We demonstrate that this posterior can be effectively trained in a DLVM setting, does not need batch norm, and yields quality that reduces risk.

Since this, the use of quantization as a way of modeling density over a continuous domain has taken off. Quantization such as the VQ-VAE (Oord et al., 2017b) has played a crucial role in the image generation tool DALLERamesh et al., 2021 and quantile regression in reinforcement learning Dabney et al., 2017b. This continues to be an interesting approach to approximate posterior modeling, and can be studied in a variety of variational inference settings.

The search for a proper Bayesian treatment of deep learning is ongoing. This area of research has fallen out of favor, as various studies to train deep learning models in a Bayesian manner reached negative conclusions (Wenzel et al., 2020). Only recently, Chen et al., 2024 demonstrate that with an adapted optimizer, achieving well-calibrated uncertainty from a large probabilistic neural networks is possible.

# CLOSING WORDS

Deep learning brings a tremendously exciting realm of possibilities for the field of medical image analysis and medicine in general. Capturing expertise in statistical models enables humanity to improve diagnostic quality. Moreover, with the spread of computation and internet to every corner of the