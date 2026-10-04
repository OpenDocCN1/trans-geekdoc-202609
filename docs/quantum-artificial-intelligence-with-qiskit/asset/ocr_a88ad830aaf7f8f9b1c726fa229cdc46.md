# Grover's Amplification 79

the mapping is defined as,

```
$$x_{j}^{new} = 2 \cdot \frac{\sum_{i=1}^{n} x_{i}^{old}}{n} - x_{j}^{old}$ $\quad (5.11)$
```

Suppose only one amplitude of $x_j$ is negative and the other one is positive. Then the amplitude grows with

```
$$x_{j}^{new} = 2 \cdot \frac{\sum_{i=1}^{n} x_{i}^{old}}{n} + x_{j}$ $\ $(5.12)$
```

the other $x_i$ with $i \neq j$ differs. With $j=2$ we get

```
$$\begin{matrix} 2 \cdot \frac{\sum_{i=1}^{n} x_{i}}{n} - x_1 & = & x_1 \\frac{2}{n}-1 & & \ 2 \cdot \frac{\sum_{i=1}^{n} x_{i}}{n} - x_2 & = & -x_2 \\frac{2}{n}+1 & \ \vdots & &vdotsvdots & &vdots \ 2 \cdot \frac{\sum_{i=1}^{n} x_{i}}{n} - x_n & = & x_n \\frac{2}{n}-1 & & \end{matrix}$ $\quad (5.13)$
```

The probability of measuring the solution on the size $n$ is

```
$$p(solution) = \frac{3}{\sqrt{n}} - \frac{4}{n \cdot \sqrt{n}}$ $\quad (5.14)$
```

and non-solution

```
$$p(non - solution) = |\frac{1}{\sqrt{n}} - \frac{4}{n \cdot \sqrt{n}}|^2$ $\$(5.15)$
```

# 5.3.1 Number Iteration

The probability of seeing one solution should be as close as possible to 1 and the number of iterations [121]. The number of iterations $r$ is the largest integer greater than $t^*$,

```
$$r = [t^*] = \lceil \frac{\pi}{4}\sqrt{\frac{2m}{k}} - \frac{1}{2} \rceil$ $\$(5.16)$
```

The value of $r$ depends on the relation of $n$ over $k$, with being the number of solutions. For $n=4$ and $k=1$ we need only one rotation, but we need as only one rotation for

```
$$\frac{n}{4}$ $
```

to find one of the $k$ solutions. For 16 qubits and one solution, $k=1, n=65536=2^{16}$, with $t^*200.562$. In this case we need 201 rotations to compute the complexity $O(\sqrt{n})$, we get a quadratic speed up to conventional method.

When $r$ is unknown (since we do not know $k$) we can repeatedly choose $r$ randomly between 1 and $\frac{1}{2}\sqrt{2^m}$. This simple strategy leads to success in $O(\sqrt{n})=O(\sqrt{2^m})$ [82].

A more advanced approach is based on the periodic property of Grover's amplification (see Figure 5.1). The period is related to $k$ and can be determined by quantum counting algorithm with the complexity $O(\sqrt{n})$. Quantum counting is based on phase estimation algorithm and will be described in chapter 20 about the phase estimation algorithm.