# 336 DATA SCIENCE

matExa: (1.0 -2.0 0.0 5.0;0.0 7.0 1.0 5.0; 0.0 4.0 4.0 0.0;0.0 0.0 2.0)

matExa

1 -2 0 5
0 7 1 5
0 4 4 0
0 0 0 2

Initialise the bucket in order to run the function:

```
bucket(`matrix`-counter(matExa;0));
```

and run the function explicitly in ten iterations:

```
bucket.(quantQ.mat.iterQR/)[10;bucket];
bucket[]
```

which gives following output:

| 1 1.414216 1.414165 5 |
| 0 8.000803 -2.999828 3.535655 |
| 0 0.0001718623 2.999897 -3.535412 |
| 0 0 2 |

The matrix is getting shape close to the upper diagonal matrix. There are elements below the main diagonal which are very small. We need to wrap the iteration into a function which algoQ is such a function, which accepts an argument dictionary with matrix to be decomposed, counter, and two control variables: max number of iterations and the numerical precision:

```
-quantQ mat.algoQR:[bucket]
// bucket -- contains matrix, counter, max number of iterations and
// precision
// QR decomposition
bucketTMP: quant.mat.QRdecomp[bucket[ matrix ]];
// define Q and R
Q: flip bucketTMP[matrixRotated];
R: bucket[matrix];
// define new matrix, similar to original
bucket[matrix]:R manu Q;
// increase counter
bucket[counter]:bucket[counter]+1;
// decide if continue
// criterion 1: counts
$bucket[counter]<bucket[maxCounts],bucket[continue]:0b;
// criterion 2: precision
$bucket[thresholdZero]:max abs {{matt;coord] matt[first[coord]], last[
-- coord]]bucket[matrix];
each raza [[dimM;x] {{x;y); (y;x)}x't where x<reverse til
-- dimM
][dimM] each tail count[bucket[matrix];bucket[continue]:0b];
bucket;
```