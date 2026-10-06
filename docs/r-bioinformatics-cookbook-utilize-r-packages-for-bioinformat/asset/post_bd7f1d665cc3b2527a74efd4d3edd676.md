
# Creating figures of protein domains using drawProteins

Protein visualization is a powerful tool in bioinformatics that allows researchers to explore the structure and function of proteins. Visualizing proteins in two domains can help researchers understand and compare the structures of different proteins, which can reveal similarities and differences that may be important for understanding their function. This can be particularly useful in the study of evolutionary relationships between proteins.

In this recipe, we'll look at a package drawProteins that can create two-dimensional renders of proteins and their domains. The package seems to have been designed to work best with Uniprot data input, but we'll look at setting up data so that you can use protein and domain information from any source.

# Getting ready

To complete this recipe, you will need the drawProteins Bioconductor package. We'll generate the sample data in the code as understanding it is the key part of this recipe.

# How to do it...

Rendering some proteins into a two-dimensional structure begins by defining the DataFrames of chain elements to be plotted:

- 1. Define a DataFrame of chain information:

```
chain_df <- tibble(
  "type" = "CHAIN",
  "description" = c("example protein", "different protein"),
  "begin" = c(1,1),
  "end" = c(300, 450),
  "length" = c(300, 450),
  "accession" = c("AB1", "AB2"),
  "entryName" = c("protein_1", "protein_2"),
  "taxid" = c(2712, 2712),
  "order" = c(1,2)
)
```

- 2. Define a DataFrame of domain information:

```
domain_df <- tibble(
  "type" = "DOMAIN",
  "description" = c("dom1", "dom1", "dom2"),
  "begin" = c(100, 150, 350),
  "end" = c(200, 250, 420),
  "length" = c(100, 100, 70),
  "entryName" = c("protein_1", "protein_2", "protein_2"),
  "taxid" = c(2712, 2712, 2712),
  "order" = c(1,2,2)
)
```

Render the plot in drawProteins:

```
library(drawProteins)
protein_df <- dplyr::bind_rows(chain_df, domain_df)

draw_canvas(protein_df) |>
draw_chains(protein_df) |>
draw_domains(protein_df, label_domains = TRUE)
```

With that, we have a nice plot of the protein and its domains.

# How it works...

The key to using drawProteins is to get the DataFrame format right. The structure is shallow but hierarchical within a single DataFrame. Each protein is referenced as a chain defined in rows; this is what we did in step 1. Consider this to be the backbone that defines the extent of the protein. The type column must contain the length of the sequence of amino acids. The accession should contain an accession if one is available, and the entryName should contain the key that identifies this protein - so, a unique protein name. The taxid column is a little irrelevant most of the time and I usually put the National Center for Biotechnology Information (NCBI) taxonomy identifier for Arabidopsis (2712). The order determines the position the protein will be drawn on the Axis, so each row should be unique.

In step 2, we set up the next layer of structure, defining the domains that will be plotted onto the backbones. type must be "DOMAIN". description gives us the name. This doesn't need to be unique - the same sort of domain can appear on multiple proteins. In this DataFrame, begin, end, and length refer to the values for the individual domain on the particular protein. The crucial column, entryName, defines which protein domain belongs to. Again, taxid is largely irrelevant. order is the position on the Y axis that the domain should render, so it should match the order of protein it belongs to.

By step 3, we can combine the DataFrames into one and then pass that to drawProteins functions to draw the things. The output looks like what's shown in Figure 8.2:

# Creating figures of protein domains using drawProteins

![](img/dd0d7d9aaacf496c4d1d0e31d8378b3_0.png)

Figure 8.2 - A drawProteins protein plot

This is an accurate, if basic, representation of our species.

# There's more...

The returned object from drawProteins is a ggplot2 object, so it can be themed using theme_*. Figure 8.3 shows what a cleaned-up version of Figure 8.2 would look like if theme_minimal() were applied:

![](img/dd0d7d9aaacf496c4d1d0e31d8378b3_1.png)

Figure 8.3 - A nicer themed plot

As we can see, adding theme_minimal() gives us a nicer background.

# Performing multiple alignments

Aligning sequences before building phylogenetic trees or determining conserved and divergent sequences is a mainstay in bioinformatics analysis and is amply covered in R Bioconductor with msa. We'll look at the straightforward procedures for going from sequence to alignment. In the first part of this recipe, we'll look at sequences on the order of a couple thousand residues, such as those that represent genes and proteins.

