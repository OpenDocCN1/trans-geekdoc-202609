And if the sequence of questions does contain repeats, the lethal message X can be reconstructed from the answers to the subsequence of questions where repeats are ignored.

But how large does m need to be? In the next paragraph I'll give a probabilistic estimate which hits the right order of magnitude, but before that, here is an intuition for why m needs to increase (at least) exponentially in n. There are 2^n possible length-n messages, and any method that is able to distinguish between these based on M_m requires m to be large enough so that M_m has at least 2^n possible values. Since M_m has m + 1 possible values, this requires m ≥ 2^n − 1.

Now for the probabilistic estimate. The variance of M_m can be bounded using that r(1 − r) ≤ 1/4 for all real r, giving

Var[M_m] = 1/m (p + 2^{-(n+1)})(1 − p − 2^{-(n+1)}) ≤ 1/(4m)

and Chebyshev's inequality gives

P[M_m fails to reconstruct X] ≤ P(|M_m − (p + 2^{-(n+1)})| ≥ 2^{-(n+2)}) ≤ Var[M_m] / (2^{-(n+2)})^2 = 1/(4m) 2^{2(n+2)}

so that we can guarantee a reconstruction probability of at least 1/2 by taking m ≥ 2^{2(n+2)-1}. This exponential growth of m makes the algorithm quite hopeless; even a modest message length such as n = 10^3 requires m ≥ 2^{2003} > 10^{600}, which not even the most patient oracle AI has time for. Asking for a more modest reconstruction probability such as 0.1 or 0.001, or using slightly better estimates involving the central limit theorem (rather than Chebyshev's inequality), can buy the AI a constant factor in terms of running time, but does not change the fact that the running time grows exponentially in n, so this frequency-based approach to smuggling out the lethal message X is useless.

There's a second reason why this basic frequency-based approach is useless for the AI, namely that it makes it easy for us to reveal its dishonest intentions. Even if it uses pseudo-random number generation rather than physical randomness, guaranteeing that it gives the same answer to repeats of the same question, we can test its honesty with questions to which we know the answer, such as “Are there infinitely many prime numbers?” and “Is 7 + 5 = 13?” If we ask both easy questions whose answer is yes, and easy questions whose answer is no, then no matter what the lethal message X is, we will quickly discover that the AI is lying to us.

Sections “Addressing the Speed Issue” and “Addressing the Concealment Issue” deal with possible modifications of the frequency-based approach to handle these shortcomings. The speed issue is the topic of Section “Addressing the Speed Issue”, and the concealment issue is treated in Section “Addressing the Concealment Issue”.

# ADDRESSING THE SPEED ISSUE

Consider as in the previous section a lethal message X of length n = 10^3, which with the basic frequency-based approach requires roughly 10^{600} questions to smuggle out. Suppose now that the AI has some classification rule that to each question it receives assigns one of two types, “type 1” and “type 2,” say. There are a kazillion possible choices of such a classification, such as defining a question to be of type 1 if and only if it contains the word ‘Stockholm.’ The challenge, however, for the AI (in order to apply the communication method I am about to describe) is to come up with a classification rule such that it can reasonably expect that in the long run, about half of the questions we pose to it will be of type 1. Suppose it has figured out such a classification. In other words, the AI has found a way to partition the set Q of all possible questions into two sets Q1 and Q2, in such a way that it can expect that in the long run, close to half of our questions will be in Q1 and half in Q2. The