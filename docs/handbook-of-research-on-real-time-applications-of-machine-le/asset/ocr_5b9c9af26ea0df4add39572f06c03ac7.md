fails, it is assumed that node 1 fails, so the sources file M can be restored by (14) that fastly locate the node other than node 1 and download its first block {X_2,X_3,.. .., X_n'}, and downloading next its second block Y_j by any surviving node j(j ≠ 1). Whenever i (i ≤ [n ] ) nodes fail, the source file M can be recovered by quickly locating the other n – i nodes and download the first block {X_i1,X_i2, ..., X_i,n-1 }, and then download the second block Y_j1, Y_j2, ... Y_ji from any i surviving nodes j_1, j_2... .., j_i (j_i > i, l = 1, 2, ... , i). Each regeneration code has three parts, namely, data domain X_i', check domain Y_i', and timestamp T_i', as. As shown in Algorithm 1, the design of distributed storage regeneration code, when one node fails, the source file can be restored by other surviving nodes.

Creation of matching flow graph information for block chain networks (Fig. 4), comprehend structure of fault-tolerant local regenerative codes in block chain networks as neighbouring local codes in fault-tolerant local regeneration codes recover from faulty local codes. Industrial block chain networks have nodes that upload data to the network and damages in network’s node data triggers data recoveries that completely restore nodes’ data by downloading relevant data Xi, Yi, Ti from surviving nodes.

# Algorithm 1.

```
Input:
Source file M, non-singular matrix U, V ;
Output:
Coding matrix G;
1: Divide souce file M into n data blocks
X_i = x_i1', x_i2', ... , x_in', i = 1, 2, ... , n;
2: for i ≤ i, j ≤ n do
3: Compute A_ij = (Vi)'U_j + c_ij E;
4: end for
5: Compute Y_i = X_i A_i1 + X_i A_i2 + ... + X_i A_in;
6: Record T_i to get coding vector B_i = X_i', Y_i', T_i';
7: Generate code B = B_1, B_2, ... , B_n;
8: return Coding matrix G.
```