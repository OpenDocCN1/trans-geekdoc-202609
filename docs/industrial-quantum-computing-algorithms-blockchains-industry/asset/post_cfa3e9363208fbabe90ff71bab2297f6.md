
# Chapter 2 Quantum machine learning: opportunities and challenges

[42] Pat V, Lihore UK A survey on different data mining & machine learning methods for credit card fraud detection. In Jci Res Comput Sci Eng Technol. 2018;3(5):320–325.

[43] Di Meglio A, Jansen K, Tavernelli I, Alexandrou C, Arunachalam S, Bauer CW, Borras KA, Carrazza S, Crippa A, Croft V, De Rutter Quantum computing working for high-energy physics: State of the art and challenges. Summary of the QCHEP working preprint arXiv:2307.02326. 2023.

[44] Meyer J, Mularski M, Gili-Fuster E, Wale, Aranzani F, Wilms A, Exploiting symmetry in quantum machine learning. PRA Quantum. 2023;M(1):010328.

[45] Smaldone AM, Kyoto GY, Batista VS Quantum Convolutional Neural Networks for Multi-Channel Supervised Learning. arXiv preprint:2305.18961, 2023.

[46] Amato F, Cicalese M, Lubicotto C, D'Ambola G, La Macca A, Pagano G, Tomeo F, Robertazzi GA, Vassallo A, Gacamora G, QuantumLight: A low-code platform to experiment with quantum machine learning. Softwares.2022;3:101399.

[47] Guntiani R, Holk P, Park DK, Federis H, Blan C, Gerasqi G, Quantum-inspired algorithms for direct machine learning. Appl Soft Comput. 2023;14:109956.

[48] Malik AJ, Versma C, Quantum computing and geometry optimization. arXiv preprint. 2023,2023-03-10.

[49] Kulkarni V, Pawale S, Kharat A, A classical–quantum neural network for detecting dementia from speech records. Neural Neural Comput. Appl. 2023;35(21):15503–15510.

[50] Schreiber FJ, Meyer JJ, Surrogates for quantum machine learning. Phys Rev Lett. 2023;130(10):108003.

[51] Chawla D, Mehta PS, A Survey on Quantum Computing for Implementation of Information Security. Soft Comput. 2023;218:2191–2200.

[52] Deng Z, Wang X, Dong B Quantum computing for real-time building HVAC controls. Appl Energy. 2023;334:120621.

[53] Batolos E, Vrougliakis, Quantum learning in embedded systems: Limitations, solutions and future challenges. In: 2023 IEEE 13th Annual Communication and Workshop on Conference (CCWC). IEEE. 2023;345–350.

[54] Daniel AM, McScale S, Berta M, Menias P, Chen GF, Gylfen A, Hann CT, Kastoranyo MJ, Khabillouine E, Kubika Albert S, Quantum algorithms: A survey of applications and end-to-end complexities. arXiv preprint arXiv:2310.03011, 2023.

[55] Cai M, Xiao S, Li Z, Rein reinforcement learning under temporal logic with reward design and quantum action selection. Sci Rep. 2023;139:1925.

[56] Chen SY, Synchronous training of quantum reinforcement learning. arXiv preprint arXiv:2301.05096, 2023.

[57] Jaeger R, Rees RM, Universal expressibility of quantum classifiers and quantum kernels for support vector machines. Nat. Comput. 2023;142:576.

[58] Campos R, Casares PA, Martin-Delgado MA, Quantum metropolis solver: A quantum walks approach to optimization problems. Quantum Mach Intell. 2023;5:228.

[59] Abdulsawal G, Mohamed S, Shaiba H. Explainable Deep Learning Prediction Using Ensemble-Quantum Machine Learning. Intell Soft Comput. 2023;136:161–779.

[60] B. Quantum, Ullah U, Murtado P, Jurardo AGO, Gonzalez ID, Merodio JM, Garcia-Zapirain B. Quantum Machine Learning to Electronic Health Records for Ischemic Disease Classification. Hum-Cent Comput Inf Sci. 2023;13(006).

[61] Kavitha SS, Kauld N Quantum KMeans clustering method for detecting heart disease using quantum circuit architecture. Soft Comput. 2023;27(18):13255–1328.

[62] Prajapati JB, Paliwal H, Prajapati BG, Saikia S, Pandey R. Quantum machine learning in prediction of breast cancer. In: Quantum Computing: A Shift from Bits to Qubits. Springer Nature Singapore; 2023. 351–382.

# Juhi Singh, Aarti Chugh, Shishir Singh Chauhan, and Arun Kumar Singh
## Chapter 3 Quantum machine learning algorithms: a comprehensive review

