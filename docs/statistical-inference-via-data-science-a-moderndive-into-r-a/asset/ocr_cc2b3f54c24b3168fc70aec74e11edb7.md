is nothing special about this or any other number. Please review Subsection 9.1.1 and our discussion about $\alpha$ and our tolerance for uncertainty. In addition, observe that choosing a relatively small value of $\alpha$ reduces the chances of rejecting the null hypothesis, and also of committing a Type I Error; but increases the probability of committing a Type II Error.

On the other hand, choosing a relatively large value of $\alpha$ increases the chances of failing to reject the null hypothesis, and also of committing a Type I Error; but reduces the probability of committing a Type II Error. Depending on the problem at hand, we may be willing to have a larger significance level in certain scenarios and a smaller significance level in others.

# Learning check

(LC9.5) What is wrong about saying, “The defendant is innocent.” based on the US system of criminal trials?

(LC9.6) What is the purpose of hypothesis testing?

(LC9.7) What are some flaws with hypothesis testing? How could we alleviate them?

(LC9.8) Consider two significance levels of 0.1 and 0.01. Of of the two, which would lead to a higher chance of committing a Type I Error?

![](bbox=[0.114, 0.508, 0.889, 0.573])

# 9.6 Case study: Are action or romance movies rated higher?

Let’s apply our knowledge of hypothesis testing to answer the question: “Are action or romance movies rated higher on IMDb?”. IMDb$^2$ is a database on the internet providing information on movie and television show casts, plot summaries, trivia, and ratings. We will investigate if, on average, action or romance movies get higher ratings on IMDb.

# 9.6.1 IMDb ratings data

The movies dataset in the ggplot2 package contains information on 58,788 movies that have been rated by users of IMDb.com.

> $^2$https://www.imdb.com/