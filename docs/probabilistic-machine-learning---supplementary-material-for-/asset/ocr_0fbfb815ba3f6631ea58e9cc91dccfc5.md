![](bbox=[0.345, 0.095, 0.655, 0.265])

Figure 4.3: Extension of Figure 4.2 to two loci, showing how the switching variables are spatially correlated. This is indicated by the $S_{ij}^m \rightarrow S_{i,j+1}^m$ and $S_{ij}^p \rightarrow S_{i,j+1}^p$ edges. Adapted from Figure 3 from [FGL00].

$G_{ij}^m$ and $G_{ij}^p$, one inherited from $i$'s mother (maternal allele) and the other from $i$'s father (paternal allele). Together, the ordered pair $\mathbf{G}_{ij} = (G_{ij}^m, G_{ij}^p)$ constitutes $i$'s hidden **genotype** at locus $j$.

Obviously we must add $G_{ij}^m \rightarrow X_{ij}$ and $G_{ij}^p \rightarrow P_{ij}$ arcs representing the fact that genotypes cause phenotypes. The CPD $p(P_{ij}|G_{ij}^m, G_{ij}^p)$ is called the **penetrance model**. As a very simple example, suppose $P_{ij} \in \{A, B, O, AB\}$ represents person $i$'s observed bloodtype, and $G_{ij}^m, G_{ij}^p \in \{A, B, O\}$ is their genotype. We can represent the penetrance model using the deterministic CPD shown in Table 4.2. For example, A dominates O, so if a person has genotype AO or OA, their phenotype will be A.

In addition, we add arcs from $i$'s mother and father into $G_{ij}^{m/p}$, reflecting the **Mendelian inheritance** of genetic material from one's parents. More precisely, let $\mu_i = k$ be $i$'s mother. For example, in Figure 4.2(b), for individual $i=3$, we have $\mu_i = 2$, since 2 is the mother of 3. The gene $G_{ij}^m$ could either be equal to $G_{kj}^m$ or $G_{kj}^p$, that is, $i$'s maternal allele is a copy of one of its mother's two alleles. Let $S_{ij}^m$ be a hidden switching variable that specifies the choice. Then we can use the following CPD, known as the **inheritance model**:

```
p(G_{ij}^m | G_{kj}^m, G_{kj}^p, S_{ij}^m) = \left\{ \begin{array}{ll} \mathbb{I} \left( G_{ij}^m = G_{kj}^m \right) & \text{if } S_{ij}^m = m \\ \mathbb{I} \left( G_{ij}^m = G_{kj}^p \right) & \text{if } S_{ij}^m = p \end{array} \right. (4.5)
```

We can define $p(G_{ij}^p | G_{kj}^m, G_{kj}^p, S_{ij}^p)$ similarly, where $\pi = p_i$ is $i$'s father. The values of the $S_{ij}$ are said to specify the **phase** of the genotype. The values of $G_{i,j}^m, G_{i,j}^p, S_{i,j}^m$ and $S_{i,j}^m$ constitute the **haplotype** of person $i$ at locus $j$. (The genotype $G_{i,j}^p$ and $G_{i,j}^m$ without the switching variables $S_{i,j}^p$ and $S_{i,j}^m$ is called the “unphased” genotype.)

Next, we need to specify the prior for the root nodes, $p(G_{ij}^m)$ and $p(G_{ij}^p)$. This is called the **founder model**, and represents the overall prevalence of difference kinds of alleles in the population. We usually assume independence between the loci for these founder alleles, and give these root nodes uniform priors. Finally, we need to specify priors for the switch variables that control the inheritance process. For now, we will assume there is just a single locus, so we can assume uniform priors for the switches. The resulting DGM is shown in Figure 4.2(b).

# 4.1.2.2 Multiple loci

We get more statistical power if we can measure multiple phenotypes and genotypes. In this case, we must model spatial correlation amongst the genes, since genes that are close on the genome are likely to be coinherited, since there is less likely to be a crossover event between them. We can model this by imposing a two-state Markov chain on the switching variables $S$'s, where the probability of switching state at locus $j$ is given by $\theta_j = \frac{1}{2}(1 - e^{-2d_j})$, where $d_j$ is the distance between loci $j$ and $j+1$. This is called the **recombination model**. The resulting DGM for two linked loci in Figure 4.3.