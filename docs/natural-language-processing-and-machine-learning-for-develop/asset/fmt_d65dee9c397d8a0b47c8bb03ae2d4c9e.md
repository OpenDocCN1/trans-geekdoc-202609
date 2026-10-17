
Discrete text representations refer to techniques in which words are represented independently of each other. For example, the tf-idf value of each word in a corpus is based on its term frequency multiplied by the logarithm of its inverse document frequency. Thus, the tf-idf value of each word is unaffected by the semantics of the other words in the corpus.

Moreover, if a new document is added to a corpus, or an existing document is reduced or increased in size, then the initial tf-idf value will change for some of the words in the original corpus. However, the new value does not include any of the semantics of the newly added words.

By contrast, distributed text representations create representations that *are* based on multiple words: thus, the representations of words are not mutually exclusive. For example, distributed text representations include co-occurrence matrices, word2vec, and GloVe, and fastText. Keep in mind that word2vec involves a neural network to generate word vectors, whereas GloVe uses a matrix oriented technique (with SVD), which is discussed in Chapter [6](#ch06.xhtml). In addition, word2vec and GloVe are limited to *one* word embedding for every word, which means that a word that’s used with two or more different contexts will have the same embedding for every occurrence of that word.

Finally, contextual word representations are representations that take into account all the other words in a given sentence. Hence, if a word appears in two sentences with two different meanings (i.e., context), then the word will have two different word embeddings for the two sentences. This is the fundamental idea that underlies the statement “all you need is attention.” The attention mechanism is used in transformers, both of which are discussed in Chapter [11](#ch11.xhtml).

## **What is Cosine Similarity?**

You are probably familiar with the Euclidean distance metric for finding the distance between a pair of points in the Euclidean plane: their distance can be calculated via the Pythagorean theorem. The Euclidean distance metric can be generalized to n-dimensions by generalizing the formula for the Pythagorean theorem from two dimensions to n-dimensions.

If we represent words as numeric vectors, then it’s reasonable to ask: if two words have similar meanings, then how do we compare their vector representations? One way involves calculating the difference between the two vectors. For instance, suppose we are in two-dimensions (because this will simplify the example), and word U is a vector u with components [u1,u2], and word V is a vector v with components [v1,v2]. Then the difference between these two vectors is [u1-v1, u2-v2].

However, the difference between these vectors increases significantly if we multiply each of these vectors by a positive integer. In essence, we want to treat the vectors u and v as having the same property as u and 10*v, which we cannot accomplish if we use the Euclidean metric.

The solution is to calculate the cosine of the *angle* between a pair of vectors, which is called the *cosine similarity* of two vectors. The *cosine* function is a trigonometric function of the angle between the two vectors. In brief, suppose that a right-angled triangle has sides of length a and b, a hypotenuse of length c (that’s the “slanted” side), and the angle between the sides of length a and c is theta. Then the cosine of the angle theta is defined as follows:

cosine(theta) = a/c 

The preceding formula applies to values of theta between 0 and 90 degrees (inclusive). Since a and c are positive, then a/c > 0, and since a < c, then a/c < 1. In addition, the definition can be extended as follows:

if   0 <= theta <= 90:  cosine(theta) = a/c (as defined above) if  90 <= theta <= 180: cosine(theta) = (-1)\*cosine(180-theta) if 180 <= theta <= 270: cosine(theta) = (-1)\*cosine(270-theta) if 270 <= theta <= 360: cosine(theta) = (+1)\*cosine(360-theta) 

As you can see, the cosine of theta is negative when theta is between 90 and 180, and its range of values is between 0 and -1. Since the cosine of theta is between 0 and 1 when theta is between 0 and 90, we arrive at the following result:

\-1 <= cosine(theta) <= 1 (for 0<= theta <= 360) 

We can generalize further for angles that are less than 0 or greater than 360: simply add (or subtract) multiples of 360 until we get an angle between 0 and 360:

cosine(-100) = cosine(-100+1\*360) = cosine(260) = (-1)\*cosine(10) cosine(750) = cosine(750-2\*360) = cosine(30) 

However, two vectors always form an angle that is between 0 and 180 inclusive. Since values of the cosine function are always between −1 and 1 inclusive, the cosine similarity of two vectors is also between −1 and 1 inclusive. As a reminder, the cosine of 0 degrees is 1, the cosine of 90 degrees is 0, and the cosine of 180 degrees is −1.

The intuition of cosine similarity is that “closer” vectors have a smaller angle between them, which means that the cosine of the angle is closer to 1, and so the words have similar meanings. Two vectors whose angle between them is close to 90 have a cosine similarity that is close to 0, and so the words are less related to each other. Finally, two vectors that “point” in opposite directions will have an angle of 180 degrees, and the cosine of 180 is -1, so the two words are potential antonyms.

You can get the inner product of two vectors A and B as:

A "dot" B = |A|\*|B|\*cosine(theta) cosine(theta) = (A "dot" B) /( |A|\*|B|)   Example: suppose that A = [1, 1] B = [2, 0]: cosine(theta) = (1\*2+1\*0)/\[sqrt(2)\*2\] = 1/sqrt(2) In this case, theta is 45 degrees 

Note that vectors are often “normalized,” which means that they are scaled so that their length equals 1. Scaling a vector involves dividing a vector by its magnitude (also called the “norm”), which is calculated via the Pythagorean theorem.

Example #1: If A = [1,1], then |A| = sqrt(1\*1+1\*1) = sqrt(2), and: A/|A| = [1/sqrt(2), 1/sqrt(2)] (about [0.707,0.707])   Example #2: If A = [2,0], then |A| = sqrt(2\*2+0\*0) = sqrt(4) = 2, and: A/|A| = [2/2, 0/2] = [1, 0]   Example #3: If A = [3,4], then |A| = sqrt(3\*3+4\*4) = sqrt(25) = 5, and: A/|A| = [3/5, 4/5]   Example #4: If A = [-4,3], then |A| = sqrt((-4)\*(-4)+3\*3) = sqrt(25) = 5, and: A/|A| = [-4/5, 3/5] 

Although cosine similarity works well in many cases, it’s not a perfect solution. For example, it’s possible to have two sparse vectors representing two sentences with similar meaning, even if they have no words in common, they could have a cosine similarity around 0.6.

In addition to cosine similarity, there are other well-known distance metrics, some of which are discussed in Appendix A.

##**Text Vectorization (aka Word Embeddings)**

In common parlance, *text vectorization* involves the creation of word embeddings, where each word embedding is a dense one-dimensional vector of floating point numbers. Moreover, the word embeddings are generated by a shallow neural network or MF. The good news is that there are various publicly available word embeddings available, so you don’t need to be concerned about generating those vectors.

Depending on your task, you might be able to work with small vectors, such as 1×16 or 1×32 vectors. By comparison, the word embeddings in the BERT model (discussed in Chapter [11](#ch11.xhtml)) are 1×512 vectors.

Since we can add floating point vectors that have the same number of components, we can calculate the average of two or more word vectors. Hence, it’s possible to represent a document as the average vector of the words vectors in that document. However, such a vector is not necessarily meaningful with respect to the document.

You can use word embeddings to find co-occurrences. For example, “good” and “bad” both appear in a corpus and are near each other in an embedding space, despite the fact that “good” and “bad” are antonyms.
