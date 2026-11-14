
Open Solver and hammer in these requirements. We’ll set Solver to minimize cell H43 by changing cells H2:K33 with the constraint that H2:K33 be <= 1 just like all the deal vectors. Make sure that the variables are checked as non-negative and that the evolutionary solver is chosen (see Figure 4.17).

![](img/9c4b3d77873bec9e7da149a75c568d36_106_0.png)

### Figure 4.17: The Solver setup for 4-means clustering

Also, setting these clusters isn't a cakewalk for Solver, so you should beef up some of the evolutionary solver’s options by pressing the options button within the Solver window and toggling over to the Evolutionary tab. It’s useful to bump up the Maximum Time Without Improvement parameter somewhere north of 30 seconds, depending on how long you want to wait for the Solver to finish. In Figure 4.18, I’ve set mine to 600 seconds (10 minutes). That way, I can set the Solver to run and go to dinner. And if you ever want to kill Solver early, just press Escape and then exit with the best solution it’s found so far. Click Solve and watch Excel do its thing until the evolutionary algorithm converges.

![](img/9c4b3d77873bec9e7da149a75c568d36_107_0.png)

### Figure 4.18: The Evolutionary tab in Solver

## Making Sense of the Results

Once Solver gives you the optimal cluster centers, the fun starts. You get to mine the groups for insight! So in Figure 4.19, you can see that Solver calculated an optimal total distance of 140.7, and the four cluster centers, thanks to the conditional formatting, all look very different.

> > NOTE
> > Note that your cluster centers may look different from the spreadsheet provided with the book. That's because the evolutionary algorithm employs random numbers and does not give the same answer each time. The clusters may be fundamentally different, or, more likely, they may be in a different order (for example, my Cluster 1 is very close to your Cluster 4, and so on).

Because you pasted the deal descriptions in columns B through G when you set up the tab, you can read off the details of the deals in Figure 4.19 that seem important to the cluster centers.

| Offer # | Campaign | Varietal | Minimum Qty | Discount (%) | Origin | Past Peak | Cluster 1 | Cluster 2 | Cluster 3 | Cluster 4 | Adams | Allen | Anderson |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | January | Malbec | 72 | 56 | France | FALSE | 0.026 | 0.012 | 0.043 | 0.275 | | | |
| 2 | February | Pinot Noir | 72 | 17 | France | FALSE | 0.234 | 0.022 | 0.108 | 0.115 | | | |
| 3 | February | Espumante | 144 | 32 | Oregon | TRUE | 0.017 | 0.023 | 0.054 | 0.160 | | | |
| 4 | February | Champagne | 72 | 48 | France | TRUE | 0.015 | 0.026 | 0.130 | 0.174 | | | |
| 5 | March | Cabernet Sauv | 144 | 44 | New Zealand | FALSE | 0.006 | 0.022 | 0.004 | 0.495 | | | |
| 6 | March | Champagne | 144 | 86 | Chile | FALSE | 0.028 | 0.010 | 0.095 | 0.297 | | | |
| 7 | March | Prosecco | 6 | 40 | Australia | TRUE | 0.034 | 0.541 | 0.123 | 0.086 | | | |
| 8 | March | Espumante | 6 | 45 | South Africa | FALSE | 0.007 | 0.430 | 0.155 | 0.122 | | | |
| 9 | April | Chardonnay | 144 | 57 | California | FALSE | 0.014 | 0.014 | 0.141 | 0.314 | | 1 | |
| 10 | May | Champagne | 72 | 53 | Italy | FALSE | 0.010 | 0.034 | 0.038 | 0.460 | | | |
| 11 | May | Champagne | 72 | 85 | France | FALSE | 0.032 | 0.025 | 0.128 | 0.280 | | | |
| 12 | May | Prosecco | 72 | 83 | Australia | FALSE | 0.016 | 0.041 | 0.073 | 0.088 | | | |
| 13 | May | Merlot | 6 | 43 | Chile | FALSE | 0.026 | 0.194 | 0.016 | 0.011 | | | |
| 14 | June | Merlot | 72 | 64 | Chile | FALSE | 0.045 | 0.034 | 0.061 | 0.126 | | | |
| 15 | June | Cabernet Sauv | 144 | 15 | California | FALSE | 0.003 | 0.094 | 0.065 | 0.171 | | | |
| 16 | June | Merlot | 72 | 18 | California | FALSE | 0.030 | 0.009 | 0.063 | 0.027 | | | |
| 17 | July | Pinot Noir | 12 | 47 | Germany | FALSE | 0.608 | 0.032 | 0.005 | 0.061 | | | |
| 18 | July | Espumante | 6 | 50 | Germany | FALSE | 0.027 | 0.439 | 0.074 | 0.054 | | 1 | |
| 19 | July | Champagne | 12 | 66 | Germany | FALSE | 0.025 | 0.015 | 0.073 | 0.072 | | | |
| 20 | August | Cabernet Sauv | 72 | 35 | Oregon | FALSE | 0.004 | 0.005 | 0.069 | 0.005 | | | |
| 21 | August | Champagne | 12 | 50 | California | FALSE | 0.014 | 0.049 | 0.050 | 0.069 | | | |
| 22 | August | Champagne | 72 | 63 | France | FALSE | 0.009 | 0.024 | 0.023 | 0.951 | | | |
| 23 | September | Chardonnay | 144 | 39 | South Africa | FALSE | 0.023 | 0.023 | 0.036 | 0.062 | | | |
| 24 | September | Pinot Noir | 6 | 39 | France | FALSE | 0.583 | 0.043 | 0.017 | 0.065 | | | |
| 25 | September | Cabernet Sauv | 72 | 59 | Oregon | FALSE | 0.025 | 0.004 | 0.083 | 0.114 | | | 1 |
| 26 | October | Pinot Noir | 144 | 83 | Australia | FALSE | 0.690 | 0.030 | 0.090 | 0.130 | | | |
| 27 | October | Champagne | 72 | 88 | New Zealand | FALSE | 0.010 | 0.021 | 0.087 | 0.141 | | 1 | 1 |
| 28 | November | Cabernet Sauv | 12 | 56 | France | TRUE | 0.028 | 0.017 | 0.090 | 0.030 | | | |
| 29 | December | Pinot Grigio | 6 | 73 | Chile | FALSE | 0.013 | 0.038 | 0.143 | 0.108 | | 1 | |
| 30 | December | Prosecco | 6 | 54 | France | FALSE | 0.020 | 0.729 | 0.079 | 0.136 | | 1 | |
| 31 | December | Champagne | 72 | 89 | France | FALSE | 0.023 | 0.027 | 0.211 | 0.259 | | | |
| 32 | December | Cabernet Sauv | 72 | 45 | Germany | TRUE | 0.093 | 0.013 | 0.053 | 0.125 | | | |

