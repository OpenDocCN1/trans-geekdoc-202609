
Once the scaled probabilities have been calculated for each case in the dataset, we have a matrix of probabilities that describes how similar each case is to each of the other cases. This is visualized in Figure 14.2 as a heatmap, which is a useful way of thinking about it.

Figure 14.1 t-SNE measures the distances from each case to every other case, converted into a probability by fitting a normal distribution over the current case. These probabilities are scaled by dividing them by their sum, so that they add to one.

Our matrix of probabilities is now our reference or template for how the data relate to each other in the original, high-dimensional space. The next step in the t-SNE algorithm is to randomize the cases along (usually) two new axes (this is where the "stochastic" bit from the name comes from).

Figure 14.2 The scaled probabilities for each case are stored as a matrix of values. This is visualized here as a heatmap, where the closer two cases are, the darker the box is that represents their distance in the heatmap.

It doesn't need to be two, but it commonly is. This is because humans struggle to visualize data in more than two dimensions at once, and because beyond three dimensions, the computational cost of t-SNE becomes more and more prohibitive.

t-SNE calculates the distances between the cases in this new, randomized, low-dimensional space and converts them into probabilities just like before. The only difference is that instead of using the normal distribution, it now uses the Student's t distribution. The t distribution looks a bit like a normal distribution, except that its not quite as tall in the middle, and its tails are flatter and extend further out (see Figure 14.3). It's a bit like if someone sat on a normal distribution and squashed it a little. This is where the "t" in t-SNE comes from. I'll explain why we use the t distribution momentarily.

![](img/a22105d68c35e8d5bd3c7bafb4644881_346_0.png)

The job for t-SNE now is "shuffle" the data points around these new axes, step-by-step, to make the probability matrix in the lower-dimensional space look as close as possible to the matrix of probabilities in the original, high-dimensional space. The intuition here is that if the matrices are as similar as possible, then the data each case was close to in the original feature space, will still be close by in the low-dimensional space. You can think of this as a game of attraction and repulsion.

To make the probability matrix in low-dimensional space look like the one in high-dimensional space, each case needs to move closer to cases that were close to it in the original data, and away from cases that were far away. So cases that should be nearby will pull their neighbor towards them, but cases that should be far away will push non-neighbors away from them. The balance of these attractive and repulsive forces causes each case in the dataset to move in a direction that makes the two probability matrices a little more similar. Now, in this new position, the low- and high-dimensional matrices look a little more similar again. This process continues until we reach a predetermined number of iterations, or until the divergence (difference) between the matrices stops improving. This whole process is illustrated in Figure 14.4.

> **NOTE** The difference between the two matrices is measured using a statistic called the Kullback–Leibler divergence, which is large when the matrices are very different, and zero when the matrices are perfectly identical.

Now why do we use the t distribution to convert distances into probabilities in the low-dimensional space? Well, notice again from Figure 14.4 that the tails of the t distribution are wider than for the normal distribution. This means that, in order to get the same probability as from the normal distribution, dissimilar cases need to be pushed further away from the case the t distribution is centered over. This helps spread out clusters of data that might be present in the data, helping us to identify them more easily. A major consequence of this however, is that t-SNE is often said to retain local structure in the low-dimensional representation, but doesn't usually retain global structure. Practically, this means that we can interpret cases that are close to each other in the final representation as being similar to each other, but we can't easily say which clusters of cases were more similar to other clusters of cases, in the original data.

![](img/a22105d68c35e8d5bd3c7bafb4644881_347_0.png)

Figure 14.4 Cases are randomly initialized over the new axes (one axis is shown here). The probability matrix is computed for this axis, and the cases are shuffled around to make this matrix resemble the original, high-dimensional matrix by minimizing the Kullback-Leibler (KL) divergence. During shuffling, cases are attracted toward cases that are similar to them (lines with circles), and repulsed away from cases that are dissimilar (lines with triangles).

Figure 14.5 The effect of changing theta (row facets) and perplexity (column facets) using the default values of eta and max_iter, on the final t-SNE embedding of the swissTib dataset.

Figure 14.6 shows the final embeddings with different combinations of max_iter (rows) and eta (columns). The effect here is a little more subtle, but smaller values of eta need a larger number of iterations in order to converge (because the cases move in smaller steps at each iteration). For example, for an eta of 100, 1000 iterations is sufficient to separate the clusters, but with an eta of 1, the clusters remain poorly resolved after 1000 iterations. If you would like to see the code I used to generate these figures, have a look at the code for this chapter, available at www.manning.com/downloads/1971).

- **perplexity**, which controls the width of the distributions used to convert distances into probabilities. High values place more focus on global structure, whereas small values place more focus on local structure. Typical values lie in the range 5 to 50. The default value is 30

- **theta**, which controls the trade-off between speed and accuracy. As t-SNE is slow, people commonly use an implementation called Barnes-Hut t-SNE, which allows us to perform the embedding much faster, but with some loss of accuracy. The theta hyperparameter controls this trade-off with 0 being "exact" t-SNE, and 1 being the fastest, but least accurate t-SNE. The default value is 0.5

- **eta**, which is how far each data point moves at each iteration (also called the learning rate). Lower values need more iterations to reach convergence, but may result in a more accurate embedding. The default value is 200 and this is usually fine

- **max_iter**, which is the maximum iterations allowed before computation stops. This will depend on your computational budget, but its important to have enough iterations to reach convergence. The default value is 1000

> **TIP** The most important hyperparameters to tune are usually perplexity and max_iter.
