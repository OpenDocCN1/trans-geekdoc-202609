# Protease Cleavage Pattern Discovery

[Karatsuba and Ofman, 1963]. With this principle, a data space with a mixture of data points of different classes is gradually divided into subspaces using some classification or partitioning rules. It is also called the binary search because the use of every partitioning rule divides a space into two subspaces [Shapiro and Haralick, 1982]. This kind of learning strategy is still in use for biological/medical pattern analysis, such as the fast DNA copy number data analysis [Ruan, et al., 2019].

Figure 3.37 shows the use of this binary search strategy. In Figure 3.37(a), either the partitioning rule $y=2$ or the partitioning rule $y=0$ can divide the whole space into two parts, i.e., two subspaces. After each partition, the data points distribute in the upper panel subspace and others distribute in the lower panel subspace. The classification performance of these two partitions depends on the how data points are distributed. Obviously, the upper panel in Figure 3.37(a) shows a great mixture of data points from two classes when using the partitioning rule $y=0$. But the partitioning rule $y=2$ in Figure 3.37(a) generates two subspaces which are more clean or pure to a single class, i.e., either subspace has a very limited mixture of data points from two classes.

In Figure 3.37(b), the partitioning rule $y=0$ certainly does not help to separate two classes of data points into two pure subspaces. Two more partitioning rules $x=0$ and $x=3$ are therefore included into the decision-making system in addition to the partitioning rule $y=0$ to make four subspaces for the classification of the data points. After this data space has been well-defined into four subspaces, data points can be classified.

![](bbox=[0.193, 0.656, 0.806, 0.876])

Fig. 3.37. An illustration of the rule of divide and conquer.