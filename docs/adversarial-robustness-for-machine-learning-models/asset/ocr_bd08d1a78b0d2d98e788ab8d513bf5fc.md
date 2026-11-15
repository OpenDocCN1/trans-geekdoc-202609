# 4.3 Empirical comparison

Here we compare the performance of EOT attack (avg.) (Athalye and Sutskever, 2018) and MinMAX attack (Wang et al., 2021a). For each input sample ($ori$), we transform the image under a series of functions, e.g., flipping horizontally ($flh$) or vertically ($flv$), adjusting brightness ($bri$), performing gamma correction ($gam$) and cropping ($crop$), and group each image with its transformed variants. ASR$_{all}$ is reported to measure the attack success rate (ASR) over groups of transformed images (each group is successfully attacked signifies successfully attacking an example under all transformers). In Table 4.1, compared to EOT, MinMax leads to 9.39% averaged lift in ASR$_{all}$ over given models on CIFAR-10 by optimizing the weights for various transformations.

Table 4.1 Comparison of average and min-max optimization on robust attack over multiple data transformations on CIFAR-10. Acc (%) represents the test accuracy of classifiers on adversarial examples. Table adopted from Wang et al. (2021a).

| Model | Opt. | Acc$_{ori}$ | Acc$_{flh}$ | Acc$_{flv}$ | Acc$_{bri}$ | Acc$_{gam}$ | Acc$_{crop}$ | ASR$_{all}$ | Lift (↑) |
|---|---|---|---|---|---|---|---|---|---|
| A | avg. | 10.80 | 21.93 | 14.75 | 11.52 | 10.66 | 20.03 | 55.88 | - |
| | min max | 12.14 | 18.05 | 13.61 | 13.52 | 11.99 | 16.78 | 60.03 | 7.43% |
| B | avg. | 5.49 | 11.56 | 9.51 | 5.43 | 5.75 | 15.89 | 72.21 | - |
| | min max | 6.22 | 8.61 | 9.74 | 6.35 | 6.42 | 11.99 | 77.43 | 7.23% |
| C | avg. | 7.66 | 21.88 | 15.50 | 8.15 | 7.87 | 15.36 | 56.51 | - |
| | min max | 8.51 | 14.75 | 13.88 | 9.16 | 8.58 | 13.35 | 63.58 | 12.51% |
| D | avg. | 8.00 | 20.47 | 13.46 | 7.73 | 8.52 | 15.90 | 61.13 | - |
| | min max | 9.19 | 13.18 | 12.72 | 8.79 | 9.18 | 13.11 | 67.49 | 10.40% |

# 4.4 Extending reading

+   - Unadversarial examples by realizing input perturbations to design robust objects that are explicitly optimized to be confidently detected or classified (Salman et al., 2020a).