We passed that information to run_meme () , along with the DNAstringSet object containing the sequences. The function also needed an output directory to write results as it doesn't return anything useful to R. The run_meme () function executes MEME in the background and once the run is finished, we can load results from the meme .txt file using read_meme (). It returns a universalmotif object. We can inspect the motifs found with the view_motifs () function – looks like what's shown in Figure 8.1.

![](bbox=[0.186, 0.233, 0.814, 0.442])

Figure 8.1 – Motifs found in sequences

The plot is a standard Logo-style plot in which the contribution of base in the motif is represented by its size in the Logo.

# There’s more...

Loading in motifs from databases such as JASPAR and TRANSFAC is very easy with universalmotif as there are straightforward replacements for the read_matrix () function. To load motifs in various formats, we can use the read cisbp(), read_homer(), read_jaspapr(), read_matrix(), read_meme(), read_motifs(), and read_uniprombe() functions.

# Finding protein domains with PFAM and bio3d

Decoding the function of a protein sequence is a key task. We can do this in many ways, including conducting whole sequence searches against databases of known proteins using tools as BLAST. If we want more informative and granular information, we can instead look for individual functional domains within a sequence. Databases such as PFAM and tools as hmmmer encode domains from Hidden Markov Models, which hmmmer uses to scan sequences and report any likely occurrences of the domains. Often, gene annotation projects will carry out the searches for us, which is a question of searching a database. Bioconductor does a great job of packing up the data in these databases in particular packages, usually with names ending in .db. In this recipe, we’ll look at how to work out