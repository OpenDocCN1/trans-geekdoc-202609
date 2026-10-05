# Biological Pattern Discovery with R

branch node B which employed the second partitioning rule, i.e., Petal.Width<1.75. This partitioning rule generated one subspace, which was composed of 54 Versicolor flowers and five Virginica flowers. Therefore based on this node (in a leaf), the probability of classifying a flower to the Versicolor class was 91% and to be the Virginica class was 9%. The other subspace was composed 46 Virginica flowers and one Versicolor flower. On this leaf node, the probability of classifying a flower to the Virginica class was 98% and to be the Versicolor class was 2%.

```
root 150 100 setosa (0.33 0.33 0.33)
A) Petal.Length<2.45 50 0 setosa (1 0 0) *
   Petal.Length>2.45 50 versicolor (0 0.5 0.5)
B) Petal.Width<1.75 54 5 versicolor (0 0.91 0.99) *
   Petal.Width>1.75 1 virginica (0 0.92 0.98) *
```

# 3.6.4 The C50 algorithm

The earliest version of decision tree was Leicester Dichotomous 3 (ID3), which was developed by Ross Quinlan [Quinlan, 1986]. ID3 was updated to C4 [Quinlan, 1993]. C5.0 (R package C50) is the most recently updated version. The basic measurement used in this algorithm for recursively partitioning a data space is the information gain. One of the best features of C50 is its wonderful graphical presentation. The R function of C50 is shown below

C5.0(formula,data,trials)

For instance, Figure 3.41 shows an example of a C50 tree generated for the Iris data.

![](bbox=[0.277, 0.693, 0.722, 0.873])

Fig. 3.41. An unpruned C50 tree constructed for the Iris data.