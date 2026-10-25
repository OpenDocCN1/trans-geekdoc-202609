first. To begin, let's go back to the Swiss banknote data from Figure 2.1. As discussed in Section 1.4.1, these data contain six continuous measurements on 200 Swiss 1000-franc banknotes: 100 genuine and 100 counterfeit. The goal is to use the six available features to classify new Swiss banknotes as either genuine or counterfeit.

The code chunk below loads the data into R and prints the first few observations:

```
head(bn <- treemisc::banknote) # load and peek at data

#>  length left right bottom  top diagonal y
#> 1   215  131   131    9.0  9.7      141 0
#> 2   215  130   130    8.1  9.5      142 0
#> 3   215  130   130    8.7  9.6      142 0
#> 4   215  130   130    7.5 10.4      142 0
#> 5   215  130   130   10.4  7.7      142 0
#> 6   216  131   130    9.0 10.1      141 0
```

A tree diagram representation of the Swiss banknote regions from Figure 2.1 is displayed in Figure 2.2. The bottom number in each node gives the fraction of observations that pass through that node (hence, the root node displays 100%). The values in the middle give the proportion of counterfeit and genuine banknotes, respectively, and the class printed at the top corresponds to the larger fraction (i.e., whichever class holds the majority in the node). The number above each node gives the corresponding node number. This is an example classification tree that can be used to classify new Swiss banknotes. For example, any Swiss banknote with bottom > 9.55 would be classified as counterfeit (y = 1); note that the split points are rounded for display purposes in Figure 2.2. The proportion of counterfeit bills in this node is 0.977 and can be used as an estimate of Pr (Y = 1|x); but more on this later.

From this tree, we can construct three simple rules for classifying new Swiss banknotes using just the bottom and top length of each bill:

```
Rule 1 (path to terminal node 2)
IF  bottom >= 9.55 (mm)
THEN classification = Counterfeit (probability = 0.977)
```

```
Rule 2 (path to terminal node 6)
IF  bottom < 9.55 (mm) AND top >= 11.15 (mm)
THEN classification = Counterfeit (probability = 0.765)
```

```
Rule 3 (path to terminal node 7)
IF  bottom < 9.55 (mm) AND top < 11.15 (mm)
THEN classification = Genuine (probability = 0.989)
```

This tree was found using the CART algorithm as implemented in rpart; the corresponding R code is used in Section 2.9.1. But how did CART determine