### Figure 4.19: The four optimal cluster centers

Now, your results might vary from mine but you'll likely see similar patterns. Let's take a look. For Cluster 1 in column H, the conditional formatting calls out deals 24, 26, 17, and, to a lesser degree, 2. Reading through the details of those deals, the main thing they have in common is that they're all pinot noir.

If you look at column I, the green cells all have a low minimum quantity in common. These are the buyers who don't want to have to buy in bulk to get a deal.

But I'll be honest: the last two cluster centers in Figure 4.19 are kind of hard to interpret. And, though we came up with ideas that explain the first two clusters, this is just speculation. In the real world, we should attempt to explain clusters with caution.

In fact, we might find it more interesting to investigate the members of each cluster to determine which deals they like. That might be more elucidating.

## Getting the Top Deals by Cluster

Instead of looking at which dimensions are closer to 1 for a cluster center, let's check who is assigned to each cluster and which deals they prefer.

To do this, let's start by making a copy of the OfferInformation tab and calling it **4MC – TopDealsByCluster**. Once you've made a copy, click into the Table Design ribbon tab and select Convert to Range so that we're just working with cells. I've cleared out the formatting on mine—feel free to do the same on yours. On this new tab, label columns H through K as **1, 2, 3, and 4**. Once that's complete, apply a filter to the range of data. We'll use a filter here instead of an Excel table. This is OK because we're not trying to store data but rather we're looking to perform a quick analysis. You can apply a filter from the Home tab > Sort & Filter > Filter (see Figure 4.20).

![](img/9c4b3d77873bec9e7da149a75c568d36_109_0.png)

### Figure 4.20: Setting up a tab to count popular deals by cluster

Back on tab 4MC, you have cluster assignments listed (1–4) on row 41. All you need to do to get deal counts by cluster is grab the column title on tab **4MC – TopDealsByCluster** in columns H through K, see who on 4MC was assigned to that cluster using row 41, and then sum up their values for each deal row. That'll give you the total customers from a given cluster that took a deal.

Start with cell H2 on 4MC – TopDealsByCluster, that is, the count of customers in cluster 1 who took offer #1, the January Malbec offer. You want to sum across L2:DG2 on the 4MC tab but only for those customers who are in cluster 1, and that is a classic use case for the SUMIF formula. The formula looks like this:

```
=SUMIF('4MC'!$L$41:$DG$41,'4MC - TopDealsByCluster'!$H$1,'4MC'!$L2:$DG2)
```

Here's how SUMIF works. First, you provide it with some values to check in the first section '4MC'!$L$41:$DG$41, which are checked against the 1 in the column header ('4MC - TopDealsByCluster'!H$1), and then for any match, you sum up row 2 by specifying '4MC'!$L2:$DG2 in the third section of the formula.

Note the use of absolute references (that's the dollar sign, $) in front of everything in the cluster assignment row, in front of the row number for our column headers, and in front of the column letter for our deals taken. By making these references absolute, you can then drag this formula through range H2:K33 to get deal counts for every cluster center and deal combination, as pictured in Figure 4.21. You can place some conditional formatting on these columns to make them more readable.
