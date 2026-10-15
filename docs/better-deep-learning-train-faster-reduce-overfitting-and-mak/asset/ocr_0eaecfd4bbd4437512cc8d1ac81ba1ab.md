Some more specific recommendations include:

+   - **Classical**: use early stopping and weight decay (L2 weight regularization).
+   - **Alternate**: use early stopping and added noise with a weight constraint.
+   - **Modern**: use early stopping and dropout, in addition to a weight constraint.

These recommendations would suit Multilayer Perceptrons and Convolutional Neural Networks. Some recommendations for recurrent neural nets include:

+   - **Classical**: use early stopping with added weight noise and a weight constraint such as maximum norm.
+   - **Modern**: use early stopping with a backpropagation-through-time-aware version of dropout and a weight constraint.

There are no silver bullets when it comes to regularization and systematic experimentation is strongly encouraged.

# 12.5 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

# 12.5.1 Books

+   - Chapter 7: Regularization for Deep Learning, *Deep Learning*, 2016.
+     https://amzn.to/2NJW3gE
+   - Section 5.5: Regularization in Neural Networks, *Pattern Recognition and Machine Learning*, 2006.
+     https://amzn.to/2Q2rEeP
+   - Chapter 16: Heuristics for Improving Generalization, *Neural Smithing: Supervised Learning in Feedforward Artificial Neural Networks*, 1999.
+     https://amzn.to/2Dxo4XU
+   - Chapter 9: Learning and Generalization, *Neural Networks for Pattern Recognition*, 1995.
+     https://amzn.to/2I9gNMP

# 12.5.2 Articles

+   - What is overfitting and how can I avoid it? Neural Network FAQ.
+     ftp://ftp.sas.com/pub/neural/FAQ3.html#A_over
+   - Regularization (mathematics), Wikipedia.
+     https://en.wikipedia.org/wiki/Regularization_(mathematics)