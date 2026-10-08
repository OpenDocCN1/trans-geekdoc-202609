# Chapter 11 Quantum computing and machine learning: a symbiotic relationship — 185

As shown in Figure 11.4 the types of data and the type of processor employed for solving the problems vary from one to another. The four classes are based on whether the data is classical (C) or quantum (Q) and whether the algorithm is running on a classical computer (C) or a quantum computer (Q).

Figure 11.5 depicts the four classes that are used to solve a problem:

![](bbox=[0.104, 0.217, 0.616, 0.413])

**Figure 11.5:** Four classes to solve the problem.

As shown in Figure 11.5, there are four classes to solve the problem: however, the algorithm is inspired by quantum computing, such as a recommendation system algorithm.

+   - CC is the classical data processing using classical computers; the algorithm is inspired by quantum computing, such as a recommendation system algorithm.
- CQ is the processing of classical data using a QML algorithm.
- QC is the processing of quantum data using a classical ML algorithm.
- QQ is the processing of quantum data using a QML algorithm, also known as fully QML (FQML).

# 11.5.1 Variational or a parametrized quantum circuit (PQC)

Variational or a parametrized quantum circuit (PQC) is a catchy quantum algorithm that hinges on free parameters. It helps to utilize real-world quantum computers to the fullest. PQCs perform two main tasks in QML: data encoding and acting as a work-model.

PQCs adjust their parameters according to the data to be encoded when used to encode data. Alternatively, they could function as quantum models, based on parameters determined through optimization. PQCs are similar to ML models and employ a variational quantum classifier with two variations of circuits.

In the first circuit, gate parameters are associated with fixed data inputs; the second circuit, free and trainable parameters are employed. This setup is a basic