
# CHAPTER 6. DISCOVERING BEHAVIORS WITH UNSUPERVISED LEARNING 192

The first argument is the transactions object. The second argument parameter specifies a list of algorithm parameters. In this case we want rules with a minimum support of 0.001 confidence of at least 0.5. The minlen argument specifies the minimum number of allowed items in a rule for the antecedent + consequent. We set it to 2 since we want rules with one element in the antecedent and one element in the consequent, for example, item1 => item2. Apriori algorithm rules with only one item in the consequent. Finally, the target parameter is used to specify that we want to find rules because the function can also return item sets of different types (see the documentation for more details). The returned rules are saved in the resrules variable that can be used later to explore the results. We can also print a summary of the returned results.

```
# Print a summary of the results.
summary(resrules)

# set of 141 rules
#
# rule length distribution (lhs : rhs):sizes
# 2 3
# 45 96
#
# Min. 1st Qu. Median Mean 3rd Qu. Max.
# 2.000 2.000 3.000 2.681 3.000 3.000
#
# summary of quality measures:
# support lift count
# Min. :0.001030 Mean :0.5045 Min. :0.6535 Mean : 338
# 1st Qu. :0.001767 1st Qu. :0.6478 1st Qu.:0.9158 1st Qu. : 580
# Median :0.004424 Median :0.7577 Median :1.0139 Median : 1452
# Mean :0.011271 Mean :0.7269 Mean :1.0906 Max : 6982
# 3rd Qu. :0.012860 3rd Qu.:0.8131 3rd Qu.:1.0933 3rd Qu. : 4254
# Max. :0.376836 Max :0.9589 Max. :4.2777 Max. :123692
#
# mining info:
# data transactions support confidence
# transactions 322838 0.001 0.5
```

By looking at the summary, we see that the algorithm found 141 rules that satisfy the support and confidence thresholds. Here the rule length distribution is printed. Here, 45

```
inspect(sort(resrules, by='lift', decreasing = T)[1:20])
| | | support | confidence | lift | count |
|---|---|---|---|---|---|---|
| [1] {R.stepson,adult} | {Blunt Object} | 0.01119732 | 0.53615268 | 0.02233106 | 42.777257 | 399 |
| [2] {R.son,adult} | {Blunt Object} | 0.01012732 | 0.51488057 | 0.01977004 | 51.00004 | 393 |
| [3] {R.mother,adult} | {Blunt Object} | 0.01055532 | 0.61443752 | 0.01644372 | 37.007257 | 202 |
| [4] {R.boyfriend,adult} | {knife} | 0.00985845 | 0.52361528 | 0.01882854 | 27.296124 | 399 |
| [5] {R.boyfriend} | {knife} | 0.01010800 | 0.50865936 | 0.02130972 | 26.688157 | 314 |
| [6] {R.stranger} | {knife} | 0.00985845 | 0.62104376 | 0.01512211 | 28.765451 | 312 |
| [7] {R.stranger,lateadult} | {handgun} | 0.01021193 | 0.63951000 | 0.01706688 | 13.508059 | 385 |
| [8] {R.husband,lateadult} | {handgun} | 0.00444236 | 0.66216432 | 0.01207268 | 12.268091 | 1454 |
| [9] {R.stranger,adult} | {handgun} | 0.01092193 | 0.61349635 | 0.01781268 | 14.494452 | 1452 |
| [10] {R.stranger} | {handgun} | 0.01465478 | 0.65168166 | 0.02239644 | 14.465444 | 1858 |
| [11] {R.stranger,adult} | {Blunt Object} | 0.01207836 | 0.61968835 | 0.01951727 | 26.104448 | 3967 |
| [12] {R.daughter,Blunt Object} | {knife} | 0.01055532 | 0.50888318 | 0.01881002 | 21.200226 | 2717 |
| [13] {R.daughter,Blunt Object} | {knife} | 0.00820057 | 0.99388450 | 0.00801068 | 12.000000 | 2719 |
| [14] {R.mother,adult} | {knife} | 0.01055532 | 0.54121532 | 0.02005098 | 17.393112 | 3739 |
| [15] {R.wife,lateadult} | {knife} | 0.01102741 | 0.57866731 | 0.02177918 | 18.350031 | 338 |
| [16] {R.In-Law,lateadult} | {knife} | 0.01671633 | 0.57715372 | 0.02902308 | 11.978641 | 5550 |
| [17] {R.stranger,adult} | {knife} | 0.01055532 | 0.58050032 | 0.02085000 | 10.500000 | 5158 |
| [18] {R.stranger,strangulation} | {adult} | 0.01617229 | 0.93194159 | 0.17700517 | 10.591199 | 531 |
| [19] {R.boyfriend/girlfriend,knife} | {adult} | 0.01402142 | 0.89419446 | 0.15665937 | 11.142895 | 460 |
| [20] {R.Girl,strangulation} | {adult} | 0.01398376 | 0.82929611 | 0.16951937 | 14.110415 | 459 |
```

