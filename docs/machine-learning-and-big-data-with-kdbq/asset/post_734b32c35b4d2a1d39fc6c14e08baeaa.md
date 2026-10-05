
## 27.2.2 Kernels and Metrics for Proteins

We proceed with proteins and define the proximity between the two kernels. The proximity measure aims to capture the similarity between proteins and to quantify the similarity of two proteins. We employ a measure based on the comparison of substrings of proteins; see Leslie et al. (2004). The motivation is as follows. The protein is represented as an ordered sequence of letters. We identify all substrings of chosen length in the protein and count their occurrence. The two proteins are then compared on the matching substrings.

Decomposing a protein into substrings means that we form a space of all substrings as a new feature space and represent a protein in the new feature space by counting the presence of substrings in the protein. If $M$ building blocks of the protein ($M$ letters) and we choose substrings of length $N$, the dimension of the feature space is $M^N$, which for any practical considerations are substantial. We do not aim to keep the representation explicitly in memory but rather able to calculate it on request.

Let us denote the set of all substrings as $L(M;N)$. Further, for the protein $P$ we define a vector $l=\{l_i\}_{L(M;N)}$, where $l_i$ is a non-negative integer which denotes how many substrings of type $i$ are contained within the protein $P$. The vector is $M^N$-dimensional. Then, for a pair of proteins $P_1$ and $P_2$, we define the inner product using the vectors as:

```
$$\langle P_1, P_2\rangle = \langle l_1, l_2\rangle,$$ (27.9)
```

where the inner product is calculated from the vectors $l_i$, which count occurrences of substrings.
The inner products themselves can be arranged into kernels. Methods like Support Vector Machines, among others, can directly work with such kernels. In the following, we derive the distance between two proteins using inner products as:

Having a measure at hand, we can employ the nearest-neighbour methods to make inference for proteins. In the following, we define a simplified version of the nearest-neighbour classifier using the inner-product based distance.

It is important to point out that our objective is not to capture the full vector from $L(M;N)$. The dimensionality is so large that this task would be practically infeasible. More importantly, it is not necessary. We can effectively work with those substrings which are only present in the proteins at hand.

## 27.2.3 Implementation of Inner Products and Nearest Neighbours Principles

We implement the matching based on an inner product for proteins data. We start by creating a sample data set of 50 proteins. We assign a random class to every protein. This will be a proxy for the problem we may face in the laboratory, where the class is, for instance, the instance of a particular disease. The data are stored in the table proteinTab:

```
proteinTab: ([ protein: .quantQ.infth.getProtein[20;40;20]] each til 50;
      classRisk:5072);
proteinTab
```

| protein | classRisk |
| :--- | :--- |
| "CIFTPPMMSINKQJMHJDFJI" | 1 |
| "LRTHFRLPRKDDQLRSNASGBPEFBTFHTCCNG" | 1 |
| "LTRBHMJIRTBSPLJQQBFEGL" | 0 |
| "KSNOLQQQHIERTJAPHTDRONTSQSDKP" | 0 |
| "CFNAATOBSIKHHJLEAPSTALMRFQHINJLDLP" | 1 |
| "EFCNSTOBCOBKHJAMLSTDNNOQQQBOIPORC" | 1 |
| "DDHDAM.JCESESOFRDJDAM" | 1 |
| "MPCCQJRJKAFQEKBLJGNNPQPRPEEELEBAIL" | 1 |
| "EMMOLFFJJAODQGFELMFRIBLIF" | 1 |
| "PNRNETHKFGGBFCQBINILLIQOEHRB" | 1 |

First, we define a function which extracts substrings of length N from the provided protein. We need to remember that the protein is an ordered array of letters. The function returns an array of substrings as are sequentially extracted from the array without any filtering:

