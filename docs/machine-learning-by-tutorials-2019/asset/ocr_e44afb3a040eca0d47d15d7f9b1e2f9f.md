ambiguous a point, is i.e. the closer the point is to the decision boundary, the closer its transformed value is to 0. The multinomial version extends this to allow for more than two classes. We'll go into the math in a later chapter. For now, it is useful to understand that this algorithm finds a straight line / hyperplane that separates the points belonging to different classes in the best way possible.

# # Looking for validation

Even though there are 4,858 images in the snacks/train dataset, Create ML uses only 95% of them for training.

During training, it's useful to periodically check how well the model is doing. For this purpose, Create ML sets aside a small portion of the training examples — 5%, so about 240 images. It doesn't train the logistic classifier on these images, but uses them to evaluate how well the model does (and possibly to tune certain settings of the logistic regression).

This is why the output graph for **training accuracy** and one for **validation accuracy:**

![](bbox=[0.258, 0.5485, 0.742, 0.7735])

After 12 iterations, validation accuracy levels off at 94%, meaning that out of 100 training examples it correctly predicts the class for 94 of them. But training accuracy keeps increasing to 100% — the classifier is correct for 10 out of 10 images.