presentation of backpropagation a little more algebraically complicated. So we'll stick with $\delta^l_j = \frac{\partial C}{\partial z^l_j}$ as our measure of error*.

* In classification problems like MNIST the term "error" is sometimes used to mean the classification failure rate. E.g., if the neural net correctly classifies 96.0 percent of the digits, then the error is 4.0 percent. Obviously, this has quite a different meaning from our $\delta$ vectors. In practice, you shouldn't have trouble telling which meaning is intended in any given usage.

**Plan of attack:** Backpropagation is based around four fundamental equations. Together, those equations give us a way of computing both the error $\delta^l$ and the gradient of the cost function. I state the four equations below. Be warned, though: you shouldn't expect to instantaneously assimilate the equations. Such an expectation will lead to disappointment. In fact, the backpropagation equations are so rich that understanding them well requires considerable time and patience as you gradually delve deeper into the equations. The good news is that such patience is repaid many times over. And so the discussion in this section is merely a beginning, helping you on the way to a thorough understanding of the equations.

Here's a preview of the ways we'll delve more deeply into the equations later in the chapter: I'll give a short proof of the equations, which helps explain why they are true; we'll restate the equations in algorithmic form as pseudocode, and see how the pseudocode can be implemented as real, running Python code; and, in the final section of the chapter, we'll develop an intuitive picture of what the backpropagation equations mean, and how someone might discover them from scratch. Along the way we'll return repeatedly to the four fundamental equations, and as you deepen your understanding those equations will come to seem comfortable and, perhaps, even beautiful and natural.

# An equation for the error in the output layer, $\delta^l$ :

The components of $\delta^l$ are given by

```
$\delta^l_j = \frac{\partial C}{\partial a^l_j} \sigma'(z^l_j)$. (BP1)
```

This is a very natural expression. The first term on the right, $\partial C/\partial a^l_j$, just measures how fast the cost is changing as a function of the $j^{th}$ output activation. If, for example, $C$ doesn't depend much on a particular output neuron, $j$, then $\delta^l_j$ will be small, which is what we'd expect. The second term on the right, $\sigma'(z^l_j)$, measures how fast the activation function $\sigma$ is changing at $z^l_j$.