# Getting ready

For this recipe, you'll need the msa package. This is a pretty package and includes external software: Clustal, Clustal Omega, ape and seqin also needed. As a test dataset, we use hemoglobin sequences stored in own. You'll need a version of LaTeX on your system too – if you have already installed, though you can get it from Bioconductor.

# How to do it?

Performing multiple alignments of genes or proteins can be done by performing the following steps:

- 1. Load in the necessary libraries and sequences:

```
library(msa)
seq_file <- fs::path("data", "hg.fa")
seqs <- readStringSet(seq_file)
```

- 2. Perform the multiple alignments:

```
alignment <- msa(seqs, method = "ClustalOmega")
```

- 3. Render a view of the result:

```
msaPrettyPrint(alignment, output="pdf", showNames="left", showLogo="none", file="whole_align.pdf")
```

- 4. View a zoomed-in region:

```
msaPrettyPrint(c(10,30), output="pdf", showNames="left", file="zoomed_align.pdf", showLogo="top", askOverwrite=FALSE);
```

This is all code we need to align the sequence and render the output:

# How it works...

This brief recipe gets us a good-looking alignment quickly. Performing MSA with msa is easy; let's take a look at the steps involved. In step 1, we load the packages and sequences with the common readStringSet function to give us an AAString object. In step 2, we give that object to the msa() function and the name of an alignment. We use ClustalOmega (you can choose ClustalOmega, ClustW, or Muscle), which specifies the program to use to do the alignment. The align runs and you get back an MSAAlignment object, which is a container for the aligned sequences. It looks like this:

```
## ClustalOmega 1.2.0
##
## Call:
msa(segs, method = "ClustalOmega")
##
## MsaMultipleAlignment with 3 rows and 142 columns
##
aln
    names
## [1] MVLSPADKTNVKAAKGVGHAGEYGA..ETPHAVLASDKFLASVSTVLKYR HBA_HUMAN
## [2] MVLSGDKNIKAAWKKGIGHAGEYGA..ADTPHAVLASDKFLASVSTVLKYR HBA_MOUSE
## [3] MLSLRTERTIILWSKISTQADADVGT..ADTAHAAWKLFLISVSGVLTEKR HBA_CAPHI
## Con MVLSDKTNIKAAWKKGIGHAEYGA..ADTPAVHAVLASDKFLASVSTVLKYR Consensus
```

In step 3, we write a visualization of the alignment to a PDF file using the msaPrint() function. This function takes many arguments that describe the output. The visualization must be written to a file. It can't be sent to a window like a normal plot. Figure 8.4 shows the alignment visualization we just created:

# Searching Gene and Protein Sequences for Domains and Motifs

| Name | Sequence | Length |
| :--- | :--- | :--- |
| HBA HUMAN | VHLTPEEKSAVSAALAHGKHKVVEALVKAHYFRGSAHHGTVGLDSAHKGAEVAAALALFDLERAEH | 110 |
| HBA MOUSE | VHLTPEEKSAVSAALAHGKHKVVEALVKAHYFRGSAHHGTVGLDSAHKGAEVAAALALFDLERAEH | 110 |
| HZ CAPHI | VHLTPEEKSAVSAALAHGKHKVVEALVKAHYFRGSAHHGTVGLDSAHKGAEVAAALALFDLERAEH | 110 |
| consensus | | * * * * * * * * * * * * * |

- non-conserved
- >50% conserved

Figure 8.4 – A full-length alignment

In *step 4*, we use the second positional argument of *aaPrettyPrint* to restrict the view between 10 and 30, which results in the output shown in *Figure 8.5*.

![](img/dd0d7d9aaacf496c4d1d0e31d8378b3_246_0)

Figure 8.5 – A zoomed-in alignment

# There’s more...

A tree visualization of sequence similarity is often useful at this stage. We can generate one of these with the ape and seqinr packages. We can convert our alignment object into a seqinr distance object that describes the sequence distances, and from that, use ape to create a simple neighborjoining tree that we can plot. This looks as follows:

# Phylogenetic Tree of HBA Sequences

![](img/dd0d7d9aaacf496c4d1d0e31d8378b3_246_1)

Figure 8.6 – A tree of the alignment
