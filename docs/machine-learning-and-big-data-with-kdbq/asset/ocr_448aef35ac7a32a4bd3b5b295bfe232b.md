# 340

# DATA SCIENCE

```
(matEx mmu eigenvectors[0])eigenvalues[0]
```

```
0.1980295 -0.6931033 -0.6931033 -2.64774e-09
```

```
(matEx mmu eigenvectors[1])eigenvalues[1]
```

```
0.2357023 -0.2357023 0.942809 3.527864e-09
```

```
(matEx mmu eigenvectors[2])eigenvalues[2]
```

```
0.9074425 -0.1814885 0.362977 0.1088931
```

```
(matEx mmu eigenvectors[3])eigenvalues[3]
```

```
1 -1.777885e-08 0.06545e-08 -2.063043e-10
```

Indeed, the eigenvectors are recovered within the numerical precision. That why we have not used ~ to compare the eigenvectors with their numerically recovered values.

Finally we wrap the functions into a numerical suite which accepts as an input matrix and returns sorted the list of eigenvectors in descending order, and a corresponding list of eigenvalues. The values are wrapped in the dictionary:

```
.quantQ.mat.eigenSystem:[matt]
// -- input matrix
// set the bucket, default controls
bucket:(`matrix' maxCounts$thresholdZero()![mat;oj
  ;;0000;10e-10]);
// solve for eigenvalues
bucket:quantQ.mat.algoQR()/[[continue]];bucket);
// extract eigenvalues
eigenvalues:quantQ.mat.extractEigenQR[bucket];
// solve for eigenvectors
evectors::quantQ.mat.eigenIteration[mat;;e-10;10000] each
  -- eigenvalues;
// output bucket
:(eigenvalues`eigenvectors)!(eigenvalues;eigenvectors));
```

Finally, we obtain the full solution with the eigensystem of the matrix:

```
flip .quantQ.mat.eigenSystem[matEx]
```

eigenvalues eigenvectors

| 8 | 0.1980295 | -0.6931033 | 3.884289e-009 |
| 3 | 0.2357022 | -0.2357023 | 0.9428091 | -5.808747e-017 |
| 2 | 0.9074425 | -0.1814885 | 0.362977 | 0.1088931 |
| 1 | 1 | -1.252761e-099 | 2.44023e-010 | 8.945528e-010 |