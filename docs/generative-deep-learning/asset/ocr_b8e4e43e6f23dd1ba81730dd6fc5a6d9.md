![](bbox=[0.19, 0.1, 0.78, 0.33])

Figure 5-6. An LSTM cell

+   1. $f_t = \sigma(W_f \cdot [h_{t-1}, x_t] + b_f)$
+   2. $i_t = \sigma(W_i \cdot [h_{t-1}, x_t] + b_i)$
+   3. $\tilde{C}_t = \tanh(W_C \cdot [h_{t-1}, x_t] + b_C)$
+   4. $C_t = f_t * C_{t-1} + i_t * \tilde{C}_t$
+   5. $o_t = \sigma(W_o \cdot [h_{t-1}, x_t] + b_o)$
+   6. $h_t = o_t * \tanh(C_t)$

2. The concatenated vector is also passed through an *input* gate that, like the forget gate, is a dense layer with weights matrix $W_i$, bias $b_i$, and a sigmoid activation function. The output from this gate, $i_t$, has length equal to the number of units in the cell and contains values between 0 and 1 that determine how much new information will be added to the previous cell state, $C_{t-1}$.

3. The concatenated vector is passed through a dense layer with weights matrix $W_C$, bias $b_C$, and a tanh activation function to generate a vector $\tilde{C}_t$ that contains the new information that the cell wants to consider keeping. It also has length equal to the number of units in the cell and contains values between -1 and 1.

4. $f_t$ and $C_{t-1}$ are multiplied element-wise and added to the element-wise multiplication of $i_t$ and $\tilde{C}_t$. This represents forgetting parts of the previous cell state and then adding new relevant information to produce the updated cell state, $C_t$.

5. The concatenated vector is passed through an *output* gate: a dense layer with weights matrix $W_o$, bias $b_o$, and a sigmoid activation. The resulting vector, $o_t$, has length equal to the number of units in the cell and stores values between 0 and 1 that determine how much of the updated cell state, $C_t$, to output from the cell.