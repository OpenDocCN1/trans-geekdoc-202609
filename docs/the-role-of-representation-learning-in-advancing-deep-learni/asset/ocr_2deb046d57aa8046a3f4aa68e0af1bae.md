Table 2.18: More extensive results on the ablation of $c_0$ for GSVM. Averages provided are calculated over all experimental runs. #Queries denotes the number of queries sent to the bidders in the iterative phase, excluding the initial queries $c_0$. Optimal Alloc. in % denotes the percentage of times the optimal allocation was found. Thanks to a better selection of initial queries, GALI allows the iterative phase to converge much faster and achieve better results. This results in fewer queries to the bidders, reducing the burden on them. This effect is apparent starting from 20 initial queries.

| $c_0$ | Sampling Technique | Average #Queries | Max #Queries | Average #Iterations | Max #Iterations | Optimal Alloc. in % |
|---|---|---|---|---|---|---|
| 10 | UF | 14.65 | 26.86 | 5.82 | 11.98 | 3.92 |
| | GALI | 13.91 | 27.47 | 6.10 | 14.61 | 13.73 |
| 20 | UF | 11.89 | 22.63 | 5.16 | 10.80 | 27.45 |
| | GALI | 9.84 | 20.69 | 4.75 | 10.69 | 35.29 |
| 30 | UF | 9.72 | 19.61 | 4.61 | 10.02 | 27.45 |
| | GALI | 7.17 | 15.49 | 3.86 | 8.39 | 52.94 |
| 40 | UF | 7.92 | 16.47 | 4.08 | 9.39 | 25.49 |
| | GALI | 5.32 | 12.22 | 3.17 | 7.33 | 47.06 |
| 50 | UF | 6.70 | 15.02 | 3.70 | 8.31 | 33.33 |
| | GALI | 5.58 | 12.78 | 3.36 | 7.59 | 54.90 |

with GALI are, especially for small $c_0$, more consistent and less distributed than with uniform sampling.

Further, we provide extended results of the ablation with respect to the number of initial queries for GSVM of Figure 2.16 and LSVM of Figure 2.17 in Table 2.18 and Table 2.19 respectively. These results show that the use of GALI not only results in improved economic efficiency, but also in a generally reduced number of queries to the bidders and a lower number of iterations.

# 2.4.2 Ablations on GALO

We analyze the individual building blocks of GALO in more detail and perform an ablation with two different variants. GALO (NN) is our baseline, where GALO is performed on the basis of a neural network as described in 2.3.2. For GALO (linear), we use a simple linear regression model as described in 2.3.2 instead of the neural network. For the second one, GALI + UF, we