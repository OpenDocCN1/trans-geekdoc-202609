
## 8.4.1.2 Case B—BPN as a Structural Analyzer

The net has been trained for different sets of training pairs ranging from 100 pairs up to 500 pairs. In order to avoid overtraining, the training process was continued up to 1% RMS. For each case, the number of nodes in the hidden layer is increased from a possible minimum to the value given by Eq. (8.8). The net is trained easily for 100 training pairs, but the error on the output units is high. The effects of increasing the number of hidden layers are investigated and no improvement is observed as compared to nets with one hidden layer.

The values given in Table 8.3 are chosen so that the training time becomes minimum, for each set of training pairs. Although the results of the BPN as compared to the CPN are better, the training time is much greater, which offsets this prevailing parameter. Besides, even if the response of CPN includes a larger error, nevertheless, its implementation as a fast analyzer in structural optimization has led to very good results [6].

Selecting a proper number of nodes for the hidden layer is very important. Choosing a small number for the nodes either causes the net not to converge to a pre-specified error tolerance or the training time increases. As it can be observed from Fig. 8.3, the tests for 300 and 400 training pairs show that as the number of training pairs is increased the training time is decreased. Besides, when the training pairs are not sufficient (100 pairs) the number of nodes based on Eq. (8.8) is appropriate, however, as the number of training pairs is increased a value much less than what is given by Eq. (8.8) will be required. Choosing a very large number of hidden nodes will increase the training time considerably and as it can be observed from Fig. 8.4, no improvement in the response of the output units will be achieved.

## 8.4.2 Example 2

A twenty-eight-bar space truss is considered as illustrated in Fig. 8.5.

## 8.4.2.1 Case A—The CPN as a Structural Analyzer

The loading condition and the element connectivities are shown in Tables 8.4 and 8.5, respectively. Members cross-sectional areas are generated randomly between 12.0 and 16.0 cm². One-tenth of the training pairs, as extra pairs, are generated to verify the accuracy of the net.

In order to see how different trained nets respond to a given untrained input vector (Table 8.6), an input vector is chosen so that all its values are in the range for which the net has been trained. For each case, the number of Kohonen units is chosen so that the average error on the output units is minimum (by modifying the parameter D). As it can be observed, when the number of training pairs is small, the associated error is large. As the number of training pairs is increased, the average error on the

Table 8.3 The response of different trained nets to a given untrained input vector RMS = 0.01

| | BPN | 100 T. Pairs | 200 T. Pairs | 300 T. Pairs | 400 T. Pairs | 500 T. Pairs |
|---|---|---|---|---|---|---|
| A (cm²) | σ | σ^N | σ^N | σ^N | σ^N | σ^N |
| 7.6 | −374.9 | −395.6 | −378.1 | −374.7 | −373.2 | −373.1 |
| 8.8 | −346.3 | −342.2 | −345.5 | −347.2 | −344.9 | −344.7 |
| 6.1 | −570.3 | −561.1 | −566.3 | −561.5 | −566.9 | −562.7 |
| 8.2 | −432.1 | −442.6 | −430.9 | −435.7 | −432.9 | −430.1 |
| 9 | −1374.7 | −1380.6 | −1363.7 | −1376.9 | −1373.8 | −1369.6 |
| 7.9 | −1570.8 | −1625.5 | −1558.5 | −1545.6 | −1568.5 | −1569.4 |
| 6.9 | −160.4 | −159.9 | −161.9 | −158.7 | −159.1 | −160.6 |
| 9.8 | −69.4 | −80.5 | −71.9 | −67.8 | −69.7 | −69.0 |
| 6.2 | −84.3 | −83.2 | −85.1 | −83.3 | −85.9 | −83.3 |
| 7.6 | 65.8 | 68.1 | 64.2 | 66.2 | 65.2 | 65.3 |
| 6.8 | 110.2 | 106.9 | 108.0 | 108.0 | 112.6 | 110.1 |
| 8.5 | 307.7 | 310.3 | 308.5 | 307.0 | 305.2 | 307.2 |
| 7.2 | 337.6 | 331.4 | 339.9 | 337.9 | 338.9 | 340.4 |
| 9.1 | −191.4 | −193.6 | −190.9 | −191.9 | −190.7 | −190.5 |
| 8.3 | −201.7 | −192.2 | −203.2 | −201.7 | −201.4 | −199.0 |
| 6.7 | 1837.2 | 1887.6 | 1874.5 | 1849.2 | 1852.8 | 1850.9 |
| H.N | | 50.0 | 50.0 | 50.0 | 50.0 | 50.0 |
| E | 0.0 | 3.1 | 1.1 | 0.8 | 0.7 | 0.6 |
| T.T | | 11.3 | 7.4 | 8.4 | 7.6 | 7.6 |

σ = Exact member stress kgf/cm²  
σ^N = Net response  
H.N = Number of hidden nodes  
E = Average error (%)  
T.T = Training Time (minutes, on PC Pentium 133)

output is reduced. For the purpose of comparison with the BPN, these training sets have been chosen. However, for CPN, in order to have smaller errors on the output units, a sufficient number of training pairs is required which is usually more than what is required for BPN.

By selecting a smaller value for the Kohonen units classifier, D, a larger network with higher accuracy on the output units is obtained, but the training time is slightly increased. For the case of 1000 training pairs, the parameter D has been increased gradually in order to see how the average error on the output units changes. The results are shown in Table 8.7. Since the training time for the CPN is very short as compared to the BPN, choosing a large number of Kohonen units seems reasonable.

