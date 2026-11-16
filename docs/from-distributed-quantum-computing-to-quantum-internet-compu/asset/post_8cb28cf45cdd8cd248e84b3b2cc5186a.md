
cannot know the client's inputs while still being able to perform the computations for the client. We also saw how the client can verify the server's computations, or at least detect, with some probability, if the server did not perform the delegated computations correctly. We also briefly discussed the notion of QaaS. Studies have been done on how a resource-limited client can trust the results from (what it thinks is a) quantum computer, e.g. by cross verification using multiple machines [Greganti et al., 2021]. Mahadev [2022] addressed the question of whether a computer is indeed a quantum one and whether it can be verified by a classical device.

## References

- Anne Broadbent. Delegating private quantum computations. *Canadian Journal of Physics*, 93(9):941–946, 2015.
- Anne Broadbent. How to verify a quantum computation. *Theory of Computing*, 14(11):1–37, 2018. doi: 10.4086/toc.2018.v014a011. URL https://theoryofcomputing.org/articles/v014a011.
- Andrew M. Childs. Secure assisted quantum computation. *Quantum Information and Computation*, 5(6):456–466, Sep 2005. ISSN 1533-7146.
- P. Drmota, D. P. Nadlinger, D. Main, B. C. Nichol, E. M. Ainley, D. Leichtle, A. Mantri, E. Kashefi, R. Srinivas, G. Araneda, C. J. Ballance, and D. M. Lucas. Verifiable blind quantum computing with trapped ions and single photons. CoRR, May 2023. URL https://doi.org/10.48550/arXiv.2305.02936.
- K. A. G. Fisher, A. Broadbent, L. K. Shalm, Z. Yan, J. Lavoie, R. Prevedel, T. Jennewein, and K. J. Resch. Quantum computing on encrypted data. *Nature Communications*, 5(1):3074, 2014.
- Joseph F. Fitzsimons. Private quantum computation: an introduction to blind quantum computing and related protocols. *npj Quantum Information*, 3(1):23, 2017.
- Alexandru Gheorghiu, Theodoros Kapourniotis, and Elham Kashefi. Verification of quantum computation: an overview of existing approaches. *Theory of Computing Systems*, 63(4):715–808, 2019.
- C. Greganti, T. F. Demarie, M. Ringbauer, J. A. Jones, V. Saggio, I. Alonso Calafell, L. A. Rozema, A. Erhard, M. Meth, L. Postler, R. Stricker, P. Schindler, R. Blatt, T. Monz, P. Walther, and J. F. Fitzsimons. Cross-verification of independent quantum devices. *Physical Review X*, 11:031049, Sep 2021. doi: 10.1103/PhysRevX.11.031049.
- Michele Grossi, Luca Crippa, Antonello Aita, Giacomo Bartoli, Vito Sammarco, Eleonora Picca, N. Said, Filippo Tramonfo, and Federico Mattei. A serverless cloud integration for quantum computing. CoRR, abs/2107.02007, 2021. URL https://arxiv.org/abs/2107.02007.

- Lei Liu and Xinglei Dou. QuCloud: a new qubit mapping mechanism for multi-programming quantum computing in cloud environment. In 2021 IEEE International Symposium on High-Performance Computer Architecture (HPCA), pages 167–178, 2021. doi: 10.1109/HPCA51647.2021.00024.

- Urmila Mahadev. Classical verification of quantum computations. SIAM Journal on Computing, 51(4):1172–1229, 2022.

- Enrique Muguel, Javier Rojo, David Valencia, Javier Berrocal, Jose Garcia-Alonso, and Juan M. Murillo. Quantum service-oriented computing: current landscape and challenges. Software Quality Journal, 30:983–1002, 2022.

- Napat Ngoenriang, Minrui Xu, Jiawen Kang, Dusit Niyato, Han Yu, and Xuemin Shen. DQC²O: distributed quantum computing for collaborative optimization in future networks. CoRR, abs/2210.02887, 2022. doi: 10.48550/arXiv.2210.02887. URL https://doi.org/10.48550/arXiv.2210.02887.

- Gokul Subramanian Ravi, Kaitlin N. Smith, Prakash Murali, and Frederic T. Chong. Adaptive job and resource management for the growing quantum cloud. In 2021 IEEE International Conference on Quantum Computing and Engineering (QCE), pages 301–312, 2021. doi: 10.1109/QCE52317.2021.00047.

- P. W. Shor. Algorithms for quantum computation: discrete logarithms and factoring. In Proceedings 35th Annual Symposium on Foundations of Computer Science, pages 124–134, 1994. doi: 10.1109/FOCS.1994.365700.

