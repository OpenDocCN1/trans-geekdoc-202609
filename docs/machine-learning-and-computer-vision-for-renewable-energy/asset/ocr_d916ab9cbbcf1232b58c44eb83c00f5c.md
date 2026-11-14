# A Deep Learning Framework for Modeling Temporal Dependencies

the prior data. The input gate, forget gate and output gate are the three gates found in every neuron. The LSTM can resolve the issue of long-term data reliance by using the input gate. Next, we outline the LSTM architecture's internal gates and explain how it addresses long-term dependency issues. There are three gates in this figure and they are discussed below

+   1) **The Forget Gate**: In Figure 2, the forget gate which is defined in equation (3) determines which information will be discarded from the cell. By entering the output $h_{t-1}$ at the previous unit (t–1) and adding the current time $t$ and input $X_t$ into a $Sigmoid$ function $S(t)$ that is defined in equation (4) as shown in Figure 3. A value between 0 and 1 is generated and this value will be multiplied with cell state $C_{t-1}$ to determine how much information will be forgotten or remembered. The 0 means completely forgotten, while 1 is completely remembered. Therefore, $W$ and $b$ are the weight matrices and bias vector parameters respectively, which need to be learned during training.

```
$f_t = \sigma\big(W_f \cdot [h_{t-1}, x_t] + b_f\big)$
```

```
$S(t) = \frac{1}{1 + \exp -t}$
```

Figure 2. Long short-term memory architecture
Source: Authors

![](bbox=[0.185, 0.565, 0.765, 0.905])