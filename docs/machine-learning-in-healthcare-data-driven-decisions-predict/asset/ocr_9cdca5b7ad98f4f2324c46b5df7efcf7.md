# Step 1: Temporal Modeling using BiLSTM

To capture the sequential patterns in a patient's health evolution, we employ a BiLSTM network. The LSTM cell is defined as:

$$\begin{aligned} f_t &= \sigma(W_f \cdot [h_{t-1}, x_t] + b_f)i_t \quad (1) \\ &= \sigma(W_i \cdot [h_{t-1}, x_t] + b_i)C_t^- \quad (2) \\ &= \tanh(W_c \cdot [h_{t-1}, x_t] + b_c)C_t \quad (3) \\ &= f_t * C_{t-1} + i_t * C_t o_t \quad (4) \\ &= \sigma(W_o \cdot [h_{t-1}, x_t] + b_o)h_t \quad (5) \\ &= o_t * \tanh(C_t) \quad (6) \end{aligned}$$

where $f_t, i_t, o_t$: forget, input, and output gates respectively, $C_t$: cell state at time t, $h_t$: hidden state at time t, $\sigma$: sigmoid activation function, $W_f, W_i, W_c, W_o$: weight matrices, $b_f, b_i, b_c, b_o$: biases.

The forward and backward hidden states are concatenated as:

$$ h_t \leftrightarrow = [\overrightarrow{h_t}; h_t \leftarrow] \quad (7) $$

This produces a context-rich representation of the patient's temporal progression.

# Step 2: Medical Knowledge Graph Construction

To integrate domain-specific relationships, we build a medical knowledge graph $G = (V, E)$ where

+   - $V = \text{set of clinical concepts (diagnoses, medications, procedures)}$
+   - $E = \text{set of relationships (e.g., "treats," "associated\_with," "contraindicates")}.$

Each concept $v_i \in V$ is embedded into a vector space using TransE, which enforces that

$$ v_i + r_{ij} \approx v_j \quad (8) $$

for each triplet $(v_i, r_{ij}, v_j) \in E$, where $r_{ij}$ is the relation embedding. The objective function minimized is:

$$\begin{aligned} L_{KG} &= \sum_{(h,r,t) \in T} [||h + r - t||_2^2] \\ &+ \sum_{(h',r,t') \in T'} [\max(0, \gamma + ||h + r - t||_2^2 - ||h' + r - t'||_2^2)] \quad (9) \end{aligned}$$

where $T$ represents the true triplets, $T^{'}$ the corrupted triplets, and $\gamma$ the margin hyper-parameter.