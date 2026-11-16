
![](img/aa2f42c739937b682075082233e335bb_239_0.png)

**FIGURE 7.4** Cell state in an LSTM model.

![](img/aa2f42c739937b682075082233e335bb_239_1.png)

**FIGURE 7.5** Schematic representation of an LSTM when unrolled in time.

the memory of the preceding cell. Also, each LSTM cell contains two outputs, \(h_t\) and \(C_t\), which are the output of the actual network and the memory of the current unit, respectively. It is composed of three kinds of gates, namely the input gate, the forget gate, and the output gate (Fig. 7.3). Each gate comprises a sigmoid neural net layer and a pointwise multiplication operation. LSTMs can be seen when unfolded as a chain-like structure. In other words, it is a loop repeating module with a different structure (Fig. 7.5). Depending on the input and the internal feedback (memory state), the output will be generated in a special manner based on gates and four embedded layers structure. The layers here have activation units based on sigmoid and tanh.

This LSTM unit provides a decision based on the actual input, previous output and memory, and then produces a new output and upgrades its memory.

- **Input gate** The key role of the input gate is to control the flow of input activation into the memory cell. Here, the sigmoid layer controls the flow by generating an output between 0 and 1 into the memory cell.

- **Output gate** The aim of the output gate is to control the output flow generated from cell activation to be injected into the network. This gate has the sigmoid layer that controls how much memory should be fed into the next LSTM unit.

- **Forget gate** The sigmoid layer output removes information from the cell state that is no longer required (when the output is 0, otherwise it will keep it). In other words, the forget gate overcomes the weakness of LSTM models by preventing them from processing continuous input streams [32]. By scaling the content of block memory, it forgets the cell's memory content in an adaptive way.

### 7.2.2.1 LSTM implementation steps

The input of each LSTM cycle is (t – 1)th memory state $C_{t-1}$ and hidden layer units $h_{t-1}$ (output), but for the first cycle we start with zero or randomized values. The main steps when implementing LSTM are described below.

- The first step of LSTM consists of deciding which information is to be forgotten or retained in the particular time instant. This step is particularly useful when the past information is no longer useful for the actual cycle which is mainly related to the current input. In other words, the aim of this step is to reveal the information that is not needed and can be omitted from the cell state. This is achieved by the sigmoid function. It looks at the past state ($h_{t-1}$) and the actual input $x_t$ and calculates the function accordingly (Fig. 7.6).

```
$f_t = \sigma(x_t U^f + h_{t-1} W^f),$
```

where $W^f$ is weight and $h_{t-1}$ is the output from the previous time.

![](img/aa2f42c739937b682075082233e335bb_240_0.png)

FIGURE 7.6 First step in LSTM: decide what information is to be forgotten or retained.

- The second step in the LSTM consists of updating the content of the memory cell. This step selects the new information that will be stored in the cell state (Fig. 7.7). The second layer (input gate) contains two parts, namely the sigmoid function and the tanh. The sigmoid layer chooses which values are to be updated. In the case of 1, the value of the input gate is unchanged, and in the case of 0 it is dropped. Next, a tanh layer creates a vector of new candidate values that can be added to the state. It provides weight to the selected values for their level of importance (-1 to 1). After that, the two are combined to update the state. The \(\tilde{C}_t\) is combined with \(C_{t-1}\) to update the memory state \(C_t\). The \(h_t\) (output) is computed according to the output gate sigmoid and the tanh of \(C_t\):

\(i_t = \sigma(x_t U^i + h_{t-1} W^i), \quad (7.4)\)
\(\tilde{C}_t = \tanh(x_t U^g + h_{t-1} W^g), \quad (7.5)\)

\(\tilde{C}_t\) is the candidate memory cell, \(W^i\), \(W^g\) are weight parameters.

- In this step, the old cell state, \(C_{t-1}\), is updated with the new cell state, \(C_t\) (Fig. 7.8). To do so, the old state is multiplied by \(f_t\) to forget the irrelevant information, and the candidate, \(\tilde{C}_t\), is added. This represents the new candidate values scaled by how much we choose to update every state value:
\(C_t = f_t \cdot C_{t-1} + i_t \cdot \tilde{C}_t. \quad (7.6)\)

