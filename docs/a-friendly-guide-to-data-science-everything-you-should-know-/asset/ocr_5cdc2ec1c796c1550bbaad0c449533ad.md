a few other approaches that can also be useful (semi-supervised), ensemble, and reinforcement). Then we'll dive into several supervised techniques, followed by unsupervised techniques, before moving on to some discussions of model explainers and machine learning coding and implementation. We'll finish the chapter by looking at some of the challenges data scientists face when carrying machine learning, including the curse of dimensionality, data leakage, overfitting and underfitting, and the bias-variance tradeoff.

# # Examples of Machine Learning in the Real World

We know machine learning has been out in the wild for a while now, but our first example, the Netflix Prize, brought machine learning more into the mainstream conscience than anything had before, probably because of the $1 million award that was on the line. The second example is one used in the medical field where results have been making meaningful improvements in patients' lives.

# # Example 1: The Netflix Prize

In 2006, Netflix offered a prize open to anyone not associated with Netflix (with a few other exclusions) who could beat their in-house system that predicted user ratings by a certain amount (used the performance metric root mean squared error, which we'll talk about in the next chapter). This would help them improve the recommendations they gave to users. If the system predicted a high rating for a movie by a particular user, it would make sense to recommend movie to them if they hadn't watched it yet. And they'd want to avoid recommending movies that the user was predicted to give low ratings to.