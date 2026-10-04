qc.cswap(6,1,4)
qc.cswap(6,2,5)
qc.h(6)
qc.measure(6,0)

```
simulator = Aer.get_backend('qasm_simulator')
result=execute(qc,simulator,shots=10000).result()
counts = result.get_counts()
print("\nTotal count are:{counts}")
plot_histogram(counts)
```

Using the swap test, after 10000 shots we measure p(0) = 0.9395 with

> $k(x,y) = |<x^T,y>|^3 \approx \sqrt{2-0.9395}-1=0.02975$

# 17.3 QUANTUM KERNELS AND INVERSION TEST

Quantum maps encode classical data into quantum data via a parametrized quantum circuit [40]. Instead of coding the classical feature vector x of dimension z by amplitudes, the feature vector defines by z parameters of the parametrized quantum circuit $U_{\phi(x)}$ with $z \geq m$

> $|\phi(x)| = U_{\phi(x)}|0^{\otimes m}$ (17.6)

with dimension of $\phi(x)$ being $2^m$. Parametrized quantum circuits based on superposition and entanglement are able to simulate classically and could lead to an advantage over classical machine learning approaches. The inversion test is based on the idea of estimating the fidelity (similarity) between two states [40]. For an input state $|0^{\otimes m}$ if we map it by parametrized quantum circuit $U_{\phi(x)}$ and un-compute it by $U_{\phi(x)}^{-1}$ the inverse if the parametrized quantum circuit $U_{\phi(x)}$ the probability of measuring the state $|0^{\otimes m}$ is one. If we represent the quantum circuit by a matrix $U_{\phi(x)}$, the inverse quantum circuit represented as a matrix corresponds to the conjugate transpose $U_{\phi(x)}^*$, also written as $U_{\phi(x)}^T$. If we parametrized quantum circuit $U$ by $x$ ($U_{\phi(x)}$) and the inverse of the parametrized quantum $U^1$ by $y$ ($U_{\phi(y)}^*$) and if $x$ and $y$ are similar, the probability of measuring $|0^{\otimes m}$ for the input $|0^{\otimes m}$ should be near 1,

> $U_{\phi(y)}^* U_{\phi(x)}|0^{\otimes m}$ (17.7)

If x and y differ a, this probability is smaller. The quantum kernel is represented as

> $k(x,y) = |<\phi(x)|\phi(y)>|^2 = |<0^{\otimes m}|U_{\phi(y)}^* U_{\phi(x)}|0^{\otimes m}>|^2$ (17.8)

We measure the final state times and record the number of $|0^{\otimes m}$ and estimate the value $k(x,y)$.