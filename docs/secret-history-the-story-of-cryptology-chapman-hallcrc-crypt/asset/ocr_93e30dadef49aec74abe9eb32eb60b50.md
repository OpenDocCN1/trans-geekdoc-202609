some cases, there is a separate edge, connecting the same vertices, but in the opposite direction, offering the traveler a simple way back. The challenge is, given a starting vertex v_in and an ending vertex v_out, to find a path that passes through all of the other vertices exactly once. The path needn't make use of every edge. Such paths do not exist for every directed graph. If one is present, it is called a Hamiltonian path after William Rowan Hamilton (1805–1865). Take a few moments to find a Hamiltonian path for the graph in Figure 21.4 with v_in = 0 and v_out = 6. Once you have found it, label the intermediate points 1, 2, 3, 4, 5, in the order your solution passes through them. For this particular problem, the solution is unique. Some graphs have several distinct solutions for a given starting point and ending point.

This simple sounding problem is NP-complete. We can solve small examples by hand, but there is no known polynomial time solution for such problems in general.

To find the solution you discovered, Adleman began by randomly choosing bases to form strands of DNA, labeled O0, O1, O2, O3, O4, O5, and O6, Known as oligonucleotides (hence, the O used in our notation), these strands are only half of the DNA “ladder” we usually picture when imagining DNA. A few sample values are given below:

```
O₂=TATCGGATCGGTATATCCGA
O₃=GCTATTCGAGCTTAAAGCTA
O₄=GGCTAGGTACCAGCATGCTT
```

We may then form the Watson-Crick complement of each of these, using the fact that the complement of A is T and the complement of G is C.

```
Ō₂=ATAGCCTAGCCATATAGGCT
Ō₃=CGATAAGCTCGAATTTCGAT
Ō₄=CCGATCCATGGTCGTACGAA
```

There is nothing special about the choices used for the bases or their order. All that matters is that we have as many strands as there are vertices in our graph. Random strings of A, C, G, and T will suffice. However, there is no flexibility in forming the complements (above) or in selecting the bases used to represent the edges (below).

```
O₂→₃=GTATATCC GAGCTATTCGAG
O₃→₄=CTTAAAGCTAGGCTAGGTAC
```

Edge O_i→j is created by taking the second half of O_i and appending to it the first half of O_j. These edges are defined so that they may join (by bonding) the oligonucleotides representing the vertices, as shown below:

```
(edge O₂→₃ joined end to end with edge O₃→₄)
GTATATCC GAGCTATTCGAG CTTAAAGCTAGGCTAGGTAC
    CGATAAGCTCGAATTTCGAT
(held together by the vertex Ō₃)
```

Thus, the vertices of our original graph are represented by Ō₁, Ō₂, Ō₃, Ō₄, Ō₅, Ō₆, and Ō₇. Notice that the edge O₃→₂ will not be the same as the edge O₂→₃. Starting with oligonucleotides of length 20 ensures that we’ll have more than enough different possibilities to encode all 7 vertices, and from these get the representations of all 14 edges. When the strands representing the vertices and edges are placed close enough to bond, the bonds will represent paths in the graph.