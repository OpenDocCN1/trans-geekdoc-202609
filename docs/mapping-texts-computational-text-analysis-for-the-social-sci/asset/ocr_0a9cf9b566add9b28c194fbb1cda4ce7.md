# Dispersion

Another way to summarize our vector is to measure how spread out or dispersed our numbers are. Measures of dispersion include the **range** and the **variance**. The first is the difference between the smallest and biggest number. The second involves subtracting the mean from our vector, then squaring and summing that vector (that’s right, _dot product_ again) and then dividing by the number of observations.<sup>18</sup>

18 We might also divide by the number of observations _minus one_, which is common when we are working with samples as opposed to a full population.

19 Elmo and Kermit are precisely 24 inches while Big Bird is at 98 inches!

Finally, the **standard deviation** is the square root of the variance. The standard deviation has the benefit of being interpreted in the metric units of the variable: for example, if we measured a sample of Muppets on _Sesame Street_ and find a mean of 24 inches and a standard deviation of 9 inches, then Muppet’s heights in this sample deviate from the mean of 24 inches by, on average, about 9 inches.<sup>19</sup>

# Types of Distributions

Statistics, as used in the social sciences, often begins with the assumption that when we measure something in the world, it will have a _normal_ (or _Gaussian_) distribution.<sup>20</sup> So, let’s start there.

20 Or, that the distribution of means from repeated samples of that “something” will be normal when the sample sizes are sufficiently large. This is known as the **Central Limit Theorem**.

Our list is normally distributed if the numbers are symmetrical above and below the mean. Here, we’ll simulate two vectors with normal distributions, slightly different means, and one with different standard deviations. These distributions are shown in Figure 4.2.

Figure 4.2: Normal (Gaussian) Distributions.

![](bbox=[0.33, 0.59, 0.92, 0.76])

21 We’ll encounter plenty of non-normal distributions in this book.

There are also many non-normal distributions—too many to elaborate here. We should not assume our data follow a normal distribution.<sup>21</sup> When comparing the two vectors, it is not enough to determine if their central tendencies differ, but also their overall dispersions and the form of their distributions.