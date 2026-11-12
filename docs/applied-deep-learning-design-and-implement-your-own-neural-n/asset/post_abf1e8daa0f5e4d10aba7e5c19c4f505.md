
## Cell update unit

```
c_t = \gamma_u \odot \tilde{c}_t + (1 - \gamma_u) \odot c_{t-1} (7.5)
```

If \(\gamma_u = 1\), then it signifies that update the cell content by \(c_t\), else remains the same and if \(\gamma_u = 0\), then \(c_t = c_{t-1}\).

## Full gated recurrent unit

In addition to simple GRU, full GRU includes one more gate as a relevance gate. It is used to show the relevance of each bit in the cell state. It is another neural network that is parameterized by \((W_r, b_r)\), where \(W_r\) is weight and \(b_r\) is corresponding bias with input as \((c_{t-1}, x_t)\). It is represented by \(\gamma_r\). It includes the following equations:

```
\tilde{c}_t = tanh[(W_c (\gamma_r \odot c_{t-1}, x_t) + b_c] (7.6)

\gamma_u = \sigma[(W_u (c_{t-1}, x_t) + b_u] (7.7)

Relevance Gate: \gamma_r = \sigma[(W_r (c_{t-1}, x_t) + b_r] (7.8)

c_t = \gamma_u \odot \tilde{c}_t + (1 - \gamma_u) \odot c_{t-1} (7.9)
```

## GRU to LSTM transition

In the case of LSTM, there is no relevance gate [equation (7.10)], and in LSTM, there are two new gates as forget gate (\(\gamma_f\)) and Output gate (\(\gamma_o\)). The following potential cell update unit (\(\widetilde{c}_t\)) and cell update gate (\(c_t\)) of GRU is updated as follows:

```
\tilde{c}_t = tanh[(W_c (h_{t-1}, x_t) + b_c] (7.10)
```

```
c_t = \gamma_u \odot \tilde{c}_t + (1 - \gamma_u) \odot c_{t-1} (7.11)
```

In this equation, \(\gamma_u \odot \tilde{c}_t\) represents what to update and \((1 - \gamma_u) \odot c_{t-1}\) represents what not to update. So in the case of LSTM, this equation (7.11) is modified as shown in equation (7.12):

```
c_t = \gamma_u \odot \tilde{c}_t + \gamma_f \odot c_{t-1} (7.12)
```

In the case of GRU, \(h_t = c_t\) (refer to Chapter 6: Sequence Modeling in Neural Networks and Recurrent Neural Networks (RNN) section 6.8.2 for \(h_t\), it is a (100 x 1 dimensional history update vector)), but in the case of LSTM \(h_t \neq c_t\), the forget gate is parameterized using \((W_f, b_f)\), where \(W_f\) is weight and \(b_f\) is corresponding bias with input as \((h_{t-1}, x_t)\). The equation for forget gate is represented in equation (7.13). LSTM will learn the forget gate separately.

