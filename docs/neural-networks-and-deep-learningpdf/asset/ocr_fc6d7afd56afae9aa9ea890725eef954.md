# CHAPTER 6

# Deep learning

In the last chapter we learned that deep neural networks are often much harder to train than shallow neural networks. That's unfortunate, since we have good reason to believe that *if* we could train deep nets they'd be much more powerful than shallow nets. But while the news from the last chapter is discouraging, we won't let it stop us. In this chapter, we'll develop techniques which can be used to train deep networks, and apply them in practice. We'll also look at the broader picture, briefly reviewing recent progress on using deep nets for image recognition, speech recognition, and other applications. And we'll take a brief, speculative look at what the future may hold for neural nets, and for artificial intelligence.

The chapter is a long one. To help you navigate, let's take a tour. The sections are only loosely coupled, so provided you have some basic familiarity with neural nets, you can jump to whatever most interests you.

The *main part of the chapter* is an introduction to one of the most widely used types of deep network: deep convolutional networks. We'll work through a detailed example - code and all - of using convolutional nets to solve the problem of classifying handwritten digits from the MNIST data set:

![](bbox=[0.305, 0.615, 0.465, 0.645])

We'll start our account of convolutional networks with the shallow networks used to attack this problem earlier in the book. Through many iterations we'll build up more and more powerful networks. As we go we'll explore many powerful techniques: convolutions, pooling, the use of GPUs to do far more training than we did with our shallow networks, the algorithmic expansion of our training data (to reduce overfitting), the use of the dropout technique (also to reduce overfitting), the use of ensembles of networks, and others. The result will be a system that offers near-human performance. Of the 10,000 MNIST test images - images not seen during training! - our system will classify 9,967 correctly. Here's a peek at the 33 images which are misclassified. Note that the correct classification

+   - Neural Networks and Deep Learning
+   - What this book is about
+   - On the exercises and problems
+   - Using neural nets to recognize handwritten digits
+   - How the backpropagation algorithm works
+   - Improving the way neural networks learn
+   - A visual proof that neural nets can compute any function
+   - Why are deep neural networks hard to train?
+   - Deep learning
+   - Appendix: Is there a *simple* algorithm for intelligence?
+   - Acknowledgements
+   - Frequently Asked Questions

If you benefit from the book, please make a small donation. I suggest $3, but you can choose the amount.

![](bbox=[0.678, 0.49, 0.81, 0.52])

# Sponsors

![](bbox=[0.678, 0.555, 0.815, 0.59])

![](bbox=[0.678, 0.6, 0.82, 0.62])

![](bbox=[0.678, 0.63, 0.82, 0.66])

![](bbox=[0.678, 0.67, 0.82, 0.69])

Thanks to all the supporters who made the book possible, with especial thanks to Pavel Dudrenov. Thanks also to all the contributors to the Bugfinder Hall of Fame.

# Resources

+   - Book FAQ
+   - Code repository
+   - Michael Nielsen's project announcement mailing list
+   - Deep Learning, draft book in preparation, by Yoshua Bengio, Ian