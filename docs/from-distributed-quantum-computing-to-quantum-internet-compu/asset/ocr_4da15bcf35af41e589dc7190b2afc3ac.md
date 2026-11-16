![](bbox=[0.136, 0.113, 0.725, 0.292])

Figure 3.1 The GHZ&M problem is for A, B, and C, on receiving inputs $i_A, i_B,$ and $i_C$ respectively, to compute the output bits $o_A, o_B,$ and $o_C$ (respectively), such that certain properties among the output bits are satisfied, without A, B, and C communicating once they receive their inputs.

Figure 3.1. The GHZ&M problem is to compute the output bits $o_A$, $o_B$, and $o_C$ such that the following condition is satisfied:

```
$$o_A \oplus o_B \oplus o_C = \begin{cases} 0, & \text{if } i_A i_B i_C = 000 \\ 1, & \text{if } i_A i_B i_C \in \{011, 101, 110\} \end{cases}$$
```

but no communication (sending of classical or quantum bits) is allowed once A, B, and C receive their inputs. Note that if the inputs are anything else other than the four combinations above, it doesn’t matter what the output is (or we assume that the inputs are always one of the four combinations (000, 011, 101, 110), each occurring with equal probability).

Let’s look at the quantum solution. Suppose A, B, and C each has one qubit $\psi_A$, $\psi_B$ and $\psi_C$, respectively, and the state of the 3-qubit system is the entangled state:

```
$$\frac{1}{2}(|000\rangle - |011\rangle - |101\rangle - |110\rangle)$$
```

which is equivalent to the GHZ state under LU operations – see Aside.

> **Aside:** There could be different possible operations; one is as follows:
> 
> 1. starting with $\frac{1}{\sqrt{2}}(|000\rangle + |111\rangle)$, we apply the operation $H \otimes H \otimes H$:
> 
> $$(H \otimes H \otimes H) \frac{1}{\sqrt{2}}(|000\rangle + |111\rangle)$$
> 
> $$= \frac{1}{\sqrt{2}}(H|0\rangle H|0\rangle H|0\rangle + H|1\rangle H|1\rangle H|1\rangle)$$
> 
> $$= \frac{1}{4}((|000\rangle + |001\rangle + |010\rangle + |011\rangle + |100\rangle + |101\rangle + |110\rangle + |111\rangle))$$