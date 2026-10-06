# Analyzing Gene Annotations

```
Red5_PS1_1.69.0
## 3 acomosus_eg_gene Ananas comosus genes
(F153) F153
## 4 ahalalleri_eg_gene Arabidopsis ahalalleri genes
(Ahal2.2) Ahal2.2
## 5 lyrata_eg_gene Arabidopsis lyrata genes
(v.1.0) v.1.0
## 6 aiofficialis_eg_gene Asparagus officinalis genes (Aspof.
V1) Aspof_V1
```

Then, one of the lyrata_eg_gene datasets to use in use() to create a connection to the dataset, storing the connection in data_set_connection.

By the end of step 4, we're done working out which datasets we can use. We use data_set_connection to connect via listAttributes() and get a dataframe of types of information we can get.

In step 5, we finally get some information with the main function, getBM(). We set the attributes to the name we want to get back; here, we get all values for chromosome_name and store them in chrom_names.

In step 6, we use filters to restrict the values we wish to receive. We first ask the data_set_connection object which filters we can use with the listFilters() function; that one we can filter on chromosome_name so we'll use.

In step 7, we set up a full query. To get all genes on the first chromosome –we have a vector of these result of step 5, we take the first element of chrom_names and perform the query with getBM() asking for the ensembl_gene_id and description attributes; we set to filter on the chromosome name (any value from the attributes list can be used). We also pass the actual connection object defining the BioMart to use. We get back a dataframe of gene IDs and descriptions filtered to be on the first chromosome.

# Getting Gene Ontology information for functional analysis from appropriate databases

The Gene Ontology (GO) is a very requested vocabulary of annotation terms for genes and gene products that describe the biological process, molecular function, or cellular component of an annotated entity. As, the terms are helpful as data in gene-set enrichment analysis and other functional -omic approaches. In this recipe, we'll look at how we prepare a list of gene IDs in a genomic region and the GO IDs and descriptions for them.

# Getting ready

We will just need the biomaRt package from Bioconductor and an internet connection.