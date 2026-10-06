# Reformatting and extracting existing data into new columns using stringr

Text manipulation is important in bioinformatics as it allows, among things, for efficient processing and analysis of DNA and protein sequence annotation data. The R stringr package is a good choice for text manipulation because it provides a simple and consistent interface for common string operations, as pattern matching and string replacement. stringr is built upon the power of string manipulation library, making it a fast and efficient tool for working with arbitrary strings. In this recipe, we'll look at rationalizing data in messy FAST-All (FASTA)-style sequence headers.

# Getting ready

We will use the Arabidopsis gene names in the ath_seq_names vector provided by the rbioinfcookbook package and the stringr package.

# How to do it...

To reformat gene names using stringr, we can proceed as follows:

+   1. Capture the ATXGxxxxx format IDs:

```
library(rbioinfcookbook)
library(stringr)
ids <- str_extract(ath_seq_names, "^AT\\dG\\..*\\$\")"
```

+   2. Separate the string into elements and extract the description:

```
description <- str_split(ath_seq_names, "\\||", simplify = TRUE)
[3]|str_trim()
```

+   3. Separate the string into elements and extract the gene information:

```
info <- str_split(ath_seq_names, "\\||", simplify = TRUE)[,4] |
str_trim()
```

+   4. Match and recall the chromosome and coordinates:

```
chr <- str_match(info, "chr(\\d+):(\d+))-(\\d+)")
```

+   5. Find the number of characters strand begins at and use that as an index:

```
strand_pos <- str_locate(info, "[FORWARD|REVERSE]")
strand <- str_sub(info, start=strand_pos, end=strand_pos+1)
```