
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_433_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_433_1.png)

Figure 13.9: A decomposition of R² into a finite set of linear decision regions produced by an MLP with ReLU activations with (a) one hidden layer of 25 hidden units and (b) two hidden layers. From Figure 1 of [HAB19]. Used with kind permission of Maksym Andriuschenko.

However, various arguments, both experimental and theoretical (e.g., [Has87; Mon+14; Rag+17; Pog+17]), have shown that deep networks work better than shallow ones. The reason is that later layers can leverage the features that are learned by earlier layers; that is, the function is defined in a compositional or hierarchical way. For example, suppose we want to classify DNA strings, and the positive class is associated with the regular expression *AA??CGCG??AA*. Although we could fit this with a single hidden layer model, intuitively it will be easier to learn if the model first learns to detect the AA and CG “motifs” using the hidden units in layer 1, and then uses these features to define a simple linear classifier in layer 2, analogously to how we solved the XOR problem in Sec. 13.2.1.

### 13.2.5.1 The “deep learning revolution”

Although the ideas behind DNNs date back several decades, it was not until the 2010s that they started to become very widely used. A breakthrough moment occurred in 2012, when [KSH12] showed that deep CNNs could significantly improve performance on the challenging ImageNet image classification benchmark, reducing the error rate from 26% to 16% in a single year (see Fig. 14.14b); this was a huge jump compared to the previous rate of progress of about 2% reduction per year. Around the same time, [DHK13] showed that deep neural networks could significantly outperform the previous state of the art on various speech recognition tasks.

The “explosion” in the usage of DNNs has several contributing factors. One is the availability of cheap GPUs (graphics processing units); these were originally developed to speed up image rendering for video games, but they can also massively reduce the time it takes to fit large CNNs, which involve similar kinds of matrix-vector computations. Another is the growth in large labeled datasets, which enables us to fit complex function approximators with many parameters without overfitting. (For example, ImageNet has 1.3M labeled images, and is used to fit models that have millions of parameters.) Indeed, if deep learning systems are viewed as “rockets”, then large datasets have been called the fuel.¹

1. This popular analogy is due to Andrew Ng, who mentioned it in a keynote talk at the GPU Technology Conference (GTC) in 2015. His slides are available at https://bit.ly/38RTxzH.

## Chapter 13. Neural networks for unstructured data

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_434_0.png)

Motivated by the outstanding empirical success of DNNs, various companies started to become interested in this technology. This has led to the development of high quality open-source software libraries, such as Tensorflow (made by Google), PyTorch (made by Facebook), and MXNet (made by Amazon). These libraries support automatic differentiation (see Sec. 13.3) and scalable gradient-based optimization (see Sec. 5.4) of complex differentiable functions. We will use some of these libraries in various places throughout the book to implement a variety of models, not just DNNs.

More details on the history of the “deep learning revolution” can be found in e.g., [Sej18].

> Note, however, that some have argued (see e.g., [B19]) that current libraries are too inflexible, and put too much emphasis on methods based on dense matrix-vector multiplication, as opposed to more general algorithmic primitives.

In this section, we discuss the connections between the kinds of neural networks we have discussed above, known as artificial neural networks or ANNs, and real neural networks. The details on how real biological brains work are quite complex (see e.g., [Kan+12]), but we can give a simple “cartoon”.

We start by considering a model of a single neuron. To a first approximation, we can say that whether neuron k fires, denoted by h_k ∈ {0,1}, depends on the activity of its inputs, denoted by x ∈ R^D, as well as the strength of the incoming connections, which we denote by w_k ∈ R^D. We can compute a weighted sum of the inputs using a_k = w_k^T x. These weights can be viewed as “wires” connecting the inputs x_d to neuron h_k; these are analogous to dendrites in a real neuron (see Fig. 13.10). This weighted sum is then compared to a threshold, b_k, and if the activation exceeds the threshold, the neuron fires; this is analogous to the neuron emitting an electrical output or action potential. Thus we can model the behavior of the neuron using $h_k(\mathbf{x}) = H(\mathbf{w}_k^\top \mathbf{x} - b_k)$, where $H(a) = \mathbb{I}(a > 0)$ is the Heaviside function. This is called the McCulloch-Pitts model of a neuron, and was proposed in 1943 [MP43].

