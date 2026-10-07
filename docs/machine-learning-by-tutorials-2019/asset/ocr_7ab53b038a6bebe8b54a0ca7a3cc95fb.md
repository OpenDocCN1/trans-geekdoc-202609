# Chapter 2: Getting Started with Image Classification

Well, unlike the binary classifier in which predictions became very uncertain (50–50), a similar thing happens but now the probabilities get divided over over more classes:

![](bbox=[0.358, 0.181, 0.641, 0.597])

In this example, the classifier correctly recognizes apples and carrots as the top choices, and it tries to split the probabilities between them.

This is why you’re looking at the top three results instead of just the single best score. In image classification competitions, classifiers are usually scored on how well they do on their five best guesses, that way, you can deal with one image containing more than one object or with objects that are a little ambiguous. As long as the correct answer is among the five (or three) guesses, we’re happy.

The top-one accuracy says, "Did the classifier get the most important object right?" while the top-three or top-five accuracy, "Did it find all of the important objects?" For example, if an image that scored 70%, watermelon 21%, and muffin 5% really contained a watermelon and not an orange, it would still be counted as a correct classification.