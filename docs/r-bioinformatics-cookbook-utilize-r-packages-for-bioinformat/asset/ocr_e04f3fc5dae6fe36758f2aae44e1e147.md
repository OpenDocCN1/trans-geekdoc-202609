# How it works...

There is a surprisingly large amount of stuff going on in this very short recipe. The general outline is that we need to define two sets of filtering rules (prefilter and filter). This is achieved by defining functions that parsed the VCF record and return TRUE if the record passes. Prefilters are generally text-based filters on the raw data of the record–the is_not_microsat() function that does by using grepl to get the word microsat in the record. The function is bundled into a FilterRules object called prefilters.

The filters are more complex. These take the parsed VCF records and operate on. Our major-alt() function uses the info() VCF accessor function to extract data from the record. It returns a DataFrame in each column is a part of the info. We extract the AF column, returning a list with an element for each VCF. To iterate over these elements, we use the lapply() function to apply an anonymous function that returns TRUE if the reference allele has a proportion lower than 0.5. We unlist() to get to a vector. We bundle the function into a FilterRules object filters.

With all the setup, we load the VCF file and run filtering with filterVCF(), after we write the results to the output file, filtered.vcf.

# See also

When using the filter function, we can take advantage of other accessor functions to get at different parts of the VCF record. There are geno() and fixed() functions that return data structures describing these parts of the VCF. You can use these to create filters in the way we did with info().

# Extracting information in genomic regions of interest

Often, you'll want to look in more detail at that falls into a particular genomic region of interest, whether that be the SNPs and variants in a gene or at a particular location. This common task is handled well by the powerful GRanges and SummarizedExperiment objects. They are a little fiddly to set up but have very flexible subsetting operations that make the effort worth it. In this recipe, we'll look at a few ways to set up these objects and a few ways we can manipulate them to get interesting information.

# Getting ready

For this recipe, we will need the GenomicRanges, SummarizedExperiment, and tracklayer Bioconductor packages. We will also use a GFF file of features of the Arabidopsis chromosome 4 and a smaller text version of gene features only. These are both in the rbioinfcookbook package, so we'll extract them from them.