Fig. 8.3 The effect of number of nodes in the hidden layer on the training time

![](img/4048998719320644ee88964326fd7995_187_0.png)

Fig. 8.4 The effect of number of nodes in the hidden layer on the average error of the output units

![](img/4048998719320644ee88964326fd7995_187_1.png)

## 8.4.2.2 Case B—BPN as a Structural Analyzer

As for the previous example, the net is trained for different sets of training pairs. In each set, the number of nodes in the hidden layer is varied from a value less than half the value p given by Eq. (8.8) up to p. As it can be observed from Table 8.8, for a small number of training pairs, the value p and as the number of training pairs is increased, a value less than half of p is appropriate for the number of nodes in the hidden layer. For the purpose of comparison with the CPN, those cases with minimum training time are chosen. Unlike for the CPN, no gain is obtained by increasing the number of training pairs. Although the average error on the output units is reduced, however,

![](img/4048998719320644ee88964326fd7995_188_0.png)

Fig. 8.5 A 28-bar space truss

Table 8.4 The loading condition

| Node | Px (kgf) | Py (kgf) | Pz (kgf) |
|---|---|---|---|
| 1 | 500 | −2500 | 5000 |
| 2 | 0 | −2500 | 5000 |
| 3 | 250 | 0 | 0 |
| 4 | 250 | 0 | 0 |

Table 8.5 Element connectives

| Member | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 | 25 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Start | 1 | 1 | 1 | 1 | 1 | 2 | 2 | 2 | 2 | 3 | 4 | 5 | 3 | 3 | 3 | 4 | 4 | 4 | 5 | 5 | 5 | 6 | 6 | 6 |
| End | 2 | 3 | 4 | 5 | 6 | 3 | 4 | 5 | 6 | 4 | 5 | 6 | 7 | 8 | 10 | 7 | 8 | 9 | 8 | 9 | 10 | 7 | 9 | 10 |

| A (cm²) | CPN σ | 200 T. Pairs σ^N | 300 T. Pairs σ^N | 400 T. Pairs σ^N | 500 T. Pairs σ^N | 1000 T. Pairs σ^N |
|---|---|---|---|---|---|---|
| 15.8 | 81.78 | 68.05 | 76.71 | 72.68 | 71.21 | 73.81 |
| 12.3 | -739.82 | -686.34 | -688.14 | -721.78 | -686.07 | -707.98 |
| 14.4 | -377.44 | -366.50 | -368.54 | -373.47 | -362.32 | -357.27 |
| 12.8 | 306.23 | 316.33 | 313.58 | 310.22 | 306.47 | 288.35 |
| 15.0 | 462.61 | 471.17 | 473.37 | 494.84 | 484.57 | 483.84 |
| 15.8 | -383.44 | -395.45 | -392.53 | -394.64 | -393.35 | -407.29 |
| 13.8 | -623.15 | -649.52 | -646.46 | -625.53 | -639.35 | -639.72 |
| 12.5 | 567.97 | 541.21 | 524.04 | 522.29 | 528.98 | 528.04 |
| 13.0 | 285.71 | 262.06 | 258.01 | 269.12 | 271.60 | 287.17 |
| 15.5 | 248.65 | 199.58 | 201.77 | 209.01 | 205.79 | 218.56 |
| 14.5 | 158.89 | 164.56 | 172.15 | 164.99 | 164.09 | 160.53 |
| 13.2 | -175.22 | -166.36 | -170.47 | -177.38 | -173.56 | -180.12 |
| 14.5 | 193.70 | 182.18 | 195.46 | 189.74 | 192.51 | 193.86 |
| 12.4 | -849.44 | -813.94 | -813.17 | -804.68 | -805.70 | -801.02 |
| 15.8 | -306.95 | -310.09 | -316.97 | -303.80 | -303.83 | -299.01 |
| 14.4 | -23.08 | -21.50 | -17.88 | -19.43 | -18.80 | -17.19 |
| 15.1 | -353.77 | -332.50 | -334.69 | -344.05 | -342.31 | -347.71 |
| 12.3 | -781.28 | -731.30 | -748.83 | -757.1 | -749.18 | -768.66 |
| 15.6 | 10.20 | 14.30 | 8.59 | 11.80 | 10.58 | 10.63 |
| 12.9 | -32.46 | -23.06 | -32.80 | -31.69 | -31.41 | -32.08 |
| 12.4 | 710.71 | 669.10 | 672.26 | 687.97 | 679.04 | 698.69 |
| 14.5 | 266.66 | 258.46 | 272.49 | 267.94 | 267.28 | 268.89 |
| 12.5 | -103.65 | -89.45 | -87.70 | -89.64 | -89.56 | -89.85 |
| 13.1 | 295.15 | 278.86 | 268.35 | 271.43 | 270.31 | 272.75 |
| 14.5 | 637.26 | 622.52 | 627.31 | 615.92 | 617.11 | 612.82 |
| D | | 4.8 | 5.3 | 4.1 | 5.0 | 4.0 |
| N | | 189 | 222 | 398 | 413 | 990 |
| N_win | 6 | 7 | 7 | 12 | | |
| E | 0.0 | 8.43 | 6.59 | 5.51 | 5.48 | 5.16 |
| T.T | 0.083 | 0.167 | 0.467 | 1 | 5.67 | |

σ = Exact member stress kgf/cm²  
σ^N = Net response  
D = Kohonen unit classifier  
N = Number of Kohonen units  
E = Average error (percent)  
T.T = Training Time (minutes, on PC Pentium 133)
