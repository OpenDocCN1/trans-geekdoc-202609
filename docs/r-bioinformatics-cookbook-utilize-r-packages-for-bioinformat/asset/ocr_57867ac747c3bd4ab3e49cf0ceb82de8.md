# Making interactive plots with plotly

Interactive plots are great tools for data exploration, allowing users to explore interactively large datasets to gain insights and identify patterns in data. They are useful for programmers wishing to create dashboards for visualizing real-time data and help with interactive presentations that communicate complex data relationships in an engaging manner. plotly is a data visualization library for Python, R, and JavaScript. It provides a high-level interface for drawing attractive and interactive statistical graphics, and the ggplot package in R allows you to convert static ggplot2 to interactive plots through a high-level interface. In this recipe, we'll create a fairly involved ggplot visualization of mutation sites on a genome and then convert it to plotly to get a first-level interaction layer.

# Getting ready

We'll need the ggplot2, plotly, and rbioinfbook packages for this recipe. The allele_freq data object that is a frame of allele frequencies of single nucleotide polymorphisms (SNPs) from genomic sequencing of a bulked population of Arabidopsis mutant line. The columns give the genomic positions of the SNP, the reference and alternative alleles, and information on the effect of the mutation in the genome.

# How to do it...

The steps we need to create an interactive plot are set out as follows:

+   1. Create a ggplot:

```
library(ggplot2)
library(plotly)
library(rbioinfbook)

p <- ggplot(allele_freq) +
  aes(x = Pos, y = Allele_Freq, label = info) +
  geom_point(aes(color = type)) +
  facet_grid(Chr ~ , scales = "freex", space = "free") +
  scale_colour_manual(values = c("steelblue", "gray", "goldenrod", "red\)) +
  theme_minimal()
```

+   2. Convert it to plotly:

```
ggplot(p, dynamicTicks = TRUE,
  dragmode = "zoom",
  tooltip = c("Chr", "Pos", "info")
)
```