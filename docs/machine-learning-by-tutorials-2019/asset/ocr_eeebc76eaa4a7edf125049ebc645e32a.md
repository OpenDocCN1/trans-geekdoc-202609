# Machine Learning

# Chapter 2: Getting Started with Image Classification

![](bbox=[0.156, 0.117, 0.303, 0.329])

![](bbox=[0.333, 0.117, 0.48, 0.329])

![](bbox=[0.507, 0.117, 0.654, 0.329])

![](bbox=[0.683, 0.117, 0.83, 0.329])

Predictions on a few test images

Pretty cool. With a few lines of code you've added a state-of-the-art image classifier to your app!

> Note: When you viewed the Core ML model in Xcode (by selecting the .mlmodel file in the Project navigator), it said that the model had two outputs: a dictionary containing the probabilities and the label for the top prediction. However, the Vision request gives you an array of VNObservation objects. Vision takes dictionary from Core ML and turns it into its own kind of “observation” objects. Later on, you'll see how to use Core ML directly, without using Vision, and in that case, you get access directly to the model's outputs.

# What if the image doesn't have a snack?

The app shows the winning class and the confidence it has in this prediction. In the above image on the left, the class is “healthy” and the confidence is 94.8%.

If the output is something like “healthy 95%”, the model feels pretty about itself. You'll see this in prediction of pictures of oranges, apples, bananas and so on. Later, if the output is “unhealthy 95%”, the model is pretty sure that it's correct about the snack being unhealthy, and you'll see this on pictures of pretzels and waffles. That is we like to see confident predictions.

The model used in this app was trained on 20 different types of snacks. But what happens when you show a kind of snack that it has never seen before, or maybe even a totally different kind of object — may have something that isn't even edible?

![](bbox=[0.156, 0.923, 0.343, 0.953])