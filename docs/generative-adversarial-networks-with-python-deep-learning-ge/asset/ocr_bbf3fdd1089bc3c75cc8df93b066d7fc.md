# Chapter 16

# How to Develop a Wasserstein GAN (WGAN)

The Wasserstein Generative Adversarial Network, or Wasserstein GAN, is an extension to the generative adversarial network that both improves the stability when training the model and provides a loss function that correlates with the quality of generated images. The development of the WGAN has a dense mathematical motivation, although in practice requires only a few minor modifications to the established standard deep convolutional generative adversarial network, or DCGAN. In this tutorial, you will discover how to implement the Wasserstein generative adversarial network from scratch. After completing this tutorial, you will know:

+   - The differences between the standard DCGAN and the new Wasserstein GAN.
+   - How to implement the specific details of the Wasserstein GAN from scratch.
+   - How to develop a WGAN for image generation and interpret model behavior.

Let’s get started.

# 16.1 Tutorial Overview

This tutorial is divided into five parts; they are:

+   1. Wasserstein Generative Adversarial Network
+   2. How to Implement Wasserstein Loss
+   3. Wasserstein GAN Implementation Details
+   4. How to Train a Wasserstein GAN Model
+   5. How to Generate Images With WGAN