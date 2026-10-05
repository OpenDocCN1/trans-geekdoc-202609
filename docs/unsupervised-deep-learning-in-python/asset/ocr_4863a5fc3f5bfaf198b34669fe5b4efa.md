```
d(-log(sum[h]) { P(v,h) } / dw
d=(-log(sum[h]) { exp(-E(v,h)) } / Z )
d=sum[h]{ P(h | v)E(v,h) -sum[v,h]{ P(v,h)E(v,h) }
=Eh|v{ E(v,h) - Ev,h{ E(v,h) }
```

This is read as “the expected value of E(v,h) over the conditional distribution P(h | v)” - “the expected value of E(v,h) over the joint distributoon P(v, h)”.

Since we end up with is the difference between 2 expectations. The first expectation is easy but the second expectation is hard because it requires an infinite number of Gibbs samples. We usually call the first term the clamped term and the second term unclamped term.

Let’s take the previous expression and expand it. Let’s do the input to hidden weights explicitly.

```
J = sum[h]{ P(h | v)E(v,h) -sum[v,h]{ P(v,h)E(v,h) }
dJ/dW(i, j) = -sum[h]{ P(h | v) h(j|i) } +sum[v]{ P(v,h)P(h | v)h(j|i) }
dJ/dW(i, j) = -prob(i|j=1 | v(i))+sum[v]{ P(v)p(h|j=1 | v(i) }
dJ/dW(i, j) = -sigmoid(c(j) + vW*(;j))v(i)+sum[v]{ P(v)sigmoid(c(j) + vW*(;j))v(i) }
```

We can denormalize the biases and use these 3 update equations:

```
dJ/dW(i, j) = -sigmoid(c(j) + vW*(;j))v(i)+sum[v]{ P(v)sigmoid(c(j) + vW*(;j))v(i) }
dJ/b(i) = v(i)-sum[v]{ P(v)v(i) }
dJ/dc(j) = sigmoid(c(j) + vW*(;j))-sum[v]{ P(v)sigmoid(c(j) + vW*(;j)) }
```

Now you see what we mean by the clamped term and unclamped term. We are going to get the first term simply by direct calculation, but we are going to get the second term - which requires a sum over all v - which is infeasible - by sampling.

Note that if we were to code the RBM using numpy, we would use the actual gradient expressions directly as I previously defined them, but since Theano automatically finds gradients we don’t have to.