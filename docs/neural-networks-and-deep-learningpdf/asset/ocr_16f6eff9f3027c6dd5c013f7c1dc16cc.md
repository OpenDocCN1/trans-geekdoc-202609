# # CHAPTER 3

# # Improving the way neural networks learn

When a golf player is first learning to play golf, they usually spend most of their time developing a basic swing. Only gradually do they develop other shots, learning to chip, draw and fade the ball, building on and modifying their basic swing. In a similar way, up to now we've focused on understanding the backpropagation algorithm. It's our "basic swing", the foundation for learning in most work on neural networks. In this chapter I explain a suite of techniques which can be used to improve on our vanilla implementation of backpropagation, and so improve the way our networks learn.

The techniques we'll develop in this chapter include: a better choice of cost function, known as the cross-entropy cost function; four so-called "regularization" methods (L1 and L2 regularization, dropout, and artificial expansion of the training data), which make our networks better at generalizing beyond the training data; a better method for initializing the weights in the network; and a set of heuristics to help choose good hyper-parameters for the network.

I'll also overview several other techniques in less depth. The discussions are largely independent of one another, and so you may jump ahead if you wish. We'll also implement many of the techniques in running code, and use them to improve the results obtained on the handwriting classification problem studied in Chapter 1.

Of course, we're only covering a few of the many, many techniques which have been developed for use in neural nets. The philosophy is that the best entree to the plethora of available techniques is in-depth study of a few of the most important. Mastering those important techniques is not just useful in its own right, but will also deepen your understanding of what problems can arise when you use neural networks. That will leave you well prepared to quickly pick up other techniques, as you need them.

# ## The cross-entropy cost function

+   - Neural Networks and Deep Learning
+   - What this book is about
+   - On the exercises and problems
+   - Using neural nets to recognize handwritten digits
+   - How the backpropagation algorithm works
+   - Improving the way neural networks learn
+   - A visual proof that neural nets can compute any function
+   - Why are deep neural networks hard to train?
+   - Deep learning
+   - Appendix: Is there a simple algorithm for intelligence?
+   - Acknowledgements
+   - Frequently Asked Questions

If you benefit from the book, please make a small donation. I suggest $3, but you can choose the amount.

![](bbox=[0.72, 0.49, 0.78, 0.505])

![](bbox=[0.677, 0.505, 0.81, 0.515])

# ## Sponsors

![](bbox=[0.677, 0.555, 0.81, 0.595])

![](bbox=[0.677, 0.6, 0.82, 0.62])

![](bbox=[0.677, 0.63, 0.82, 0.65])

![](bbox=[0.677, 0.66, 0.82, 0.68])

Thanks to all the supporters who made the book possible, with especial thanks to Pavel Dudrenov. Thanks also to all the contributors to the Bugfinder Hall of Fame.

# ## Resources

+   - Book FAQ
+   - Code repository
+   - Michael Nielsen's project announcement mailing list
+   - Deep Learning, draft book in preparation, by Yoshua Bengio, Ian