**Abstract:** Quantum machine learning (QML) combined with classical learning provides hitherto unexplored capabilities for problem resolution. The goal of this chapter is to present a thorough analysis of the ideas and uses of quantum computing capacity on machine learning. A full analysis of QML algorithms, such as principal component analysis, support vector machines, and quantum neural networks, is conducted after an explanation of the foundations of quantum concept and its distinguishing features. The critical assessment considers robustness, interpretability, and scalability in evaluating the benefits and drawbacks of each model. The primary focus is on merging of classical and quantum models, looking at areas that make the most advantageous aspects of both. This work addresses challenges associated with putting quantum algorithms into practice, including hardware constraints and error reduction. This chapter evaluates the state of quantum computing technologies and their applicability to real-world applications, in addition to reviewing particular trends that shed light on where QML will go in the future. The final section of this chapter discusses potential future paths for QML, emphasizing the need for unified benchmarks, enhanced hardware, and cooperative efforts between machine learning and quantum computing. The concise review attempts to serve as a useful reference for scholars, professionals, and hobbyists navigating the quickly evolving field of machine learning by providing an extensive overview of QML.

**Keywords:** Quantum Computing, Qubits, Machine Learning, Quantum Neural Networks

**Juhi Singh**, Department of Computer Science, School of Science and Engineering, Manipal University, Jaipur, e-mail: juhisinh17@gmail.com
**Aarti Chugh**, IILM University, Gurgaon, e-mail: a.chugh@ilm.edu
**Shishir Singh Chauhan**, Department of Computer Science, School of Science and Engineering, Manipal University, Jaipur, e-mail: shishirsingh13@gmail.com
**Arun Kumar Singh**, Amity University, Haryana, e-mail: arunsingh86@gmail.com

https://doi.org/10.1515/9788313548420-3

### 3.1 Fundamentals of quantum computing

Electronic data that is extremely dense can be processed more quickly thanks to quantum computing. Computers process any binary (0s and 1s) sequentially. Instead of being limited to two states, quantum computers store data as quantum bits, or qubits, which may simultaneously be both 0 and 1 in a process known as superposition. Quantum computing is a subsection of information systems which are used to process information utilizing mechanical processes. Qubits, which are nothing more than quantum bits, are encoded using two kinds of quantum mechanical phenomena: superposition and entanglement. For the comparable idea, the qubits represent exponentially more values than their classical bit counterparts. Compared to a traditional 0 and 1 bit, a qubit superposition indicates a greater state.

![](img/003d10cd18c2ce02e1f86a5992a292b_47_0.png)

**Figure 3.1:** Representation of classical bits and qubits.

#### 3.1.1 Representation of qubits

The quantum mechanics state of qubits is represented using Dirac notation, which is the matrix representation. As Figure 3.1 illustrates, the chance of collapsing to state 0 is represented by the higher value, while the possibility of collapsing to state 1 is represented by the bottom value inside each matrix (3.1):

```0 = [1; 0]; 1 = [0; 1]
```

As the number of qubits increases, so does the representation of a quantum matrix. In this case, the matrix may hold $2^n$ records for every $n$ qubits.

#### 3.1.2 Superposition and entanglement

Superposition is the capacity of a quantum system to exist in many states concurrently; in other words, a system can exist in "here" and "there," or "up" and "down" at the same time [1]. A quantum mechanical notion known as superposition allows a qubit to be simultaneously represented in the states "0" and "1". The $n$ qubits are essentially in a superposition state with $2^n$ states [17].

Entanglement, on the other hand, describes a strong connection between two particles. The linked qubit state will instantly reflect the transition in the first qubit state. This contributes to quantum computers operating at higher speeds [1].

#### 3.1.3 Qubit technology

The methodical study of algorithmic methods and techniques that define and reform information is referred to as quantum computing. Utilizing the foundations of quantum physics, quantum computing addresses difficult computational issues. By using the storage and transport capabilities of small items, such as ions, electrons, or photons, it offers novel computing possibilities. Qubits, or quantum bits, are used in quantum computing and are similar to bits, or 0 and 1, in the way many concurrent processes do quicker than a regular computer in applications, such as quantum simulation and prime factorization. Table 3.1 enumerates the challenges related to qubit technology. Five conditions had to be met for qubit technology to be physically implemented, according to IBM’s David DiVincenzo 2000. Later on with reference to quantum information transmission, two more conditions were added [1].

**Table 3.1:** Technological challenges of qubit technologies.

| Qubit technology | Description | Key challenges | References |
| --- | --- | --- | --- |
| Superconducting technology | Using superconducting circuits, the qubits are constructed. Solid-state computation uses superconducting qubits, which have two logic states: the ground and excited states. | Choosing particle mass, low operating temperature, nonuniform qubit splitting, scaling, poor lifetime, calibration, manufacturing problems, etc. | [2] |