- Balwinder Sodhi and Ritu Kapur. Quantum computing platforms: assessing the impact on quality attributes and SDLC activities. In 2021 IEEE 18th International Conference on Software Architecture (ICSA), pages 80–91, 2021. doi: 10.1109/ICSA51549.2021.00016.

## The Quantum Internet

This chapter discusses some of the key concepts and ideas of the quantum Internet, including the central role that entanglement plays, the concepts of entanglement swapping and entanglement purification, and briefly reviews the notion of quantum repeaters and quantum Internet architectures. We will also look at quantum computations in relation to the quantum Internet.

### 6.1 Entanglement Over Longer Distances

So far we have seen that entanglement is key to many distributed quantum computing protocols and computations. Any two nodes which want to do computations together (e.g. perform a distributed–CNOT operation) need to share entangled qubits, even when the two nodes are geographically far apart. One can think of the quantum Internet as a “black box” from which nodes can request an entanglement between two qubits (on two nodes), or roughly speaking, providing “entanglement-as-a-service” (with the associated service-based ideas of “quality” of the entangled pair and “efficiency,” e.g. generating entanglement qubits in a timely manner). How is such an entangled pair generated? Answering this question in detail will take us further into the physics which we will not do so here. But generally, there are a number of mechanisms to generate an entangled pair (e.g. a Bell state) between two nodes.¹ One key point, however, is that due to decoherence affecting entangled qubits, distance is a limitation – e.g. it is hard to directly transmit a qubit over long distances without it suffering loss – so that generating an entangled pair between two nodes far apart over long distances requires what has been called quantum repeaters (analogous to repeaters for classical networks, but a totally different technology), which has a mechanism to take two entangled pairs (e.g. between qubits A on node 1 and A′ on node 2, and

1 A readable overview is at https://www.forbes.com/sites/chadorzel/2017/02/28/how-do-you-create-quantum-entanglement/?sh=2664a2c11732 [last accessed: 15/11/2022].

between qubits B' on node 2 and B on node 3) and generate an entangled pair over a longer distance (e.g. between A on node 1 and B on node 3). Key to this mechanism is the notion of entanglement swapping, which we will look into. We will also look into a mechanism to transmit quantum information robustly over longer distances using tree-cluster states. But before all that, we need the idea of Bell State Measurement.

#### 6.1.1 Bell States and Bell State Measurement

The four Bell states are \(|\Phi^+\rangle = (|00\rangle + |11\rangle)/\sqrt{2}\), \(|\Phi^-\rangle = (|00\rangle - |11\rangle)/\sqrt{2}\), \(|\Psi^+\rangle = (|01\rangle + |10\rangle)/\sqrt{2}\), and \(|\Psi^-\rangle = (|01\rangle - |10\rangle)/\sqrt{2}\). Since they are orthogonal, they form a basis, the *Bell basis*. For example, a state \(|\psi\rangle\) written in the basis \(\{|00\rangle, |01\rangle, |10\rangle, |11\rangle\}\):

\(|\psi\rangle = \alpha |00\rangle + \beta |11\rangle + \gamma |01\rangle + \delta |10\rangle\) where \(|\alpha|^2 + |\beta|^2 + |\gamma|^2 + |\delta|^2 = 1\), can be rewritten in the Bell basis as
\(|\psi\rangle = \frac{\alpha + \beta}{\sqrt{2}} |\Phi^+\rangle + \frac{\alpha - \beta}{\sqrt{2}} |\Phi^-\rangle + \frac{\gamma + \delta}{\sqrt{2}} |\Psi^+\rangle + \frac{\gamma - \delta}{\sqrt{2}} |\Psi^-\rangle\)

A Bell state measurement asks which of the Bell states \(|\psi\rangle\) is in.

How can we measure in the Bell basis if we can only measure in the *Z* basis (due to the instruments available, for example)? See Aside.

> Aside: Note that measuring a qubit in the X basis is applying the Hadamard gate first and then measuring in the Z basis in the sense that prob(+1) (or the probability of getting the state |0⟩) in this case is the same as X(+1) when measuring in the X basis.² The Pauli X measurement |ψ⟩ —X— can be implemented as |ψ⟩ —H— X— since prob(+1) are the same in both.
>
> Similarly, suppose |ψ⟩ is a two-qubit state, and if we want to measure in the Bell basis but only can measure in the basis {|00⟩, |01⟩, |10⟩, |11⟩}, we need a U such that: U |Φ⁺⟩ = |00⟩, U |Φ⁻⟩ = |10⟩, U |Ψ⁺⟩ = |01⟩, and U |Ψ⁻⟩ = |11⟩, and use it as follows (where the |ψ⟩ below is a two-qubit state):
>
> [Circuit Diagram: |ψ⟩ — U — Z — with measurement symbols]
