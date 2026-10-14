# World Models

# Chapter Goals

In this chapter you will:

+   - Walk through the basics of reinforcement learning (RL).
+   - Understand how generative modeling can be used within a *world model* approach to RL.
+   - See how to train a variational autoencoder (VAE) to capture environment observations in a low-dimensional latent space.
+   - Walk through the training process of a mixture density network–recurrent neural network (MDN-RNN) that predicts the latent variable.
+   - Use the covariance matrix adaptation evolution strategy (CMA-ES) to train a controller that can take intelligent actions in the environment.
+   - Understand how the trained MDN-RNN can itself be used as an environment, allowing the agent to train the controller within its own hallucinated dreams, rather than the real environment.

This chapter introduces one of the most interesting applications of generative models in recent years, namely their use within so-called world models.

# Introduction

In March 2018, David Ha and Jürgen Schmidhuber published their “World Models” paper.¹ The paper showed how it is possible to train a model that can learn how to perform a particular task through experimentation within its own generated dream environment, rather than inside the real environment. It is an excellent example of