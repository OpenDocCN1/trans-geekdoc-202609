# # 16 Deep neural networks

# ## 16.1 Introduction

The term “deep neural network” or **DNN**, in its modern usage, refers to any kind of differentiable function that can be expressed as a **computation graph**, where the nodes are primitive operations (like matrix multuplication), and edges represent numeric data in the form of vectors, matrices, or tensors. In its simplest form, this graph can be constructed as a linear series of nodes or “layers”. The term “deep” refers to models with many such layers.

In Section 16.2 we discuss some of the basic building blocks (node types) that are used in the field. In Section 16.3 we give examples of common architectures which are constructed from these building blocks. In Section 6.2 we show how we can efficiently compute the gradient of functions defined on such graphs. If the function computes the scalar loss of the model’s predictions given a training set, we can pass this gradient to an optimization routine, such as those discussed in Chapter 6, in order to fit the model. Fitting such models to data is called “**deep learning**”.

We can combine DNNs with probabilistic models in two different ways. The first is to use them to define nonlinear functions which are used inside conditional distributions. For example, we may construct a classifier using \(p(y|x,\theta) = \text{Cat}(y|\text{softmax}(f(x;\theta)))\), where \(f(x;\theta)\) is a neural network that maps inputs \(x\) and parameters \(\theta\) to output logits. Or we may construct a joint probability distribution over multiple variables using a directed graphical model (Chapter 4) where each CPD \(p(x_i|\text{pa}(x_i))\) is a DNN. This lets us construct expressive probability models.

The other way we can combine DNNs and probabilistic models is to use DNNs to approximate the posterior distribution, i.e., we learn a function \(f\) to compute \(q(z|f(\mathcal{D};\phi))\), where \(z\) are the hidden variables (latents and/or parameters), \(\mathcal{D}\) are the observed variables (data), \(f\) is an **inference network**, and \(\phi\) is its parameters; for details, see Section 10.1.5. Note that in this latter setting, the joint model \(p(z, \mathcal{D})\) may be a “traditional” model without any “neural” components. For example, it could be a complex simulator. Thus the DNN is just used for computational purposes, not statistical/modeling purposes.

More details on DNNs can be found in such books as [Zha+20a; Cho21; Gér19; GBC16; Raf22], as well as a multitude of online courses. For a more theoretical treatment, see e.g., [Ber+21; Cal20; Aro+21; RY21].

# ## 16.2 Building blocks of differentiable circuits

In this section we discuss some common building blocks used in constructing neural networks. We denote the input to a block as \(x\) and the output as \(y\).