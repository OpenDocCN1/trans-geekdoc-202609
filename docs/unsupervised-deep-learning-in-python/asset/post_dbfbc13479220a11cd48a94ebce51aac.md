
```python
plt.imshow(X, cmap='gray')
```

To ensure the image is grayscale rather than a heatmap.

For the layers beyond the input-to-hidden, we can't solve in closed-form, so we return to our old friend gradient descent.

This should be simple since Theano can calculate gradients for us. The only caveat is that you now need to take the derivative with respect to the input, not the weights, like we usually do during training.

## Chapter 6: Tricking a Neural Network

Now that you know how to take the derivative of a variable with respect to the inputs instead of the weights, we are ready to talk about how to trick a neural network.

The key is the cost function, J.

We want to increase the cost function as much as possible, while inducing minimal changes in X.

To do that, we simply ask, "in what direction should I change X, such that it results in the maximum change in J?"

This is again just a calculus problem - we want to find dJ/dX.

And again, we use Theano to automatically calculate the gradient.

Once you've done that, we simply change X by a small amount in that direction.

```python
X = X + eps*dJ/dX
```

Where eps is a small number.

What you should find that is the image itself doesn't look any different (remember, matplotlib will scale your values to be from 0..255), but the neural network has a good chance of classifying the image wrong, even when it classifies the original image right.

What implications does this have in terms of training a neural network?

You surely don't want your neural network to be so easily fooled, and the key here is something we've already talked about before:

Data augmentation.

The example I like to give: an upside-down cat is still a cat. A cat shifted to the left is still a cat. A rotated cat is still a cat.

So if you only have one cat, you should create these invariant transformations and include them as training data.

Similarly, a cat with some noise is still a cat.

This is like what we did with autoencoders - set some of the inputs to 0. A cat with some 0s is still a cat, so add that as training data.

And like we've seen in this chapter, a cat + some “intelligently designed” noise is still a cat, so include that as training data too.

By including all these forms of data augmentation, you are making your neural network more robust.

## Conclusion

I really hope you had as much fun reading this book as I did making it.

Did you find anything confusing? Do you have any questions?

I am always available to help. Just email me at: info@lazyprogrammer.me

I do 1:1 coaching and consulting as well.

Do you want to learn more about deep learning? Perhaps online courses are more your style. I happen to have a few of them on Udemy.

My first course in deep learning is a lot like the book, but you get to see me derive the formulas and write the code live:

Data Science: Deep Learning in Python

https://udemy.com/data-science-deep-learning-in-python

Are you comfortable with this material, and you want to take your deep learning skillset to the next level? My follow-up Udemy course on deep learning is for you. Similar to this book, I take you through the basics of Theano and TensorFlow - creating functions, variables, expressions, and build up neural networks from scratch. I teach you about ways to accelerate the learning process, including batch gradient descent, momentum, and adaptive learning rates. I also show you how to create a GPU instance on Amazon AWS EC2, and prove to you that training a neural network with GPU optimization can be orders of magnitude faster than on your CPU.

Data Science: Practical Deep Learning in Theano and TensorFlow

https://www.udemy.com/data-science-deep-learning-in-theano-tensorflow

When you've got the basics of deep learning down, you're ready to explore alternative architectures. One popular alternative is the convolutional neural network, created specifically for image classification. These have promising applications in medical imaging, self-driving vehicles, and more. In this course, I show you how to build convolutional nets in Theano and TensorFlow.

### Deep Learning: Convolutional Neural Networks in Python

https://www.udemy.com/deep-learning-convolutional-neural-networks-theano-tensorflow

In part 4 of my deep learning series, I take you through unsupervised deep learning methods (that's this book!). We study principal components analysis (PCA), t-SNE (jointly developed by the godfather of deep learning, Geoffrey Hinton), deep autoencoders, and restricted Boltzmann machines (RBMs). I demonstrate how unsupervised pretraining on a deep network with autoencoders and RBMs can improve unsupervised learning performance.

### Unsupervised Deep Learning in Python

https://www.udemy.com/unsupervised-deep-learning-in-python

Would you like an introduction to the basic building block of neural networks - logistic regression? In this course I teach the theory of logistic regression (our computational model of the neuron), and give you an in-depth look at binary classification, manually creating features, and gradient descent. You might want to check this course out if you found the material in this book too challenging.

### Data Science: Logistic Regression in Python

https://udemy.com/data-science-logistic-regression-in-python

To get an even simpler picture of machine learning in general, where we don't even need gradient descent and can solve for the optimal model parameters directly in “closed-form”, you'll want to check out my first Udemy course on the classical statistical method - linear regression:

### Data Science: Linear Regression in Python

https://www.udemy.com/data-science-linear-regression-in-python

If you are interested in learning about how machine learning can be applied to language, text, and speech, you’ll want to check out my course on Natural Language Processing, or NLP:

Data Science: Natural Language Processing in Python

https://www.udemy.com/data-science-natural-language-processing-in-python

If you are interested in learning SQL - structured query language - a language that can be applied to databases as large as the ones sitting on your iPhone, to databases as large span multiple continents - and not learn the mechanics of the language but know how to apply it to real-world data analytics and marketing problems? Check out my course here:

SQL for Marketers: Dominate data analytics, data science, and big data

https://www.udemy.com/sql-for-marketers-data-analytics-data-science-big-data

Are you interested in stock prediction, time series, and sequences in general? My Hidden Markov Models course is where you want to be. I teach you not all the classical theory of HMMs, but I also show you how to write in Theano using gradient descent! This is great practice for writing deep learning models and it will prepare you for its sequel, Deep Learning Python Part 5: Recurrent Neural Networks in Python. You can get the HMM course here:

Unsupervised Machine Learning: Hidden Markov Models in Python

https://udemy.com/unsupervised-machine-learning-hidden-markov-models-in-python

Finally, I am always giving out coupons and letting you know when you can get my stuff for free. But you can only do this if you are a current student of mine! Here are some ways I notify my students about coupons and free giveaways:

- My newsletter, which you can sign up for http://lazyprogrammer.me (it comes with a free 6-week intro to machine learning course)
- My Twitter, https://twitter.com/lazy_scientist
- My Facebook page, https://facebook.com/lazyprogrammer.me (don’t forget to hit “like”!)
