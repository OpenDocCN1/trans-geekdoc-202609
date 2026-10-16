
We've now performed a real-deal—no mock-up—kernel method. We computed a SVM with `SVC(kernel='poly')`. It has something pretty amazing going on under the hood. Somehow, we can tell `SVC` to use a kernel internally and then it takes the raw data and operates *as if* we are doing manual feature construction. Things get even better. We don't have to explicitly construct all the features. More specifically, we don't have to build the full set of all the features that a kernel implies building. We don't do it and `SVC` doesn't do it either. Through the *kernel trick*, we can replace (1) explicitly constructing features and comparing examples in the bigger feature space with (2) simply computing distances between objects using the kernel.

## 13.2.3 Kernel Methods and Kernel Options

Now, let's talk a bit about what kernels are and how they operate.

### 13.2.3.1 Overview of Kernels

Kernels may seem like a magic trick that can solve very serious problems. While they aren't really magic, they are really useful. Fundamentally, kernel methods involve two plug-and-play components: a kernel and a learning method. The kernel shows up in two forms: a kernel function and a kernel matrix. The function form may be a bit abstract, but a kernel matrix is simply a table of example similarities. If you give me two examples, I tell you how similar they are by looking up a value in the table. The learners used with kernel methods are often linear methods, but a notable exception is nearest neighbors. Whatever method is used, the learner is often described and implemented in a way that emphasizes relationships between *examples* instead of relationships between *features*. As we said before, covariance-based methods are all about feature-to-feature interactions. Kernel methods and the kernel matrices are about example-to-example interaction.

Up to now, we've been representing examples by a set of features—remember the ruler dude from Chapter 1?—and then compared examples based on the similarity or distance between those feature values. Kernels take a different view: they compare examples by directly measuring similarity between pairs of examples. The kernel view is more general: anything our traditional representation can do, kernels can do also. If we simply treat the examples as points in space and calculate the dot product between the examples—*presto!*—we have a simple kernel. In fact, this is what a *linear kernel* does. In the same way that *all*-Nearest Neighbors—that is, a nearest neighbors method which includes information from *everyone*—relies on the information from every example, kernel methods also rely on these pairwise connections. I'll make one last point to minimize confusion. Kernels measure similarity which *increases* as examples become more alike; distance measures distance-apart-ness which *decreases* as examples become more alike.

