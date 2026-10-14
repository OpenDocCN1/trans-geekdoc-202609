If you are able to take a complex task, and break it down into simpler sub-tasks, then by coding in the steps of the sub-tasks explicitly, you are giving the algorithm prior knowledge that can help it learn a task more efficiently.

![](bbox=[0.26, 0.15, 0.73, 0.4])

Suppose you are building a Siamese cat detector. This is the pure end-to-end architecture:

![](bbox=[0.28, 0.44, 0.78, 0.51])

In contrast, you can alternatively use a pipeline with two steps:

![](bbox=[0.18, 0.56, 0.82, 0.63])

The first step (cat detector) detects all the cats in the image.