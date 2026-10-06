
## Getting ready

As in the previous recipe, the data is provided as a count DataFrame, similar to what we might load in from a text file, and an ExpressionSet object. A Bioconductor ExpressionSet object is a data structure that's used to store and manipulate gene expression data in R. It is a list-like object that contains the raw expression data and associated metadata, such as sample annotations and features.

## How to do it...

With edgeR, we're going to look at how to do this from two different starting points – first with a count matrix and then with an ExpressionSet object.

## Using DESeq2 from a count matrix

Estimating differential expression with DESeq2 from a count table is done as follows:

- 1. Load the count data and convert it into a matrix:

```r
library(rbioinfocookbook)
genes <- count_dataframe[['gene']]
count_dataframe[['gene']] <- NULL
count_matrix <- as.matrix(count_dataframe(count_dataframe)
rownames(count_matrix) <- genes
```

- 2. Specify experiments of interest:

```r
experiments_of_interest <- c("L1Larvae", "L2Larvae")
columns_of_interest <- which(
pheno_data['stage'] %in%
experiments_of_interest
)
```

- 3. Form the grouping factor:

```r
stages <- pheno_data['stage'][columns_of_interest] |>
forcats::as_factor()
grouping <- data.frame(
stage = stages
)
```

- 4. Form the subset of count data:

```r
counts_of_interest <- count_matrix[,columns_of_interest]
```

```r
res <- results(dds,
  contrast=c("stage", "L2Larvae", "L1Larvae"))
```

log2 fold change (MLE): stage L2Larvae vs L1Larvae
Wald test p-value: stage L2Larvae vs L1Larvae
DataFrame with 1489 rows and 6 columns

| baseMean | log2FoldChange | lfcSE | stat | pvalue |
| :--- | :--- | :--- | :--- | :--- |
| <numeric> | <numeric> | <numeric> | <numeric> | <numeric> |
| 1 0.000 | NA | NA | NA | NA |
| 2 562.467 | -0.0567898 | 0.0553041 | -1.02686 | 3.04488e-01 3.87814e-01 |
| 3 894.891 | -0.7973532 | 0.045610 | -17.48159 | 19.7888e-08 1.54327e-06 |
| 4 323.316 | -0.8454425 | 0.0475500 | -11.34061 | 8.25709e-30 6.34632e-29 |
| 5 862.122 | -0.2538090 | 0.0480525 | -5.28191 | 1.27845e-07 2.92354e-07 |
| ... | ... | ... | ... | ... |
| ... | ... | ... | ... | ... |
| 14865 0.0000 | NA | NA | NA | NA |
| NA | NA | NA | NA | NA |
| 14866 71.9698 | -2.201803 | 0.0156498 | -14.23735 | 5.37280e-46 3.11925e-04 |
| 14867 311.1002 | -0.311300 | 0.0686318 | -4.53580 | 5.73868e-06 1.19202e-05 |
| 14888 1477.7729 | -0.557711 | 0.0446208 | -12.49888 | 7.57122e-36 3.70604e-35 |
| 14869 1214.1409 | 0.346754 | 0.0481392 | 7.20316 | 5.88342e-13 1.67726e-12 |

## Performing Quantitative RNA-seq

That is how we do it with a standard count table that could have come from many upstream sources. Now, let's look at the next input type.

## Using DESeq2 from an ExpressionSet object

To estimate differential expression with DESeq2 from an ExpressionSet object, we must perform the following steps:

- Load the eset data and convert it into a DESeqDataSet ():

```r
library(SummarizedExperiment)
sum_exp <- makeSummarizedExperimentFromExpressionSet(modfile.eset)
ddsSE <- DESeqDataSet(sum_exp, design = stage)
```

- Carry out analysis and the results:

```r
ddsSE <- DESeq(ddsSE)
resSE <- results(ddsSE, c("stage", "L2Larvae", "L1Larvae"))
```

log2 fold change (MLE): L2Larvae vs L1Larvae
Wald test p-value: L2Larvae vs L1Larvae
DataFrame with 14869 rows and 6 columns

| baseMean | log2FoldChange | lfcSE | stat | pvalue |
| :--- | :--- | :--- | :--- | :--- |
| <numeric> | <numeric> | <numeric> | <numeric> | <numeric> |
| FBgn0000003 | 0.000 | NA | NA | NA |
| FBgn0000008 | 918.783 | -0.115736 | 0.052270 | -2.21474 2.6778e-02 |
| FBgn0000014 | 867.608 | -0.856229 | 0.0379936 | -22.53616 1.83576e-12 |
| FBgn0000015 | 306.805 | -0.904863 | 0.0760892 | -11.89213 1.30043e-32 |
| FBgn0000017 | 1755.817 | -0.313555 | 0.0522008 | -6.00671... |
| ... | ... | ... | ... | ... |
| FBgn00261571 | 51.2588 | 0.000000 | 0.135855 | -5.00000 1.00002e+00 |
| FBgn00261572 | 44.6647 | -2.260062 | 0.1546197 | -14.32691 2.19130e-48 |
| FBgn00261573 | 563.7757 | -0.369160 | 0.0844196 | -4.37292 1.22596e-05 |
| FBgn00261574 | 2091.9427 | -0.617805 | 0.0883834 | -7.36918 1.71682e-13 |

## Estimating differential expression with DESeq2

(Note: The table above continues from OCR)

With that, we've learned how to work through DESeq2 using multiple inputs.

## How it works…

Similar to what we covered edgeR, we will go through to do this from a count matrix, not an ExpressionSet object.

## Using DESeq2 from a count matrix

In step 1, the count_dataframe DataFrame is loaded and a matrix called count_matrix is created by creating count_dataframe and setting the row names to the gene column from count_dataframe. The gene column is removed from count_dataframe.

In step 2, a character vector experiments_of_interest is created that contains the L1Larvae and L2Larvae elements. Then, a numeric vector columns_of_interest is created by finding the indices in the stage column of pheno_data that are elements of experiments_of_interest.

In step 3, a character vector stages is created by subsetting the stage column of pheno_data using columns_of_interest and converted into a factor using the as_factor() function from the forcats package. A DataFrame grouped is created with a single column stage containing the stages vector.

In step 4, a matrix counts_of_interest is created by subsetting count_matrix using columns_of_interest.

In step 5, the DESeq2 package is loaded and a DESeq object dds is created using the DESeqDataSetFromMatrix() function. counts_of_interest and grouping are passed to the countData and colData arguments, respectively. The design argument is set to a formula specifying that the stage column of grouping should be used as a predictor.

In step 6, the dds object is passed to the DESeq() function to carry out the analysis.

In step 7, a res object is created by calling the results() function on the dds object and setting the contrast argument to a contrast comparing the L2Larvae and L1Larvae levels of the stage factor. The res object is a DataFrame that contains several columns that summarize the results of a differential expression analysis carried out using the DESeq2 package. The headings of the DataFrame and the column's contents are as follows:

- 'baseMean': the mean of the normalized counts across all samples.
- 'log2FoldChange': the log2-fold change in expression between the levels of the factor being compared in the contrast argument.
- 'lfSE': the standard error of the 'log2FoldChange' value.
- 'stat': the test statistic for the hypothesis test for differential expression.
- 'pvalue': the p-value for the hypothesis test for differential expression.
- 'padj': the adjusted p-value, which takes into account the multiple hypothesis testing problem. Genes with a small 'padj' value are considered differentially expressed.
