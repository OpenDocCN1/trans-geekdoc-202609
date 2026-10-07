# Curse of Dimensionality: Recall the example, when we were talking about how neural networks actually work where we were building a NN for a Property Evaluation (Recall Section 8.2.1).

So this is what it looked like when we Trained Up Already. Here we know which one are the best weights.

But Before Training we didn't know the optimal weights. The actual NN before training looks like this. We have all these different possible Synapses and we still have to train them (4 x 5 = 20) and output (5) with 25 weights. Input (25 weights)

![](bbox=[0.125, 0.165, 0.875, 0.345])

And let's see how we could possibly brute 25 ways. Now it is a simple neural network we have right now. We have just one Hidden Layer.

But to do this we have to try 10⁷ possible combination. Which is impossible unless we use a super computer 93 peta FLOPS. 1 FLOP = 1 floating point operation per second. Normal computer can get several GFLOPS.

1000 x 1000 x ... x 1000 = 10³⁵ = 10¹⁷ combinations

Sunway TaiLight: World's fastest Super Computer

93 FLOPS

93 x 10¹

10⁷ / (93 x 10¹¹)

= 1.08 x 10⁻⁸ seconds

= 3.42 x 10⁻⁵ years

![](bbox=[0.515, 0.395, 0.875, 0.585])

Now for an NN like it is possible to use a Brute-Force technique.

![](bbox=[0.295, 0.645, 0.705, 0.805])

NOTES:

Brute-Force Search: In computer science, Brute-Force search or Exhaustive search, also known as Generate And Test, is a very general problem-solving technique and algorithmic paradigm that consists of systematically enumerating all possible candidates for the solution and checking whether each candidate satisfies the problem's statement.

Brute-Force Algorithms are exactly what they sound like - methods of solving a problem that rely on sheer computing power and trying every possible rather than advanced techniques to improve efficiency.

For example, imagine you have a small padlock with 4 digits, from 0-9. You forget your combination, but you don't want to buy another padlock. You can remember any of them unless you use a brute-force method to open the lock.