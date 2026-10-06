# Using AnnoDB packages for genome annotation

Bioconductor AnnoDB packages provide a set of software tools and resources for the annotation and functional analysis of genomic data, including DNA sequences, microarray data, and high throughput sequencing data. These packages are designed to help researchers in the field of genomics to better understand the biological significance of their data by providing them with access to a comprehensive database of biological annotations and functional annotations, such as GO pathway analysis, and functional enrichment analysis.

The Bioconductor AnnoDB packages are designed to work with a wide range of genomic data types from various organisms and are regularly updated to include the latest annotations and functional information. Some of the key features of these packages include tools for mapping genomic data to annotated genomic features, tools for retrieving functional annotations for specific genomic regions, and tools for performing various types of functional analyses. In this recipe, we'll look at how to use an example AnnoDB package to get annotations on the human genome assembly.

# Getting ready

We'll need the Bioconductor org.Hs.eg db and GO.db packages, as well as the rbioinfocookbook and dplyr packages.

# How to do it...

Annotating a vector of H. sapiens gene symbols goes like this:

+   1. Load the library and check the available data:

```
library(org.Hs.eg.db)
columns(org.Hs.eg.db)
```

+   2. Check the searchable keys:

```
keytypes(org.Hs.eg.db)
```

+   3. Get a list of one isotype and search columns:

```
library(rbioinfocookbook)
annot <- select(org.Hs.eg.db,
keys = hu_gene_symbols,
keytype = "SYMBOL",
columns = c("ALIAS",
"GO",
"UNIPROT"))
```