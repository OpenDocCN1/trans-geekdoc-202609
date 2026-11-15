Moreover, as recurrent neural networks maintain an internal state which gets updated according to new information, we can view RNNs as a description of a program. In fact, a paper by Siegelman in 1995 shows that recurrent neural networks are Turing complete, they can simulate arbitrary programs.

# But what is a recurrent neural network, really?

How does the network keep track of the previous states? To put it in the context of text generation, think of our training data as a list of character sequences (tokenized words). For each word, from the first character, we will predict the following:

Formally, let's denote a sequence of \(t+1\) characters as \(x = [x_0, x_1, x_2 \dots , x_t]\). Let \(s_1 = 0\).

For \(k=0,2\dots t\), we construct the following sequence:

```
\(s_k = \tanh(U x_k + W s_{k-1})\)
\(o_k = \text{softmax}(V s_k)\)
```

This is summarized in the following diagram, when input \(x\) is received, the internal state, \(s\), of the network is modified, and then used to generate an output, \(o\):

![](bbox=[0.24, 0.52, 0.76, 0.7])

Figure 1: Information flow for an RNN. The representations are equivalent; the unfolded representation hints at how backpropagation could work in this setup.

The hidden state, \(s\), need not be one-dimensional, as you might have imagined. Of course, it should not be too big, otherwise you might experience overfitting. A good way to start is to choose a hidden layer one order of magnitude smaller than the input space, so that if your input vector has lives in a thousand-dimensional space (not uncommon in text problems), then your hidden state should be in the hundreds.