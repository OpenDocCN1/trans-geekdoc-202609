
# 3D structure protein alignment in bio3d

step. You can use the whole sequence as well. The getPredictionProfile() function needs the kernel and model objects to work.

In step 6, we plot () the prediction profile. This profile shows the contribution of each amino acid to the overall decision and adds to the interpretability of the learning results. Here, the fourth residue, D, makes a strong contribution to the decision made for this profile. By examining this across many sequences, the patterns contributing to the decision can be elucidated. It's worth noting that you may get a slightly different picture to that in Figure 8.9 – because of random parts of this recipe and algorithm – so you should build into your analysis: make sure that any differences aren't due to random choices while running the code. The strongest contribution should still come from D in this example:

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_253_0.png)

This prediction profile is a simple but effective display of the most important amino acids.

# 3D structure protein alignment in bio3d

Three-dimensional structural alignments between two molecular models can reveal structural properties that are common or unique to either of the proteins. These can suggest evolutionary or functional commonalities. In this recipe, we'll look at how to get the alignment of two protein sequences in dimensions and view them in 3D.

# Getting ready

For this recipe, we need to install a sequence aligner. We'll take advantage of the fact that the msa package comes with a version of MUSCLE and install that. You can also use conda to install it separately.

We will also need to install a viewer. We will use PyMOL, which can be installed into a conda environment as follows:

```
conda install -c conda-forge -c schrodinger pymol-bundle
```

# Searching Gene and Protein Sequences for Domains and Motifs

We'll also use the bio3d package and some data files in the rbioinfcookbook package.

# How to do it...

We can predict structure by performing the following steps:

- 1. Load the necessary library and files:

```
library (bio3d)

flxwc.pdb <- fs::path_package(
  "extdata",
  "1xwc.pdb",
  package="rbioinfcookbook"
)
f3trx.pdb <- fs::path_package(
  "extdata",
  "3trx.pdb",
  package="rbioinfcookbook"
)

a <- read.pdb(flxwc.pdb)
b <- read.pdb(f3trx.pdb)
```

- 2. Carry out the alignment:

```
pdbs <- pdbaln(list("1xwc"=a,"3trx"b), fit=TRUE, exfile="msa")
```

- 3. Launch and render the alignment in PyMol:

```
env_path <- function(env, program = "") {
  df <- reticulate::conda_list(
  b <- df$python[which($dfname == env)]

  if (length(b) == 0) {
    stop("no environment with name found")
  }

  file.path(dirname(b), program)
}

pymol_path <- env_path("informatics_project", "pymol")

pymol(pdbs, exfile = pymol_path, type = "launch", as="cartoon")
```

These are all the steps we need to perform to get a rendered view of our predicted structure.

# How it works...

As usual, step 1 is to load the library and the input data – two different protein database (PDB) files with the read.pdb() function. In step 2, we do the alignment with the pbaln() function. All the PDBs we want to align into a list object with an appropriate name. The fit argument is set to TRUE to carry out the superposition of the structures based on all the aligned sequences. The exefile argument tells the function where to find the aligner – here, a value of msa tells it to look in the msa package we installed.

Once we have an alignment, we want to visualize it in PyMOL. The executable is installed in a conda environment so that we can use the custom env_path() function defined at the start of step 3 to extract the path and pass it to pymol() as an argument. PyMOL should start and the alignment render.

# There’s more...

If you don’t want to use MUSCLE in msa, you can use a path to an alternative executable in step 2 or replace exefile with web.args="your.email@something.org" to carry out the alignment over the web at EBI.

Omitting the type argument in step 3 will result in a PyMOL script being written that you can use in a separate PyMOL session.

# Phylogenetic Analysis and Visualization

Phylogenetics is the study of the evolutionary relationships among species or other groups of organisms. It involves the use of molecular and computational techniques to construct phylogenetic trees, which depict the evolutionary history of the organisms under study.

In bioinformatics, phylogenetics is studied using various computational tools and methods, including sequence alignment, distance-based methods, maximum likelihood, and Bayesian inference. These methods allow researchers to compare DNA or protein sequences from different organisms and infer their evolutionary relationships based on similarities and differences in their genetic makeup. Phylogenetics has many applications in biology, and is used to help understand the evolutionary history of species, to study the origins and spread of diseases (phylogenetic analysis can be used to trace the origins and spread of infectious diseases), and to inform conservation efforts by identifying species or populations that are evolutionarily distinct and particularly important to preserve.

Phylogenetics has a long history in R and not just in Bioconductor. In the recipes in this chapter, we will take a good look at how to work with tree formats from a variety of sources. A key focus will be how to manipulate trees to focus on particular parts and with visualizations based on ggttree-based packages, and the latter's usefulness in viewing and annotating large trees.

In this chapter, we will cover the following recipes:

- Reading and writing varied tree formats with `ape` and `treeio`
- Visualizing trees of many genes quickly with `ggtree` 
- Quantifying and estimating differences between trees with `treespace`
- Extracting and working with subtrees using `ape`
- Creating dot plots for alignment visualizations
- Reconstructing trees from alignments using pangorn
- Finding orthologue candidates using reciprocal BLASTs

# Technical requirements

We will use renv to manage packages in a project-specific way. To use renv to install packages, you will first need the renv package. You can do this by running the following commands in your console:

- 1. Install renv:

```
install.packages("renv")
```

- 2. Create a new renv environment:

```
renv::init()
```

This will create a new directory called .renv in your current project.

- 3. You can then install packages with the following:

```
renv::install()
```

- 4. You can also use the renv package manager to install Bioconductor packages by running the following command:

```
renv::install("bioc::package name")
```

- 5. For example, to install the Biobase package, you would run this:

```
renv::install("bioc::Biobase")
```

- 6. You can use renv to install development packages from GitHub like this:

```
renv::install("user name/repo name")
```

- 7. For example, to install the damnaclean user rbioinfcookbook package, you would run this:

```
renv::install("damnaclean/rbioinfcookbook")
```

You can also install multiple packages at once by separating the package names with a comma. renv will automatically handle any required dependencies for the packages you install.

Under renv, all packages will be installed in the local project directory and not the main central library, meaning you can have multiple versions of the same package, one specific for each project.

All the sample data you need for this package is in the specially created data package on GitHub, damnaclean/rbioinfcookbook. The data will become available in your project after installing that.

For this chapter, we'll need the following packages:

- Regular packages:
  * adographics
  * ape
  * cowplot
  * data.table
  * dplyr
  * fs
  * ggplot2
  * pangorn
  * readr
  * reticulate
  * treespace
 GitHub:
  * damnaclean/rbioinfcookbook
  * evolvedmicrobe/dotplot
- Bioconductor:
  * Biostrings
  * dotplot
  * ggtree
  * msa
  * treeio

In addition to these packages, we will also need some R tools, such as conda. All these will be described when needed.
