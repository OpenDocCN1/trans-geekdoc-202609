
# Chapter 15 : Part 2
Deep Learning
Auto-Encoders (AE) : Regularization & Other types

## 3 Regularization techniques & Other types of Auto-Encoders

### 15.2.1 Sparse Auto-Encoders: Regularization technique 1

- A sparse AE is an autoencoder which looks like this diagram, where the hidden layer is greater than the Input Layer. But a regularization technique that introduces sparsity has been applied.
- A regularization technique basically means something that helps prevent over-fitting or stabilizes the algorithm.
- In this case, if it was just sending the values through the hidden layer, it would be over-fitting in a way.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_529_0.png)

Sparse AE is one of regularization techniques that prevent over-fitting.

- Basically Sparse auto-encoder introduces a constraint on the loss function, or a penalty of a loss function, which doesn't allow the auto-encoder to use all of its hidden layer every single time.
- So that the Auto-Encoder can only use a certain number of nodes from its hidden layer.
- For instance, in this image, Auto-Encoder can use two nodes in this case.
- When the values go through these disable-nodes, output will be very small.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_529_1.png)

In following two passes the disable nodes aren't participating in encoding.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_529_2.png)

- While training this whole hidden layer, you are extracting features from each one of these hidden-nodes, but at the same time, you're not using all of nodes.
- So the auto-encoder cannot cheat because even though it has more nodes in the hidden layer than in the input layer, but it is not able to use all of them at any given pass. And that's how the sparse auto-encoder works.
- In reality, it is still compressing the information but just every time is using different nodes.

### 15.2.2 Additional Reading

A very interesting tutorial here by Chris McCormick called Deep Learning tutorial Sparse Autoencoder. This is a MATLAB tutorial. It will walk you through how to do it in MATLAB.

- There are some introductory mathematics, not too complex, but some basic level formulas which allow you to gently introduced to the mathematics behind the sparse Auto-Encoders.

## Additional Reading:

Deep Learning Tutorial - Sparse Autoencoder

By Chris McCormick (2014)

Link:

http://mccormickml.com/2014/05/30/deep-learning-tutorial-sparse-autoencoder/

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_530_0.png)

- If you want to understand how the equations work, don't allow the auto-encoders to switch on all of its nodes at the same time, at any given point, at any given pass.

- The next one is called, Deep Learning Sparse Autoencoders by Eric Wilkinson. It's a very short blog post on the essence of sparse auto-encoders.

## Additional Reading:

Deep Learning: Sparse Autoencoders

By Eric Wilkinson (2014)

Link:

http://www.ericwilkinson.com/blog/2014/11/19/deep-learning-sparse-autoencoders

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_530_1.png)

- A very powerful, heavy artillery paper on Sparse Auto-Encoders. It's called, K-Sparse Auto-encoders by Alireza Makhzani, 2014. You might find this paper interesting if you want to learn more about sparse autoencoders.

- K-Sparse Auto-Encoders used all over the place and it's constantly mentioned.

## Additional Reading:

k-Sparse Autoencoders

By Alireza Makhzani et al. (2014)

Link:

https://arxiv.org/pdf/1312.5663.pdf

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_530_2.png)

### 15.2. Denoising Auto-Encoders: Regularization technique 2

Denoising Autoencoders is another regularization technique, quite a popular technique actually, which resolves the problem when we have more nodes in the hidden-layer than in the input-layer and the Auto-encoder simply copy input values to output-values without finding any meaningful features.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_531_0.png)

- We are here replacing the actual input-values with noised-input-values.
- Noised-input-values are the input-values where we randomly make some of the input-values equal to zero.
- Noised-input-values are modified version of our input values. So, let's say we have input values {X1, X2, X3, X4}. Now we're going to take these inputs randomly and turn some of them into zeros {X1, 0, X3, 0}.
- You can specify the number of zeros in the setup of your Auto-encoder, for instance, half of your inputs are turned into zeros every single time and it happens randomly. It is also important to note that this type of Auto-Encoder is a Stochastic Auto-Encoder.

- Once you put this data through your Auto-Encoder then in the end you compare the output not with noisy-input-values but with original input-values.
- And that prevents the Auto-encoder from simply copying inputs all the way because it's actually comparing the output with its original inputs that helps resolve the problem we are facing.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_531_1.png)

> Additional Reading: In terms of additional reading, there is a great paper by Pascal Vincent and others, 2008, it's called Extracting and Composing Robust With Denoising Autoencoders.

Additional Reading:

Extracting and Composing Robust Features With Denoising Autoencoders

By Pascal Vincent et al. (2008)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_531_2.png)

Link:

http://cs.toronto.edu/~laroche/publications/icml-2008-denoising-autoencoders.pdf

### 15.2 Contractive Auto-Encoders: Regularization technique 3

Contractive Auto-Encoders is another regularization technique like sparse Auto-Encoders and denoising Auto-Encoders, designed to resolve the same problem of over-complete hidden layer in Auto-Encoders.

- Without going into much detail, Contractive Auto-Encoders adds a penalty into the loss function during back propagation which doesn't allow the Auto-Encoders to simply copy these values.
- Additional Reading: A wonderful article by Salah Rifai. It's called "Contractive Auto-Encoders: Explicit Invariance During Feature Extraction". This article has a lot of authors and one of them is Yoshua Bengio, so it is an in-depth study into the topic.
- Based on this article they say they can even get better results than Denoising Auto-Encoders on some datasets.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_532_0.png)

## Additional Reading:

Contractive Auto-Encoders: Explicit Invariance During Feature Extraction

By Salah Rifai et al. (2011)

Link:

http://machinelearning.wust.edu/mlpapers/paper_files/ICML2011Rifai_455.pdf

### 15.2.5 Stacked Auto-Encoders (AE)

Here is a Stacked AE. A stacked AE is an AE with another hidden layer. We have two stages of encoding and one stage of decoding here. And what we get is a very powerful algorithm.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_532_1.png)

In fact it's been shown that sometimes AE can supersede the results achieved by DBN. Where DBN is an undirected NN and Stacked AE is a directed NN.

**Additional reading:** A great paper to look into this topic is by Pascal Vincent and others called *Stacked Denoising Autoencoders: Learning Useful Representations in a Deep Network with a Denoising Criterion*. It's quite a large paper.

It also has Yoshua Bengio one of the co-authors on this paper and it builds upon their 2008 paper which we have already referred to.

## Additional Reading:

**Stacked Denoising Autoencoders: Learning Useful Representations in a Deep Network with a Denoising Criterion**

By Pascal Vincent et al. (2010)

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_533_0.png)

Link:

http://www.jmlr.org/papers/volume11/vincent10a/vincent10a.pdf

### 15.2.6 Deep AE

## Stacked AE <> Deep AE

Note that *Stacked AE* are not the same thing as *Deep AE*.

- Right side image is a *Deep AE*. These are actually stacked *pre-trained*, layer by RBMs.
- *Deep AE* basically are RBMs that are stacked. They are pre-trained layer by layer. Then they are unrolled. Then they are fine-tuned with back propagation.
- Here you get directionality in your network and then you have back propagation. In essence a Deep AE comes from RBMs.

![](img/0aa092657a6eb1b9f2dd65bbb79055a3_533_1.png)

NOTE:

- *Stacked AE* are just *normal AE* that are stacked.
- A *AE* is *RBMs* stacked on top of each other, and then certain things are done with them to achieve an *AE mechanism*.

**Additional reading:** if you'd like to learn more **deep AE**, a great paper by Geoffrey Hinton and others called: *Reducing the Dimensionality of Data with Neural Networks*.
