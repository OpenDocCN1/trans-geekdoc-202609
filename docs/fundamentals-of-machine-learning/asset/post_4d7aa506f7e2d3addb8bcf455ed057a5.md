
# Models with symmetric lateral connections

![](img/2087e3fd78fc2bbc9ee0bfaab66e3bde_203_0.png)

**Fig. 9.12** Restricted Boltzmann machine in recurrences within each layer are removed.

awake state, whereas the freely running state could be associated with a sleep phase. Unfortunately, it turns out that this learning rule is too demanding in practice. The reason for this is that the averages, indicated by the angular brackets in Eqn 9.32, have to be evaluated at thermal equilibrium. Thus, after applying each sensory state, the system has to run for a long time to minimize the initial transient response of the system. The same has to be done for a long time for the freely running phase. When the system reaches equilibrium, it has to be sampled for a long time to allow sufficient accuracy of the averages so that the difference of the two is meaningful. Further, the applicability of the gradient method can be questioned since such methods are problematic in recurrent systems without hidden states since small changes of system parameters (weights) can trigger large changes in the dynamics of the dynamical systems. These problems prevented, until recently, more practical progress in this area. Hinton and colleagues developed more practical systems which are described next.

## 9.4.4 The restricted Boltzmann machine and contrastive Hebbian learning

Training of the Boltzmann machine with the above rule is challenging because the states of the nodes are always changing. Even with the visible states clamped, the states of the hidden nodes are continuously changing for two reasons. First, the update rule is probabilistic, which means that even with constant activity of the visible nodes, hidden nodes receive variable input. Second, the recurrent connections between hidden nodes can change the states of the hidden nodes rapidly and generate rich dynamics in the system. We can certainly keep the probabilistic update rule until we need to generate different responses of the system in response to sensory data. However, we can simplify the system by eliminating recurrent connections within each layer, although connections between the layers are bi-directional. While the simplification of omitting recurrent connections is potentially severe, any of the abilities of general recurrent networks with hidden nodes can be recovered through the use of many layers, which bring back recurrences. A restricted Boltzmann machine (RBM) is shown in Fig. 9.12.

When applying the learning rule of Eqn 9.32 to one layer of an RBM, we can expect faster convergence of the rule due to the restricted dynamics in the hidden layer. We can also write the learning rule in a slightly different format by the following procedure. A sensory input is applied to the input layer, which triggers some recognition in the hidden layer. The states of the visible and hidden nodes can then be used to update the expectation value of the correlation between these nodes $\langle s_i^v s_j^h \rangle^0$, at the initial time step. The pattern in the hidden layer can then reconstruct approximately the pattern of visible nodes. This alternating Gibbs sampling is illustrated in Fig. 9.13 for a connection between one visible node and one hidden node, although this can be done in parallel for all connections. The learning rule can be written in the form,

$$\Delta_{ij} \propto (s_i^v s_j^h)^t - (s_i^v s_j^h)^{\infty}$$

![](img/2087e3fd78fc2bbc9ee0bfaab66e3bde_204_0.png)

**Fig. 9.13** Alternating Gibbs sampling.

Alternating Gibbs sampling becomes equivalent to the Boltzmann machine learning rule (Eqn 9.32) when repeating this procedure for an infinite number of time steps, at which point it produces. However, this procedure still requires averaging over long sequences of simulated activities, and sufficient evaluations of thermal averages still take long time. Also, the learning rule of Eqn 9.33 does not seem to correspond to biological learning. While developmental learning takes some time, it does not seem reasonable that the brain produces long sequences of responses to stimuli. Instead, it seems reasonable to allow some finite number of alternations, which is an important step in solving the learning problem for practical problems, which is a form of contrastive divergence introduced by Geoffrey Hinton. In each step we create only a rough approximation of ideal averages, the system learns from many examples, and it continuously improves its expectations. The Boltzmann machine with visible and hidden layer can easily decomposed into hierarchical networks by using the layer as the next. Hinton and colleagues have demonstrated the power of restricted Boltzmann machines for a number of examples. For example, they applied RBMs as autoencoders where restricted Gibbs sampling was used as pre-training to find appropriate internal representations that could be fine-tuned with backpropagation techniques to yield results surpassing support vector machines. This work was mentioned in Chapter 4 and shown in Fig. 9.7. A stacked RBM was therefore used as unsupervised

## Example of basic RMB on MNIST data

While the principles behind RBMs are advanced, their implementation is straightforward. We can illustrate the principle with a simplified layer model and training on some examples from the MNIST dataset. For this we load the MNIST dataset from Keras although we do not need Keras for the network in this program. We choose selected examples for each number from the training set.

### Listing 9.11 RMB.ipynb (part 1)

```python
import numpy as np
import matplotlib.pyplot as plt
from keras.datasets import mnist
data=10; nhiddn=100; visible=28+28; epochs=200; e=0.01; noise=.05; ngbs=5; T=1/4
w=0.1*np.random.randn(visible,nhiddn)
bias=np.zeros(visible); hbias=np.zeros(hidden)

(x_train, y_train, x_test, y_test) = mnist.load_data()
x_train=x_train.reshape(60000,28*25)
x_train=np.array([x_train[3::],x_train[8::],x_train[5::],x_train[7::],x_train[9::],x_train[0::],x_train[32::],x_train[15::],x_train[17::],x_train[22::]] )
```

![](img/2087e3fd78fc2bbc9ee0bfaab66e3bde_205_0.png)

**Fig. 9.14** Reconstruction error during training of MNIST examples.

We train the network by applying a pattern, calculating the hidden activation that represents the probability, sampling the activation of the hidden state with this probability, using this activation to calculate the reconstruction activity for the input nodes, and then using the corresponding terms to modify the weight values.

### Listing 9.12 RBM.ipynb (part 2)

```python
sig = lambda x: 1 / (1 + np.exp(-x)) #sigmoid activation function

err = np.zeros(epochs)
for epoch in range(epochs): #train RBM
    for v in x.train:
        h = sig(v @ w + bias)
        #sample hidden state
        nhidden = h > np.random.random(hidden)
        vrecon = sig(w @ nhidden + bias)
        hrecon = sig(vrecon @ w + bias)
        #update parameters
        w += e*(np.outer(v,h) - np.outer(vrecon,hrecon))
        bias += e*(v-vrecon)
    err[epoch] = e*((v-vrecon)**2).sum()
```

```python
plt.figure()
plt.plot(err, '.'); plt.xlabel('epoch'); plt.ylabel('error')
```

![](img/2087e3fd78fc2bbc9ee0bfaab66e3bde_206_0.png)
