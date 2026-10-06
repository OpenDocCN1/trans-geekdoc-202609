# Performing Quantitative RNA-seq

One tip I do have when installing this fiddly package is that it sometimes tells you lots of dependencies that you are certain are not installed. If this happens, restarting R and it should straighten things out.

The data we use for this recipe will be from a set Arabidopsis thaliana plant samples infected with Pseudomonas syringae hrc mutant versus a set of control infection samples (mock). There are three replicates in each sample type. These are available in the rbioinfcookbook data package as a single matrix with six columns called arab_infection.

# How to do it...

Let's do the analysis by performing the following steps:

+   1. Estimate the simulation parameter values:

```
library (rbioinfcookbook)

means_mock <- rowMeans(arab_infection
```

+   2. Examine the distribution of the log2fc change ratios:

```
finite_log2fc <- log2fc(is.finite(log2fc))
plot (density(finite_log2fc))
extExtremes::qnorm(finite_log2fc)
```

+   3. Set up parameter values for the simulation run:

```
library (powsimR)
params <- estimateParam(
countData = arab_infection,
Distribution = "NB",
RNAseq = "bulk",
Normalisation = "TMM")
```

```
de_opts <- Setup(
genes = 1000,
nsims = 25,

p.DE = prop_de,
plLFC = finite_log2fc,
```