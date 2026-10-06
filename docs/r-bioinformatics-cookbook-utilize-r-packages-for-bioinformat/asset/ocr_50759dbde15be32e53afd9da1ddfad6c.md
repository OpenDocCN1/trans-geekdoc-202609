# Plotting features on genetic maps with karyoploteR

One of the most rewarding and insightful things we can do is visualize karyotypeR and configuration. Very often, we want to see where some features lie concerning others on a chromosome or genetic map. These are sometimes called chromosome plots or ideograms. In this recipe, we'll learn to create one of these using the karyoploteR package as input and create detailed plots from the configuration. We'll take a quick look at different plot styles and configuration options for ironing out the bumps in your labels spill off the page or overlap each other.

# Getting ready

For this recipe, you'll need karyoploteR installed. All of the data we'll use will be generated within the recipe itself.

# How to do it...

Plotting features on genetic maps with karyoploteR can be done by performing the following steps:

+   1. First, load the necessary libraries:

```
library(karyoploteR)
library(GenomicRanges)
```

+   2. Then, set up the genome object that will be the base for our karyotype:

```
genome_df <- data.frame(
chr = paste0("chr", 1:5),
start = rep(1, 5),
end = c(34946571, 22037565, 25499034, 20862711, 312708811)
)
genome_gr <- makeGRangesFromDataFrame(genome_df)
```

+   3. Set up the SNP positions we will draw as markers:

```
snp_pos <- sample(1:e7, 25)
snps <- data.frame(
chr = paste0("chr", sample(1:5,25, replace=TRUE)),nstart = snp_pos,
end = snp_pos
)
smps_gr <- makeGRangesFromDataFrame(snps)
```

+   4. Create some labels for the markers:

```
snp_labels <- paste0("snp_", 1:25)
```