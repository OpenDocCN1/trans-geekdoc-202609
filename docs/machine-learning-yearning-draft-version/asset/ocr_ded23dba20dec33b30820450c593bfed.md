# 44 The Optimization Verification test

Suppose you are building a speech recognition system. Your system works by inputting an audio clip A, and computing some Score_A(S) for each possible output sentence S. For example, you might try to estimate Score_A(S) = P(S|A), the probability that the correct output transcription is the sentence S, given that the input audio was A.

Given a way to compute Score_A(S), you still have to find the English sentence S that maximizes it:

Output = arg max_S Score_A(S)

How do you compute the “arg max” above? If the English language has 50,000 words, then there are (50,000)^N possible sentences of length N—far too many to exhaustively enumerate. So, you need to apply an approximate search algorithm, to try to find the value of S that optimizes (maximizes) Score_A(S). One example search algorithm is “beam search,” which keeps only K top candidates during the search process. (For the purposes of this chapter, you don’t need to understand the details of beam search.) Algorithms like this are not guaranteed to find the value of S that maximizes Score_A(S).

Suppose that an audio clip A records someone saying “I love machine learning.” But instead of outputting the correct transcription, your system outputs the incorrect “I love robots.” There are now two possibilities for what went wrong:

+   1. **Search algorithm problem.** The approximate search algorithm (beam search) failed to find the value of S that maximizes Score_A(S).
+   
+   2. **Objective (scoring function) problem.** Our estimates for Score_A(S) = P(S|A) were inaccurate. In particular, our choice of Score_A(S) failed to recognize that “I love machine learning” is the correct transcription.

Depending on which of these was the cause of the failure, you should prioritize your efforts very differently. If #1 was the problem, you should work on improving the search algorithm. If #2 was the problem, you should work on the learning algorithm that estimates Score_A(S).

Facing this situation, some researchers will randomly decide to work on the search algorithm; others will randomly work on a better way to learn values for Score_A(S). But unless you know which of these is the underlying cause of the error, your efforts could be wasted. How can you decide more systematically what to work on?