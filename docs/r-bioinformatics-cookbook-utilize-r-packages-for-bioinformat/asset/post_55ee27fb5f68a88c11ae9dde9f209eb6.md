
## Performing Quantitative RNA-seq

*step 5*, the `plotFeatures()` function is used on the calculated splice data values in the `sgf_ucsc` variable, and the `geneID` argument is used to create a plot of the expression values for the gene ID 1. The plot, which is a heatmap of exon coverage, is not saved to a variable; instead, it is plotted directly to the screen, but a DataFrame of intron/exon junctions is saved to the `df` variable. The resulting heatmap plot looks like this:

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_172_0.png)

Figure 6.1 – Predicted exon heatmap

*step 6*, the `analyzeVariants` function is used to predict splice variants using the `sgvc` variable created in *step 4*. The output is assigned to the `sgvc_pred` variable.

*step 7*, the `SGSeq` data is prepared for differential analysis using the DEXSeq package. The `rowRanges` function is used to extract the exon information from the `sgvc_pred` variable. The `getSGVariantCount` function is used to extract the counts of the variants for each exon in sample. The counts, exon ID, and group ID are assigned to variables. A typical `sample_info` DataFrame containing the sample names and conditions is created and assigned to assign the first four BAM files to a TEST condition and the rest to a CONTROL condition. Lastly, the `DEXSeqDataSet` function is used to create a DEXSeq dataset from the counts, sample information, and exon and group IDs. The design parameter is the simple test versus by exon design that we expect for a straightforward one-sample analysis. The R formula expresses that. These are the preliminary objects that we need for a differential analysis in DEXSeq.

## Performing power analysis with powsimR

In step 8, the DEXSeq package is used for differential analysis. We move through the typical workflow using the estimateSizeFactors, estimateDispersions, testForDEU, estimateExonFoldChanges functions, which are used together to test for differential exon usage. The output is assigned to the `dx` variable and final results are obtained from that object using the DEXSeq result. The padj and log2fc of the counts expressed as Fragments Per Kilobase Per Million fragments (FPKM) can be found in that table.

## Performing power analysis with powsimR

Statistical power analysis is used to determine the sample size to detect an effect of a certain size with a level of statistical significance. This is important because it allows researchers to ensure that their studies are adequately powered (that is, enough replicates have been sampled) to detect the effects they are interested in. Without sufficient power, there is a higher risk of failing to reject the null hypothesis when it is false — to miss differentially expressed genes. In this recipe, we use the powsimR package (which is not in Bioconductor) to perform two types of power analysis. Both of them will be performed with a small real dataset. First, we will test and control, and then we will estimate the replicates that need to spot differences in gene expression of a particular magnitude – if they’re present. powsimR takes a simulation-based approach in that it generates many datasets and evaluates the detection power in each to create a distribution of detection power. The first step is to estimate some parameters for these simulations for which we’ll need sample or preliminary data. With that, we simulate and assess power.

## Getting ready

powsimR has a lot of dependencies, some of which are a bit fiddly to install. I recommend manual installation, often, that isn’t necessary. Try installing the Python magic-impute dependency first and then installing the R package from GitHub before installing the powsimR package itself. The following steps outline the procedure:

- 1. In a terminal, run the following command to install the Python magic-impute dependency:

```
pip install --user magic-impute
```

- 2. Then, we can install the R packages as usual:

```
renv::install("cran/Rmagic")
remv::install("bvieth/powsimR")
```

The package should be installed. If it raises any errors, please see the complete documentation for this package on its GitHub page: https://github.com/bvieth/powsimR.

## Performing Quantitative RNA-seq

One tip I do have when installing this fiddly package is that it sometimes tells you lots of dependencies that you are certain are not installed. If this happens, restarting R and it should straighten things out.

The data we use for this recipe will be from a set Arabidopsis thaliana plant samples infected with Pseudomonas syringae hrc mutant versus a set of control infection samples (mock). There are three replicates in each sample type. These are available in the rbioinfcookbook data package as a single matrix with six columns called arab_infection.

## How to do it...

Let's do the analysis by performing the following steps:

- 1. Estimate the simulation parameter values:

```
library (rbioinfcookbook)

means_mock <- rowMeans(arab_infection)
```

- 2. Examine the distribution of the log2fc change ratios:

```
finite_log2fc <- log2fc(is.finite(log2fc))
plot (density(finite_log2fc))
extExtremes::qnorm(finite_log2fc)
```

- 3. Set up parameter values for the simulation run:

```
library (powsimR)
params <- estimateParam(
countData = arab_infection,
Distribution = "NB",
RNAseq = "bulk",
Normalisation = "TMM")
```

de_opts <- setup(
n = 1000,
propDE = 0.1,
log2fc = finite_log2fc,
nsims = 25,
params = params)

- 4. Run the simulation:

```
simDE <- simulateDE(de_opts,
test_method = "edgeR-LRT",
Normalisation = "TMM",
verbose = FALSE)
```

- 5. Run the evaluation:

```
evalDE <- evaluate(simDE,
method = "adjusted",
alpha = 0.1,
stratify = "mean",
filter = NULL,
target = "log",
delta = 0)
```

- 6. Plot the evaluation:

```
plotEvaluateDE(evalDE,
rate = "marginal",
quick = FALSE,
annotate = TRUE)
```

## How it works

In step 1, the rbioinfcookbook is loaded. Then, the rowMeans() function is used to calculate the mean of the mock samples and assign the result to log2fc.

In step 2, the is.finite() function is used to select only finite log2fc. This is done to ensure any potential infinite ratios caused by zero count are removed. The plot() function is then used to create a density plot of the log2fc, and the qnorm() function from the extExtremes library is used to create a quantile-quantile plot of log2fc.

In step 3, the estimateParam() function from powsimR is used to estimate the parameters needed to run a simulation based on the data. The distribution of the data is specified as a negative binomial, the type of RNA sequencing is specified as bulk, and the normalization method is specified as TMM. The result is assigned to params.

Then, the Setup() function from powsimR is used to set up the options for the simulation run. The number of genes is set to 1000, the proportion of differentially expressed genes is set to 0.1, the log2 change ratios are set to finite_log2fc, and the estimated parameter values are set to params. The result is assigned to de_opts.

num_replicates is then defined as a vector with values of 3, 6, 12, and 18.

In step 4, the simulateDE() function from powsimR is used to run the simulation with the options specified in de_opts. The method for identifying identifying expressed genes is edgeR-LRT, the normalization method is specified as TMM, and verbosity is turned off. The result is assigned to simDE.

In step 5, the evaluate() function from powsimR is used to evaluate the results of the simulation stored in simDE. The type of adjustment is specified as adjusted, the multiple test method is specified as the Benjamini-Hochberg procedure, the normal alpha level is set to 0.1, the data is stratified by mean expression level, no filtering is applied, the first stratum is used for filtering, the target for evaluation is log fold change, and the delta value is set to 0. The result is assigned to evalDE.

This shows the proportion of differentially expressed:
[1] 0.20
