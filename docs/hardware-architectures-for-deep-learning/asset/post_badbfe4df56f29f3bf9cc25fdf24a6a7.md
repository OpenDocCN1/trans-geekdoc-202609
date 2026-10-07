
# 30 Hardware architectures for deep learning

In problems, it only needs to consider recent information to perform the present task, but it is very likely for the gap between the relevant information and the point where it is needed to be large. When that gap grows, RNNs become unable to learn to connect the information, because they usually keep a short memory, in which long-term dependencies may not fit. This shortcoming is explored and analyzed in depth by [8,9]. This problem of baseline RNNs led to the emergence of LSTM and GRU. We will describe the basics of these models in the following sections.

## 2.1.1 Long short term memory

LSTMs are a special kind of RNN, which allows the network to capture information from inputs for a long time using a special hidden unit, called the LSTM cell [10]. LSTMs emerged as an effective and scalable model for several learning problems related to sequential data. Earlier RNN models for attacking problems have either been tailored to a specific problem or did not scale to long-time dependencies. LSTMs, on the other hand, are general and effective in capturing long-term temporal dependencies.

All repeated neural networks have the shape of a series of repeating neural network modules. As shown in Figure 2.3, in a baseline RNN, these repeating modules have a simple structure, similar to one tanh layer.

LSTMs inherit this chain-like structure, but implement the repeating module in a different and more complex way (Figure 2.4). Instead of a single neural network layer, there are four layers interacting in a special way. Figure 2.4 shows the internal structure of an LSTM and how the current instance, the middle box, interact with the instances at the previous and next time steps. An LSTM has a similar control flow as a RNN. It processes data as it propagates. The major differences are the operations within the LSTM cells. These operations are used to allow the LSTM to keep or forget information.

Figure 2.5 shows the notations used in LSTM dataflow. Each line carries an entire vector, from the output of one node to the inputs of others. The circles represent pointwise operations, such as vector addition, while the boxes are learned neural network layers. A line merging indicates concatenation, whereas a line forking content, with each copy going to a different way.

![](img/e6e752b99eb1621488c89445a57e2a86_55_0.png)
Figure 2.3 The repeating module in a standard RNN

![](img/e6e752b99eb1621488c89445a57e2a86_56_0.png)
Figure 2.4 The repeating module in an LSTM

![](img/e6e752b99eb1621488c89445a57e2a86_56_1.png)
Figure 2.5 Notations in LSTM dataflow

![](img/e6e752b99eb1621488c89445a57e2a86_56_2.png)
Figure 2.6 The core idea behind LSTM

### 2.1.1.1 Main concept of LSTMs

In addition to standard RNN units, LSTM adds some special units to the network. The units that are unique to LSTM include a *memory cell* that can maintain information in memory for long periods of time. A set of gates is used to control when information enters the memory, when it goes out, and when it is forgotten. These extra parts allow LSTMs learn longer-term dependencies. The main idea of LSTM network is the *cell state* which is a piece of intermediate information (or result) stored in memory cell and represented by the horizontal line running through the top of Figure 2.6.

LSTM can remove or add the information to the cell state, regulated by the gate structures. Gates are composed of a sigmoid neural network layer and a multiplication operation. describing how much of each component should be let through. The sigmoid layer returns numbers between “0” and “1” as output, at the two extreme points, “0” value means “let nothing through,” while a “1” value means “let everything through.” In order to control the cell state, the repeating module in an LSTM (Figure 2.4) has three colors of sigmoid gates. A typical sigmoid gate used in LSTM cells for removing or adding information is shown in Figure 2.7.

### 2.1.1.2 Steps in LSTM

The first step in the LSTM is to decide what information we need to throw away from the cell state. Figure 2.8 represents the forget operation. Information from the previous hidden state ($h_{t-1}$) and information from the current input ($x_t$) are passed through the sigmoid function and the layer generates a number between “0” and “1.” If the generated value is “0,” the corresponding data is eliminated from the previous state ($C_{i-1}$) and if the value is “1,” the associated data completely goes through.

![](img/e6e752b99eb1621488c89445a57e2a86_57_0.png)
Figure 2.7 Sigmoid layer in LSTM for removing or adding information

![](img/e6e752b99eb1621488c89445a57e2a86_57_1.png)
Figure 2.8 Forget operation

Equation (2.1) represents the forget operation formula:

```
$f_i = \sigma(W_f \cdot [h_{i-1}, x_i] + b_f) \quad (2.1)$
```

Where $W_f$ is forget weight vector and $b_f$ is the bias value for forget operation. The next step in the LSTM is to decide what new information is needed to be stored in the cell state. Figure 2.9 represents the update gate operation. This step has two parts. First, a sigmoid layer called the “input gate layer” decides which values should be updated. Next, a tanh layer creates a vector of new candidates $\tilde{C}_i$ that can be added to the state. Finally, these two layers will be combined to create an update to the state, as represented in (2.2) and (2.3):

```
$i_i = \sigma(W_i \cdot [h_{i-1}, x_i] + b_i) \quad (2.2)$
```

```
$\tilde{C}_i = \tanh(W_c \cdot [h_{i-1}, x_i] + b_c) \quad (2.3)$
```

where $W_i$ and $W_c$ are weight and $b_i$ and $b_c$ are bias. The next step is to update the old state $C_{i-1}$ into the new state $C_i$ (Figure 2.10). First, the cell state goes through a multiplication by $f_i$. Then we take the output from the input gate ($i_i$) multiplied by $\tilde{C}_i$ and do a pointwise addition:

```
$C_i = f_i \times C_{i-1} + i_i \times \tilde{C}_i \quad (2.4)$
```

![](img/e6e752b99eb1621488c89445a57e2a86_58_0.png)
Figure 2.9 Update operation

Finally, it should be decided what to deliver as output (Figure 2.11). First, a sigmoid layer is run on the cell state to specify what parts of the cell state should appear. Then, the cell state is passed through the tanh function and multiplied by the output of the gate (to push the value to be between -1 and 1) as:

```
$o_t = \sigma(W_o \cdot [h_{t-1}, x_t] + b_o)$
```

```
$h_t = o_t \times \tanh(C_t)$
```

where $o_t$ is the output of sigmoid gate, $W_o$ is the weight vector, and $b_o$ is the bias value.

### 2.1.1.3 Variants on the LSTM model

In several researches, different variants of LSTMs are proposed. In [10], a comprehensive comparison of popular variants of LSTM is presented.

One of the most popular LSTM variants, introduced in [3], adds a set of the so-called peehole connections to the base architecture. Peehole connections provide feedback from the cell to the gates, allowing the gates to carry out their operations as a function of both the incoming inputs and the previous state of the cell. Figure 2.12 and (2.7) show how peeholes are added to all gates:

```
$f_t = \sigma(W_f[C_{t-1}, h_{t-1}, x_t] + b_f)$
$i_t = \sigma(W_i[C_{t-1}, h_{t-1}, x_t] + b_i)$
$o_t = \sigma(W_o[C_t, h_{t-1}] + b_o)$
```

Another important variation couples forget and input gates, as shown in Figure 2.13. Instead of separately deciding about what to forget and what new values to add.

![](img/e6e752b99eb1621488c89445a57e2a86_60_0.png)
Figure 2.12 Peehole connections

![](img/e6e752b99eb1621488c89445a57e2a86_60_1.png)
Figure 2.13 Input new values to the state when something older is forgotten
