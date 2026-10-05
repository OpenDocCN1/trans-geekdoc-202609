
# Biological Pattern Discovery with R

The R package for RBFNN is caret,

```
train(formula,data,method=`gaussprRadial`)
```

Table 3.9 shows the confusion matrix of a RBFNN model constructed for the seeds data [Ajaz and Hussain, 2015]. Figure 3.27 shows the ROC curve of this model.

Table 3.9. The confusion matrix of the RBFNN model constructed for the seeds data.

| A | B | % |
|---|---|---|---|
| A | 61 | 10 | 85.9 |
| B | 8 | 57 | 87.7 |
| % | 88.4 | 85.1 | 85.7 |

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_138_0.png)

## 3.6.3 The bio-basis function neural network algorithm

Most machine learning algorithms except the decision tree algorithms are used to model numerical data. Therefore, how to deal with nonnumerical variables as the amino acids of a sequence data requires careful experimental design.

One popularly used approach is the binary encoding of the amino acids or the nucleic acids in peptides [Wu, et al., 1995; Kawabata and Doi, 1997; White and Seffens, 1998]. With this approach, each nucleic acid is encoded by a four-bit binary vector and each amino acid is encoded by a 20-bit binary vector. For instance, the amino acid alanine (A) is expressed by 000000000 000000001 and the amino acid cysteine (C) is expressed by 00000000 000000010. This encoding method is simple and straightforward. However, it is not biologically sound because the mutation rate between the nucleic acids or between the amino acids in peptides may not be a constant.

Based on the principle of the kernel method, the principle of using a mutation matrix to quantify how similar two sequences are, which is used in sequence homology alignment can be considered to measure the similarity between peptides as well [Holm and Sander, 1996]. For instance, to align two protein sequences, an amino acid mutation matrix such as the Dayhoff matrix [Dayhoff and Schwartz, 1978] has been considered [Lipman, et al., 1989]. This idea has led to the development of the algorithms which employ a mutation matrix for protease cleavage pattern discovery.

A mutation is normally derived based on a large number of protein sequences. A substitution in a mutation matrix actually represents the mutation rate between two amino acids. A mutation matrix is commonly derived through investigating thousands of sequences within a biological family. This means that a mutation matrix is perhaps more biologically sound and robust to measure the similarity between peptides.

Here are three factor X protease cleaved peptides, $x_1$=IEGRT, $x_2$=IEGRI and $x_3$=IEGR. When using the binary encoding approach, a binary vector for each amino acid in a peptide has only one entry as one, leaving other entries as zeros. Therefore, the pairwise distance between a pair of peptides actually depends on the difference of residues in these peptides. The pairwise distance between these sub-sequences is always one because one residue is occupied by different amino acids. However, the pairwise homology score (similarity) between these sub-sequences will not be a constant. Table 3.10 shows a partial Dayhoff amino acid mutation matrix. Suppose this mutation matrix is used to measure the pairwise-similarity between these three-sequences. The partial similarity between $x_1$ and $x_2$ for the fifth residue (between the amino acid T and I) is -2. The partial similarity between $x_1$ and $x_3$ is -4. The partial similarity between $x_2$ and $x_3$ for the fifth residue (between the amino acid T and the amino acid D) is -6. It can be seen that they are not constants at all. This shows a very important concept that the binary encoding approach may not be able to reflect the true biological relationship between peptides.

## Biological Pattern Discovery with R

Table 3.10. The partial Dayhoff amino acid mutation matrix.

| | D | I | T |
|---|---|---|---|
| D | 7 | -6 | -4 |
| I | -6 | 8 | -2 |
| T | -4 | -2 | 7 |

### 3.6.3.1 The bio-basis function neural network algorithm

