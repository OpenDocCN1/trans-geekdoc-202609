![](bbox=[0.285, 0.018, 0.715, 0.263])

What is this doing is it is not allowing any clusters that would have dissimilarity of greater than the threshold value (1.7 in the figure) within them.

Calculating clusters numbers: You can quickly tell how many clusters you will have at a certain threshold by just looking at how many vertical lines this horizontal actually crosses.

So in above Dendrogram figure, the horizontal threshold crosses two vertical line, hence we get two clusters.

In following case we have 4-clusters:

![](bbox=[0.125, 0.453, 0.874, 0.638])

Finding Optimal number of Clusters: Large vertical line means 'Long distance/gap/void between the clusters'. So we need to find a 'threshold' that crosses maximum number 'large vertical lines'.

We cannot consider the vertical lines that crosses hypothetical extended horizontal line that forms dendrogram.

One of the standard approaches is to look for the highest vertical distance that you can find in dendrogram. Any line that will not cross any horizontal lines.

For example: at P2 and P3 can be considered because P1 cannot be considered because it crosses hypothetical horizontal line (extended) that joins P2 and P3 because it does not represent the distance between {P2, P3} cluster. it actually represents the distance between the single points P2, P3 and the actual distance between {P2, P3} and P1 is the shortest vertical line (top on P2, P3).

So we have to find the largest vertical line that does not cross any of the extended horizontal lines that forms the dendrogram.

![](bbox=[0.535, 0.73, 0.874, 0.963])