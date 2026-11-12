

$$
\frac{\partial S_4}{\partial W} = \frac{\partial S_4}{\partial S_4} \frac{\partial^* S_4}{\partial W} + \frac{\partial S_4}{\partial S_3} \frac{\partial^* S_3}{\partial W} + \frac{\partial S_4}{\partial S_2} \frac{\partial^* S_2}{\partial W} + \frac{\partial S_4}{\partial S_1} \frac{\partial^* S_1}{\partial W}
$$

We got the preceding equation by short-circuiting some of the parts of the equation as follows:

$$
\frac{\partial S_4}{\partial S_3} \frac{\partial S_3}{\partial S_2} \frac{\partial^* S_2}{\partial W} : - \frac{\partial S_4}{\partial S_2} \frac{\partial^* S_2}{\partial W}
$$

And

$$
\frac{\partial S_4}{\partial S_3} \frac{\partial S_3}{\partial S_2} \frac{\partial S_2}{\partial S_1} \left( \frac{\partial^* S_1}{\partial W} \right) : - \frac{\partial S_4}{\partial S_1} \frac{\partial^* S_1}{\partial W}
$$

And the preceding equation can be written as follows:

$$
\frac{\partial S_4}{\partial W} = \frac{\partial S_4}{\partial S_4} \frac{\partial^* S_4}{\partial W} + \frac{\partial S_4}{\partial S_3} \frac{\partial^* S_3}{\partial W} + \frac{\partial S_4}{\partial S_2} \frac{\partial^* S_2}{\partial W} + \frac{\partial S_4}{\partial S_1} \frac{\partial^* S_1}{\partial W} = \sum_{N=1}^{4} \frac{\partial S_4}{\partial S_N} \frac{\partial^* S_N}{\partial W}
$$

So, finally, we can write as a derivative of the loss function as follows:

$$
\frac{\partial L_4(\theta)}{\partial W} = \frac{\partial L_4(\theta)}{\partial S_4} \frac{\partial S_4}{\partial W} \tag{6.15}
$$

Now, we know that

$$
\frac{\partial S_4}{\partial W} = \sum_{N=1}^{4} \frac{\partial S_4}{\partial S_N} \frac{\partial^* S_N}{\partial W}
$$

Putting the preceding equation in \(\frac{\partial L_4(\theta)}{\partial W} = \frac{\partial L_4(\theta)}{\partial S_4} \frac{\partial S_4}{\partial W}\), we get the following:

$$
\frac{\partial L_4(\theta)}{\partial W} = \frac{\partial L_4(\theta)}{\partial S_4} \sum_{N=1}^{4} \frac{\partial S_4}{\partial S_N} \frac{\partial^* S_N}{\partial W}
$$

Now, here N=4 is for our use case of predicting the alphabet; generally, for N = t, we can write as follows:

$$
\frac{\partial L_t(\theta)}{\partial W} = \frac{\partial L_t(\theta)}{\partial S_t} \sum_{N=1}^{t} \frac{\partial S_t}{\partial S_N} \frac{\partial^* S_N}{\partial W} \tag{6.16}
$$

The preceding equation defines the back-propagation concerning time clearly. So, we have done the derivation concerning V and W, and similarly, we can calculate the derivative for U as well.

Now, let us discuss the issues here with the backpropagation, as can be seen in figure 6.78:

![](img/7e519fee1b702b91799cdf1664598392_484_0.png)

Figure 6.78: Problems with back-propagation in RNN

### Vanishing gradient and exploding gradient problems in RNN

So, in vanishing gradient, what happens is when we get the predicted output from the model, we calculate the error by subtracting the predicted output from the actual output as follows:

$e = \text{Actual Output} - \text{Predicted Output}$

So, we calculate the error using the preceding equation. Now, after that, we calculate the change in error concerning the change in weight or concerning any other variable by using the following equation:

\(\Delta w = n.\frac{\partial e}{\partial w}\)

Where w is the weight of the parameter and n is the learning rate here. Then, we must add the change in weight to the old weight to get a new weight as follows:

$w = w + \Delta w$

Now, what can happen here? Can you tell? Here, if the value of \(\frac{\partial e}{\partial w}\) becomes very smaller than 1, that is, 0.00002 as follows:

$$
\frac{\partial e}{\partial w} \ll 1
$$

So, now, if we multiply the learning rate with this term, where again the learning rate is smaller than 1, then we will get a change of weight that is almost negligible.

So, let us take an example:

> "I went to Delhi..............'"

> "Few of them speak................."

Now, we need to predict what comes after speaks. So, for that, we need to go back in time and check what the context was actually, which becomes very complex.

And due to that, we have to perform a lot of iterations, and hence, this change in error will become very small or almost negligible. So, the new weight which will be getting here is almost the same in this case. For a proper understanding of this, look at figure 6.79:

![](img/7e519fee1b702b91799cdf1664598392_485_0.png)

Figure 6.79: Vanishing gradient problem

Similarly, when we talk about the exploding gradient problem. It is just the opposite of the vanishing gradient problem. Here, if the value of $\frac{\partial e}{\partial w}$ becomes very large than 1, that is,

$\frac{\partial e}{\partial w} \gg 1$

