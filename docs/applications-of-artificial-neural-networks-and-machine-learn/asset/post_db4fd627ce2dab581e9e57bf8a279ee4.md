

| Number of net | No. of nodes in hidden layer 1 | No. of nodes in hidden layer 2 | Input data | Output data | Correlation coefficient (Learning set) | Correlation coefficient (Testing set) | RMS | Activation function | Software employed |
|---|---|---|---|---|---|---|---|---|---|
| H1weit | 5 | 2 | (-1, 1) | (-1, 1) | 0.9998 | 0.9998 | 0.0160 | T | NW |
| H2weit | 5 | 3 | (-1, 1) | (-1, 1) | 0.9998 | 0.9998 | 0.0117 | S | NW |
| H3weit | 5 | 2 | (0.1, 1) | (0, 1) | 0.9995 | 0.9993 | 0.0089 | S | NW |
| H4weit | 5 | 2 | (0.02, 1) | (0, 1) | 0.9997 | 0.9996 | 0.0087 | S | NW |
| H5weit | 5 | 2 | (0.01, 1) | (0, 1) | 0.9993 | 0.9992 | 0.0090 | S | NW |
| H6weit | 5 | 2 | (0.05, 1) | (0, 1) | 0.9995 | 0.9994 | 0.0100 | S | NW |
| H7weit | 6 | 2 | (0.1, 1) | (0, 1) | 0.9995 | 0.9994 | 0.0094 | S | NW |
| H8weit | 5 | 3 | (0.05, 1) | (0, 1) | 0.9995 | 0.9994 | 0.0100 | S | NW |
| H9weit | 5 | 2 | (0.1, 0.9) | (0.1, 0.9) | – | – | 0.0073 | S | NT |
| H10weit | 3 | 2 | (0.1, 0.9) | (0.1, 0.9) | – | – | 0.0090 | S | NT |

Number of the hidden layers of the nets: 3; learning rule: delta-bar-delta; number of pairs for learning: 179; number of pairs for testing: 40; NW: NEURALWORKS; NT: NETS 201; S: sigmoid; T: tangent hyperbolic

by the trained neural net “H1weit” are shown. Figure 4.7 illustrates the difference between the exact and predicted weights.

### 4.5.4 Neural Networks for Structural Design

This network consists of three inputs comprising of the span length L, the height h, of the grids both in meters, and the region’s number, where the element considered is being located. The output consists of a single node representing the cross-sectional area A (in cm²) of the element in the concerned region.

The number of training pairs has been 179 × 16 = 864 and for testing 40 × 16 = 640 pairs are used. The factor 16 represents the number of element groups associated with the structure.

Different topologies are considered, the details of which are illustrated in Table 4.3.

- The optimal net contains 13 and 14 nodes in the first and the second hidden layers, respectively. This net uses hyperbolic tangent as an activation function.
- Increasing the number of nodes in the hidden layers did not improve the results.

![](img/4048998719320644ee88964326fd7995_106_0.png)

Fig. 4.5 The RMS of trained net

![](img/4048998719320644ee88964326fd7995_106_1.png)

Fig. 4.6 The test result

The RMS for the trained net is shown in Fig. 4.8. The result of testing are provided in Fig. 4.9 where the cross-sections from exact design and the cross-sections predicted by the trained neural net “H1dszn” are shown. Figure 4.10 illustrates the difference between the exact and predicted cross-sections.

![](img/4048998719320644ee88964326fd7995_107_0.png)

Fig. 4.7 The difference between the exact and predicted weight

| NGS | 1 | 2 | 6 | 7 | 11 | 12 | 13 | 15 | 16 |
|---|---|---|---|---|---|---|---|---|---|
| ASave | 149.6 | 69.5 | 174.6 | 74.9 | 210.1 | 127.2 | 34.3 | 35.2 | 36.6 |

NGS: The numbers associated with the regions in the structure; ASave: Average cross-sectional area required for the regions

![](img/4048998719320644ee88964326fd7995_107_1.png)

Fig. 4.8 The RMS of trained net

## 4.6 Data Ordering

In order to reduce the nonlinear nature of the problem and to avoid occurrence of possible instability, a special approach is adopted for data ordering. For this purpose the indices of the regions are altered in such a manner that the regions of higher indices correspond to larger cross-sectional areas, as far as possible. In other words,

![](img/4048998719320644ee88964326fd7995_108_0.png)

Fig. 4.9 The test result

![](img/4048998719320644ee88964326fd7995_108_1.png)

Fig. 4.10 The difference between the exact and predicted cross-section

