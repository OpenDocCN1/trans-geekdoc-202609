# Chapter 23

# The last chapter

# 23.1 List decoding

Block codes of minimum distance d can correct e errors per block, where e is the largest number such that 2e < d. This is the classical philosophy which we observed in Section 1.3. In Section 13.3 we finally encountered a usable decoder. It is based on the Euclidean algorithm.

It is natural to ask what happens if more than e errors occur. Shall we abandon all hope then? Anyway, decoding will be done automatically. We should make sure the decoder does its best to generate good quality, no matter what happens in the channel. The best we can hope for is that, upon reception of an n-tuple y, the decoder produces the list of all codewords in a ball of some radius e′ around y. Here e′ should be chosen such that this list of codewords is not empty and in most of the cases consists of exactly one codeword. This is then the decoder's best guess. Important progress has been made fairly recently in the list decoding of Reed-Solomon codes. These methods can be extended to cover other classes of codes, including AG codes. In the present section we concentrate on Reed-Solomon codes. The exposition follows the 1999 paper [102] by Guruswami and Sudan. As we shall see, this is a nice application of some classical algebra.

The definition of the Reed-Solomon codes as evaluations of polynomials (see Chapter 4) shows that list decoding of these codes and their projections (truncations) can be formulated as follows:

The input consists of a field F = 𝔽_q, a length n ≤ q, pairs (x_i, y_i) for i = 1, …, n (where x_i, y_i ∈ F and the x_i are pairwise different), a maximum degree k and a radius n − t. The output we wish to produce is the list of all polynomials f(X) ∈ F[X] of degree ≤ k satisfying f(x_i) = y_i for at least t of the indices i. In other words, we use a truncation of the Reed-Solomon code RS(k + 1, q), the (x_i, y_i) describe a received word and we want to produce the list of all codewords at distance ≤ n − t from the received word. The main point is to find a fast algorithm.

The first idea is to work with polynomials in two variables. Here we view Q(X, Y) as a polynomial with just one variable Y whose coefficients are in the field of rational functions (polynomials divided by polynomials) over F. We encountered this field F(X) in the preceding chapter and called it the