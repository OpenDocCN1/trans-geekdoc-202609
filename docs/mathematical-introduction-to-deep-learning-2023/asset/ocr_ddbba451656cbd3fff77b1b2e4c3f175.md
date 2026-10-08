for applications of CNNs to audio processing, and we refer, for example, to [46, 105, 236, 348, 408, 440] for applications of CNNs to time series analysis. Finally, for approximation results for feedforward CNNs we refer, for instance, to Petersen & Voigtländer [34] and the references therein.

# ### 1.4.1 Discrete convolutions

**Definition 1.4.1** (Discrete convolutions). *Let* $T \in \mathbb{N}$, $a_1, a_2, \ldots, a_T$, $w_1, w_2, \ldots, w_T$, $\mathbf{d}_1, \mathbf{d}_2, \ldots, \mathbf{d}_T \in \mathbb{N}$ *and let* $A = (A_{i_1,i_2,\ldots,i_T})_{(i_1,i_2,\ldots,i_T) \in (\times_{t=1}^T \{1,2,\ldots,a_t\})} \in \mathbb{R}^{a_1 \times a_2 \times \ldots \times a_T}$, $W = (W_{i_1,i_2,\ldots,i_T})_{(i_1,i_2,\ldots,i_T) \in (\times_{t=1}^T \{1,2,\ldots,w_t\})} \in \mathbb{R}^{w_1 \times w_2 \times \ldots \times w_T}$ *satisfy for all* $t \in \{1, 2, \ldots, T\}$ *that*

$$\mathbf{d}_t = a_t - w_t + 1. \quad (1.106)$$

*Then we denote by* $A * W = ((A * W)_{i_1,i_2,\ldots,i_T})_{(i_1,i_2,\ldots,i_T) \in (\times_{t=1}^T \{1,2,\ldots,\mathbf{d}_t\})} \in \mathbb{R}^{\mathbf{d}_1 \times \mathbf{d}_2 \times \ldots \times \mathbf{d}_T}$ *the tensor which satisfies for all* $i_1 \in \{1, 2, \ldots, \mathbf{d}_1\}$, $i_2 \in \{1, 2, \ldots, \mathbf{d}_2\}$, $\ldots$, $i_T \in \{1, 2, \ldots, \mathbf{d}_T\}$ *that*

$$(A * W)_{i_1,i_2,\ldots,i_T} = \sum_{r_1=1}^{w_1} \sum_{r_2=1}^{w_2} \cdots \sum_{r_T=1}^{w_T} A_{i_1 - r_1 + 1, i_2 - r_2 + 1, \ldots, i_T - r_T + 1} W_{r_1,r_2,\ldots,r_T}. \quad (1.107)$$

# ### 1.4.2 Structured description of feedforward CNNs

**Definition 1.4.2** (Structured description of feedforward CNNs). *We denote by* $\mathbf{C}$ *the set given by*

$\mathbf{C} = \bigcup_{T,L \in \mathbb{N}} \bigcup_{l_0,l_1,\ldots,l_L \in \mathbb{N}} \bigcup_{(c_k, i)_{k=0}^{L} \in (\{1,2,\ldots,L\} \times \{1,2,\ldots,T\})^{L+1} \subseteq \mathbb{N}} \left( \bigtimes_{k=1}^{L} \left( (\mathbb{R}^{c_k} \times \mathbb{R}^{c_k} \times \ldots \times \mathbb{R}^{c_k})^{l_k} \times l_{k-1} \times \mathbb{R}^{l_k} \right) \right). \quad (1.108)$$

**Definition 1.4.3** (Feedforward CNNs). *We say that* $\Phi$ *is a feedforward CNN if and only if it holds that*

$$\Phi \in \mathbf{C}. \quad (1.109)$$

*(cf. Definition 1.4.2.)*

# ### 1.4.3 Realizations of feedforward CNNs

**Definition 1.4.4** (One tensor). *Let* $T \in \mathbb{N}$, $d_1, d_2, \ldots, d_T \in \mathbb{N}$. *Then we denote by* $\mathbf{I}_{d_1,d_2,\ldots,d_T} = (\mathbf{I}_{i_1,i_2,\ldots,i_T})_{(i_1,i_2,\ldots,i_T) \in (\times_{t=1}^T \{1,2,\ldots,d_t\})} \in \mathbb{R}^{d_1 \times d_2 \times \ldots \times d_T}$ *the tensor which satisfies for all* $i_1 \in \{1, 2, \ldots, d_1\}$, $i_2 \in \{1, 2, \ldots, d_2\}$, $\ldots$, $i_T \in \{1, 2, \ldots, d_T\}$ *that*

$$\mathbf{I}_{i_1,i_2,\ldots,i_T}^{d_1,d_2,\ldots,d_T} = 1. \quad (1.110)$$