There's one last major win of the kernel approach. Since kernels rely on pairwise relationships between examples, *we don't have to have our initial data in a table of rows and columns to use a kernel*. All we need are two individuals that we can identify and *look up* in the kernel table. Imagine that we are comparing two strings—"the cat in the hat" and “the cow jumped over the moon”. Our traditional learning setup would be to measure many features of those strings (the number of a's, the number of occurrences of the word cow, etc.), put those features in a data table, and then try to learn. With kernel methods, we can directly compute the similarity relationship between the strings and work with those similarity values. It may be significantly easier to define relationships—similarities—between examples than to turn examples into sets of features. In the case of text strings, the concept of edit distance fits the bill very nicely. In the case of biological strings—DNA letters like AGCCAT—there are distances that account for biological factoids like mutation rates.

Here’s a quick example. I don’t know how to graph words in space. It just doesn’t make sense to me. But, if I have some words, I can give you an idea of how similar they are. If I start at 1.0 which means “completely the same” and work down towards zero, I might create the following table for word similarity:

|  | cat | hat | bar |
|---|---|---|---|
| cat | 1 | .5 | .3 |
| hat | .5 | 1 | .3 |
| bar | .3 | .3 | 1 |

Now, I can say how similar I think any pair of example words are: cat versus hat gives .5 similarity.

What’s the point? Essentially, we can directly apply preexisting background knowledge—also known as assumptions—about the similarities between the data examples. There may be several steps to get from simple statements about the real world to the numbers that show up in the kernel, but it can be done. Kernels can apply this knowledge to arbitrary objects—strings, trees, sets—not just examples in a table. Kernels can be applied to many learning methods: various forms of regression, nearest-neighbors, and principal components analysis (PCA). We haven’t discussed PCA yet, but we will see it soon.

### 13.2.3.2 How Kernels Operate

With some general ideas about kernels, we can start looking at their mathematics a bit more closely. As with most mathematical topics in this book, all we need is the idea of dot product. Many learning algorithms can be kernelized. What do we mean by this? Consider a learning algorithm ℒ. Now, reexpress that algorithm in a different form: ℒ_dot, where the algorithm has the same input-output behavior—it computes the same predictions from a given training set—but it is written in terms of dot products between the examples: dot(E, F). If we can do that, then we can take a second step and replace all occurrences of the dot(E, F) with our kernel values between the examples K(E, F). Presto—we have a kernelized version ℒ_k of ℒ. We go from ℒ to ℒ_dot to ℒ_k.

When we use K instead of dot, we are mapping the Es into a different, usually higher-dimensional, space and asking about their similarity there. That mapping essentially adds more columns in our table or axes in our graph. We can use these to describe our data. We'll call the mapping from here to there a warp function—cue Picard, “make it so”—φ(E). φ is a Greek “phi”, pronounced like “fi” in a giant’s fee-fi-fo-fum. φ takes an example and moves it to a spot in a different space. This translation is precisely what we did by hand when we converted our circle problem into a line problem in Section 13.2.2.

In the circle-to-line scenario, our degree-2 polynomial kernel K₂ took two examples E and F and performed some mathematics on them: K₂(E, F) = (dot(E, F))². In Python, we’d write that as `np.dot(E,F)**2` or similar. I’m going to make a bold claim: there is a φ—a warp function—that makes the following equation work:

$$K_2(E, F) = \text{dot}(\varphi_2(E), \varphi_2(F))$$

That is, we could either (1) compute the kernel function K₂ between the two examples or (2) map both examples into a different space with φ₂ and then take a standard dot product. We haven’t specified φ₂, though. I’ll tell you what it is and then show that the two methods work out equivalently. With two features (e₁, e₂) for E, φ₂ looks like

$$\varphi_2(E) = \varphi_2(e_1, e_2) \rightarrow (e_1 e_1, e_1 e_2, e_2 e_1, e_2 e_2)$$

Now, we need to show that we can expand—write out in a longer form—the left-hand side K₂(E, F) and the right-hand side dot(φ₂(E), φ₂(F)) and get the same results. If so, we’ve shown the two things are equal.

Expanding K₂ means we want to expand (dot(E, F))². Here goes. With E = (e₁, e₂) and F = (f₁, f₂), we have dot(E, F) = e₁f₁ + e₂f₂. Squaring it isn’t fun, but it is possible using the classic (a + b)² = a² + 2ab + b² formula:

$$\begin{aligned}
(\text{dot}(E, F))^2 &= (e_1 f_1 + e_2 f_2)^2 \\
&= (e_1 f_1)^2 + 2(e_1 f_1 e_2 f_2) + (e_2 f_2)^2 \quad \star
\end{aligned}$$

Turning to the RHS, we need to expand dot(φ₂(E), φ₂(F)). We need the φ₂ pieces which we get by expanding out a bunch of interactions:

$$\varphi_2(E) = (e_1 e_1, e_1 e_2, e_2 e_1, e_2 e_2)$$

$$\varphi_2(F) = (f_1 f_1, f_1 f_2, f_2 f_1, f_2 f_2)$$

With those in place, we have

$$\begin{aligned}
\text{dot}(\varphi_2(E), \varphi_2(F)) &= e_1^2 f_1^2 + 2(e_1 f_1 e_2 f_2) + e_2^2 f_2^2 \\
&= (e_1 f_1)^2 + 2(e_1 f_1 e_2 f_2) + (e_2 f_2)^2 \quad \star\star
\end{aligned}$$

We can simply read off that ★ and ★★ are the same thing. Thankfully, both expansions work out to the same answer. Following the second path required a bit more work because we had to explicitly expand the axes before going back and doing the dot product. Also, the dot product in the second path had more terms to deal with—four versus two. Keep that difference in mind.
