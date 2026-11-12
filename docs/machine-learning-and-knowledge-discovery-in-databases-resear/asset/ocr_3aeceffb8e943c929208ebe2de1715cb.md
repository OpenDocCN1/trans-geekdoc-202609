# Table 1. Median amount of degeneracy in 33 samples per observed network, obtained by NuDHY.

| Dataset | Degenerate edges Count | Normalized | Nodes in degenerate edges Count | Normalized |
|---|---|---|---|---|
| CONGRESS | 178 | 9.55% | 100 | 99.01% |
| IAF1260B | 129 | 6.19% | 247 | 14.81% |
| IJO1366 | 152 | 6.75% | 294 | 16.29% |
| ECOLI (ND) | 29 | 3.17% | 60 | 8.55% |
| CIT-SW | 179 | 0.34% | 806 | 4.87% |
| DBLP-9 (ND) | 272 | 0.29% | 1023 | 4.87% |
| ENRON | 379 | 0.25% | 1859 | 3.28% |
| MATH (ND) | 58 | 0.06% | 228 | 0.66% |
| ORD (ND) | 378 | 0.08% | 722 | 0.11% |
| SYNTHETIC 160 | 1274 | 99.53% | 1280 | 100% |
| SYNTHETIC 80 | 927 | 72.42% | 1280 | 100% |
| SYNTHETIC 40 | 351 | 27.42% | 1280 | 100% |
| SYNTHETIC 20 | 96 | 7.5% | 1000 | 78.12% |
| SYNTHETIC 10 | 27 | 2.11% | 227 | 17.73% |

our second goal, and justifies the need to develop our new algorithm DiNGHY to sample directly from the space of non-degenerate EODs.

To further evaluate the importance of using the right null model when performing statistical hypothesis testing, we compare the distributions of the numbers of directed cycles of sizes 2 and 3 in the digraph projections of samples obtained with NuDHY and with DiNGHY.9 Figure 2 shows the distributions of the number of directed 3-cycles for some of the datasets. Results for other datasets are in the supplementary materials, and are qualitatively similar. For all datasets, the distributions are clearly different. For IAF1260B and IJO1366, this difference leads to opposite outlooks of hypothesis tests. We compute the empirical p-value of a quantity \(q(\tilde{G})\) as the ratio of sampled dihypergraphs \(G\) where \(|q(G) - \mu| \ge |q(\tilde{G}) - \mu|\), where \(\mu\) is the mean value of \(q\) over the samples. The number of directed 3-cycles in IAF1260B and IJO1366 is marked as non-significant under the degeneracy-allowed null model (NuDHY), with p-values of 0.97 and 0.73 respectively. Under our more appropriate null model, the p-values are 0 and 0.33 respectively, indicating that existing knowledge about the DGP does not explain the observed number of directed 3-cycles. The p-values for other real datasets is zero under both null models, since the observed value is outside both distributions, but the distributions are still distinct.

9 For this experiment, we exclude ENRON, ORD (ND), MATH (ND), and DBLP-9 (ND) due to a prohibitive runtime of more than 22 h per dataset. Corollary 1 does not hold on some of the dihypergraphs we consider, because it is not tight. We conjecture that the MCs for these cases are still irreducible. If not, the distribution would be uniform over the strongly connected component that includes the observed network.