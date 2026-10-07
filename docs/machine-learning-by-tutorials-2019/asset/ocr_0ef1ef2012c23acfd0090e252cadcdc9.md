# Machine Learning

# Chapter 1: Machine Learning, iOS & You

Showing the model all the training examples just once is not enough. You'll need to repeat this process over and over, for hundreds of iterations. In each iteration, the loss will become a little bit lower, meaning that the error between the prediction and the true value becomes smaller and, thus, the model is less wrong than before. And that's a good thing!

If you repeat this enough times, and assuming that the chosen model has enough capacity for learning this task, then gradually the model's predictions become better and better.

Usually people keep training until the model reaches some minimum acceptable accuracy, up to a maximum number of iterations, or until they run out of patience... For neural networks, it's not uncommon to use millions of images and go through thousands of iterations.

Of course, training is a bit more complicated than in practice (it's not always?). For example, it's possible to train for too long, actually making your model worse. But you get the general idea: show the training examples, make predictions, update the model's parameters based on how the predictions are, repeat until the model is good enough.

As you can tell, training machine-learning models is a brute-force and time-consuming process. The algorithm has to figure out how to solve the problem through trial and error. It's no surprise that it takes a lot of processing power. Depending on the complexity of the algorithm you've chosen and the amount of training data, training a model can take anywhere from several minutes to several weeks, on a computer with very fast processors. If you want to do serious training, you can rent time on an Amazon, Google or Microsoft server, or even a cluster of servers, which does the job much faster than your laptop or desktop

# What does the model actually learn?

Exactly what a model learns depends on the algorithm you've chosen. A decision tree, for example, literally learns the kind of if-then-else rules a human would have created. But most other machine-learning algorithms don't learn rules directly, but a set of numbers called the learned parameters, or just "parameters", of the model.

These numbers represent what the algorithm has learned, but they don't always make sense to us humans. We can't simply interpret them as if-then-else, the math is more complex than that.