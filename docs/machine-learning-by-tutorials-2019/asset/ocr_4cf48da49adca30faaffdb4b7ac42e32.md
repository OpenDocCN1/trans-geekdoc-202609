See what it does on the test set:

```
model.evaluate_generator(test_generator, steps=len(test_generator))
```

For the author, the output is about 0.15 or 15% correct. It's better than a random guess, and better than the model with just a single Dense layer, but not by much. Adding more Dense layers might boost the validation and test scores by a little, but you're still very far off the accuracy scores you got from Create ML and Turi Create.

It should be noted that these classical methods, logistic regression and fully connected neural networks, just don't work well for image data. One reason is that the model you've created destroys the spatial nature of the training data.

Images have a width and height, the first thing the model does is Flatten the image so it can be connected to a Dense layer. As you've seen, Flatten unrolls the original three-dimensional image data — height, width and color channels — into a one-dimensional vector. This destroys the relationships between neighboring pixels that was present in the original image. By doing this, you've unintentionally been making it hard on the model to understand our data.

It would be better if you could use a model that kept the spatial relationships intact, and that understood the true nature of images. That's exactly what convolutional layers do. That's the topic of the next chapter!

# Challenge

Try adding more layers to the neural network, and varying the number of neurons inside these layers. Can you get a better test score this way? You'll find that the more layers you add, the harder it actually becomes to train the model.