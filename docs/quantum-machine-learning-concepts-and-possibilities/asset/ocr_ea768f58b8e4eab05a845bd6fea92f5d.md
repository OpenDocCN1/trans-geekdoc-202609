# Quantum Machine Learning

Concepts and possibilities
Andrea Delgado and Kathleen E Hamilton

# Chapter 5

# Quantum variational optimization

Variational quantum algorithms (VQAs) [1] represent a pivotal shift in how intermediate-scale quantum computers can be harnessed for practical problem-solving in the noisy intermediate-scale quantum (NISQ) [2] era. These hybrid algorithms blend the quantum computer's ability to represent and manipulate quantum states with the classical computer's strength in performing optimization. The foundational idea is to use a parameterized quantum circuit to prepare a trial quantum state, evaluate an objective function (usually an expectation value), and use a classical optimizer to update the parameters and minimize the cost.

The origins of variational methods trace back to classical quantum chemistry, where the variational principle is a fundamental tool for approximating the groundstate energy of a quantum system. This principle states that for any normalized wavefunction |ψ>, the expectation value of the Hamiltonian H provides an upper bound to the ground state:

```
E_0 = ⟨ψ|H|ψ⟩ (5.1)
```

This led to the development of methods such as Hartree–Fock and configuration interaction, where trial wavefunctions are optimized within a parameter to approximate molecular eigenstates. These methods became corners of computational chemistry and electronic structure theory throughout the twentieth century.

In the context of quantum computing, the variational eigensolver (VQE) was proposed in 2014 by Peruzzo et al [3] as a quantum-classical hybrid analog of this variational principle. VQE marked one of the first major algorithms designed specifically for NISQ devices. Instead of representing trial wavefunctions as linear combinations of basis functions (as in Hartree–Fock), VQE uses a quantum circuit with tunable parameters to generate quantum states that approximate the ground state of a given Hamiltonian. This allowed for representing entangled states that are difficult to model classically.