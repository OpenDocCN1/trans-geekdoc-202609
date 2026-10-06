# Analyzing Gene Annotations

In this case, this is the same as the columns wasn't always be. Now that we know the data can get out and the type of data we can query, we need some values for the query keys, which may often come from your analysis, but for this example, we have the gene_symbols data from the rbioinfcookbook package that contains a vector of 10 symbols. We apply this in step 3 using the select () function, using the keytype argument to SYMBOL, and asking for the ATLAS, GO, and UNIPROT IDs with the symbols. Note that the annot dataframe is over 1000 rows, indicating one-to-many relationships in the data, particularly in the GO IDs.

In step 4, we expand on the GO annotations; we only received an ID in the previous step, but we really want the full description well. That wasn't in the org.Hs.eg db columns so we couldn't retrieve it from that annotation package. We can retrieve it from the specialized GO db package, which uses virtually the same syntax, so step 4 echoes step 3 with values for keys from the annot specific columns selected. Finally, in step 5, we combine the two search results into one dataframe.

# See also

Bioconductor provides a resource called AnnotationHub, which is a web interface about 800 online resources. The AnnotationHub package provides functions for accessing the data in easily and programmatically. The data types covered are much more wide-ranging than those in the AnnotDB packages and searching it can save a lot of processing time.

# Using ClusterProfiler for determining GO enrichment in clusters

GO analysis involves using ontologies to annotate genes based on their biological function, cellular component, and molecular processes. The GO Consortium provides a controlled vocabulary of terms that describe gene function, and these terms are arranged in a hierarchical structure. It aids in the interpretation of high-throughput genomic data, such as microarray and RNA-seq data, by identifying enriched biological terms and pathways among the differentially expressed genes.

In Bioconductor, GO analysis can be performed using various packages as org.Hs.eg db, GOStats, and clusterProfiler. These packages allow the user to map gene identifiers to GO and perform statistical tests to identify enriched terms in a set of genes.

In this recipe, we will look at how to go from a set of genes in a generic input to assessing them with plots from different GO-related packages.

# Getting ready

For this recipe, we'll need the clusterProfiler and ggplot Bioconductor packages. We will take a dataframe of expression values for Magnaporthe oryzae genes and a dataframe of full GO annotation in the rbioinfcookbook data package.