The bio-basis function neural network (BBFNN) has been developed based on this idea, i.e., mapping a non-numeric peptide space to a numerical space which is supported by the homology alignment scores between peptides using an amino acid mutation matrix [Thomson, et al., 2003; Yang and Berry, 2004; Berry, et al., 2004; Yang and Chou, 2004b; Senawongse, et al., 2005; Yang, et al., 2005; Yang, 2005b; Yang, 2005c; Yang and Thomson, 2005; Sidhu and Yang, 2006; Yang, et al., 2006; Yang and Hammer, 2007; Maji and Das, 2010; Maji and Das, 2010b]. Suppose a peptide is denoted by $x_n$ and its functional status is denoted by $y_n \in [0,1]$, which is either functional (cleaved) or non-functional (non-cleaved). Suppose set of cleaved peptides is denoted by $\Omega^+$ and protease cleavage discovery is a discrimination problem. It is well-understood that only cleaved peptides will show the amino acid composition trend. Moreover, a basis used in function network mode is served as supporting coordinate in kernel space. Such a supporting coordinate must be composed of rich information. Non-cleaved peptides are certainly non-informative. Therefore, only cleaved peptides are employed as bio-bases in BBFNN. Suppose a bio-basis, $s_k$, which is a cleaved peptide, is denoted by $B(x_n, s_k)$, which stands for the alignment between $x_n$ and $s_k$ and is calculated using mutation matrix. It is thus assumed that a cleaved peptide $(x_n \in \Omega^+)$ will show a high homology score (similarity) with some bio-basis peptides because they belong to the same category and should show similar biological property.

## Protease Cleavage Discovery

On the other hand, a non-cleaved peptide ($x_n \in \Omega^-$) will show a small homology score (similarity) with the bio-basis peptides. The non-cleaved peptides will not maintain any amino acid composition pattern or trend, but random distribution. In other words, each amino acid has the same probability to appear at each residue of non-cleaved peptide. Therefore, it is expected that the homology scores of cleaved peptides and the homology scores of non-cleaved peptides should show different densities. Based on the above analysis, BBFNN is designed in the following ways. Suppose there are $K$ bio-bases. A non-numerical peptide is mapped to a $K$-dimensional space, i.e., $B(x_n, s_1), B(x_n, s_2), \dots,$ and $B(x_n, s_K)$. A linear function is generated for combining bio-basis functions through weighting parameters $w_k$:

```
$$\sum_{k=1}^K w_k B(x_n, s_k) \quad (3.42)$$
```

It is expected that this linear combination of the bio-basis functions will have bimodal distribution if weights $(w_k)$ have been well-estimated. Such a bimodal distribution is expected to fit the classification of peptides in terms of peptide status $(y_n)$. A linear classifier can then be built in the $K$-dimensional bio-basis function space:

```
$$y_n = \sum_{k=1}^K w_k B(x_n, s_k) \quad (3.43)$$
```

Suppose $X$ is a collection of peptides and $S$ is a matrix of all peptides mapped to this $K$-dimensional bio-basis function space. The matrix $S$ has $N$ rows for $N$ peptides and $K$ columns for $K$ bio-bases. A target vector of classification labels is denoted by $y$:

```
$$y = (y_1, y_2, \dots, y_N)^T \quad (3.44)$$
```

Finally, a weight vector is represented by $w$:

```
$$w = (w_1, w_2, \dots, w_K)^T \quad (3.45)$$
```

Based on the above vector-matrix notation of data, a BBFNN model is defined as below, where $B(X)$ stands for the transformation using the bio-basis peptides:

```
$$\hat{y} = Sw + e = B(X)w + e \quad (3.46)$$
```

A simple implementation of BBFNN is to use a maximum likelihood approach of a logistic regression model to estimate $w$. The sigmoid function is used for squashing $\hat{y}$ into the interval between zero and one:

```
$$\pi = \frac{1}{1 + e^{-\hat{y}}} \quad (3.47)$$
```

A Bernoulli likelihood function is generated based on the logit vector $y$:

```
$$\mathcal{L} = \sum_{n=1}^{N} \pi_n^{y_n} (1 - \pi_n)^{1-y_n} \quad (3.48)$$
```

Maximising this likelihood can estimate $w$. Based on the estimated model parameters $\hat{W}$, which is the estimated version of $w$, a constructed BBFNN model can be used to scan a long protein sequence to identify potential protease cleavage sites for a specific protease or posttranslational sites for a specific chemical.

BBFNN has been implemented in different versions. For instance, a Bayesian BBFNN and an orthogonal kernel machine.

### 6.6.3.2 The Bayesian BBFNN algorithm

The Bayesian BBFNN is an extension to BBFNN. The aim of developing the Bayesian BBFNN is for generating a more robust BBFNN modelling algorithm for protease cleavage peptide data analysis [Yang, 2005b]. Suppose an error vector is denoted by $e = (e_1, e_2, \dots, e_N)^t$, a linear combination of $K$ bio-basis functions is defined as below:

```
$$\hat{y}_n = \sum_{k=1}^{K} w_k B(x_n, s_k) = y_n - e_n \quad (3.49)$$
```
