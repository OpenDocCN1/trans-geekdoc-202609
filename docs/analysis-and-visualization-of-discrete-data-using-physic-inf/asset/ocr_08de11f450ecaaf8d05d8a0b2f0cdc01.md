![](bbox=[0.07, 0.05, 0.58, 0.52])

| u | x | t | ux | ut |
|---|---|---|---|---|
| 0 | -24 | 0 | 0 | 0 |
| 0 | -22 | 0 | 0 | 0 |
| 0 | -2 | 0 | 0 | 0 |
| 0 | -18 | 0 | 0 | 0 |
| 0 | -16 | 0 | 0 | 0 |
| 0 | -14 | 0 | 0 | 0 |
| 0 | -12 | 0 | 0 | 0 |
| 0 | -1 | 0 | 2 | -2 |
| 0.36 | -08 | 0 | 1.6 | -1.6 |
| 0.64 | -06 | 0 | 1.2 | -1.2 |
| 0.84 | -04 | 0 | 0.8 | -0.8 |
| 0.96 | -02 | 0 | 0.4 | -0.4 |
| 1 | 0 | 0 | 0 | 0 |
| 0.96 | 02 | 0 | -0.4 | 0.4 |
| 0.84 | 04 | 0 | -0.8 | 0.8 |
| 0.64 | 0.6 | 0 | -1.2 | 1.2 |
| 0.36 | 0.8 | 0 | -1.6 | 1.6 |
| 0 | 1 | 0 | -2 | 2 |
| 0 | 1.2 | 0 | 0 | 0 |
| 0 | 1.4 | 0 | 0 | 0 |
| 0 | 1.6 | 0 | 0 | 0 |
| 0 | 1.8 | 0 | 0 | 0 |
| 0 | 2 | 0 | 0 | 0 |
| 0 | 2.2 | 0 | 0 | 0 |
| 0 | 2.4 | 0 | 0 | 0 |
| 0 | 2.6 | 0 | 0 | 0 |

Figure 1.13. Derivation of advection equation.

is assumed for partial differential terms. Even for nonlinear terms where a coefficient is a function of physical data, they can be reduced to a regression analysis problem by integrating the nonlinear parts with partial differential terms.

For the partial differential terms, if an exact solution is given, an exact differential value can be obtained. If not, the calculation of a differential value becomes an issue. One possible strategy is to obtain and differentiate an approximate function that distributes physical data continuously in some manner. One such approximate function that attracts attention is an approximate function based on neural network (NN). This will be discussed in Chapter 2.

# ### 1.2. Basic operations of Google Colab (Colab)

Approximately 1000 rows of data can be processed with Excel; however, in order to understand data analysis techniques handling a large amount of data, Google Colab is used. Google Colab (Colab) is Google’s cloud environment for data analysis [2]. Colab allows you to start analyzing data