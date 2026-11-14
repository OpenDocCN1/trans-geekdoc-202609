Adams and Brown share an edge on the adjacency matrix, so you get 1 point for clustering them ('WineNetwork-radj'!K2 in the formula), but Adams has a stub count of 14 and Brown is a 15, so their expected edge count is 14 * 15 / 858, which comes out to 0.245. Bringing it all together, you get 1 – 0.245 = 0.755 for the score.

# Let's Get Clustering!

You now have the scores you need. All you need to do now is set up an optimization model to find the community assignments.

Now, I'm going to be honest with you up front. Finding optimal communities using graph modularity is a more intense optimization setup than what you encountered in Chapter 4.

To make this possible, you're going to attack the problem using an approach called divisive clustering or hierarchical partitioning. All that means is that you're going to set up the problem to find the best way to split the graph into two communities. Then you're going to split those two into four, and on and on until Solver decides that the best way to maximize modularity is to stop dividing the communities.

> **NOTE**
> Divisive clustering is the opposite of another often-used approach called *agglomerative clustering*. In agglomerative clustering, each customer starts in their own cluster, and you recursively join together the two closest clusters until you reach a stopping point.

# Split Number 1

You start this divisive clustering process by dividing the graph into two communities so the modularity score is maximized.

First, create a new sheet called Split1. Then, in A1 create a label called Customers. Next, list your customers below in cell A2 (either formulaically or with a paste values operation). Each customer's community assignment will go in column B, which you should label Community. Since you're splitting the graph in half, have the Community column be a binary decision variable in Solver, where the 0/1 value will denote whether you're in community 0 or community 1. Neither community is better than the other. There's no shame in being a 0.

# Scoring Each Customer's Community Assignment

In column C, you're going to calculate the scores you get by placing each customer in their respective community. By that, I mean if you place Adams in community 1, you'll