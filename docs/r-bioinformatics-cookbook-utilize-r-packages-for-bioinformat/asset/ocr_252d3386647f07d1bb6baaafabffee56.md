# Phylogenetic Analysis and Visualization

Together these steps help us build trees with selected nodes.

# There's more...

A minor problem with the preceding functions is that they expect us to know the node number we want to work with. A simple way to access this is by using the interactive `subtreereeplot()` function. This `subtree` (newick) call will generate an interactive plot for the tree provided. By clicking on nodes, the image is updated to show the subtree and clicked node ID.

# Creating dot plots for alignment visualizations

Dot plots of aligned sequences are possibly the oldest alignment visualization. In these plots, the positions of two sequences are plotted on the x axis and y axis, and for every coordinate in space, a point is drawn if the letters (nucleotides or amino acids) correspond at (x,y) coordinate. Since the plot can show regions that match in the same region of the two sequences (as lines away from the diagonal), the plot is a good way to visualize plot insertions and deletions and structural rearrangements in the two sequences. In this recipe, we'll look at a speedy method for constructing a dot plot using the dotlot package and a bit of code for getting a grid plot of all pairwise dot plots for sequences in a file.

# Getting ready

We'll need the bhlh.fa file, which contains three basic helix-loop-helix (bHLH) transcription factors from pea, soy, and lotus. The file is provided by the rbioinf package. We'll also need the Biostrings package and the evolvedmicrobe/dotplot GitHub-hosted package.

# How to do it...

Generating dot plots for alignment visualization can be executed using the following steps:

+   1. Load the libraries and sequences:

```
library(Biostrings)
library(ggplot2)
library(dotplot)
seqfile <- fs::path_package(
  "extdata",
  "bhlh.fa",
```