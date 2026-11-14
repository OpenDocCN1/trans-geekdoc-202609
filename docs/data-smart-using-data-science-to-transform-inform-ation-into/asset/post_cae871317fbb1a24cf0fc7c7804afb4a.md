
| | Employee ID | k-distance |
|---|---|---|
| 372 | 136042 | 1.97785485 |
| 373 | 134999 | 2.13477118 |
| 374 | 137910 | 2.90875649 |
| 375 | 136944 | 2.49260293 |
| 376 | 136145 | 2.86666113 |
| 377 | 143406 | 4.84535388 |
| 378 | 145176 | 1.89063923 |
| 379 | 143091 | 2.69303616 |
| 380 | 138759 | 2.54302974 |
| 381 | 144013 | 2.56364579 |
| 382 | 138843 | 2.74345782 |
| 383 | 133915 | 2.93093569 |
| 384 | 131731 | 2.40722467 |

**Figure 10.15: Employee 143406 has a high 5-distance**

![](img/9c4b3d77873bec9e7da149a75c568d36_382_0.png)

**Figure 10.16: k-distance fails on local outliers**

Are those diamonds really weirder than that triangle? Not to my eyes!

The issue here is that the triangle is not a *global outlier*, so much as it is a *local outlier*. The reason why your eyeballs pick it up as the odd point out is that it's nearest to the tight cluster of circles. If the triangle were among the spaced-out diamonds, it'd be fine. But it's not. Instead, it looks nothing like its circular neighbors.¹

¹ But the broader reason has to do with how we perceive information. Technically, the difference in shapes that we detect are called pre-attentive attributes, and we're able to perceive them before giving them conscious attention. You can read more about how they work in *Information Visualization: Perception for Design* by Colin Ware (Morgan Kaufmann Series in Interactive Technologies, Amsterdam, 2012).

## Graph Outlier Detection Method 3: Local Outlier Factors Are Where It's At

Just like using k-distance, local outlier factors provide a single score for each point. The larger the score, the more of an outlier they are. But LOF gives you something a little cooler than that: the closer the score is to 1, the more ordinary the point is locally. As the score increases, the point should be considered less typical and more like an outlier. And unlike k-distance, this “1 is typical” fact doesn’t change no matter the size or scale of your graph, which is really cool.

At a high level here’s how it works: you are an outlier if your k-nearest neighbors consider you farther away than their neighbors consider them. The algorithm cares about a point’s friends and friends of friends. That’s how it defines “local.”

Looking back at Figure 10.16, this is exactly what makes the triangle an outlier, isn’t it? It may not have the highest k-distance, but the ratio of the triangle’s distance to its nearest neighbors over their distance to each other is quite high (see Figure 10.17).

![](img/9c4b3d77873bec9e7da149a75c568d36_383_0.png)

**Figure 10.17:** The triangle is not nearly as reachable by its neighbors as they are by their neighbors.

## Starting with Reach Distance

Before you can put together your local outlier factors for each employee, you need to calculate one more set of numbers, called reachability distances.

> The reachability distance of employee A with respect to employee B is just their ordinary distance, unless A is within B’s k-distance neighborhood, in which case the reachability distance is just B’s k-distance.

In other words, if A is inside B’s neighborhood, you round up A’s distance to B to the size of B’s neighborhood; otherwise, you leave it alone.

Using reachability distance rather than ordinary distance for LOF helps stabilize the calculation a bit.

Create a new tab called Reach-dist to replace the distances from the Distances tab with the new reach distances.

The first thing you'll want is to create yet another employee grid. Start the new matrix on row 3. Then place the k-distances from the K-Distance tab across the top (you'll need to transpose them). This gives you the sheet shown in Figure 10.18.

| | A | B | C | D | E | F | G |
|---|---|---|---|---|---|---|---|
| 1 | k-Distance | 2.98518 | 1.798456 | 2.553674 | 2.354415 | 3.106026 | 2.227832 |
| 3 | | 144624 | 142619 | 142285 | 142158 | 141008 | 145082 |
| 4 | 144624 | | | | | | |
| 5 | 142619 | | | | | | |
| 6 | 142285 | | | | | | |

Figure 10.18: The skeleton of the reach distance tab

Starting in cell B4, you're going to slide in the distance of 144624 to itself from the Distances tab (Distances!C3) unless it's less than the k-distance in B1. It's a simple MAX formula.

```
=MAX(B$1, Distances!C3)
```

Drag the formula through OK4, then double-click the cell-anchor to send them through row 403. This fills in all the reach distances, as shown in Figure 10.19.

