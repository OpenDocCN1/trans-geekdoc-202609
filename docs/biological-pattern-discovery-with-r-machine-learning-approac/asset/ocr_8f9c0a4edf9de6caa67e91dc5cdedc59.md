detect chemicals from the Raman spectroscopic data [Vyumvuhore, et al., 2014; Acikgoz, et al., 2018]. The Whittaker-Henderson algorithm is a typical regularised LSE variant for the baseline estimation [Whittaker, 1923; Henderson, 1924; Taylor, 1992].

# 5.3 The Whittaker-Henderson algorithm

The Whittaker-Henderson algorithm (WH) is a special case of the ridge linear regression algorithm (RLR). The main concept and implementation of RLR has been introduced in the last chapter. The error term used in RLR is named as the fidelity in WH. Suppose a spectrum is expressed as a vector of $n$ entries, $\mathbf{s} = (s_1, s_2, \dots, s_n)$. Each entry of this vector is called a wave intensity or simply intensity. As aforementioned, such intensity may not represent a real signal or a peak of a chemical. It is instead a mixture between a baseline intensity and a signal intensity, i.e., $s_i = b_i + e_i$, where $b_i$ stands for the baseline intensity contained in the $i^{th}$ intensity and $e_i$ stands for the distance between the $i^{th}$ signal intensity $s_i$ and the $i^{th}$ baseline intensity $b_i$. Such a distance is also called an error. The vector-matrix expression of this relationship is $\mathbf{s} = \mathbf{b} + \mathbf{e}$, where three values are expressed by three vectors. Both $\mathbf{b}$ and $\mathbf{e}$ are unknown. In addition to the fidelity definition, which is $d_i = b_i - b_{i-1}$. A vector $\mathbf{d}$ is used to represent all the smoothness values. WH has employed an objective function by introducing a regularisation constant $\lambda$ to make a balance between the fidelity (regression error) and the smoothness. The WH objective function is defined as below,

```
$O = \mathbf{e}^T\mathbf{e} + \lambda\mathbf{d}^T\mathbf{d} \quad (5.1)$
```

The LSE optimisation of this objective function leads to the solution of an unknown baseline below,

```
$\mathbf{b} = (\mathbf{I} + \lambda\mathbf{d}^T\mathbf{d})\mathbf{s} \quad (5.2)$
```

Figure 5.1 shows an example based on a simulated spectrum, where the baseline ($\mathbf{b}$) is expressed by a solid line and the spectrum ($\mathbf{s}$) is expressed by a dotted line. It can be seen that if the baseline has very