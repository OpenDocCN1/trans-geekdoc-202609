
## Getting ready

We'll need a tabix index VCF file; one is provided in the rbioinf package. To extract it, we'll use the fs package. For analysis, we shall use the VariantAnnotation Bioconductor package.

## How to do it...

Selecting and classifying variants with VariantAnnotation can be done by:

- 1. Create a prefilter function:

```r
library(VariantAnnotation)
is_not_microsat <- function(x) { grepl("microsat", x, fixed = TRUE) }
```

- 2. Load the prefilter function:

```r
prefilters <- FilterRules(list(microsat = is_not_microsat) )
```

- 3. Create a filter to keep variants where the reference allele is represented in less half the reads:

```r
major_alt <- function(x) {
af <- info(x) $AF ## also geno(fixed)
result <- unlist(lapply(af, function(x) (x[1] < 0.5))
return(result)
}
```

- 4. Load the filter function into a FilterRules object:

```r
filters <- FilterRules(list(alt_is_major = major_alt) )
```

- 5. Load the input VCF and apply filters:

```r
vcf_file <- fs::path_package("extdata",
  "sample.vcf.gz",
  package="rbioinfcookbook"
)
filterVcf(vcf_file, "hg17", "filtered.vcf", prefilters =
prefilters, filters = filters)
```

This is all we need to do to filter variants.

## How it works...

There is a surprisingly large amount of stuff going on in this very short recipe. The general outline is that we need to define two sets of filtering rules (prefilter and filter). This is achieved by defining functions that parsed the VCF record and return TRUE if the record passes. Prefilters are generally text-based filters on the raw data of the record–the is_not_microsat() function that does by using grepl to get the word microsat in the record. The function is bundled into a FilterRules object called prefilters.

The filters are more complex. these take the parsed VCF records and operate on. Our major-alt() function uses the info() VCF accessor function to extract data from the record. It returns a DataFrame in each column is a part of the info. We extract the AF column, returning a list with an element for each VCF. To iterate over these elements, we use the lapply() function to apply an anonymous function that returns TRUE if the reference allele has a proportion lower than 0.5. We unlist() to get to a vector. We bundle the function into a FilterRules object filters.

With all the setup, we load the VCF file and run filtering with filterVCF(), after we write the results to the output file, filtered.vcf.

## See also

When using the filter function, we can take advantage of other accessor functions to get at different parts of the VCF record. There are geno() and fixed() functions that return data structures describing these parts of the VCF. You can use these to create filters in the way we did with info().

## Extracting information in genomic regions of interest

Often, you'll want to look in more detail at that falls into a particular genomic region of interest, whether that be the SNPs and variants in a gene or at a particular location. This common task is handled well by the powerful GRanges and SummarizedExperiment objects. They are a little fiddly to set up but have very flexible subsetting operations that make the effort worth it. In this recipe, we'll look at a few ways to set up these objects and a few ways we can manipulate them to get interesting information.

## Getting ready

For this recipe, we will need the GenomicRanges, SummarizedExperiment, and tracklayer Bioconductor packages. We will also use a GFF file of features of the Arabidopsis chromosome 4 and a smaller text version of gene features only. These are both in the rbioinfcookbook package, so we'll extract them from them.

## How to do it...

Extracting information in genomic regions of interest can be done by performing the following steps:

- 1. Load in the packages and define some custom functions that create GRanges from common files: 

```r
library(GenomicRanges)
library(rtracklayer)
library(SummarizedExperiment)

get_ranges_from_gff <- function(file_name) {
  gff <- rtracklayer::import.gff(file_name)
  as(gff, "GRanges")
}

get_ranges_from_bed <- function(file_name) {
  bed <- rtracklayer::import.bed(file_name)
  as(bed, "GRanges")
}

get_ranges_from_text <- function(file_name) {
  df <- readr::read_tsv(file_name, col_names = TRUE)
  GenomicRanges::makeGRangesFromDataFrame(df, keep.extra.columns = TRUE)
}

get_annotated_regions_from_gff <- function(file_name) {
  gff <- rtracklayer::import.gff(file_name)
  as(gff, "GRanges")
}
```

