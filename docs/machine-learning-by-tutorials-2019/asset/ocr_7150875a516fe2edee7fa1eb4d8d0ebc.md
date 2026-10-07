# Machine Learning Chapter 3: Training the Image Classifier

You may be familiar with another type of regression called linear regression. This is the act of fitting a line through points on a graph, something you may have done in high school where it was likely called the method of (ordinary) least squares.

![](bbox=[0.226, 0.177, 0.773, 0.366])

# Linear and logistic regression

Logistic regression does the same thing, but: All points on one side of the line belong to class A, and all points on the other side of the line belong to class B. See how we're literally drawing a line through space to separate it into two classes?

Because books cannot handle 2,048-dimensional illustrations, the logistic regression in the above illustration is necessarily two-dimensional, but the algorithm works well, regardless of how many dimensions the input data has. Instead of a line, the decision boundary is really a high-dimensional object we've mentioned before: a hyperplane. But because humans have trouble thinking in more than two or three dimensions, we prefer to visualize it with a straight line.

Create ML actually uses a small variation of the algorithm — multin logistic regression — handles more than two classes.

Training the logistic regression algorithm to transform the 2,048-dimensional features into a space that allows us to draw separating lines between the 20 classes is fairly easy we already start with features that say something meaningful about the image, rather than pixel values.

> Note: If you're wondering about exactly how logistic regression works, as usual it involves a transformation of some kind. The logistic regression model tries to find "coefficients" (its learned parameters) for the line so that a point that belongs to class A is transformed into a (large) negative value, and a point from class B is transformed into a (large) positive value. Whether a transformed point is positive or negative determines its class. The more

raywender.com 107