After calculating distance for all 9-output-nodes, we can see that first-row or first-input in our data-set is three times closer to 3rd output-node than left-output-node.

+   Best Matching Unit (BMU): Now we calculated all of the distances between first-row (first-input) and 9-output-nodes then we found that the closest one is 3rd-output-node.

+   Here 3rd-output-node is the BMU, or the best matching unit.

# 13.3.3 SOM moves towards the Data-points

Let's look at a larger SOM of 9x12 size (i.e. 108 output-nodes).

+   Let's say in this larger map we found the BMU for first-row (the Green colored point).

+   Next SOM is actually going to update the weights, according to BMU, so that the output-node gets even closer to our first-input (first row) in our data-set.

+   The reason we are updating the weights is because we don't have control of our inputs, the only thing that we can control in that formula is the weights.

![](bbox=[0.115, 0.315, 0.885, 0.623])

In simple words, the SOM(white structure/grids) is coming closer to that data point(purple colored cloud). In the following image we can see that the SOM is moving over the data-point-cloud(Purple colored).

+   At the very start SOM is initialized with some weights and then it updates the weights and move over the data-points.

![](bbox=[0.115, 0.753, 0.885, 0.913])