# 7.2.2.1 LSTM implementation steps

The input of each LSTM cycle is (t – 1)th memory state $C_{t-1}$ and hidden layer units $h_{t-1}$ (output), but for the first cycle we start with zero or randomized values. The main steps when implementing LSTM are described below.

+   • The first step of LSTM consists of deciding which information is to be forgotten or retained in the particular time instant. This step is particularly useful when the past information is no longer useful for the actual cycle which is mainly related to the current input. In other words, the aim of this step is to reveal the information that is not needed and can be omitted from the cell state. This is achieved by the sigmoid function. It looks at the past state ($h_{t-1}$) and the actual input $x_t$ and calculates the function accordingly (Fig. 7.6).

```
$f_t = \sigma(x_t U^f + h_{t-1} W^f),$
```

where $w_f$ is weight and $h_{t-1}$ is the output from the previous time.

![](bbox=[0.31, 0.4, 0.67, 0.55])

FIGURE 7.6 First step in LSTM: decide what information is to be forgotten or retained.

+   • The second step in the LSTM consists of updating the content of the memory cell. This step selects the new information that will be stored in the cell state (Fig. 7.7). The second layer (input gate) contains two parts, namely the sigmoid function and the tanh. The sigmoid layer chooses which values are to be updated. In the case of 1, the value of the input gate is unchanged, and in the case of 0 it is dropped. Next, a tanh layer creates a vector of new candidate values that can be added to the state. It provides weight to the selected values

![](bbox=[0.31, 0.75, 0.67, 0.9])

FIGURE 7.7 Second step in LSTM: updating the content of the memory cell.