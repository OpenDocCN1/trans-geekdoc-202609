![](bbox=[0.118, 0.29, 0.442, 0.715])

After applying this transformation, both classes get cleanly separated. You can easily draw a line between them at **z = 0.5**. Any point with z-coordinate less than 0.5 belongs to class A, and any point with z greater than 0.5 belongs to class B.

The closer a point s z-coordinate is to the line, the less confident the model is about the class for that point. This also explains why probabilities get closer to 50% when the HealthySnack model can't decide whether the snack in the image is healthy or unhealthy. Usually, in that case, the image gets transformed to a point that is near the decision boundary. Usually, the decision boundary is a fuzzy line and points with z close to 0.5 belongs to either class A (triangles) or class B (circles).

The cool thing about neural networks is that they can automatically learn to make these kinds of transformations, to convert the input data from a coordinate space where it's hard to tell the points apart, into a coordinate space where it's easy. That is, exactly what happens when the model is trained. It learns the transformations and how to find the best decision boundary.

To classify a new image, the neural network will apply all the transformations it has learned during training, and then it looks at which side of the line the transformed image falls. And that's the secret sauce of neural network classification!

The only difference between this simple example and our image classifier is that you're dealing with 150,000 dimensions instead of two. The idea – and the underlying mechanics — exactly the same for 150,000 dimensions as it is for two.