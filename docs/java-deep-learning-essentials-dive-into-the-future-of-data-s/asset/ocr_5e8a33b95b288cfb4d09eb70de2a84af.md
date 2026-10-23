The equation to update the model parameters is as follows:

```
w.addi(x.transpose().mul(t).mul(learningRate));
```

Here, again, you can implement the code like you write a math equation. The equation is represented as follows:

$w^{(k+1)} = w^{(k)} + \eta x_n t_n$

The last time we implemented this part, we wrote it with a for loop:

```
for (int i = 0; i < nIn; i++) {
    w[i] += learningRate * x[i] * t;
}
```

Furthermore, the prediction after the training is also the standard forward activation, shown as the following equation:

$y(x) = f(w^T x)$

Here:

$f(a) = \begin{cases} +1, & a \ge 0 \\ -1, & a < 0 \end{cases}$

We can simply define the predict method with just a single line inside, as follows:

```
public int predict(INDArray x) {
    return step(x.mmul(w).getDouble(0));
}
```

When you run the program, you can see its precision and accuracy, and the recall is the same as we get with the previous code.

Thus, it'll greatly help that you implement the algorithms analogous to mathematical equations. We only implement perceptrons here, but please try other algorithms by yourself.