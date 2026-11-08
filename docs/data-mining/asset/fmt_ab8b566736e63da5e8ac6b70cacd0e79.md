
Deep learning technologies have revolutionized the fields of artificial intelligence, machine learning, computer vision, and natural language processing, and the effects are beginning to impact our daily lives. In this chapter, we overview advanced and recent deep learning methodologies, including generative deep learning (`GANs`, `VAEs`, `diffusion models`), and models for natural language processing beginning with `word2vec` and building up to transformer language models. We also discuss other important deep learning topics including adversarial examples, knowledge distillation, and deep reinforcement learning.

## Key Words

Deep learning; `generative AI`; natural language processing; word embeddings; transformer language models; `BERT`; `GPT`; knowledge distillation; deep reinforcement learning

## Chapter Outline

*   11.1 **Generative AI via Deep Learning** [**434**](#Ch012_433-471_B9780443158889000121.xhtml#s0010)  

    *   [Generative Adversarial Networks](#Ch012_433-471_B9780443158889000121.xhtml#s0015) 434

    *   [Variational Auto-Encoders](#Ch012_433-471_B9780443158889000121.xhtml#s0020) 437

    *   [Diffusion Models](#Ch012_433-471_B9780443158889000121.xhtml#s0025) 438

*   11.2 **Introduction to Natural Language Processing and Large Language Models** [**440**](#Ch012_433-471_B9780443158889000121.xhtml#s0030)  

    *   [Word Embeddings](#Ch012_433-471_B9780443158889000121.xhtml#s0035) 442

    *   [Word2vec Models](#Ch012_433-471_B9780443158889000121.xhtml#s0040) 445

    *   [Training word2vec Models](#Ch012_433-471_B9780443158889000121.xhtml#s0045) 448

    *   [Document Classification With Deep Neural Networks](#Ch012_433-471_B9780443158889000121.xhtml#s0050) 449

    *   [Unsupervised and Self-Supervised Training of Large Language Models](#Ch012_433-471_B9780443158889000121.xhtml#s0055) 451

    *   [Attention](#Ch012_433-471_B9780443158889000121.xhtml#s0060) 452

*   11.3 **Transformer Architecture** [**453**](#Ch012_433-471_B9780443158889000121.xhtml#s0065)  

    *   [Scaled Dot-Product Attention](#Ch012_433-471_B9780443158889000121.xhtml#s0070) 453

    *   [Multihead Attention](#Ch012_433-471_B9780443158889000121.xhtml#s0075) 455

    *   [Transformer Blocks](#Ch012_433-471_B9780443158889000121.xhtml#s0080) 457

    *   [Positional Encoding](#Ch012_433-471_B9780443158889000121.xhtml#s0085) 458

*   11.4 **Transformer-Based Language Models** [**459**](#Ch012_433-471_B9780443158889000121.xhtml#s0090)  

    *   [Decoder-Only Architecture](#Ch012_433-471_B9780443158889000121.xhtml#s0095) 459

    *   [Generative Pretrained Transformers](#Ch012_433-471_B9780443158889000121.xhtml#s0100) 460

    *   [Bidirectional Encoder Representations from Transformers](#Ch012_433-471_B9780443158889000121.xhtml#s0105) 461

    *   [Transformer-Based Neural Machine Translation](#Ch012_433-471_B9780443158889000121.xhtml#s0110) 462

*   [11.5 **Adversarial Examples**](#Ch012_433-471_B9780443158889000121.xhtml#s0115) **463**

*   [11.6 **Knowledge Distillation**](#Ch012_433-471_B9780443158889000121.xhtml#s0120) **464**

*   [11.7 **Deep Reinforcement Learning**](#Ch012_433-471_B9780443158889000121.xhtml#s0125) **465**

*   [11.8 **Further Reading and Bibliographic Notes**](#Ch012_433-471_B9780443158889000121.xhtml#s0130) **467**

*   [11.9 **Exercises**](#Ch012_433-471_B9780443158889000121.xhtml#s0135) **469**

In the machine learning (`ML`) community in the early 2000s, there was a running joke that “neural networks are the second-best solution to every problem.” This is no longer the case, as presently these methods, rebranded as “deep learning,” are now the best method for most ML tasks and problem domains. Moreover, deep learning methods have pushed back the boundary of what is understood to be possible for machines to do, particularly in their ability to *create* new things, a capability that was previously only associated with humans.

In this chapter, we continue our discussion of deep learning, diving into more recent and advanced techniques. We begin by discussing deep learning methods for generative AI, particularly those that can generate high-quality and compelling “AI art” works, as well as realistic images, video, audio, and more. We then shift our focus to deep learning methods for natural language processing (`NLP`), beginning with word embedding models and building toward modern transformer-based language models. Finally, we discuss other important advanced topics including adversarial examples, knowledge distillation, and deep reinforcement learning.

## 11.1 Generative AI via Deep Learning

Models that can generate artificial data are called, quite naturally, `generative models`. This term is in direct contrast to models that do not generate, but only predict, normally in a supervised fashion, which are called `discriminative models`. While there is currently a lot of excitement around generative models that are based on deep neural networks, probabilistic models can be generative too (topic models, for example. See [Chapter 14](#Ch015_516-570_B9780443158889000157.xhtml#Ch015_516-570_B9780443158889000157), “Advanced probabilistic methods”). Here, we focus on the neural network kind of generative model. These models have impressed with their ability to generate realistic synthetic images, audio, video, text, and more. Having reached the public consciousness, the field has adopted the public’s preferred nomenclature, and these generative ML models are now called `generative AI`. The term nevertheless seems apt, since these methods now seem to *artificially* imitate creativity, a property we normally associate with *intelligence*.

### Generative Adversarial Networks

As we will discuss further in [Chapter 15](#Ch016_571-615_B9780443158889000169.xhtml#Ch016_571-615_B9780443158889000169), “Moving on: applications and their consequences,” deep neural networks can now be used to generate beautiful artworks. They are already winning art contests, and generally causing artists to worry that they might be out of a job soon. They can even make many unique images that we might dream up—limited only by our imaginations—such as a chair in the shape of an avocado or a flying elephant; the sky is the limit. It really feels like we are living in the future sometimes.

`Generative Adversarial Networks` (`GANs`) are a classic and influential way to accomplish this. `GANs` are “adversarial” in that they are trained by playing a competitive game with themselves. Although they are no longer the only game in town when it comes to generative AI (pun intended), `GANs` remain a fundamental and influential approach. It is important to note that even though `GANs` are commonly associated with image data, there is nothing in their architecture that prevents them from being applied to other kinds of data. For example, `GANs` can be used to generate audio data including speech and music, as well as video and three-dimensional shapes, and even to propose candidate drug molecules.

`GANs` consist of two neural networks that compete with each other: the `generator` network and the `discriminator` network. The generator network tries to create realistic data that are similar to those in the training data. The discriminator network is a classifier that tries to distinguish between the real and generated data. Although the discriminator is not directly involved in the generation process, it provides the “signal” that is used to train the generator, by teaching it to produce artificial data that is indistinguishable from the real data.
