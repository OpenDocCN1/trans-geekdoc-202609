# IOP Publishing

# Quantum Machine Learning
Concepts and possibilities

Andrea Delgado and Kathleen E Hamilton

# Chapter 7

# Quantum generative models

Generative models play a foundational role in machine learning by enabling systems to learn and replicate the underlying structure of data distributions. Unlike discriminative models (discussed in chapter 6), which aim to distinguish between different classes or outputs, generative models are useful for unconditioned density estimation given a set of unlabeled data features. This capability allows them to synthesize new data samples, estimate probabilities, and support a wide range of applications, including image generation, data augmentation, anomaly detection, and unsupervised representation learning.

Quantum generative models (QGMs) extend these capabilities into the quantum domain, leveraging quantum correlations to learn and represent complex distributions that may be intractable for classical models. Unitary quantum dynamics implicitly represent probability amplitudes without the additional overhead associated with evaluation functions. Leveraging quantum dynamics and the expressivity of quantum systems may lead to richer families of distributions, or compact representations of data, or powerful candidates for sampling tasks that underlie generative modeling. The prospect of quantum advantage, demonstrating that quantum models can outperform classical ones in practical, real-world tasks, is a compelling motivation for studying QGMs. However, a stronger motivation is also found in the connection of quantum dynamics and probabilistic model structure.

In recent years, many QGM frameworks have been proposed, ranging from energy-based models such as quantum Boltzmann machines to circuit-based architectures such as quantum Born machines and quantum generative adversarial networks. This chapter explores the theory and practice of QGMs, paying special attention to the Boltzmann machine [1–3] which was one of the early adapted quantum models. We introduce several classes of quantum generative models, discuss their training methods, and examine the concept of expressivity, which is