We can combine multiple such neurons together to make an ANN. The result has sometimes been viewed as a model of the brain. However, ANNs differ from biological brains in many ways, including the following:

- Most ANNs use backpropagation to modify the strength of their connections (see Sec. 13.3). However, real brains do not use backprop, since there is no way to send information backwards along an axon [Ben+15b; BS16; KH19]. Instead, they use local update rules for adjusting synaptic strengths.
- Most ANNs are strictly feedforward, but real brains have many feedback connections. It is believed that this feedback acts like a prior, which can be combined with bottom up likelihoods from the sensory system to compute a posterior over hidden states of the world, which can then be used for optimal decision making (see e.g., [Doy+07]).
- Most ANNs use simplified neurons consisting of a weighted sum passed through a nonlinearity, but real biological neurons have complex dendritic tree structure (see Fig. 13.10), with complex spatio-temporal dynamics.
- Most ANNs are smaller in size and number of connections than biological brains (see Fig. 13.11). Of course, ANNs are getting larger every week, fueled by various new hardware accelerators, such as GPUs and TPUs (tensor processing units), etc. However, even if ANNs match biological brains in terms of number of units, the comparison is misleading since the processing capability of a biological neuron is much higher than an artificial neuron (see point above).
- Most ANNs are designed to model a single function, such as mapping an image to a label, or a sequence of words to another sequence of words. By contrast, biological brains are very complex

systems, composed of multiple specialized interacting modules, which implement different kinds of functions or behaviors such as perception, control, memory, language, etc (see e.g., [Sha88; Kan+12]).

Of course, there are efforts to make realistic models of biological brains (e.g., the **Blue Brain Project** [Mar06; Yon19]). However, an interesting question is whether studying the brain at this level of detail is useful for “solving AI”. It is commonly believed that the low level details of biological brains do not matter if our goal is to build “intelligent machines”, just as aeroplanes do not flap their wings. However, presumably “AIs” will follow similar “laws of intelligence” to intelligent biological agents, just as planes and birds follow the same laws of aerodynamics.

Unfortunately, we do not yet know what the “laws of intelligence” are, or indeed if there even are such laws. In this book we make the assumption that any intelligent agent should follow the basic principles of information processing and Bayesian decision theory, which is known to be the optimal way to make decisions under uncertainty (see Sec. 8.4.2).

Of course, biological agents are subject to many constraints (e.g., computational, ecological) which often require algorithmic “shortcuts” to the optimal solution; this can explain many of the **heuristics** that people use in everyday reasoning [KST82; GTA00; Gri20]. As the tasks we want our machines to solve become harder, we may be able to gain insights from other areas of neuroscience and cognitive science (see e.g., [MVWK16; Has+17; Zak+17]).

## 13.3 Backpropagation

In this section, we describe the famous **backpropagation algorithm**, which can be used to compute the gradient of a loss function applied to the output of the network wrt the parameters in each layer. This gradient can then be passed to a gradient-based optimization algorithm, as we discuss in Sec. 13.4.

The backpropagation algorithm was originally discovered in [BH69], and independently in [Wer74]. However, it was [RHW86] that brought the algorithm to the attention of the “mainstream” ML community.

We initially assume the computation graph is a simple linear chain of stacked layers, as in an MLP. In this case, backprop is equivalent to repeated applications of the chain rule of calculus (see Eq. (B.42)). However, the method can be generalized to arbitrary directed acyclic graphs (DAGs), as we discuss in Sec. 13.3.3. This general procedure is often called **automatic differentiation** or **autodiff**.

### 13.3.1 Feedforward networks

Consider the following objective function, corresponding to ℓ₂ loss for a 1-layer MLP:

$$\mathcal{L}((\mathbf{x},\mathbf{y}),\theta)=\frac{1}{2}\left\|\mathbf{y}-\mathbf{W}_2\varphi(\mathbf{W}_1\mathbf{x})\right\|_2^2 \tag{13.27}$$

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_435_0.png)

Figure 13.11: Plot of neural network sizes over time. Models 1, 2, 3 and 4 correspond to the perceptron [Ros58], the adaptive linear unit [WH60] the neocognitron [Fuk80], and the first MLP trained by backprop [RHW86]. From Figure 1.11 of [GBC16]. Used with kind permission of Ian Goodfellow.
