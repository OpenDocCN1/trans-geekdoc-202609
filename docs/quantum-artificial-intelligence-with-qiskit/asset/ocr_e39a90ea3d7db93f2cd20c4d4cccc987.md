![](bbox=[0.318, 0.085, 0.642, 0.365])

**Figure 15.18** Superposition states not equal to zero. The measured probability (control qubit equal to one) indicates the firing of the units is 0.838, the measured probability values are 0.213, 0.125, and 0.25.

```
qc.cp(pi/8,18,22)
qc.cp(pi/8,19,22)
qc.barrier()
qc.h(22)
qc.draw()
```

The measured probability (control qubit = 1) indicating a firing of the units is 0.838 and there are six states not equal to zero, see Figure 15.18, and compare with Figure 15.11.

# 15.5 CONCLUSION

The cost of the sleep phase and the active phase are the same as one of a conventional associative memory $O(n^2)$. We assume that we have enough time to prepare several quantum Lernmatrics in superposition. The quantum Lernmatrics are kept in superposition until they are queried in the active phase. Each of the copies of the quantum Lernmatrix can be queried only once. We argue that the advantage to conventional associative memories is present in the active phase the fast determination of information $O(\log(n)-n)$ is essential by the use of the quantum Lernmatrics in superposition compared to the cost of the classical $O(n \cdot \sqrt{n})$ or of the Grover's algorithm $O(n^2)$

```
$O(n \cdot \sqrt{L}) = O \frac{n^2}{\log(n)}$
```