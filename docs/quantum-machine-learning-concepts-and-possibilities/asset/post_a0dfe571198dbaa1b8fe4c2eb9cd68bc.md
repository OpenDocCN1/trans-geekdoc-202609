
- 7.4.3 Gradient estimation 7-11
- 7.4.4 Training challenges 7-11
- 7.5 Case studies and applications 7-12
- 7.5.1 Learning classical data distributions 7-12
- 7.5.2 Quantum state learning and tomography 7-12
- 7.5.3 Quantum circuit compilation and data compression 7-13
- 7.5.4 Anomaly detection 7-13
- 7.5.5 Physical simulation and sampling 7-13
- 7.6 Open challenges and future directions 7-14
- 7.6.1 Challenges 7-14
- 7.6.2 Evaluation metrics and benchmarks 7-15
- 7.6.3 Opportunities 7-15
- 7.7 Summary 7-16
- References 7-17

# 8 Theory, expressivity, and learning bounds 8-1
- 8.1 Definitions and frameworks for expressivity 8-2
- 8.1.1 Hypothesis classes 8-2
- 8.1.2 Quantifying expressivity 8-3
- 8.1.3 Expressivity versus trainability 8-4
- 8.2 Learning performance: sample complexity and generalization 8-6
- 8.2.1 PAC and agostic learning 8-6
- 8.2.2 Quantum sample complexity 8-7
- 8.2.3 Generalization bounds for quantum models 8-8
- 8.3 Positive results from quantum learning 8-9
- 8.3.1 Query and time complexity speedups 8-9
- 8.3.2 Quantum kernels and feature maps 8-10
- 8.3.3 Quantum generative models 8-10
- 8.4 Limitations, no-go theorems, and dequantization 8-12
- 8.4.1 Sample complexity lower bounds 8-12
- 8.4.2 Barren plate and optimization barriers 8-13
- 8.4.3 Dequantization results 8-13
- 8.4.4 Robustness and noise sensitivity 8-14
- 8.5 Open problems and future directions 8-14
- References 8-15

# Preface

Quantum computing and machine learning are some of today's most active and rapidly expanding fields of research and development. Quantum machine learning has evolved in recent years as a subdiscipline of quantum computing that explores how quantum computers can be used for machine learning tasks—in other words, how quantum computers can learn from data, either quantum or classical. Quantum machine learning is an exciting field because it holds the promise of accelerating classical machine learning algorithms.

This book will showcase the growing number of algorithms and practical applications of quantum machine learning. Starting from the foundational approach that reformulates learning theory in a quantum setting, this book will highlight recent efforts to find quantum algorithms that speed up machine learning regarding computational complexity. The book will also cover new machine learning applications tailored for noisy intermediate-scale quantum (NISQ) devices from near-term or co-design perspective, quantum-classical methods. The aim of this book is to help readers develop a clear understanding of the promises and limitations of the current machine learning, and help them define directions for future research in this exciting field. We start by looking at the quantum mechanical principles that enable quantum computing and helping the reader gather some intuition about how to harness these quantum mechanical properties to speed up some computational tasks. Then, we introduce the reader to some of the basic quantum algorithms that are often used to develop more complicated algorithms. Later, we explore the different fields of study in quantum machine learning, which are related to the choice of algorithm, and whether it operates on quantum or classical data. Finally, we describe the state-of-the-art for quantum machine learning algorithms including both supervised and unsupervised learning, discussing their applications and limitations for implementation on near-term devices.

Quantum machine learning is a subject in the making, with endless possibilities for applications in the near and long term. Nonetheless, to find out what quantum machine learning has to offer, its numerous avenues first have to be explored by an interdisciplinary community of scientists and quantum computing enthusiasts. We intend this book to be a possible starting point for this journey, as it is intended to introduce some key concepts, ideas, and algorithms that are the result of the first few years of quantum machine learning research. Our aim is to provide a comprehensive literature review and to summarize key topics that appear often in quantum machine learning, to put them into context and make them accessible to a broader audience in order to foster future research and applications.

# Author biographies

# Dr Andrea Delgado

Dr Andrea Delgado is a Research Scientist in the Physics Division at Oak Ridge National Laboratory. Her research focuses on quantum computing applications to high-energy physics, with an emphasis on developing novel algorithms for data analysis and simulation in large-scale particle physics experiments, such as those at the Large Hadron Collider. She is a recipient of the prestigious Eugene Wigner Fellowship, awarded for her pioneering work at the intersection of quantum information science and fundamental physics. Dr Delgado serves on the steering committee of the IBM/CERN Quantum Computing for High Energy Physics Working Group and has played a leadership role in IEEE Quantum Week since its inception, multiple terms as Technical Program Chair. She is also an Associate Editor for IEEE Transactions on Quantum Engineering. Dr Delgado received her PhD in Physics from Texas A&M University, where she specialized in searches for new physics. Her current work explores quantum machine learning, quantum generative modeling, and hybrid quantum-classical algorithms with the aim of advancing discovery in high-energy and nuclear physics.

# Dr Kathleen E Hamilton

Dr Kathleen E Hamilton is a Research Scientist in the Quantum Science Group at Oak Ridge National Laboratory. Her research interests cover the development of benchmarks and algorithms for next-generation processors in quantum computing. Her work in machine learning includes natural language processing, reservoir computing, and using machine learning workflows to benchmark near-term quantum devices. She has served on the Program Committee for the International Conference on Neuorphic Systems (ICONS) from 2019 to 2021, and has organized the Quantum Artificial Intelligence Workshop which has been a part of IEEE’s Quantum Week since 2020. She received her PhD from the University of California at Riverside.

# Quantum Machine Learning Concepts and possibilities

Andrea Delgado and Kathleen E Hamilton

# Chapter 1 Introduction

## 1.1 Motivation and scope

The accelerating development of quantum technologies has opened new frontiers in computation, communication, and sensing. Among the most promising direction is **quantum machine learning (QML)**.

QML aims to explore whether and how quantum resources can enhance learning tasks, improve model expressivity, or accelerate training and inference. It combines the principles of quantum mechanics and machine learning to explore new ways of processing, analyzing, and generating data.

This book introduces the core ideas, algorithms, and challenges in *QML*, presenting both theoretical foundations and practical applications tailored for current and near-term quantum devices. The text is structured to serve as a *self-contained textbook*, suitable for graduate students or researchers with a working knowledge of quantum computing and a general background in classical machine learning.

Quantum speedup in learning

QML is motivated by the potential for *computational speedups* over classical algorithms [1]. But what ‘speedup’ mean in general? A quantum algorithm exhibits *quantum speedup* when it solves a problem with lower resource usage (e.g. time, queries, or samples) than any known algorithm [2]. These speedups can take various forms:

- **Polynomial speedup**: Occurs when a quantum algorithm reduces the runtime from $O(n^k)$ to $O(n^m)$ for $m < k$. *Example*: Grover's algorithm [3] for unstructured search achieves a quadratic speedup ($O(N)$ to $O(\sqrt{N})$).
- **Exponential speedup**: Occurs when a quantum algorithm solves a task in poly(n) while classical solutions require exp(n). *Example*: Shor's factoring algorithm [4].
