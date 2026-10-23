The parameters of the model are optimized layer by layer during pre-training and then adjusted as single deep neural networks during fine-tuning. Deep learning, the breakthrough of AI, is a very simple algorithm.

# Deep learning algorithms

Now, let's look through the theory and implementation of deep learning algorithms. In this chapter, we will see DBN and SDA (and the related methods). These algorithms were both researched explosively, mainly between 2012 and 2013 when deep learning started to spread out rapidly and set the trend of deep learning on fire. Even though there are two methods, the basic flow is the same and consistent with pre-training and fine-tuning, as explained in the previous section. The difference between these two is which pre-training (that is, unsupervised training) algorithm is applied to them.

Therefore, if there could be difficult points in deep learning, it should be the theory and equation of the unsupervised training. However, you don't have to be afraid. All the theories and implementations will be explained one by one, so please read through the following sections carefully.

# Restricted Boltzmann machines

The method used in the layer-wise training of DBN, pre-training, is called Restricted Boltzmann Machines (RBM). To begin with, let's take a look at the RBM that forms the basis of DBN. As RBM stands for Restricted Boltzmann Machines, of course there's a method called Boltzmann Machines (BMs). Or rather, BMs are a more standard form and RBM is the special case of them. Both are one of the neural networks and both were proposed by Professor Hinton.

The implementation of RBM and DBNs can be done without understanding the detailed theory of BMs, but in order to understand these concepts, we'll briefly look at the idea BMs are based on. First of all, let's look at the following figure, which shows a graphical model of BMs: