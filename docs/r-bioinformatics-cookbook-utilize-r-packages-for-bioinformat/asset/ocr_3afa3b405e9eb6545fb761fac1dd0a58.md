# Finding Genetic Variants with HTS Data

```
IRanges(c(40700), width = c(1500) )
\overlap_hits <- findOverlaps(region_of_interest, se)
data_in_region <- se[subjectHits(overlap_hits)]
assay(data_in_region)
```

This is all we need to estimate the copy number.

# How it works...

In step 1, we use the csaw package to get read counts in 100 bp windows over our small section of human chromosome 17. The read filtering options are in the param argument. In step 2, we extract the first and only column of data to give us a simple vector of the counts using the assay () function and subsetting. Next, in step 3, we use the quantile () function to get the min_count value in the lower 10th percentile of counts vector. The double-bracket subsetting is needed to get a single number from the named vector that the quantile () function returns. The min_count value is a cut-off. All values in counts vector lower than this are set to NA to remove them from the analysis - this acts as a low coverage threshold and the percentile used can be modified in your adaptations of the recipe as needed.

In step 4, we add some regions with doubled coverage so that we can detect them. We select several windows to double and then create a multiplier of equal length that contains 1 where we want to change counts and 2 where we want them. We apply the multiplication. Step 4 will not likely be in your analysis as it is a synthetic data generation step.

In step 5, we compute the background coverage level. Here our function is a simple mean that is saved in mean_cov, but you can use many other summary functions. We also calculate log2 () of the ratio of each window count to the global mean_cov and save it in a one-column matrix called ratio since we need the result to a matrix in our final SummarizedExperiment object. We quickly use plot and can see the count of doubled windows in the middle of the data

![](bbox=[0.155, 0.706, 0.823, 0.866])

Figure 7.3 – A window count plot