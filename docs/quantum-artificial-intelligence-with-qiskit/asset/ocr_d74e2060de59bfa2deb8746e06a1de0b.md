# Quantum Associative Memory ■ 193

![](bbox=[0.179, 0.114, 0.819, 0.513])

Figure 14.5. The circuit representing the three Grover's rotations with two times the cost of marking all present states.

cost influence of the Grover's amplification algorithm. In our case we need three Grover's rotation with two times the cost of marking all present states (see Figure 14.5). For four states in superposition and one target value, we would only need one rotation.

# 14.3 INPUT DESTRUCTION PROBLEM

Most quantum machine learning algorithms including quantum associative memory suffer from the input destruction problem (ID problem) [3, 126, 1]:

+   - The input (reading) problem: The amplitude distribution of a quantum state is initialized by reading data points. The existing quantum algorithm requires only $O(\sqrt{n})$ steps or less and is faster than the classical algorithms, $n$ data points must be read. Hence, the complexity of the algorithm does not improve and is $O(n) + O(\sqrt{n})$.

+   - The destruction problem: A quantum associative memory [114, 115, 110], [111, 112] for $n$ data points for dimension $m$ requires only $m \cdot \log(n)$ or fewer