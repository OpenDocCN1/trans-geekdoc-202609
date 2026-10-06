Other packages, as GOplot, offer alternative visualizations but need the enrichment
result in a different format. In step 6, we convert enrich object by creating a custom function
that extracts the gene names from the provided enrich object, converts the term type from
to initials (for example, from biological_process to BP) and creates a dataframe from
other data in the enrich object and returns that. After running that, we move on to step 7. To use
tnGOBubble function(), we need to rename the gene ID and expression value columns of our
mo_exp data to ID and logFC, prepare a dataframe of the right format from using
circle_dat() function. We pass the DAVID object and the expression data. We also
trim the GO definitions in the returned circle object, as they are very long strings so
don't render well in some plot types. Here, with dplyr::mutate() and substr(), we just take
the first 20 characters of the string and use that

Finally, in step 7, we get to plot; we use GOBubble() and par it options to ensure that we get all
GO categories in a single panel, the legend, and the bubbles are annotated with the GO ID
(not the full description). We get a plot as Figure 10.2.

![](bbox=[0.136, 0.381, 0.862, 0.663])

As we can see, it's a nice representation of the GO terms. It suffers a little for space sometimes, which
is why the accompanying table is useful.

# Finding GO enrichment in an Ontology Conditional way with topGO

The GO is a hierarchical ontology that describes the biological processes, molecular functions, and
cellular components of gene products in a standardized way. The ontology is structured as a directed\acyclic graph (DAG) with three main categories: Biological Process (BP), Molecular Function (MF),
and Cellular Component (CC).