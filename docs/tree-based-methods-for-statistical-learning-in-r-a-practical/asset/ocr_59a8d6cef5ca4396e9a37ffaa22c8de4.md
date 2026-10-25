```
#> 17) stalk.color.below.ring=brown 80 16 Edible (0.80000 0...
#> 34) stalk.root=bulbous 64 0 Edible (1.00000 0.00000) *
#> 35) stalk.root=missing 16 0 Poison (0.00000 1.00000) *
#> 9) stalk.color.below.ring=yellow 24 0 Poison (0.00000 1...
#> 5) spore.print.color=green 72 0 Poison (0.00000 1.00000) *
#> 3) odor=creosote,fishy,foul,musty,pungent,spicy 3796 0 Poiso...
```

This is a complex tree with many splits, so let's use **treemisc**'s `tree_diagram()` function to plot it (see Figure 2.20).

```
tree_diagram(mushroom.tree) # Figure 2.20
```

![](bbox=[0.15, 0.3, 0.85, 0.6])

FIGURE 2.20: Decision tree diagram for classifying the edibility of mushrooms.

Setting cp = 0 won't necessarily result in the most complex or saturated tree. This is because rpart() sets a number of additional parameters by default, many of which help control the maximum size of the tree; these are printed below for the current mushroom.tree object. For instance, minsplit, which defaults to 20, controls the number of observations that must exist in a node before a split can be attempted.

```
unlist(mushroom.tree$control)
#> minsplit minbucket cp
#> 20 7 0
#> maxcompete maxsurrogate usesurrogate
#> 4 5 2
#> surrogateestyle maxdepth xval
```