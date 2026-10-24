
![](img/90c930779c8f928df6ff4481fc59f9a3_563_0.png)

FIGURE 10.32
An example of using two RNN models for machine translation. Note that the first input unit of the second RNN model is a special token <EOS>, which stands for the end of the sentence. This will cause the second RNN to start to produce the first output (“Yo”). The process will continue until the second RNN model outputs a special token <EOS>. Adapted from Charu C. Aggarwal “Neural Networks and Deep Learning.”

However, this means that we will have to use a deep RNN, with many hidden states (one for each preceding word). Similar to deep feed-forward neural networks, it is very challenging to train a deep RNN, due to gradient vanishing or gradient exploding problems. Even worse, the gradient vanishing problem or the gradient exploding problem with deep RNNs could be further exacerbated due to its recurrent nature (i.e., the same activation function Eq. (10.19) is repeatedly applied to different hidden states).

One of the most successful techniques to address the long-term dependence challenge in RNNs is called long short-term memory (LSTM) model. Fig. 10.33 provides a pictorial comparison between a traditional RNN model and an LSTM model. Fig. 10.33(a) is the same as the RNN model without any output unit described in Fig. 10.31(a). To see this, we introduce the vector concatenation operation that connects two vectors and combines them into a single vector. In Fig. 10.33, the vector concatenation is denoted as a black dot, and it connects the input x^t and the previous hidden state h^{t-1}, and combines them into a single vector [x^t, h^{t-1}] whose length is equal to the length of x^t and that of h^{t-1}. A hidden unit in Fig. 10.33(a) feeds the concatenated vector [x^t, h^{t-1}] to the nonlinear activation function (e.g., tanh) to generate the new hidden state h^t, which will be fed into the next hidden unit. Note that this process is equivalent to Eq. (10.19). To see this, let us use tanh as the activation function f() in Eq. (10.19). We introduce a 2 x 2 block matrix W~, whose first diagonal block is the input-to-hidden weight matrix W in Eq. (10.19), and the two off-diagonal blocks are zeros. Then, Eq. (10.19) becomes h^t = tanh(W~[x^t, h^{t-1}] + a), which is the same as the hidden unit described in Fig. 10.33(a). By repeatedly applying the same activation function (i.e., to replace h^{t-1} by the previous input x^{t-1} and its preceding hidden state h^{t-2}, and so on), we can see that the influence of a distant input x^{t-\tau} on the current hidden state h^t will decrease rapidly as the gap \tau increases.

![](img/90c930779c8f928df6ff4481fc59f9a3_564_0.png)

(a) A traditional RNN model

![](img/90c930779c8f928df6ff4481fc59f9a3_564_1.png)

(b) A long short-term memory (LSTM) model

**FIGURE 10.33**

A comparison between a traditional RNN model (a) and an LSTM model (b). Each gray box in (a) is a hidden unit of the RNN model. Each gray box in (b) is an LSTM cell of the LSTM model. The black dot (at the left side of the hidden unit or LSTM cell) denotes vector concatenation operation. For clarity, the output units and the bias vectors are not shown. Adapted from http://colah.github.io/posts/2015-08-Understanding-LSTMs/.

An LSTM model (Fig. 10.31(b)) addresses this issue by replacing the hidden unit in the traditional RNN model by an LSTM cell, which is indicated as a gray box in Fig. 10.31(b). Like the traditional RNN model, an LSTM cell concatenates the input x^t and the previous hidden state h^{t-1} and eventually produces a new hidden state h^t that will be fed into the next LSTM cell. However, unlike the traditional RNN model, an LSTM cell has an additional input called cell state C^t. The cell state is the key of the LSTM model. It is specifically designed to accumulate (or to remember) the information from the past for a long time, and thus it is able to address the long-term dependence challenge.

“How does the LSTM cell do the magic to address the long-term dependence challenge?” Let us take a close look at Fig. 10.34. At a given time stamp t, an LSTM cell takes the previous cell state C^{t-1} as the input (the top left corner), updates it, and feeds the updated cell state C^t to the next time stamp

![](img/90c930779c8f928df6ff4481fc59f9a3_565_0.png)

FIGURE 10.34
An illustration of an LSTM cell. The black dot represents vector concatenation operation. The two tanh layers (the two blue (mid gray in print version) boxes) are used for generating temporary cell state (the middle bottom) and the temporary hidden state (the right middle), respectively. The three gates (the yellow (light gray in print version) parts) are used to control how much information is passed through the corresponding variables, including the forget gate \(f^t\) for the old cell state, the input gate \(i^t\) for the temporary cell state, and the output gate \(o^t\) for the temporary hidden state, respectively. Adapted from http://colah.github.io/posts/2015-08-Understanding-LSTMs/.

