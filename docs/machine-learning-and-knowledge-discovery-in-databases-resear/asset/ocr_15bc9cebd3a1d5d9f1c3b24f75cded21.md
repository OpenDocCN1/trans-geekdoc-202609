# ## 2.1 Symmetric Label Noise

Symmetric Label Noise (SLN) [4,13] assumes that the label of a node is changed with some fixed probability \(\rho\) (and hence retained with probability \(1 - \rho\)). Also, the probability of a label being reassigned to each of the other classes is the same, which is \(\rho/(K - 1)\). Mathematically, if \(y\) and \(y'\) denote true and noisy label respectively, then \(P(y' = n|y = m) = \frac{\rho}{K-1}\), where \(n, m \in \{1, 2, ..., K\}\) and \(m \neq n\). Transition probability matrix for SLN (\(Q_{sln}\)) is given by

```
\[\begin{equation*}\begin{array}{ c } Q_{sln} = \left[ \begin{array}{ c c c c c } 1 - \rho & \frac{\rho}{K-1} & \frac{\rho}{K-1} & \cdots & \frac{\rho}{K-1} \\ \frac{\rho}{K-1} & 1 - \rho & \frac{\rho}{K-1} & \cdots & \frac{\rho}{K-1} \\ \vdots & \ddots & \ddots & \ddots & \vdots \\ \frac{\rho}{K-1} & \cdots & \ddots & 1 - \rho & \frac{\rho}{K-1} \\ \frac{\rho}{K-1} & \frac{\rho}{K-1} & \cdots & \frac{\rho}{K-1} & 1 - \rho \end{array} \right] \\ (1) \end{array}\end{equation*}\]
```

# ## 2.2 Class Conditional Noise

In Class Conditional Noise (CCN) [4,13], the probability with which the label is changed depends on both \(y\) and \(y'\). The probability of a node of class \(m\) being reassigned to class \(n\) is given by \(\rho_{mn}\) (\(P(y' = n|y = m) = \rho_{mn}\)), where \(m \neq n\). So, a node with label \(m\) is flipped with probability \(\rho_m = \sum_{i=1, i \neq m}^K \rho_{mi}\) and the label is retained with the probability \(1 - \rho_m\). The transition probability matrix (\(Q_{ccn}\)) is given by

```
\[\begin{equation*}\begin{array}{ c } Q_{ccn} = \left[ \begin{array}{ c c c c c } 1 - \rho_1 \&\rho_{12} & \rho_{13} & \dots & & \rho_{1K} \\ \rho_{21} & 1 - \rho_2 \& \rho_{23} \& & & \rho_{2K} \\ \vdots & & & \ddots & \vdots \\ \rho_{(K-1)1} & & & 1 - \rho_{K-1} & \rho_{(K-1)K} \\ \rho_{K1} & \rho_{K2} & \dots & \rho_{K(K-1)} & 1 - \rho_K \end{array} \right] \end{array}\end{equation*}\]
```

**Pairwise Noise:** Pairwise Noise (PWN) [13] is a special class of CCN. The motivation behind Pairwise Noise is that one is more likely to mislabel two similar classes. For Pairwise Noise \(\rho_1 = \rho_2 = \dots = \rho_K = \rho\), and the label is flipped to the next label (with probability \(\rho\)). The transition probability matrix \(Q_{pwn}\) is given by

```
\[\begin{equation*}\begin{array}{ c } Q_{pwn} = \left[ \begin{array}{ c c c c c } 1 - \rho \,\&\rho & 0 & \dots & & 0 \\ 0 & 1 - \rho & \rho \, & & 0 \\ \vdots & & & \ddots & \vdots \\ 0 & & & 1 - \rho & \rho \\ \rho & 0 & \dots & 0 & 1 - \rho \end{array} \right] \\ (2) \end{array}\end{equation*}\]
```

Many label noise robust algorithms for graphs have been proposed to tackle existing node label noise. DGNN [6] employs backward loss correction. PIGNN