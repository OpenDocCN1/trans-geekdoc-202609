![](bbox=[0.15, 0.09, 0.8, 0.42])

FIGURE 5.8: A typical binary classification problem .

+   1 . Given the sigmoid function: $g(x) = \frac{1}{1 + e^{-x}}$ what is the expression for the hypothesis in logistic regression?

+   2 . What is the decision boundary?

+   3 . What does h_Θ (x) = 0.8 mean?

+   4 . Using an Autograd based Python program, implement both the forward and backward pass for the sigmoid activation function and evaluate it's derivative at x = 1

+   5 . Using an Autograd based Python program, implement both the forward and backward pass for the ReLU activation function and evaluate it's derivative at x = 1

PRB-124 CH.PR B- 5.25. Your friend, a veteran of the DL community wants to implement a custom activation function using Autograd and asks for your help. Consider a function accepting two tensors as input and an output obeying the following mapping:

```
```python
(u, v) ↦ |uv|²
```
```