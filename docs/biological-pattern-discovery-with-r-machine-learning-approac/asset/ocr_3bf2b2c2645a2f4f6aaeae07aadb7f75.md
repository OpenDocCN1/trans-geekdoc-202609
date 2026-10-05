# Optimised Peptide Pattern Discovery 371

GA employ the elite candidates (the candidates with smaller regression errors) as ancestors to breed new candidates, i.e., the descendants. Representatively, a breeding process in GA is to generate new chromosomes based on the existing elite chromosomes. There are mainly two breeding operators which have been widely used in GA. They are the mutation operator and the crossover operator.

The mutation operator is to generate a new chromosome based on a single elite chromosome. For a binary chromosome shown in Figure 8.3, a mutation operator is to turn a binary value around. For instance, for the chromosome (suppose it is an elite chromosome) shown in the upper panel of Figure 8.3, a mutation operation may generate a new chromosome shown in Figure 8.4, where $x_5$ and $x_{10}$ are removed by switching off two ones to zeros and $x_1$ is included by switching a zero to one from the old chromosome, leading to a new chromosome for a new system description, which is $f(x_1, x_3, x_8)$.

![](bbox=[0.303, 0.452, 0.696, 0.483])

Figure 8.4. A new chromosome mutated from the upper chromosome from Figure 8.3.

The crossover operator happens to two elite chromosomes to generate two new chromosomes. For instance, two chromosomes shown in Figure 8.3 can be used to generate two new chromosomes through the crossover operation, supposing they are the elite chromosomes. To do the crossover operation for these two elite chromosomes, a cutting point is required at first, which is commonly randomly. Suppose two chromosomes are labelled by $A$ and $B$. The left part of the cutting point in chromosome $A$ is merged with the right part of the cutting point in chromosome $B$ to generate one new chromosome. The left part of the cutting point in chromosome $B$ is merged with the right part of the cutting point in chromosome $A$ to generate another new chromosome.

For instance, a randomly selected cutting point is between the variables $x_5$ and $x_6$ as shown in Figure 8.5. After a crossover operation on these two elite chromosomes based on the cutting point, two new chromosomes are generated. Two resulting chromosomes for two new system descriptions are $f(x_3, x_5, x_7)$ and $f(x_2, x_4, x_8, x_{10})$.