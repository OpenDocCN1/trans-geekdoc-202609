
# Biological Pattern Discovery with R

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_400_0.png)

Fig. 8.21. The distribution of the target values of a simulated data set using GP to solve a function approximation problem.

After the 13th cycle, the stabilisation criterion was satisfied and the learning process was terminated for this function approximation problem. The elite RPN chromosome was $zx-zy+$, which was exactly what was expected. Figure 8.22(a) shows how the sum of the squared errors evolved with the learning cycle and Figure 8.22(b) shows how the fitness measurement evolved with the learning cycle.

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_400_1.png)

Fig. 8.22. (a) The sum of the squared errors evolved with the learning cycle. (b) The fitness measurements evolved with the learning cycle.

Figure 8.23 shows how the predicted values were correlated with the target values based on the top model in the elite set. It can be seen that two sets of values have an extremely high correlation.

# Optimised Peptide Pattern Discovery

# 387

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_401_0.png)

Fig. 8.23. The correlation between the target values and the predicted values from the best model generated using the GP learning.

Figure 8.24 shows the correlation between the target values and the predicted values from two non-elite models. In Figure 8.24(a), it can be seen that the positive correlation was still there for the first non-elite model from the non-elite set. The first non-elite model was a model which was at the top of non-elite models after sorting the RPN chromosomes. However, Figure 8.24(b) shows a completely failed model (the last non-elite model), where there was no correlation between the target values and the predicted values.

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_401_1.png)

Fig. 8.24. (a) The correlation between the target values and the predicted values from the first non-elite model (zz-*) generated using the GP learning. (b) The correlation between the target values and the predicted values from the last non-elite model (zx-z*zy+) generated using the GP learning.

## 8.4 Factor X protease protease interplay

Factor Xa protease cleavage data were similar to all other protease cleavage data, which were composed of two types of peptides, i.e., 122 cleaved peptides and 359 non-cleaved peptides [Yang, et al., 2006]. Each peptide was a short protein amino acid sequence. Factor X peptide was denoted by $R_4R_3R_2R_1R'_1$. The cleavage happened between $R_1$ and $R'_1$. Each peptide of length $d$ was denoted by a vector $x \in C^d$, where $\mathcal{C}$ is the set of the amino acids. In most protease cleavage analysis projects, all peptides had the same length. A set of peptides was denoted by $\Omega = \Omega_A\Omega_B$, $\Omega_A$ was used to denote a set of the non-cleaved peptides and $\Omega_B$ was used to denote a set of the cleaved peptides.

Before starting the description of how to use GP to model factor X protease cleavage data, the first thing was how to quantify the similarity between residues, which were the amino acids, from two peptides. The idea of bio-basis function [Thomson and Yang, 2002; Thomson et al., 2003] was used to measure how a rule fit a data point (an amino acid). Suppose the $m^{th}$ residue of a peptide $x$ was denoted by $x_m$ and the $m^{th}$ residue in a GP rule was denoted by $r_m$. The fitness was defined as below, where $\pi()$ was the mutation probability between two acids based on a mutation matrix,

$$\pi(x_m, r_m) \quad (8.11)$$

Suppose a number of residues between a peptide and a rule were involved in decision-making. The min-max function was developed for this kind of analysis [Yang, et al., 2003]. The min function was defined as below, where x was a peptide and r was a GP rule,

$$\psi^+(\mathbf{x, r}) = \min\{\pi(x_m, r_m)\} \quad (8.12)$$

To express the min function, a RPN chromosome was expressed as below, where $r_m$ was the $m^{th}$ residue of the GP rule and $c_m$ was the amino acid used by $r_m$.

$$\psi^+(\mathbf{x, r}) = \prod \{(r_m c_m)\} + \quad (8.13)$$

Using the RPN chromosome to represent a rule, the residue indexes in a peptide were encoded using the letters, such as $a, b, c$, etc. For instance, an example of the min function was $(aYdS)^$. In this example, $a$ and $d$ were the first and the fourth residues of peptide $Y$ and $S$ were two amino acids used in this rule for two residues, respectively. The fitness of this rule was calculated in the following way. Two similarities were first calculated. They were the similarity between the first residue of a peptide x and the amino acid S, i.e., $\pi(x_1, S)$ as well as the similarity between the fourth residue of a peptide and the amino acid Y, i.e., $\pi(x_4, Y)$. The fitness was calculated using the smaller similarity,

$$\psi^+(\mathbf{x}, \mathbf{r}) = \min\{\pi(x_1, S), \pi(x_4, Y)\}$$

The max function was defined as below,

$$\psi^&(\mathbf{x}, \mathbf{r}) = \max\{\pi(x_m, r_m)\} \quad (8.14)$$

The RPN chromosome expression for this function was shown as below,

$$\psi^&(\mathbf{x}, \mathbf{r}) = \{[\(r_m c_m)]\} + \& \quad (8.15)$$

Suppose an example of the max function was $(bReK)$. In this example, b and e were the second and fifth residue of peptide x while R and K were amino acids used in this rule for two residues, respectively. The fitness of this rule was calculated in the following way. Two similarities were first calculated. They were the similarity between the second residue of a peptide x and the amino acid R, i.e., $\pi(x_2, R)$ as well as the similarity between the fifth residue of a peptide and the amino acid K, i.e., $\pi(x_5, K)$. The fitness was calculated using the greater similarity,

$$\psi^&(\mathbf{x}, \mathbf{r}) = \max\{\pi(x_2, R), \pi(x_5, K)\}$$

The min-max function allowed operations to more than two units. For instance, another example of the min function was $(cH)(bQaGcYdG))$. In this rule, the second subunit (eFbL) involves two residues, but the fourth subunit (bQaGcYdG) involves four residues as variables. The next question was the fitness of each RPN rule formulated using the min-max function. Because analysing the factor Xa protease cleavage data for pattern discovery was a classification problem, therefore equations (8.8) and (8.9) were used for the fitness analysis. The pool size was 100, and the value of $\alpha$ was 0.9 for the factor Xa protease pattern discovery. The mutation, dual-chromosome crossover, and single-chromosome crossover operations were randomly selected with an equal probability during a learning process. The learning process was terminated when the top fitness measurement was unchanged for more than 20 cycles or maximum learning cycle. Two mutation matrices were used to measure the similarity between amino acids and were used for a comparison. One was the Dayhoff mutation matrix [Dayhoff and Schwartz, 1978] and the other was the BLOSUM62 mutation matrix [Henik and Henikov, 1992].

In addition to three breeding operators, a special treatment as a supplement to the old approach [Yang, et al., 2003] was also introduced. This treatment was used to ensure a sufficient diversity within a population so as to promote the breeding performance, i.e., generating more diverse chromosomes to allow new and better ones to be generated through

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_404_0.png)

Fig. 8.25. A tree structure of a complicated RPN chromosome for the min-max function.