```
quantQ.infth.proteinSubstring([p;N])
// p - protein
// N - length of substring
// return all substrings of length N
// [[dict] dict[`strings`];dict[`strings`],enlist 3*dict[`protein`];dict[`n//      protein]=1_dict[`protein`];dict( /)]
// [[x;N] N=count x[protein];[N];strings`protein`((());p)][`strings
//]];
```

and apply it to the first entry of proteinTab table:

```
"CIFTPPMMSINKQJMHJDFJI"
```

The decomposition results:

```
quantQ.infth.proteinSubstring[exec first protein from proteinTab;3]
```

```
("(\CIF";"IFT";"FTP";"TPP";"PPM";"PMS";"MSI";"SIN";"INK";"NK";"QQQ";"QQM QMJ";"MJH";"JHD";"HDF";"DFJ";"FJI")
```

The array of substrings itself can contain repeated patterns. We are further interested in knowing the number of occurrences for every unique substring. Thus, we create another simple function group which creates the substrings and a dictionary with values corresponding to its occurrence rate

```
.quantQ.infth.proteinGetFeatureVector{{[substrings}
// substrings outcome of .quantQ.infth.proteinGetSubstring function
// returns the vector of features as dictionary of substrings and its occurrence
(::*) [group substrings];
};
```

The function takes as argument the outcome of proteinGetSubstring function:

```
.quantQ.infth.proteinGetFeatureVector[.quantQ.infth.proteinGetSubstring[
    exec first protein from proteinTab|3];
("CIF";"IFT";"FTP";"TPP";"PPM";"MSI";"SIN";"INK";"NKQ";"QQQ";"QQM QMJ";"MJH";"HDE";"DFJ";"FJI")1j, 1j, 1j, 1j, 1j, 1j, 1j, 1j, 1j, 1j, 1j, 1j, 1j, 1j;
```

We can proceed with the definition of the inner product. The inner product will work with the substrings present in either of the two proteins. We need vastly subspace of L(I;M;N), which makes the entire calculation numerically feasible.

```
.quantQ.infth.proteinInnerProduct:[[p1;p2;N]
// p1 -- protein 1
// p2 -- protein 2
// N -- length of substring
// calculate vector of features for both proteins
d1::quantQ.infth.proteinGetFeatureVector[.quantQ.infth.
    ->proteinGetSubstring[p1;3]];
d2::quantQ.infth.proteinGetFeatureVector[.quantQ.infth.
    ->proteinGetSubstring[p2;3]];
// return inner product
exec (f*d1)-(ALG07)*/f*d2 from ([substring: key d1]; value d1) uj ([
    substring: key d2]; value d2);
```

and calculate the inner product between the two rows of proteinTab table.

```
.quantQ.infth.proteinInnerProduct[exec first protein from proteinTab;exec
first 1_protein from proteinTab|3];
```

There is no overlap between the two proteins. This is likely as we created completely random proteins and given that we use as building block 20 letters of the alphabet.

Finally, we can define the measure of distance as defined in (27.10). The measure employs the inner products as implemented in innerProduct.

```
.quantQ.infth.proteinDistance:[[p1;p2;N]
// p1 -- protein 1
// p2 -- protein 2
// N -- length of substring
// return measure
quantQ.infth.proteinInnerProduct[p1;p1;N]+quantQ.infth.
->proteinInnerProduct[p2;p2;N]-
2.0.*quantQ.infth.proteinInnerProduct[p1;p2;N];
```

The function returns the metrics of distance, which can be used to compare any two proteins:

```
.quantQ.infth.proteinDistance[exec first protein from proteinTab;exec
-> 1_protein from proteinTab;3]
```

which can be compared to a distance measured between two identical proteins:

```
.quantQ.infth.proteinDistance[exec first protein from proteinTab;exec
-> protein from proteinTab;3]
```

The illustration confirms the notion of measure: two identical proteins have zero distance between themselves while two distinct have non-zero positive distance. Let us stress that this is just an illustration, though. We would need medical background to assess whether the distance has real medical sense as well.

Let us continue with our example and sketch the path of how to employ the nearest-neighbors algorithm to classify a new protein using the training sample. We start with defining an out-of-sample protein. Since we want to have one which is close to the existing proteins in our training sample, proteinTab, we create the new protein by random re-shuffling of a selected protein from the training sample. Below, we create a simple query to perform an activated switch of blocks for a protein:

```
pOut: ((perm:first[7floor 0.5*count[x]]; raze (neg[perm] = x; perm neg[
-> perm_x; perm x == x ))/5);exec first protein from proteinTab;)
```

where the new out-of-sample protein reads

> "FJIMSITPPNKJHDQQQMCIF"

We use the distance metric function and create a new column with the distance between the out-of-sample protein and the protein in a given row. We sort the table