![](img/aa2f42c739937b682075082233e335bb_241_0.png)

**FIGURE 7.8** Step 3 in LSTM modeling.

- Finally, the output is computed in two steps (Fig. 7.9). First, a sigmoid layer is utilized to select the relevant portions of the cell state to be transmitted to the output (Eq. 7.7):
\(o_t = \sigma(x_t U^o + h_{t-1} W^o). \quad (7.7)\)

![](img/aa2f42c739937b682075082233e335bb_241_1.png)

**FIGURE 7.9** Step 4 in LSTM modeling.

The cell state is then passed via tanh (for normalizing values within the range -1 and 1) and multiplied by the output of the sigmoid gate; thus we keep only the portions we selected to output (Eq. (7.8)):

```
$h_t = \tanh(C_t) \cdot o_t.$ (7.8)
```

At the end of the cycle, the \( h_t \) hidden layer units which represent the output of the cycle and the \( C_t \) memory state are ready for the next cycle usage. In summary, in the LSTM model, the three gates are trained for learning what information can be maintained in the memory, how long it can be stored, and when it can be read out. Combining several memory cells into blocks permits them to share the same gates, and hence the number of adaptive parameters is reduced.

## 7.2.3 Gated recurrent neural networks

In this section we present another extended version of RNN, called a gated recurrent unit (GRU), which was primarily introduced by Cho et al. [9]. GRU can be considered as a reduced version of LSTM. It is also designed to alleviate the vanishing gradient problem, which is the main weakness of the standard RNN. GRU is built without a cell state and comprises only two gates instead of three, as in LSTM [9]. GRU models have demonstrated their efficiency during the last decade in several applications involving sequential or temporal data [11, 10, 12, 13]. Their successful application comes from their ability to model complex nonlinearity between data points and extract relevant features from time series data.

In comparison with LSTM, GRU comprises two gates instead of three, i.e., update and forget (also called reset). Indeed, the update gate in GRU can be viewed as a combination of the forgetting gate and input gate in LSTM (Fig. 7.10). These two gates consist of a sigmoid layer and a pointwise multiplication operation represented by two vectors, resulting in values within the interval [0, 1]. Similar to LSTM, the impact of the previous historical information on the actual cycle is controlled by these gates. When the output of the reset gate is zero, the memory information is ignored; otherwise it will influence the evolution of the final response.

![](img/aa2f42c739937b682075082233e335bb_242_0.png)

FIGURE 7.10 Gated recurrent unit.

Generally speaking, the forget or reset gate determines how to merge the new input with the previous memory [10]. In other words, this gate is employed to decide the amount of historical information to quash:

```
r_t = \sigma(x_t U^r + h_{t-1} W^r). (7.9)
```

On the other hand, the update gate, which is acting similarly to the forget and input gate of an LSTM, decides how much of the previous memory to keep and what new information to add:

```
z_t = \sigma(x_t U^z + h_{t-1} W^z). (7.10)
```

The new hidden state output at the current time point merges current and previous time points and can be computed as

```
h_t = (1 - z_t) \cdot h_{t-1} + z_t \cdot \tilde{h}_t. (7.11)
```

We can see that the complement of gate-update is utilized to decide the information to maintain from the h_{t-1} rather than creating a new gate for this purpose. The new candidate, \tilde{h}_t, for hidden layer output is computed as

```
\tilde{h}_t = \tanh(x_t U^h + (r_t \cdot h_{t-1}) W^h). (7.12)
```

Here, r_t is used to manage what part of h_{t-1} is needed to incorporate when computing a new candidate. Table 7.1 summarizes the main features of LSTM and GRU models.

| LSTM | GRU |
|---|---|
| Three gates | Two gates |
| Control the exposure of memory content (cell state) | Expose the entire cell state to other units in the network |
| Has separate input and forget gates | Performs both of these operations together via update gate |
| More parameters | Fewer parameters |

## 7.3 Hybrid deep models

In practice, several data sequences are high-dimensional, such as words in a text and images in a video. Thus, using only received observations at the previous time points cannot guarantee a good prediction of the expected value at the next time point. With such high-dimensional objects, using RNNs alone to uncover correlated patterns would be very expensive. To overcome this issue, energy-based models such as the Boltzmann machine (RBM) are integrated into
