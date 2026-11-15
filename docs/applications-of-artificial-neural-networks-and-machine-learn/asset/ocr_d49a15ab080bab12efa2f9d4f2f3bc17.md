| Neuro-optimizer | ANNs are trained based on different numbers of training pairs (T.P.) |
|---|---|
| Design variables | Exact solution | 50 T.P. N = 50 | 100 T.P. N = 99 | 200 T.P. N = 194 | 300 T.P. N = 281 | 4 T.P. N = 367 |
| X1 | 8.10 | 8.62 | 8.67 | 8.62 | 8.68 | 8.62 |
| X2 | 9.00 | 9.11 | 9.20 | 9.12 | 9.21 | 9.12 |
| X3 | 18.21 | 18.25 | 18.45 | 18.26 | 18.60 | 18.26 |
| X4 | 9.18 | 9.46 | 9.55 | 9.46 | 9.60 | 9.46 |
| X5 | 4.78 | 5.08 | 5.11 | 5.09 | 5.12 | 5.08 |
| X6 | 13.89 | 14.39 | 14.52 | 14.40 | 14.56 | 14.40 |
| X7 | 9.01 | 8.78 | 8.89 | 8.79 | 8.95 | 8.79 |
| OBJ (kgs) | 1278.3 | 1303.00 | 1315.30 | 1303.60 | 1320.80 | 1303.50 |
| E | 0.00 | 0.03 | 0.04 | 0.03 | 0.04 | 0.03 |

Note D = 7.0 (Kohonen units classifier), E = average error; N = number of Kohonen units made by the ANNs; domain of search = A* ± 0.2A*

The training process is very fast and the trained ANNs will respond rapidly to constraint or gradient requirements in the optimization process. Presented numerical examples demonstrate the ability of the approach.

Although the CPN is very fast and can efficiently be incorporated in the optimization of a wide range of practical problems, nevertheless, for large-scale problems, a considerable number of training pairs will be involved, and selecting a small value for D results in large networks. This, in turn, makes the training of neural nets timely. Therefore, for such problems, selecting appropriate values for the number of training pairs and D becomes an important task.

# ## References

+   1. Iranmanesh A, Kaveh A (1999) Structural optimization by gradient-based neural networks. Int J Numer Methods Eng 46:297–311
+   2. Fausett L (1994) Fundamentals of Neural Networks. Prentic Hall International. Inc.: Upper Saddle River, NJ, USA
+   3. Chen HM, Tsai KH, Qi GZ, et al (1995) Neural network for structure control. Journal of computing in civil Engineering 9:168–176
+   4. Szewczyk ZP, Noor AK (1996) A hybrid neurocomputing/numerical strategy for nonlinear structural analysis. Comput Struct 58:661–677
+   5. Kishi M, Kodera T, Iwao Y, Hosoda R (1993) Structural optimization by neuro-optimizer. In: Proceedings of the IFIP WG7. 5 Fifth Working Conference on Reliability and Optimization of Structural Systems VTakamatsu. pp 113–120
+   6. Hajela P, Berke L (1991) Neurobiological computational models in structural analysis and design. Comput Struct 41:657–667
+   7. Hajela P, Fu B, Berke L (1993) ART networks in automated conceptual design of structural systems. Comput Syst Eng 4:121–133