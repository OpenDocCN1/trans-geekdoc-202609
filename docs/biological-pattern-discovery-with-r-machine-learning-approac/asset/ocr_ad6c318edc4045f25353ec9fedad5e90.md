d(TGGCT, TGCT) = d(TGGC, TGC) + δ(T, T) = 1 + 0

The cell (4, 3) was moved diagonally from the cell (3, 2). Therefore the distance decomposition is shown below, where the residues on the right side of a bar was for the residues which were passed in the previous backward propagation steps

d(TGGC, TGC) = d(TGG, TG) + δ(C|T, C|T) = 1 + 0

The cell (3, 2) was moved diagonally from the cell (2, 1). The distance decomposition is shown below,

d(TGG, TG) = d(TG, T) + δ(G|CT, G|CT) = 1 + 0

The cell (2, 1) was moved vertically from the cell (1, 1) with the distance decomposition shown below,

d(TG, T) = d(T, T) + δ(G|G, -GCT) = 0 + 1

The final decomposition is shown below,

d(T, T) = d(-,-) + δ(T|GGCT, T|-GCT) = 0 + 0

The final optimal alignment is shown below, which had four matches, zero mismatch and one gap.

```
TGGCT
| |||
T-GCT
```

There is no R package available for the Sellers algorithm. An R code of the Seller algorithm can be requested from the author via an email.

# 7.2.3 The Needleman-Wunsch algorithm

The Needleman-Wunsch alignment algorithm was also developed based on the dynamic programming approach and is used for the global homology alignment as well [Needleman and Wunsch, 1970]. The algorithm employs a scoring approach, i.e., a match score is one, a mismatch score is zero and a gap score is zero as well. The algorithm has