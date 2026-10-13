
# Chapter 7: Algorithms and Applications

**Authors:**

*   **R. Thenmozhi**  
    SRM Institute of Science and Technology, India
*   **D. Vetriselvi**  
    [![Orcid Image](i/orcid.svg)https://orcid.org/0009-0001-3870-9061](https://orcid.org/0009-0001-3870-9061)  
    SRM Institute of Science and Technology, India
*   **A. Arokiaraj Jovith**  
    SRM Institute of Science and Technology, India

## Abstract

Cryptography is the process of encrypting data or transforming plain text to ciphertext so that it can be deciphered only by an appropriate key. Quantum cryptography employs quantum physics principles to encrypt and transport data in an unbreakable manner. Quantum Key Distribution (`QKD`) is a technique for creating and exchanging private keys over quantum channels between two parties. Then, using standard cryptography, the keys can be used to encrypt and decrypt messages. Unbreakable encryption is something we really must have. The integrity of encrypted data is now in danger due to the impending development of quantum computers. Fortunately, quantum cryptography, via `QKD`, provides the answer we require to protect our information for a very long time to come. This is all based on the intricate principles of quantum mechanics. This chapter discusses the various algorithms used and the applications of quantum cryptography.

## Introduction

### Quantum Computing

Quantum computing is a multidisciplinary field that integrates computer science, mathematics, and physics. We can solve complex problems far faster with quantum physics than we can with conventional computers. Quantum computing includes both hardware and software development and research. Two examples of quantum mechanical characteristics that quantum computers employ to surpass classical computers in particular problem types are superposition and quantum interference. This is so that quantum computers may make use of these phenomena. Machine Learning (`ML`), optimisation, and simulation of physical systems could all profit from the faster processing rates provided by quantum computers. Potential applications in the future include enhancing financial portfolios and modelling chemical reactions, two tasks that require resolving issues that are beyond the capabilities of even the most potent supercomputers available today.

Quantum bits, or `qubits`, are represented by symbols called quantum particles. The control devices play a major role in the success of the attempt to maximise the processing capabilities of a quantum computer by manipulating `qubits`. The bits found in traditional computer types are comparable to the `qubits` seen in quantum computers. A traditional machine's `CPU` is primarily in charge of manipulating bits to accomplish its tasks. Parallel to this, the manipulation of `qubits` is the only way the quantum processor can perform its duties ([Raymer, 2017](#979-8-3693-1642-9.ch007.xhtml#r20)).

An electronic signal that can exist in one of two states—on or off—is referred to as a "bit" in the context of classical computing. Depending on the circumstance, the classical bit's value can be either one (on) or zero (off). Owing to its foundation in the concepts of quantum physics, the `qubit` can exist in a superposition of states.

## Background

### Quantum Mechanics

In the study of very small-scale particle behaviour, physics offers a field known as quantum mechanics. The equations governing particle behaviour at the subatomic scale are not the same as those describing the macroscopic environment. The utilisation of these phenomena by quantum computers results in computational processes that are radically novel (Sasaki, 2012).

### Basic Concepts Behind Quantum Computing

The application of quantum ideas forms the foundation of quantum computing. A new lexicon of terms is required to fully comprehend quantum principles. These include concepts like decoherence, entanglement, and superposition. Let us get a deeper comprehension of these principles ([Banafa, 2023](#979-8-3693-1642-9.ch007.xhtml#r4)).

#### Superposition

Superposition is the idea that two or more quantum states can be combined in a way that is like how waves are combined in conventional physics, and the outcome will be another valid quantum state. Conversely, any given quantum state can also be defined as the sum of two or more other unique states. The inherent parallelism of quantum computers, which allows them to perform millions of tasks simultaneously, comes from this superposition of `qubits`.

#### Entanglement

When two systems are connected in such a way that knowledge about one system instantly provides knowledge about the other, regardless of the distance between the two systems, this phenomenon is called quantum entanglement. Quantum computers can infer information about the initial particle by measuring another particle. They can determine, for example, that when one `qubit` spins upward, the other will necessarily spin downward, and vice versa. By utilising quantum entanglement, quantum computers can solve complex issues faster. When a quantum state is measured, the wavefunction collapses, and the state is measured as either a zero or a one depending on the measurement outcome. When in this known or predictable state, the `qubit` behaves similarly to a conventional bit. Entanglement occurs when `qubits` can correlate their states with those of other `qubits`.

#### Decoherence

Decoherence is the process by which a `qubit` loses its quantum state. The collapse of the `qubits`' quantum state can occur under a variety of environmental circumstances, including radiation. The design of the many features that try to postpone the state's decoherence is one of the biggest engineering hurdles in the process of creating a quantum computer. As an illustration, the creation of specific structures that protect the `qubits` from outside fields.

### Components of Quantum Computer

In the same way that classical computers have hardware and software, quantum computers also operate in this manner.

| Figure 1. Components of Quantum Computing |
| --- |
| ![Figure979-8-3693-1642-9.ch007.f01](i/ch007.f01.png) |

#### Quantum Hardware

Hardware for quantum computing consists of three primary components.

*   **Quantum Data Plane**  
    The core of the quantum computer is the quantum data plane, which contains all the physical `qubits` and the structures required to hold them in place.
*   **Control And Measurement Plane**  
    The control and measurement plane converts digitalized signals into either wave control signals or analogue signals.  
    The analogue signals in the quantum data plane are responsible for executing the `qubit` operations.
*   **Control processor plane and host processor**  
    The control processor plane implements both the sequence of operations and the quantum algorithm.  
    The host processor communicates with the quantum software and sends a digital signal or a set of classical bits to the control and measurement plane.

#### Quantum Software

Using quantum circuits to implement unique quantum algorithms is known as quantum software. A kind of computing process known as a quantum circuit describes a series of logical quantum operations that are carried out on the `qubits` that make up the circuit. To write quantum algorithms, programmers can make use of a broad range of software development tools and libraries.

### Cryptography

The translation of the word "cryptography" is "hidden," and the suffix "-graph" denotes writing. Hence, writing that is secure or hidden is called cryptography.
