use the retained $e^a$ and $e^b$ when calculating the contrastive loss with $p^a$ and $p^b$, considering $e^a$ or $e^b$ as constant values when applying the stop-gradient operation. This allows the two contrastive losses to be calculated simultaneously.

![](bbox=[0.13, 0.27, 0.88, 0.64])

Figure 3. (a) We design the training process of Lite-SRL as a sequential structure to adapt model parallelization. (b) Schematic of the proposed distributed hybrid parallel (DHP) training baseline.

Each convolution layer within a CNN structure can be used as a single partition to achieve highly efficient model parallelism training capabilities. Given a network $M$ that consists of layers $\{L_1, L_2 \cdots, L_q\}$. Divide network $M$ into $n$ partitions $\{P_1, P_2 \cdots, P_n\}$ where $P_i = \{L_{i}, L_{i+1} \cdots, L_{i+K}\}$, $\{L_i, L_{i+1} \cdots, L_{i+K}\}$ denotes partition $P_i$ is start from layer $L_i$ and contains $k$ layers. Except for this, the calculation of all partitions is sequential, partition $P_i$ transmit its output feature to its next partition $P_{i+1}$, while the gradient calculated by partition $P_i$ is transmitted to the front partition $P_{i-1}$. At iteration $t$, during forward propagation send the input $A^t_{L_{i-1}}$ from partition $P_{i-1}$ to partition $P_i$ and delivers activation $A^t_{L_i}$. Identically, during backward propagation of iteration $t$, the $G^t_{L_{i+1}}$ indicates the gradient calculated by partition $P_{i+1}$. With each layer $L_i \le L_x \le L_q$, we denote the weight parameter of layer $L_x$ as $w_x$, the gradient is given as:

$$\hat{G}_{w_x}^{t-i} = \frac{\delta A_{L_x}^{t-i}}{\delta w_x^{t-i-1}} \cdot G_{L_x+1}^{t-i} \tag{6}$$

We denote the learning rate as $\gamma_{t-i}$. Equation (6) is updated by the following equation:

$$w_x^{t-i} = w_x^{t-i-1} - \gamma_{t-i} \hat{G}_{w_x}^{t-i} \tag{7}$$

For layers in non-sequential CNN, parallel paths are not partitioned; instead the parallel zone is considered as a block. After the network partitioning, the network can be trained in model parallelism mode.