# # Chapter 5

# # Neural Networks

# ## 5.1 Neural Networks

Neural networks are a class of compositional function approximators. Unlike other function approximators we have seen (e.g. polynomials), they are nonlinear in their parameters.
(Aside) In information processing we have several perspectives:

+   - Procedural perspective – thinking in terms of an imperative programming language
- Functional perspective – mathematical equations and reasoning
- Circuit/graph perspective – information is processed as it flows through the system

We will consider neural nets from the circuit/graph perspective.
Consider the circuits below:

![](bbox=[0.283, 0.611, 0.715, 0.786])

These circuits represent matrix multiplications, with the weights on the edges being the entries of the matrix. Assuming that the flow of information is from left to right, the circuit on the left is multiplication by a $3 	imes 4$ matrix, and the circuit on the right is multiplication by a $2 	imes 4$ matrix followed by multiplication by a $3 	imes 2$ matrix.

Are these circuits equally expressive? Certainly not, as the one on the left has rank at most 2, while the one on the right may have rank 3. However, the one on the left has more layers