in column 3 of the input data (see Sect. 5.1), for larger regional indices, the cross-sectional areas in column 4 should be selected larger. For this purpose a program “Orderdat” is developed. This program reads the input data and calculates the average cross-sectional areas needed for each region (for different values being considered for L and h). Table 4.3 illustrates the results of employing the program.

Now the average cross-sectional areas are associated with regions as their new indices for use in training the neural net. The ordered data from the previous section is used in the training new nets having different topologies as illustrated in Table 4.4.

Table 4.4 Neural nets for designing grids after data ordering

| Name of the net | No. of nodes in hidden layer 1 | No. of nodes in hidden layer 2 | Input data | Output data | Correlation coefficient (Learning set) | Correlation coefficient (Testing set) | RMS | Activation function |
|---|---|---|---|---|---|---|---|---|
| H1dszn | 13 | 13 | (-1, 1) | (-1, 1) | 0.0230 | 0.9881 | 0.9973 | T |
| H2dszn | 12 | 14 | (-1, 1) | (-1, 1) | 0.0240 | 0.9862 | 0.9964 | T |
| H3dszn | 11 | 15 | (-1, 1) | (-1, 1) | 0.0270 | 0.9858 | 0.9958 | T |
| H4dszn | 13 | 12 | (-1, 1) | (-1, 1) | 0.0243 | 0.9847 | 0.9974 | T |
| H5dszn | 13 | 14 | (-1, 1) | (-1, 1) | 0.0270 | 0.9821 | 0.9957 | T |
| H6dszn | 12 | 13 | (-1, 1) | (-1, 1) | 0.0320 | 0.9810 | 0.9944 | T |
| H7dszn | 11 | 16 | (-1, 1) | (-1, 1) | 0.0260 | 0.9775 | 0.9954 | T |
| H8dszn | 13 | 14 | (0, 1) | (0.07, 1) | 0.0230 | 0.9738 | 0.9884 | S |

Number of pairs for learning: 2864; number of pairs for testing: 640; number of nodes in input layer: 3; number of nodes in output layer: 1; learning rule: delta-bar-delta; employed software: NEURALWORKS; T: tangent hyperbolic; S: sigmoid

## 4.7 Improved Neural Net for Structural Design

Optimal topology corresponds to a net with 13 nodes in the first hidden layer and 13 nodes in the second hidden layer, as shown in Fig. 4.11.

Before ordering, 3-13-14-1 was the best net which is altered to 3-13-13-1 after ordering. By reducing the nonlinear nature of the problem, the number of nodes at hidden layers are reduced. Training is performed more efficiently after the ordering. Finally hyperbolic tangent function performed better than sigmoid in here.

![](img/4048998719320644ee88964326fd7995_109_0.png)

Fig. 4.11 The RMS of trained net

![](img/4048998719320644ee88964326fd7995_110_0.png)

Fig. 4.12 Topology of the selected network

The method presented for data ordering improves the training considerably and increases the speed and accuracy of the training. This is apparent from the comparison of the RMS curves for the neural nets for design before data ordering in Fig. 4.8 and after ordering in Fig. 4.12.

The RMS curve for the trained net is shown in Fig. 4.12.

## 4.8 Concluding Remarks

The networks trained can efficiently be used in the design of double layer grids within the bounds being considered. These bounds can easily be extended to cover a wider range of grids. The methods presented in here can also be employed for training networks for other types of space structures such as barrel vaults, domes, and antenna type of structures.

The method presented for data ordering improves the training considerably and increases the speed and accuracy of the training.

## References

- 1. Kaveh A., & Servati H. (2001). Design of double layer grids using backpropagation neural networks, Comput Struct, 79:1561–1568
- 2. Makowski ZS. (1981). Analysis, design and construction of double-layer grids. London: Appl Sci.
- 3. Nooshin H. (1984). Configuration classification in structural engineering. London: Elsevier
- 4. Waszczyszyn Z. (1996). Some recent and current problems of neurocomputing in civil and structural engineering. In: Topping BHV, editor. Edinburgh: Civil-Comp Press; 43–58
- 5. Iranmanesh A, & Kaveh A. (1999). Structural optimization by gradient-based neural networks. Int J Numer Meth Engng 46:297–311
- 6. Nooshin H, Disney P, & Yamamoto C. (1993). Formian. UK: Multi-Science Pub
- 7. Rumelhart DE, Hinton GE, & Williams RJ. (1986). Learning representations by backpropagation errors. Nature (London) 323:533–6
- 8. Baffes PT. (1991). NET user's guide. Software Technology Branch of NASA's Johnson Space Center
- 9. NeuralWare, (1993). Using NeuralWorks. Neuralware, USA

