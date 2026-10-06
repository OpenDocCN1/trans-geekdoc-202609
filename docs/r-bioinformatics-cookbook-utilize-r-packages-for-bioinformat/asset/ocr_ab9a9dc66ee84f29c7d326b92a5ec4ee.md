# Performing Quantitative RNA-seq

In this example, we have two prepared DataFrames in the rbinfocookbook package - count_dataframe, which contains the actual counts for transcripts, and pheno_data, which is a metadata DataFrame that provides information about the samples. Refer to the following steps:

+   1. Begin by loading the count data and converting it into a matrix:

```
library(rbioinfcookbook)
genes <- count_dataframe[['gene']]
count_dataframe[['gene']] <- NULL
count_matrix <- as.matrix(count_data)
rownames(count_matrix) <- genes
```

+   2. Specify experiments of interest:

```
experiments_of_interest <- c("L1Larvae", "L2Larvae")
columns_of_interest <- which(
pheno_data[['stage']] %in% experiments_of_interest
)
```

+   3. Form the grouping:

```
grouping <- pheno_data[['stage']][columns_of_interest] |>
forcats::as_factor()
```

+   4. Form subset of count data:

```
counts_of_interest <- count_matrix[, counts = columns_of_
interest]
```

+   5. Create the DGE object:

```
library(edgeR)
count_dge <- edgeR::DGEList(
counts = counts_of_interest,
group = grouping
)
```

+   6. Perform differential expression analysis:

```
design <- model.matrix(-grouping)
set_dge <- edgeR::estimateDis(count_dge, design)
fit <- edgeR::glmQFit(set_dge, design)
result <- edgeR::glmQLTest(fit, coef=2)
topResults(result)
```

| Coefficient | logFC | logCPM | Pvalue | FDR |
|---|---|---|---|---||
|bn027527 | 6.318665 | 11.148756 | 42854.72 | 1.132951e-41 | 1.684584e- |