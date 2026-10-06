# The Idea Behind k-Nearest Neighbors

The following two sections will explain the idea behind k-Nearest Neighbors. In Section 4.5.1, we start with the most basic k-Nearest Neighbors model (k = 1). It predicts the predicted neighbors (wine color) for a new observation by finding the observation contrast to it — the nearest neighbor. Then the class (wine color *WineColor*) of the neighbor observation is used to predict the unknown observer's class (*WineColor*).

k-Nearest Neighbors considers more than one neighboring point (k > 1), e.g., the four nearest neighbors (k = 4), the class of the majority of these neighbors is the predicted class. In case of a tie, the prediction is chosen randomly (see Section 4.5.2 for a visualization of a k-Nearest Neighbors model).

In a k-Nearest Neighbors model, the hyper-parameter determines the number of neighbors to be considered. k is called a hyper-parameter because, in contrast to parameters that are determined based on data, it has to be chosen at the stage of the model.

# 4.5.1 k-Nearest Neighbors for k=1

We start with k = 1, which means that k-Nearest Neighbors focuses only on the closest neighbor.

To introduce the idea, it is best to zoom in Figure 4.1 closer to the wine we would like to predict (the blue point). This makes it easier to identify the closest neighbor to the blue point.

Figure 4.5 shows the result after zooming. Eyeballing makes it easy to identify the neighbor to the blue point. The nearest neighbor is the wine (point) connected with the bold magenta line to the wine we want to predict (the blue point). Since the closest neighbor's wine color is red, k-Nearest Neighbors with k = 1 predicts red for the unknown wine color.

Eyeballing is a good tool when working with graphs. Still, for a machine learning model like k-Nearest Neighbors, we have to find a way to measure the distances between the point (the wine) we like to predict and all points in the training dataset. This is the only way to find the nearest neighbor programmatically.

In Figure 4.5, the two black lines and the magenta line form a right-angled triangle, which means Pythagoras is here to help. If we name the blue point with an index p (for predict) and the red point we want to calculate the distance to an index i, then the length of the triangle's leg a equals Sulfur_i - Sulfur_p, and the length of leg b equals Acid_i - Acid_p. The length