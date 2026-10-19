# ABSTRACT

Generative Adversarial Networks are a class of artificial intelligence algorithms used in unsupervised learning. They are implemented by a system of two neural networks competing with each other in a zero-sum game framework. The Generative Adversarial Networks (GAN) is based on the Minimax game theory. The idea behind the GAN is to train the discriminator network to determine if the given input image is real (from actual dataset) or fake (from the generator network). On the other hand, the generator tries to generate images that are indistinguishable from the real images. This might be used to improve existing discriminators, generate new samples of datasets, etc.

# ## 1. INTRODUCTION

The generative model is a growing field of machine learning which involves generation of new data samples from the same distribution as the training set. The Generative Adversarial Network is one of the most popular approaches used for this purpose. The GAN consists of two models: a generative model and a discriminative model, where the generative model is trained to generate new data, and the discriminative model is trained to distinguish between the real data and the generated data.

![](bbox=[0.25, 0.48, 0.75, 0.68])

# ### 1.1 Contributions

+   - Introduce a new framework for generating data using adversarial process.
+   - Present both theoretical and empirical results showing the potential of the framework.

The rest of the paper is organized as follows. Section 2 discusses related work, Section 3 presents the proposed model, Section 4 describes the experiments, and Section 5 concludes the paper.