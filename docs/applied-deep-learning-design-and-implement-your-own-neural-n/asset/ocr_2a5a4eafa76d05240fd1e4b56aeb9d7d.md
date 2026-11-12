Forget gate is shown in figure 7.4:

![](bbox=[0.53, 0.13, 0.58, 0.45])

Figure 7.4: Forget Gate of LSTM

The equation for the forget fate can be written as follows:

$$\gamma_f = \sigma[(W_f (h_{t-1}, x_t) + b_f]$$

Or

$$f(t) = \sigma[(W(F)[h(t-1), x(t)] + b(t)]$$

Where Wf and bf are weight and bias, respectively. In forget gate’s input and output, we are using the Sigmoid activation function; therefore, it returns values between 0 and 1, where forget gate output values:

+   - 0—Completely forget what information is present in the memory cell.
+   - Represents completely, providing all the information present in the memory cell.

# # Input modulation gate or potential cell update unit in LSTM

Instead of the sigmoid (σ) activation function, it uses the tanh activation function. It creates a vector of new candidate value. The input modulation gate is shown in figure 7.5: