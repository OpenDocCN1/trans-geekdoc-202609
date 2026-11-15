Of course, each tool has its time and place and, more importantly, an application domain where it excels. I find recurrent neural networks quite interesting for the many features they can achieve:

+   - Produce consistent markup text (opening and closing tags, recognizing timestamp-like data)
+   - Write Wikipedia articles with references, and create URLs from non-existing addresses, by learning what a URL should look like
+   - Create credible-looking scientific papers from LaTeX

All these amazing features are possible without the network having any context information or metadata. In particular, without knowing English, nor what a URL or a bit of LaTeX syntax looks like.

These and even more interesting capabilities of neural networks are superbly described by Andrej Karpathy in The Unreasonable Effectiveness of Recurrent Neural Networks: http://karpathy.github.io/2015/05/21/rnn-effectiveness/.

> What makes recurrent neural networks exciting? Instead of a constrained fixed-input size to fixed-output size, we can operate over sequences of vectors instead.

A limitation of many machine learning algorithms, including standard feed-forward neural networks, is that they accept a fixed size vector as input and produce a fixed size vector as output. For instance, if we want to classify text, we receive a corpus of documents from which we create a vocabulary to vectorize each document and the output is a vector with class probabilities. Recurrent neural networks instead allow us to take sequences of vectors as input. So, from a one-to-one correspondence between fixed input size and fixed output size, we have a much richer landscape, one-to-one, one-to-many, many-to-one, many-to-many.

Why is that desirable? Let's look at a few examples:

+   - One-to-one: Supervised learning, for instance, text classification
+   - One-to-many: Given an input text, generate a summary (a sequence of words with important information)
+   - Many-to-one: Sentiment analysis in text
+   - Many-to-many: Machine translation