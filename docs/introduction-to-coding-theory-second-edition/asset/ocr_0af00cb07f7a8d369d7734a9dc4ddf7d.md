with 12 columns and entries from a 16 set. Each row corresponds to a test run.

One frequently used approach is the following: choose the array of test runs such that, for every pair (or for every triple) of parameters, each possible combination of parameter values does actually occur at least once (is covered). Generalizing from pairwise or triplewise covering to t-wise covering for arbitrary t, this leads to the following definition:

# 4.9 Definition.

*A covering array of strength t (parameters CA(N; t, n, q)) is an array with N rows and n columns, with entries from a q-set, such that in the projection onto any t columns each possible t-tuple of entries appears at least once (is covered).*

In order to save time and money in software testing, we wish to construct covering arrays, most often of strength 2 or 3, with a minimum number of rows.

It is clear that N ≥ q^t, with equality if and only if there is an OA₁(t, n, q); in other words, covering arrays are generalizations of orthogonal arrays of index 1. In the case of the parameters considered above, we are lucky, as RS(2,16) and RS(3,16) yield (after throwing away four columns) OA₁(2,12,16) and OA₁(3,12,16), respectively.

Typically, we will not be that lucky. For example, in the binary case q = 2, Reed-Solomon codes will not help us at all. Here is an (optimal) CA(10; 3, 5, 2) (see Chateauneuf and Kreher [47]):

0 0 0 0 0
1 1 1 1 1
1 0 0 1 1
0 1 1 0 0
1 1 0 0 1
0 0 1 1 0
1 1 0 1 0
0 0 1 0 1
1 0 1 0 0
0 1 0 1 1

Most diverse methods are being used for the construction of covering arrays, from combinatorial design theory and coding theory to heuristic search methods. Also, various names are employed, from qualitatively independent partitions (Rényi [174]) to t-independent sets and universal sets (see Goldreich [95]).