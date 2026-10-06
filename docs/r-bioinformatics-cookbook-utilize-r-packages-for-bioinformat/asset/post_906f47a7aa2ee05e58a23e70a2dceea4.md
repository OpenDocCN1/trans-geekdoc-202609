
The final plot is created with the final call. We can't see it here as it's a dense multi-faceted plot with axes that do not render legibly in print format. You should be able to see it on your screen, though. Once you've got it, you should be able to see the different powers at different replicate numbers. Note that the X-axis identifies the number of replicate samples used and the metrics include False Detection Rate (FDR), False Negative/Positive Rate (FNR/FPR), and True Negative/Positive Rate (TNR/TPR).

## There’s more...

When we have only one sample (or maybe just one replicate), we have difficulty estimating the log2 fold change distribution and the number of differentially expressed genes. In place of estimates, we can use a function that generates numbers for us. The body of the function needs to generate numbers as needed. An example that normally distributed numbers with a mean of 0 and a standard deviation of 2 is as:

```
log2fc_func <- function(x) { rnorm(x, 0, 2) }
```

This can be used in place of the estimate in the PLFLC slot of the Setup() function.

## Finding unannotated transcribed regions

Finding unannotated regions can be useful in several different genomics applications. One of the main cases is identifying novel genes. Unannotated transcribed regions may represent novel genes that have not been previously identified.

By identifying these regions, researchers can gain a better understanding of the genome and potentially discover new biological pathways or proteins. Another use case is identifying alternative splicing, where different exons are used to create different protein products. Identifying these events can provide insight into how the genome is regulated and how different proteins are produced from the same gene. Additionally, unannotated transcribed regions may include **untranslated RNAs (UTRs)**, lncRNAs, miRNAs, and other types of non-coding RNAs, which can provide a more complete understanding of the functional elements in the genome and characterize the non-coding genome. Lastly, unannotated transcribed regions may also be specific to certain tissues, which can provide insight into tissue-specific functions and pathways. In this recipe, we’ll learn how to find regions in a genome that have sequence reads that can be mapped to them but are not currently covered by our available annotation.

## Getting ready

Conceptually, unannotated regions look like what's shown in Figure 6.2, with the annotated genes having reads aligned to them (known as coverage) and a third peak of reads in:

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_178_0.png)

Figure 6.2 - Example coverage diagram of our reads

We wish to find this unannotated region from the alignment directly. We'll need the Bioconductor csaw, IRanges, SummarizedExperiment, and rtracklayer packages to do so.

Our dataset will be a synthetic one that has a 6 kb genome region and two gene features. Aligned reads will be in a BAM file and the gene annotations will be in a GFF file. The data can be found in book's data package and the recipe explicitly shows how to get it.

## How to do it...

Here is how we can find unannotated regions:

- 1. Set up a loading function:

```
library(rtracklayer)
get_annotated_regions_from_gff <- function(file_name) {
gff <- rtracklayer::import.gff(file_name)
as (gff, "Ranges")
}
```

- Get counts in windows across the genome:

```
library (csaw)
library (rbioinfocookbook)
```

```
bam_path <- fs::path_package("extdata",
    "windows.bam",
    package="rbioinfocookbook"
)
```

```
gff_path <- fs::path_package("extdata",
    "genes.gff",
    package="rbioinfocookbook"
)
```

```
whole_genome <- csaw::windowCounts(
    bam_path,
    bin = TRUE,
    filter = 500,
    param = csaw::readParam(minq = 20,
        dedup = TRUE,
        pe = "both"
)
```

```
colnames(whole_genome) <- c("small_data")
annotated_regions <- get_annotated_regions_from_gff(gff_path)
```

```
windows_in <- IRanges::overlaps(whole_genome, annotated_regions)
```

```
annotated_regions <- whole_genome[windows_in, ]
```

```
nonannotated_regions <- whole_genome[!windows_in, ]
```

- 5. Put the data in:

```
window_counts <- data.frame(assay(nonannotated_regions))
window_ranges <- data.frame(ranges(nonannotated_regions))
results <- cbind(window_ranges, window_counts)
```

## How it works...

In step 1, a loading function is set up to import GFF using rtracklayer. Specifically, it takes a filename and returns it GRanges.

In step 2, csaw and rbioinfocookbook are loaded and the bam_path and gff_path are specified. The windowCounts function from csaw is used to count in windows. Then, the get_annotated_regions_from_gff function is called on gff and the resulting GRanges object

In step 3, IRanges and SummarizedExperiment are loaded and IRanges::overlaps() is used to identify which of the whole_genome overlap annotated regions. The result is a logical vector indicating whether each window, which is stored in windows_in.

In step 4, subsets of the whole_genome are created based on the windows_in vector. The annotated_regions holds the windows that overlapped annotated regions and nonannotated_regions holds the windows that did not.

In step 5, the assay() function is used to extract the count data from nonannotated_regions object and is converted into a more friendly DataFrame. Similarly, the ranges() function is used to output the windows that were used. The cbind function is used to join the DataFrames into one results. The output DataFrame contains the counts of reads in windows of width 500 across the entire genome that did not overlap with any regions - in this case, the genes. It looks like this:

```
## start end width_data
## 1 1501 2000 500 0
## 2 2001 2500 500 0
## 3 2501 3000 500 24
## 4 3001 3500 500 25
## 5 3501 4000 500 0
## 6 5501 6000 500 0
```