| | A | B | C | D | E | F | G | H |
|---|---|---|---|---|---|---|---|---|
| 1 | k-Distance | 2.98518 | 1.798456 | 2.553674 | 2.354415 | 3.106026 | 2.227832 | 2.444413 |
| 3 | | 144624 | 142619 | 142285 | 142158 | 141008 | 145082 | 139410 |
| 4 | 144624 | 2.985 | 4.859 | 6.693 | 5.390 | 5.835 | 4.885 | 5.508 |
| 5 | 142619 | 4.859 | 1.798 | 4.051 | 2.393 | 5.061 | 4.298 | 3.132 |
| 6 | 142285 | 6.693 | 4.051 | 2.554 | 4.880 | 4.859 | 4.866 | 2.635 |
| 7 | 142158 | 5.390 | 2.393 | 4.880 | 2.354 | 5.530 | 4.646 | 3.932 |
| 8 | 141008 | 5.835 | 5.061 | 4.859 | 5.530 | 3.106 | 3.106 | 4.162 |
| 9 | 145082 | 4.885 | 4.298 | 4.866 | 4.646 | 3.106 | 2.228 | 3.872 |
| 10 | 139410 | 5.508 | 3.132 | 2.635 | 3.932 | 4.162 | 3.872 | 2.444 |
| 11 | 135014 | 5.289 | 1.798 | 4.286 | 2.955 | 5.690 | 4.847 | 4.035 |

Figure 10.19: All reach distances

## Putting Together the Local Outlier Factors

Now you're ready to calculate each employee's local outlier factor. To start, create a new tab called LOF and place the employee IDs down column A, starting at A2.

Local outlier factors gauge how a point is viewed by its neighbors versus how those neighbors are viewed by their neighbors. If I’m 30 miles outside of town, my closest neighbors may view me as a country bumpkin, whereas they are viewed by their neighbors as members of their community. That means locally I’m viewed more as an outlier than my neighbors are.

These values hinge on the average reachability of each employee with respect to their k-nearest neighbors.

Consider employee 144624 on row 2. You’ve already set k to 5, so the question is, what is the average reachability distance of 144624 with respect to that employee’s five nearest neighbors?

To calculate this, pull a vector of 1s from the Rank tab for the five employees closest to employee 144624 and 0s for everyone else (similar to what you did on the K-Distance tab). Such a vector can be created using Booleans and SUMPRODUCT to grab the top-ranked neighbors while excluding the actual employee. You could then multiply this indicator vector times 144624’s reach distances, sum up the product, and divide them by k=5. In cell B2, then, you have this:

```
=SUMPRODUCT(
(Rank!B2:OK2 <= 'K-Distance'!$B$1) *
(Rank!B2:OK2 > 0) *
'Reach-dist'!B4:OK4
) / 'K-Distance'!$B$1
```

You can send this formula down the sheet by double-clicking it (see Figure 10.20).

| | A | B |
|---|---|---|
| 1 | | Average Reachability Distance w.r.t. Neighbors |
| 2 | Employee ID | Neighbors |
| 3 | 144624 | 2.806363355 |
| 4 | 142619 | 1.794406085 |
| 5 | 142285 | 2.449893931 |
| 6 | 142158 | 2.378938602 |
| 7 | 141008 | 3.068076277 |
| 8 | 145082 | 2.199004025 |
| 9 | 139410 | 2.226959731 |
| 10 | 135014 | 1.773335938 |
| 11 | 139356 | 2.411607259 |
| 12 | 137368 | 2.668928489 |
| 13 | 141982 | 2.243972159 |

**Figure 10.20:** Average reachability for each employee with respect to their neighbors

So, this column indicates how the five nearest neighbors of each employee view them.

The local outlier factor then for an employee is the average of the ratios of the employee's average reachability distance divided by the average reachability distances of each of their k-neighbors.

You will tackle the LOF calculation for employee 144624 in cell C2 first. Let's build the formula piece by piece. Just as on previous sheets, use Booleans to give you a vector of 1s for 144624's top five nearest neighbors.

```
(Rank!B2:OK2 <= 'K-Distance'!$B$1) *
(Rank!B2:OK2 > 0)
```

You then multiply the ratio of 144624's average reachability divided by each neighbor's average reachability as follows:

```
(Rank!B2:OK2 <= 'K-Distance'!$B$1) *
(Rank!B2:OK2 > 0) *
B2 / TRANSPOSE(B$2:B$401)
```

Note that the neighbors' reachability distances referenced in range B2:B401 on the bottom of the ratio are transposed so that the column is turned into a row, just like the vector of Booleans.

You can average these ratios by summing them and dividing by k.

```
=SUMPRODUCT(
(Rank!B2:OK2 <= 'K-Distance'!$B$1) *
(Rank!B2:OK2 > 0) *
B2 / TRANSPOSE(B$2:B$401)
) / 'K-Distance'!$B$1
```

It's 1.34'ish, which is somewhat over a value of 1, meaning that this employee is a bit of a local outlier.

You can send this formula down the sheet by double-clicking and then check out the other employees. Conditional formatting is helpful to highlight the most significant outliers.

Lo and behold, when you scroll down, you find that employee 143406, the resident slacker, is the most outlying point with a LOF of 1.97 (see Figure 10.21). His neighbors view him as twice as distant as they are viewed by their neighbors. That's pretty far outside the community.

That's it! You now have a single value assigned to each employee that ranks them as a local outlier and is scaled the same no matter the size of the graph. Pretty flippin' awesome.

Between the graph modularity chapter and this chapter on outlier detection, you've been exposed to the power of analyzing a dataset by “graphing” your data, that is, assigning distances and edges between your observations.