And when we have some long-term dependencies, so in that case $\frac{\partial e}{\partial w}$ will be increasing fast and the value of $\frac{\partial e}{\partial w}$ will become very large, and because of that, the new weight will vary from the old weight significantly, as shown in figure 6.80:

![](img/7e519fee1b702b91799cdf1664598392_486_0.png)

Figure 6.80: Exploding gradient problem

Now, let us discuss these problems concerning our use case example here mathematically. As we know that

$\frac{\partial L_t(\theta)}{\partial W} = \frac{\partial L_t(\theta)}{\partial S_t} \sum_{N=1}^{t} \frac{\partial S_t}{\partial S_N} \frac{\partial^* S_N}{\partial W}$

So now, from the preceding equation, we will take the term $\frac{\partial S_t}{\partial S_N}$ and concerning this term, discuss the problems of vanishing gradient and exploding gradient here.

Now, let us expand the term $\frac{\partial S_t}{\partial S_N}$ again shown as follows:

$$
\frac{\partial S_t}{\partial S_N} = \frac{\partial S_t}{\partial S(t-1)} \frac{\partial S(t-1)}{\partial S(t-2)} \cdots \cdots \frac{\partial S(N+1)}{\partial S_N}
$$

So, we can again write the preceding equation as follows:

$$
\prod_{i=N}^{t-1} \frac{\partial S(i+1)}{\partial S_i}
$$

Now, let us take one of the terms of the preceding equation shown as follows:

$$
\frac{\partial S(i+1)}{\partial S_i}
$$

Or we can also write as follows:

$$
\frac{\partial S_i}{\partial S(i-1)}
$$

Now, we know that \(a_i\) is a pre-activation function given as follows:

$$
a_i = WS(i-1) + b
$$

And is the representation after applying the non-linearity activation function, which can be given as follows:

$$
S_i = \sigma(a_i)
$$

Now, using the chain rule of differentiation we can write \(\frac{\partial S_i}{\partial S(i-1)}\) as follows:

$$
\frac{\partial S_i}{\partial S(i-1)} = \frac{\partial S_i}{\partial (a_i)} \frac{\partial (a_i)}{\partial S(i-1)} \tag{6.17}
$$

Now, let us expand \(a_i\) and \(S_i\) we get the following:

$$
a_i = [a_{i1}, a_{i2}, a_{i3}, \dots, a_{id}]
$$

$$
S_i = [\sigma(a_{i1}), \sigma(a_{i2}), \sigma(a_{i3}), \dots, \sigma(a_{id})]
$$

Where \(a_i\) is a d-dimension vector and S is the non-linear activation applied to the \(a_i\).

Now, as we are interested in finding

$$
\frac{\partial S_i}{\partial S(i-1)} = \frac{\partial S_i}{\partial (a_i)} \frac{\partial (a_i)}{\partial S(i-1)}
$$

So, \(\frac{\partial S_i}{\partial(a_i)}\) can be given as follows:

$$
\frac{\partial S_i}{\partial(a_i)} = \left[ \begin{matrix} \frac{\partial S_{i1}}{\partial a_{i1}} & \frac{\partial S_{i2}}{\partial a_{i1}} & \frac{\partial S_{i3}}{\partial a_{i1}} & \cdots \\ \frac{\partial S_{i1}}{\partial a_{i2}} & \frac{\partial S_{i2}}{\partial a_{i2}} & \frac{\partial S_{i3}}{\partial a_{i2}} & \cdots \\ \cdots & \cdots & \cdots & \\ \cdots & \cdots & \cdots & \frac{\partial S_{id}}{\partial a_{id}} \end{matrix} \right]
$$

The preceding matrix can be written as follows:

$$
\frac{\partial S_i}{\partial(a_i)} = \left[ \begin{matrix} \sigma'(a_{i1}) & 0 & 0 & 0 \\ 0 & \sigma'(a_{i2}) & 0 & 0 \\ 0 & 0 & \cdots & \cdots \\ 0 & 0 & \cdots & \sigma'(a_{id}) \end{matrix} \right]
$$

The preceding matrix can also be written as follows:

$$
\frac{\partial S_i}{\partial(a_i)} = diagonal(\sigma'(a_i))
$$

And

$$
\frac{\partial(a_i)}{\partial S(i - 1)} = W
$$

Therefore, we can write

$$
\frac{\partial S_i}{\partial S(i - 1)} = diagonal \left( \sigma'(a_i) \right) . W
$$

So, the magnitude of the preceding equation can be written as follows:

$$
\left\| \frac{\partial S_i}{\partial S(i - 1)} \right\| = \left\| diagonal \left( \sigma'(a_i) \right) . W \right\|
$$

Now, we know that if ||z|| = ||xy|| then, we can write as ||z|| <= ||x||. ||y||

Therefore, we can write

$$
\left\| \frac{\partial S_i}{\partial S(i - 1)} \right\| \leq \left\| diagonal \left( \sigma'(a_i) \right) \right\| . \|W\|
$$

Now, we know that as we are using the logistic activation function, therefore we can say that \(\sigma(a_i)\) is a bounded function, and hence, \(\sigma'(a_i)\) is also bounded here.