- 2. Create GRanges using these functions:

```r
library(rbioinfcookbook)
gff_file <- fs::path_package(
  "extdata",
  arabidopsis_chr4.gff",
  package="rbioinfcookbook"
)
```

```r
txt_file <- fs::path_package(
  "extdata",
  "arabidopsis_chr4.txt",
  package="rbioinfcookbook"
)
```

```r
gr_from_gff <- get_annotated_regions_from_gff(gff_file)
gr_from_txt <- get_granges_from_text(txt_file)
```

- 3. Extract a region by filtering on attributes:

```r
genes_on_chr4 <- gr_from_gff[ gr_from_gff$type == "gene" &
seqnames(gr_from_gff) %in% c("Chr4") ]
```

- 4. Manually create a region of interest:

```r
region_of_interest_gr <- GRanges(
seqnames = c("Chr4"),
Ranges(c(10000), width= c(1000))
)
```

- 5. Use the region of interest to subset the larger object:

```r
overlap_hits <- findOveraps(region_of_interest_gr, genes_on_chr4)
features_in_region <- genes_on_chr4[overlap_hits]
```

## How it works...

In step 1, we create GRanges objects. In step 2, we use GFF and text to create. The general outline is that we need to define two sets of filtering rules (prefilter and filter). This is achieved by defining functions that parsed the VCF record and return TRUE if the record passes. Prefilters are generally text-based filters on the raw data of the record–the is_not_microsat() function that does by using grepl to get the word microsat in the record. The function is bundled into a FilterRules object called prefilters.

The filters are more complex. these take the parsed VCF records and operate on. Our major-alt() function uses the info() VCF accessor function to extract data from the record. It returns a DataFrame in each column is a part of the info. We extract the AF column, returning a list with an element for each VCF. To iterate over these elements, we use the lapply() function to apply an anonymous function that returns TRUE if the reference allele has a proportion lower than 0.5. We unlist() to get to a vector. We bundle the function into a FilterRules object filters.

With all the setup, we load the VCF file and run filtering with filterVCF(), after we write the results to the output file, filtered.vcf.

## Finding Genetic Variants with HTS Data

The output looks like this:

```
## GRanges objects with 1 range and 10 metadata columns:
##
    segnames        ranges strand
    source      type        phase      ID      Derives_from
    Note        Name
##    <Rle><Ranges><Rle> | <factor><factor><numeric>
    <integer><character><character> <CharacterList><CharacterList>
    <character> <character>
## [1]       Chr 2895-1045
    TAIR10          NA        <NA> AT4G0020    AT4G020
    protein_coding_gene     <NA>                 <NA>
    -------
## seqinfo: 1 sequence from an unspecified genome; no selens
```

This is a summary of the data in our original region of interest.

## There’s more...

It's also possible to extract the subsets of DataFrames or matrices in the same way by taking advantage of GRanges that are part of other objects. In the following example, we’re creating a matrix of random data and using that to build a SummarizedExperiment object that uses a GRanges object to describe its rows:

```r
set.seed(4321)
experiment_counts <- matrix(runif(4308 * 6, 1, 100), 4308)
sample_names <- c(rep("ctrl",), rep("test", ))
se <- SummarizedExperiment::SummarizedExperiment(gr_from
txt, assays = list(experiment_counts), colData = sample_names)
overlap_hits <- findOverlaps(region_of_interest_gr, se)
data_in_region <- se[subjectHits(overlap_hits)]
assay(data_in_region)
```

This will give us the following output:

```
## [1] [2] [3] [4] [5] [6]
## [1] 91.00481 34.41582 42.7602 36.13053 47.6775 19.21672
```

This shows the summary of the data in that region of interest from a different type of input object.
