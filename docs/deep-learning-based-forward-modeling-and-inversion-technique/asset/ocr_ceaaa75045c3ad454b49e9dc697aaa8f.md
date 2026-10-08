# # 5 Advanced Deep Learning Techniques in Computational Physics

Computational physics is a new discipline that uses computers and computer science as tools and approaches, applies appropriate mathematical methods, conducts numerical analysis of physical problems, and performs numerical simulation of practical processes. Traditional physics methods include finite difference method [1, 2, 3], finite element method [4, 5, 6], variational dynamics method [9, 10], Monte Carlo simulation method [11]. In recent years, with the continuous development of deep learning technology, new methods combining computational physics with various neural networks emerged in. In this chapter, the applications of various emerging deep learning technologies in computational physics in recent years are reviewed firstly, and then it will focus on the specific implementation of special methods.

# ## 5.1 Informed Neural Network

# ### 5.1.1 Fully Connected-Based PINN

The physics informed neural network is by fully connected neural networks (FCNN) as universal function approximators [13]. The core idea of the fully connected PINN is the automatic differentiation technique [14], which is utilized to differentiate the FCNN with respect to the input coordinates or parameters. An exquisitely devised loss function is employed to constrain the field quantities to respect the corresponding physical laws in the form of partial differential equations. In fact, the FCNN based PINN is able to tackle multidimensional physical problems in computational science.

First of all, it is requisite to establish a DL framework to simulate the operator equation $\mathcal{L}[u] = f$. A prototyped structure includes an input layer, several hidden layers and an output layer, each of which is followed by an activation function. The input element is a vector of $N+1$ dimension, indicating