(the top right corner). The cell state is designed to fulfill two seemingly competing objectives. First, it needs to accumulate the information from the past for a long time to address the long-term dependence challenge. Meanwhile, we want to update the cell state based on the current information, and in this way, it is able to “forget” the irrelevant information from the past. The LSTM model achieves these design objectives through three gates, namely the forget gate \(f^t\), the input gate \(i^t\) and the output gate \(o^t\) (the yellow (light gray in print version) parts in the figure).

Each gate takes the concatenated vector \([x^t, h^{t-1}]\) as the input of a sigmoid activation function \(\sigma()\). Since the sigmoid activation function produces an output between 0 and 1, by multiplying the output of the sigmoid activation function with the corresponding variable (the yellow (light gray in print version) circles marked with \(\times\)), we can control how much information we want to pass through or remove with respect to the corresponding variable. To be specific, each of the three gates is defined as follows:

\(f^t = \sigma(W_f[x^t, h^{t-1}] + a_f), \quad (10.21)\)
\(i^t = \sigma(W_i[x^t, h^{t-1}] + a_i), \quad (10.22)\)
\(o^t = \sigma(W_o[x^t, h^{t-1}] + a_o), \quad (10.23)\)

where subscripts for the weight matrices and bias vectors are used to differentiate among different gates: \(f\) for the forget gate, \(i\) for the input gate, and \(o\) for the output gate, respectively.

The output of the forget gate \(f^t\) is multiplied with each element of the previous cell state \(C^{t-1}\). In other words, it is used to control how much information of the previous cell state \(C^{t-1}\) will be removed (or “forgotten”): the smaller the \(f^t\), the more information will be forgotten. In order to update the cell state, we first feed the concatenated vector \([x^t, h^{t-1}]\) to an tanh activation function (the blue (mid gray in print version) box in the middle bottom part) to generate a temporary cell state: \(\tilde{C}^t =\)

tanh(W_c[x^t, h^{t-1}] + a_c), where W_c and a_c are the weight matrix and bias vector for the temporary cell state, respectively. The temporary cell state \tilde{C}^t is then multiplied with the input gate i^t, which is further used to update the cell state:

\[ C^t = \underbrace{f^t}_{\text{forget gate}} \cdot \underbrace{C^{t-1}}_{\text{old cell state}} + \underbrace{i^t}_{\text{input gate}} \cdot \underbrace{\tilde{C}^t}_{\text{temporary cell state}} , \quad (10.24) \]

where the forget gate f^t controls how much old information from the previous cell state is removed, and the input gate i^t controls how much new information from the temporary cell state is added. By adjusting the forget gate and input gate, the LSTM cell strikes a balance between accumulating the past information (from C^{t-1}) and updating with the new information (from \tilde{C}^t).

Finally, the updated cell state C^t is used to generate a temporary hidden state \tilde{h}^t = tanh(\tilde{W}C^t + a), which is further multiplied with the output gate o^t to generate the new hidden state h^t

\[ h^t = \underbrace{o^t}_{\text{output gate}} \cdot \underbrace{\tilde{h}^t}_{\text{temporary hidden state}} . \quad (10.25) \]

We can see that the key of the LSTM model is to use various gates to control how much information is passed through. In particular, the forget gate f^t controls how much information of the old cell state C^{t-1} is kept (or forgotten); the input gate i^t controls how much new information from the temporary cell state is used to update the cell state vector; and the output gate o^t controls how much information of the new cell state is used to generate the new hidden state. RNNs model equipped with gate functions is called gated RNNs. Many variants of the LSTM model exist. For example, some variant only uses two gates, by setting the input gate i^t = 1 - f^t; some variant (called gated recurrent units, or GRUs for short) further merges the cell state and hidden state.

LSTM and its variants have been successfully applied in a variety of real-world applications, such as machine translation, speech recognition, image captioning, and question answering.

## 10.4.3 Other techniques for addressing long-term dependence

In addition to gated RNNs, other techniques for addressing long-term dependence exist. For example, we can apply the shortcut connections method (Section 10.2.7) to add additional links between nonadjacent hidden states; alternatively, we can replace some links between adjacent hidden states by longer connections; we can also add self-connections to the hidden units with the weights close to 1 in order to “remember” the historical information (such units are called leaky units).

Another alternative strategy to address long-term dependence is through attention mechanism. In the machine translation example (Fig. 10.32), the sentence in the source language is summarized as the hidden state of the last time stamp of the first RNN model, which is used as the initial hidden state of the second RNN model. For short sentences, this treatment works fine. However, when the sentence to be translated becomes longer or even becomes paragraphs, the influence of such a summary vector on translation becomes weaker and weaker as the time stamp of the second RNN increases. In other words, the gap between the summary vector h_S^T, and the current word to translate x_D^t becomes larger.
