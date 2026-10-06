# Estimating the copy number at a locus of interest 203

In step 6, we build a new SummarizedExperiment object called se to hold the window ranges and the new ratio data. We take the GRanges and colData objects from window_counts and add our new ratio matrix. We can now subset this and see what coverage is in our region of interest. This generates the following output:

```
## [1]
## [1,] 0.01725283
## [2,] 0.03128239
## [3,] -0.05748934
## [4,] 0.05893873
## [5,] 0.94251006
## [6,] 0.88186246
## [7,] 0.87927929
## [8,] 0.63780103
## [9,] 1.00308550
## [10,] 0.75515798
## [11,] 0.80228189
## [12,] 1.05207419
## [13,] 0.82393626
## [14,] NA
## [15,] NA
## [16,] -0.16269298
```

We can see that the region has a log2 ratio of 1 (twofold) coverage relative to the background, and we can interpret it as a copy number of two.

# See also

The calculation for the background level in this recipe is really simple – which is great for learning the recipe, but it might be quite underpowered in your real data. There are numerous options you could take to modify the way you calculate the background level for your data. Check out the rollmeans() and rollmedians() functions in the zoo package. These can give you the mean or median in rolling windows of arbitrary step length and give you a moving window background average that may be more appropriate. A related analysis to copy number is the estimation of ploidy from SNP allele frequencies. You can check out the vocR package's freq_peaks() function as a starting point to estimate ploidy from variant information in BAM files.