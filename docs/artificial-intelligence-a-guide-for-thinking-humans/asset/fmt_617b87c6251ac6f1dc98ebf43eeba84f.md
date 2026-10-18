
> In linguistics, this idea is known more formally as distributional semantics. The underlying hypothesis of distributional semantics is that “the degree of semantic similarity between two linguistic expressions A and B is a function of the similarity of the linguistic contexts in which A and B can appear.”^() ![FIGURE 34: A, illustration of two word-clusters in a semantic space in which words with similar meanings are located close to one another; B, a three-dimensional semantic space in which words are plotted as points](images/Figure34.jpg)

> FIGURE 34: *A*, illustration of two word-clusters in a semantic space in which words with similar meanings are located close to one another; *B*, a three-dimensional semantic space in which words are plotted as points

When we’re talking about semantic *spaces* with multiple *dimensions*, we find ourselves in the realm of geometry. Indeed, NLP practitioners often frame the “meaning” of words in terms of geometric concepts. For example, [figure 34*B*](#chapter11.xhtml#fig34) shows a three-dimensional space, with *x-*, *y-*, and *z-*axes, along which words can be placed. Each word is identified with a point (black circle), defined by three coordinates—that is, the *x*, *y*, and *z* locations of the point. The semantic distance between two words is equated with the geometric distance between points on this plot. You can see that *charm* is now close to both *wit* and *humor* and to *bracelet* and *jewelry*, but along different dimensions. In NLP, people use the term *word vector* to refer to the coordinates of a particular word in such a semantic space. In mathematics, *vector* is just a fancy term for the coordinates of a point.^()

The idea here is that once all the words in the vocabulary are properly placed in the semantic space, the *meaning* of a word can be represented by its location in this space—that is, by the coordinates defining its word vector. And what is a word vector good for? It turns out that using word vectors as numerical inputs to represent words, as opposed to the simple one-hot scheme I sketched above, greatly improves the performance of neural networks in NLP tasks.

How do we actually obtain all the word vectors corresponding to words in a vocabulary? Is there an algorithm that will properly place all the words in our network’s vocabulary in a semantic space in order to best capture the many dimensions of each word’s meaning? A lot of important work in NLP has gone into solving this exact problem.

## Word2Vec

Many solutions have been suggested for the problem of placing words in a geometric space, some going back to the 1980s, but today’s most widely adopted method was proposed in 2013 by researchers at Google.^()

The word2vec method embodies the notion of “you shall know a word by the company it keeps.” To create the training data for the word2vec program, the Google group started by taking a massive set of documents from the Google News service. (In modern NLP, nothing beats having “big data” lying around!) The training data for the word2vec program consisted of a collection of pairs of words, where each word in the pair had occurred near the other word in the pair somewhere in the Google News documents. To make the process work better, extremely frequent words such as *the*, *of*, and *and* were discarded.

As a concrete example, assume that the words of each pair occur immediately adjacent to each other in a sentence. In this case, the sentence “a man went into a restaurant and ordered a hamburger” first would be transformed into “man went into restaurant ordered hamburger.” This would yield the following pairs: (man, went), (went, into), (into, restaurant), (restaurant, ordered), (ordered, hamburger), plus the reverse of all the pairs—for example, (hamburger, ordered). The idea is to train the word2vec network to predict what words are likely to be paired with a given input word.

![FIGURE 35: Illustration of the word2vec neural network, given the word pair (hamburger, ordered)](images/Figure35.jpg)

FIGURE 35: Illustration of the word2vec neural network, given the word pair (hamburger, ordered)

[Figure 35](#chapter11.xhtml#fig35) illustrates the word2vec neural network.^()

The Google researchers trained their network on billions of word pairs collected from Google News articles. Given a word pair such as (hamburger, ordered), the input corresponding to the first word in the pair (hamburger) is set to 1; all other inputs are set to 0. During training, each output unit’s activation is interpreted to be the network’s confidence that the corresponding word in the vocabulary has occurred adjacent to the input word. Here, the *correct* output activations would assign high confidence to the second word in the pair (ordered).

After the training is completed, one can extract the learned *word vector* for any word in the vocabulary. [Figure 36](#chapter11.xhtml#fig36) illustrates how this is done. The figure shows the weighted connections between one input (corresponding to the word *hamburger*) and the three hundred hidden units. These weights, which have been learned from the training data, have captured information about the contexts in which the corresponding word is used. These three hundred weight values are the components of the word vector assigned to the given word. (The connections from the hidden units to the outputs are completely ignored in this process; all the necessary information resides in the input-to-hidden-layer weights.) Thus, the word vectors learned by this network have three hundred dimensions. The collection of word vectors for all words in the vocabulary constitutes the learned “semantic space.”

Here’s how you can visualize this three-hundred-dimensional semantic space in your head. Just think of the three-dimensional plot from [figure 34](#chapter11.xhtml#fig34) and then try to visualize a similar plot with a hundred times as many dimensions, and with seven hundred thousand words plotted, each with three hundred coordinates. Just kidding! It’s impossible to visualize such a thing.

What do these three hundred dimensions represent? If we ourselves were three-hundred-dimensional creatures who had the brains to visualize such a space, we’d see that any given word is close to other related words across many meanings. For example, the vector for *hamburger* is close to the vector for *ordered*; it is also close to the vectors for *burger*, *hot dog*, *cow*, *eat*, and so on. *Hamburger* is also close to *dinner* even if it has never been seen in a pair with *dinner*; this is because *hamburger* is close to words that are also close to *dinner* in similar contexts. If the network sees word pairs from “I ate a hamburger for lunch” as well as from “I devoured a hot dog for dinner,” and if *lunch* and *dinner* also appear close together in some training sentences, then the system can learn that *hamburger* and *dinner* should also be close.

![FIGURE 36: Illustration of how to obtain a word vector from the trained word2vec network](images/Figure36.jpg)

FIGURE 36: Illustration of how to obtain a word vector from the trained word2vec network

Let’s remember that the goal of this whole process is to find a numerical representation—a vector—for each word in the vocabulary, one that captures something of the semantics of the word. The hypothesis is that using such word vectors will result in high-performing neural networks for natural-language processing tasks. But to what extent does the “semantic space” created by word2vec actually capture word semantics?
