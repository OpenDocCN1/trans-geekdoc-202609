# 13.3.2 SOMs organize itself: Distance calculation

Now we go through each of rows of our data set, and we're going to find out which of the weight assigned output-nodes (W1,W2,W3), i = 1, 2, ..., 9 from SOM's first iteration) is closest to each of our rows (inputs) in our data set.

+   - Let's start with row number one:
- We first put the first row's 3 values into our input nodes.
- After we've inputted first row from our data set into our input nodes, we'll go through all 9 output-nodes and calculate the distance from the first to our input nodes.

![](bbox=[0.102, 0.165, 0.865, 0.36])

Remember, here (X1,X2,X3) inside input-nodes are the inputs from first-row of our Data-set. (X1,X2,X3) inside input-nodes does not changes when we are calculating distance from SOMs output-nodes. We are not changing the row.

+   - We're going to go through every one of these original input space, and find out which of these is the closest in that original is closest to our first-row.
- We calculate the distance as a Euclidean distance.

Feature scaling: Also note that we will get a value close to 1. Because our is between 0 and 1, to make this algorithm work properly.

So we need to apply normalization and standardization to our data-set. Then we input the data into the SOM

![](bbox=[0.102, 0.375, 0.865, 0.98])