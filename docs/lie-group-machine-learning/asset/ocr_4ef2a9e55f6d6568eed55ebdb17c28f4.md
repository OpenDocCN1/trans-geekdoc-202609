the Lie algebraic differential by a Lie algebra. Then, the Lie algebra differential (equiv-alent to solving in linear space) is calculated, the numerical solution of the Lie algebra differential is pulled back to the Lie group, and the numerical solution of the Lie group learning system is obtained, which ensures that the numerical solution of the system is on the manifold. Massive amounts of data are always divided into groups that satisfy their group structure and groups that do not satisfy their group structure (intermediate data can be transformed by cohomology). The purpose of learning is to find effective data that fits specific learning objectives from the massive data of this learning system for analysis and use. However, the labelled data that is currently known to meet its group structure and meet the specific learning objectives may not be sufficient, and the vast majority of data is unlabelled data that is not aware of the learning objectives. Hence, Lie group can be used in a semi-supervised learning model to mine data [46]. Lie group semi-supervised learning is expressed as follows:

Through the analysis of the learning system, Lie group *G* that meets the specific structure is found. Suppose that there is a large sample set, where the sample number *n = l + k* is massive and the sample dimension *D* is high.

```
G = {x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>l</sub>, x<sub>l+1</sub>, x<sub>l+2</sub>, ..., x<sub>l+k</sub> \in R<sup>D</sup>}
```

where x<sub>1</sub>, x<sub>2</sub>, . . . , x<sub>l</sub> is a set of marked data that satisfies the structure of the learning system, i.e., there is a set L = {(x<sub>1</sub>, y<sub>1</sub>), (x<sub>2</sub>, y<sub>2</sub>), . . . , (x<sub>l</sub>, y<sub>l</sub>)} \subset G, U = {x<sub>l+1</sub>, x<sub>l+2</sub>, . . . , x<sub>l+k</sub>} which is a large set of unlabelled data sets (*l* \ll *k*) that do not know whether the group structure is satisfied. The purpose of the study is to mine as much data as possible, which meets the learning objectives, through the analysis and use of the structure and the Lie group (Lie algebra) to make sense of the structure and provide sufficient information for dimension reduction and structure learning.

# **8.2.2 Semi-supervised learning model based on Lie group algebra structure**

Semi-supervised learning is considered from the algebraic group structure of the Lie group generating element, single parameter subgroup, and Lie algebra.

**Definition 8.1.** All things that meet certain conditions constitute a collection, and each of them is called an element of the collection.

**Definition 8.2.** If a linear combination is defined for elements in a collection and any linear combination of any set of elements in the set is still an element of the set, the set is called a linear set or a linear space.

**Definition 8.3.** If a set of linearly independent elements in a linear set can linearly be combined into any element in the set, it can be called a set of base of the linear set, where the number of linearly independent elements is called the dimension number of the linear set.