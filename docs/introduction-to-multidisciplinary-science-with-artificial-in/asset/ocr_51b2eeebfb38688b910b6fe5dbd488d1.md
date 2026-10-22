![](bbox=[0.12, 0.09, 0.85, 0.18])

Figure 4.16. An example of quantum computing where X is the NOT gate and H is the Hadamard gate.

computation is based in the construction chains of logic gates, as illustrated in Figure 4.16.

> Quiz: (1) Determine H ⊗ H |ud⟩ as a function of |−⟩ and |−⟩.
> (2) We consider a system of n qubits. A number of quantum-computing algorithms use the n-bit Hadamard transformation which is the tensor product of a Hadamard transformation for each bit:
> 
> W_n = H ⊗ H ⊗ H ⊗ ... ⊗ H,
>       n times
> 
> where W_n is the Walsh-Hadamard transformation. Determine W_3 |uuu⟩ function of the Walsh-Hadamard transformation.

# 4.2.2. A Formulation of Quantum Entanglement

Quantum entanglement is one of the key components of modern quantum information theory, with endless potential applications. How can we define and quantify that the state of our quantum system is entangled? The goal of this subsection is to answer these question, starting with the definition of entangled state and Schmidt decomposition. This decomposition provides one of the simplest methods for determining whether a pure state is separable or entangled. Gühne and Tóth (2009) and Horodecki et al. (2009) are two of the key references used in developing this subsection.

# Mathematical definition of quantum entanglement

Let us consider two electrons with the following states: |a₁⟩ = α₁ |u⟩ + β₁ |d⟩ and |a₂⟩ = β₁ |u⟩ + β₂ |d⟩ with α₁² + α₂² = 1 and β₁² + β₂² = 1. Let us emphasize that each electron has its own state. In mathematical terms, |a₁⟩ is a two-dimensional vector of ℋ₁ and |a₂⟩ is a two-dimensional vector of ℋ₂. The two electrons can be written as the product of states:

|a₁a₂⟩ = α₁α₂ |uu⟩ + α₁β₂ |ud⟩ + β₁α₁ |du⟩ + β₁β₂ |dd⟩ . (4.85)

We have a state of two separate states, which is also known as a product state; entangled particles cannot be factored into completely separate local terms without reference to the other. In quantum physics world, it is common to call electron 1 Alice’s electron and electron 2 Bob’s electron. Then for a product state Alice’s and Bob’s electrons are independent of one another. (In terms of their states, that is. The electrons will still interact electrically and magnetically with one another.) The fact that they are independent means that Alice can do whatever she want with