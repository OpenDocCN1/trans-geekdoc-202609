# Listing 15.12 Performing and plotting LLE on the flea dataset

```
```r
lleFleaK <- calc_k(fleaScald, m = 2, kmin = 1, kmax = 20,
                  parallel = TRUE, cpus = parallel::detectCores())

lleBestFleaK <- filter(lleFleaK, rho == min(lleFleaK$rho))

lleBestFleaK

  k    rho
1 12 0.2482

lleFlea <- lle(fleaScald, m = 2, k = lleBestFleaK$k)

fleaTib <- fleaTib %>%
  mutate(LLE1 = lleFlea$Y[, 1],
         LLE2 = lleFlea$Y[, 2])

ggplot(fleaTib, aes(LLE1, LLE2, col = species)) +
  geom_point() +
  theme_bw()
```
```

The resulting plots from code listing 15.12 are shown in figure 15.16 (I combined the plots into a single figure to save room). LLE seems to do a decent job of separating the different species of flea, though the result isn’t quite as impressive as how it was able to unravel the s curve dataset.

> **IMPORTANT** Sadly, as each case is reconstructed as a weighted sum of its neighbors, new data cannot be projected onto an LLE map. For this reason, LLE cannot be easily used as a pre-processing step for other machine learning algorithms, as new data can’t be passed through it.