\(\gamma_f = \sigma[(W_f (h_{t-1}, x_t) + b_f]\) (7.13)
\(\gamma_u = \sigma[(W_u (h_{t-1}, x_t) + b_u]\) (7.14)

The output gate is parameterized using \((W_o, b_o)\), where \(W_o\) is weight and \(b_o\) is corresponding bias with input as \((h_{t-1}, x_t)\).

\(\gamma_o = \sigma[(W_o (h_{t-1}, x_t) + b_o]\) (7.15)

In the case of GRU, the final output is equal to the cell update; that is, \(h_t = c_t\) but in the case of LSTM output gate is used to generate the final output, as shown in equation (7.16):

\(h_t = \gamma_o \odot \tanh c_t\) (7.16)

The LSTM gated unit described previously is pictured in figure 7.1:

![](img/7e519fee1b702b91799cdf1664598392_504_0.png)

Figure 7.1: LSTM Gated unit

Why are we moving from hidden layer nodes to Gated units? What is the advantage of using Gated units here in LSTMs?

Suppose for a sequence prediction example, we want to predict the sequence, say after the 500th timestamp in place of the 5th or 10th timestamp, the hidden layer nodes used in RNN forget all the information by then, but the gated units used in LSTM remembers it for long. For this, first, we should understand how the hidden layer nodes behave. The hidden layer nodes which we have used in RNN are the traditional ANN nodes, and the nodes of ANN have two working functionalities.

- Summation
- Activation

![](img/7e519fee1b702b91799cdf1664598392_505_0.png)

Figure 7.2: Moving from RNN to LSTM

Let us consider that some information is coming from various sources, and the ANN node first adds up all these values coming from different sources and finally passes to the activation part.

Let us take an example to understand this better. From figure 7.2, take the RNN part. Now, let us say from branch h(t - 1) to h(t), the weight is w(t - 1).

And from branch I(t) to h(t), the weight is w(t), then the value at hidden node h(t) can be given as the summation of the product of the weight along with the previous state information as shown in the following equation:

```
h(t) = h(t - 1) x w(t - 1) + x(t) x w(t)
```

Now, this summation part is passed through the activation part, which can be written as follows:

```
Out(h(t)) = σ(h(t - 1) x w(t - 1) + x(t) x w(t))
```

Or we can write it as follows:

```
Out(h(t)) = 1 / e^-(h(t-1) x w(t-1) + x(t) x w(t))
```

Now, this output is being fed into the next neural network node, that is, h(t + 1), this is the behavior of a traditional ANN node being used in RNN.

So, now let us look at the gated unit of LSTM, which is used in place of RNN's hidden node. The Gated unit of LSTM is shown in figure 7.1. It has three gates, input gate (i), forget gate (f), and output gate (o). The sigmoid function is used to adjust the output between 0 and 1. The 0 value in forget gate disregards the old memory and resting the input gate to 0 disregards or ignores the newly computed state.

In figure 7.1, c(t) is a memory or cell update unit and it is used to store meaningful information. It is also known as the cell-state and is shown in figure 7.3. The gates shown in figure 7.1 are described in detail from section Forget gate to section Output gate.

![](img/7e519fee1b702b91799cdf1664598392_507_0.png)

Figure 7.3: Cell state (c(t) or ) of LSTM

The equation for the cell state of LSTM can be given as follows:

```
c_t = \gamma_u \odot \tilde{C_t} + \gamma_f \odot c_{t-1}
```

Or

```
c(t) = i(t) \otimes c'(t) + f(t) \otimes c(t-1)
```

Which can be easily observed from figures 7.1 and 7.3. Now, to understand the working of the LSTM gated unit, let us first discuss all the gates used in the gated unit of LSTM.

## Forget gate

It is the first gate of the LSTM cell, and it decides which data or information to keep and what information to forget. Forget gate is also called a remember vector. It takes input from two different sources as follows:

- The output from the previously hidden layer node, that is, h(t − 1).
- Finally, current input, that is, x(t).
- And multiply it with the previous memory state value c(t-1).

Forget gate is shown in figure 7.4:

![](img/7e519fee1b702b91799cdf1664598392_508_0.png)

Figure 7.4: Forget Gate of LSTM

The equation for the forget gate can be written as follows:

$$\gamma_f = \sigma[(W_f (h_{t-1}, x_t) + b_f]$$

Or

$$f(t) = \sigma[(W(F)[h(t-1), x(t)] + b(t)]$$

Where Wf and bf are weight and bias, respectively. In forget gate’s input and output, we are using the Sigmoid activation function; therefore, it returns values between 0 and 1, where forget gate output values:

- 0—Completely forget what information is present in the memory cell.
- Represents completely, providing all the information present in the memory cell.

## Input modulation gate or potential cell update unit in LSTM

Instead of the sigmoid (σ) activation function, it uses the tanh activation function. It creates a vector of new candidate value. The input modulation gate is shown in figure 7.5:

![](img/7e519fee1b702b91799cdf1664598392_509_0.png)

Figure 7.5: Input or potential cell update modulation gate \(\tilde{c}_t\) or \(c'(t)\) of LSTM

Here, as the input gate uses the sigmoid activation function, it will again give values between 0 and 1.

Now, because the LSTM cell equation performs the summation of previous state cells along with the current input, therefore, using the Sigmoid activation function can only help add more data to the memory and will not remove or forget data from memory. For example, if we have a floating-point number as output between 0 and 1, then the number will never come to 0 as output, and thus, the data will never be forgotten by the memory. Therefore, we use the input modulation gate, which uses tanh activation function that gives the output in the range of -1 and 1, and thus, allowing the cell state the forget or remove the data from memory.

The equation for the input modulation gate is given as follows:

```
\(\tilde{c}_t = tanh[(W_c (h_{t-1}, x_t) + b_c]\)
```

Or

```
\(c'(t) = tanh[(W(c)[h(t - 1), x(t)] + b(c)]\)
```

## Input or update gate

The input gate helps in finding out what type of information and which information should move in the cell state of LSTM. It is also known as save vector. The architecture of the input gate is the same as that of forget gate, as it uses a sigmoid activation function.