Figure 16: Output of inspect() rules are of size 2 and 96 rules are shown. Then, some standard statistics are shown for support, confidence, and lift. The inspect() function can be used to show the actual rules. Rules can be sorted by one of the measures. The code sorts by lift and shows the first 20 rules. Figure 6.13 shows the output. The first rule with a lift of 4.27 shows that a homicide was committed by an adult blunt object used for the crime. Looking at the rules one can note that whenever blunt object appears either in the left or rhs the victim was probably an infant. Another thing to note is that the victim boyfriend, the crime was likely committed with a knife. This is also mentioned in the reports "Homicide trends in the United States" (Cooper et al., 2012): From 1980 through 2008 “Boyfriends were more likely to be killed by knives than any other group of intimates.” According to rule 20, rules involving girlfriend have a strong relationship with strangulation. This can also be confirmed by (Cooper et al., 2012): From 1980 through 2008 “Girlfriends were more likely to be killed by force…”

CHAPTER 6. DISCOVERING BEHAVIORS WITH UNSUPERVISED LEARNING 194

# Scatter plot for 141 rules

![](img/91c4cc243e5af2971580c9dda8b_206_0.png)

Figure 6.14: Scatterplot of rules support v.s. confidence colored by lift. The resulting rules can be plotted with the plot() function. By default, it generates a scatterplot with the support in the x axis and confidence in the y axis colored by lift.

```
# Plot a default scatterplot of support v.s. confidence colored by lift.
plot(resamples)
```

The plot shows that rules with a high lift also have a low support and confidence. Hassler (2017) mentioned that rules with high lift typically have low support. The plot can be customized for example to show the support and lift in the axes and colored by confidence. The axes can be set with the measure parameter and the coloring with the shading parameter. The function also supports different engines including static and interactive. The following code generates a customized interactive plot by setting engine = "htmlwidget". This is very handy if you want to know which points correspond to which rules. By hovering the mouse on the desired point the corresponding rule is shown as a tooltip box (Figure 6.15). The interactive plots also allow to zoom in regions by clicking and dragging.

```
# Customize scatterplot to make it interactive
# and plot support v.s. lift colored by confidence.
plot(resamples, engine = "htmlwidget",
measure = c("support", "lift"), shading = "confidence")
```

CHAPTER 6. DISCOVERING BEHAVIORS WITH UNSUPERVISED LEARNING 195

![](img/91c4cc243e5af2971580c9dda8b_207_0.png)

Figure 6.15: Interactive scatterplot of rules. The arulesViz package has a nice option to plot rules as a graph. This is done by setting method = "graph". We can also make the graph interactive for easier exploration by setting engine="htmlwidget". For clarity, the font size is reduced with cex=0.9. Here we plot the first 25 rules.

```
# Plot rules as a graph.
plot(head(sort(resrules)
```

Figure 6.16 shows a zoomed-in portion of the entire graph. Circles represent rules and rounded squares items. The size of the circle is relative to the support and color relative to the lift. Incoming arrows represent the items in the antecedent and the outgoing arrow of a circle points to the item in the consequent part of the rule. From this graph, some interesting patterns can be seen. First, when the age of the perpetrator is lateAdulthood the victims are the husband or ex-wife. When the perpetrator is a teen, the victim was likely a friend or stranger.

CHAPTER 6. DISCOVERING BEHAVIORS WITH UNSUPERVISED LEARNING 196

![](img/91c4cc243e5af2971580c9dda8b_208_0.png)

Figure 6.16: Interactive graph of rules. The arulesViz package has a cool function ruleExplorer() that generates a shiny app with interactive controls and several plot types. When running the following code (output not shown) you may be asked to install additional shiny related packages.

```
# Opens a shiny app with several interactive plots.
ruleExplorer(resrules)
```

Sometimes Apriori returns thousands of rules. There is a convenient subset() function to extract rules of interest. For example, we can select only the rules that contain R.Girlfriend in the antecedent (lhs) with:

```
# Subset transactions.
rulesGirlfriend <- subset(resrules, subset = lhs %in% "R.Girlfriend"
```

```
# Print rules with highest lift.
inspect(head(rulesGirlfriend
```
