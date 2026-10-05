
Table 1.1. Correspondence between classical and quantum machine learning terminology. While classical models operate on vectors and real-valued functions, quantum models manipulate quantum states using parameterized circuits and observables.

| Classical machine learning | Quantum machine learning |
|---|---|
| Data | Quantum state |
| Model | Parametric circuit |
| Feature map | Data encoding |
| Loss function | Observable |
| Training | Optimization |

In contrast, unsupervised learning seeks to uncover hidden structure in data without explicit labels, by identifying clusters, reducing dimensionality, or learning generative representations. In both settings, the concepts of generalization, overfitting, and regularization are essential for understanding model performance on unseen data. These challenges arise because the learner must strike a balance between flexibility and inductive bias—choosing a rich enough to capture relevant patterns but constrained enough to avoid fitting noise.

The training process is typically framed as an optimization problem. A cost function, or loss quantifies how the models' predictions are from the desired outcomes, and the model's parameters are adjusted iteratively using optimization algorithms such as gradient descent or its variants. In deep learning, the hypothesis class is often a highly non-linear, layered composition of functions with millions of parameters. See table 1.1 for the correspondence between classical and quantum machine learning terminology. Given the complexity of such models, empirical evidence shows they can perform remarkably well when trained on large datasets, provided that the optimization landscape is well-behaved and the model capacity is sufficient.

These foundational ideas will recur throughout the book as we explore quantum models for learning. Many of the concepts—such as model selection, generalization, and optimization—carry over to the quantum domain, but they must be reconsiderined in light of quantum constraints, such as measurement-induced noise, circuit depth limitations, and the probabilistic nature of quantum state preparation and inference. The challenge, and promise, of QML lies in identifying which elements of this classical framework can be enhanced or replaced by quantum mechanisms, and in understanding when such replacements yield practical or theoretical benefits.

## 1.5 Types of quantum machine learning

QML encompasses a broad range of algorithmic strategies, shaped by the interplay between the data and the computational model used. At its core, QML research asks whether quantum resources can offer an advantage over classical methods in tasks such as classification, regression, sampling, or generative modeling. However, not all QML algorithms engage with quantum mechanics in the same way. The extent to which quantum mechanics is utilized depends not only on whether the algorithm runs on a quantum device, but also on the nature of the input data and how they are represented.

Some QML methods aim to process entirely classical data, using quantum circuits as models with potentially advantageous expressivity or trainability. Others are designed for quantum-native tasks, such as learning from quantum states produced by physical systems or quantum simulations. Others fall somewhere in between, using classical inputs but relying on quantum subroutines—such as state overlap estimation or kernel computation—to accelerate specific components of the learning process. This diversity has led to a need for a coherent framework that distinguishes between the different modes of operation in QML.

To classify these, the following taxonomy presents QML approaches in terms of two orthogonal criteria: the type of data being learned from, and the type of model performing the learning. This classification not only provides a conceptual map of the field but also highlights the assumptions, limitations, and opportunities inherent in each approach.

## Taxonomy of QML approaches

QML algorithms can be broadly categorized by two features, the nature of the data and the model/algorithm. This leads to four types of QML workflows:

| Data type | Model type | Example use case |
| :--- | :--- | :--- |
| Classical | Classical | Standard ML: SVMs, CNNs, Gaussian mixture models, gradient boosting |
| Quantum | Quantum | Variational quantum classifiers, quantum kernel methods, quantum circuit Born machines trained on classical datasets |
| Quantum | Classical | Shadow tomography, quantum measurement data classification, classical post-processing of quantum sensor outputs |
| Quantum | Quantum | Full quantum generative models, quantum autoencoders, quantum state determination, quantum-enhanced metrology |

Remarks:

- The classical data + quantum model category is most relevant for near-term applications using hybrid quantum-classical algorithms.
- The quantum data + quantum model scenario is natural for quantum-native tasks such as quantum error correction, state classification, or entangled sensor networks.
- Some algorithms (e.g. QANs) can bridge multiple categories depending on how the generator, discriminator, and data encoding are structured.

## Quantum Machine Learning

This chapter established the foundation for exploring Quantum QML by outlining the motivations, scope, and structural organization of the book. We introduced the central question driving the field: how quantum computing can enhance or redefine learning tasks in terms of computational efficiency, model expressivity, or data representation. To anchor the reader, we reviewed the key principles of quantum computing and classical machine learning, identifying conceptual parallels and differences that will inform subsequent chapters.

A critical component of this chapter was the classification of QML approaches based on the nature of both the input data and the model, highlighting the spectrum of hybrid and fully quantum strategies that define the field. This taxonomy provides a conceptual map for the reader, helping to locate various algorithms, techniques, and applications within a coherent framework.

By the end of this chapter, the reader should be prepared to navigate the interplay between quantum and classical paradigms, understanding the significance of encoding choices, and appreciate the high-level design space of QML workflows. The remainder of the book builds on this foundation, beginning with a more detailed examination of quantum primitives and classical learning theory, and gradually advancing towards the state-of-the-art models, and open challenges in the field.

## References

- [1] Biamonte J, Wittek P, Pancotti N, Rebentrost P, Wiebe N and Lloyd S 2017 Quantum machine learning Nature 549 195–202
- [2] Montano A 2016 Quantum algorithms: an overview npi Quantum Inf. 2 150233
- [3] Grover L K 1996 A fast quantum mechanical algorithm for database search Proc. 28th Annual ACM Symp. on Computing pp 212–219
- [4] Shor P W 1997 Polynomial-time algorithms for prime factorization and discrete logarithms on a quantum computer SIAM J. Comput. 26 1484–509
- [5] Cross A W, Smith G and Grolmal J 2015 Quantum learning robust against noise noise Phys. Rev. 92 012327
- [6] Rist D, da Silva M P, Ryan C A, Cross W A, Cócoles D, Smolin J A, Gambetta J M, Chow J M and Johnson B R 2017 Demonstration of quantum advantage in machine learning any Quantum Inf. 3 16
- [7] Tucanasalam S and de Wolf R 2017 Guest column: A survey of quantum learning theory ACM SIGACT News 48 41–67
- [8] Servideo R A and Gottler S J 2004 Equalities and separations between quantum and classical learnability SIAM J. Comput. 33 1067–92
- [9] Bernstein E and Vazirani U 1997 Quantum complexity theory SIAM J. Comput. 26 1411–73
- [10] Aci A and Servideo R 2007 Quantum algorithms for learning and testing quantum Quantum Inf. Process. 6 323–48
- [11] Havlíček V, Cócoles A D, Temme K, Harrow A W, Kandala A, Chow J M and Gambetta J M 2019 Supervised learning with quantum-enhanced feature spaces Nature 567 209–12
- [12] Schuld M and Killoran N 2019 Quantum machine learning in Hilbert spaces Phys. Rev. Lett. 122 040504
