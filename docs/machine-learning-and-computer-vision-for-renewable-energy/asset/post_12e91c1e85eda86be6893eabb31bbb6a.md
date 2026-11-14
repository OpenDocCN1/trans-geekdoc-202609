
## AI Approach Towards Optimal Finding of Renewable Sources of Energy

\[
\gamma_{j=m}^i = \arg\min_{\gamma} \sum_{x_i \in R_j} \mathcal{L}(y_i, F_{m-1}(x_i) + \gamma) \tag{7}
\]

\[
F_m(x) = F_{m-1}(x) + \nu \sum_{j=1}^J r_{jm} I(x \in R_{jm}) \tag{8}
\]

Let M represent the number of trees. For any tree “m” in the training sequence, pseudo residuals, denoted as \(r_{im}\), are computed using equation (6) across all input samples. Following this, the tree is tailored to predict these residuals, with the tree structure potentially restricted based on the user-defined parameter known as the maximum depth. The output of each leaf in the tree is determined by equation (7). The prediction output of the current tree undergoes an update based on the output of the preceding tree and the learning rate \(\nu\) multiplied by the leaf output, as illustrated in equation (8). This iterative process continues until the convergence conditions are satisfied.

### D. XGBoost (XGB)

XGBoost (XGB) (Abadi et al., 2016) stands out as a robust machine learning model comprising an ensemble of decision trees. The architecture of these trees is determined using a quality score, akin to the impurity score employed by other tree-based models through greedy algorithms. Operating as a boosting algorithm, XGBoost constructs each tree based on the performance of the preceding tree, minimizing the objective function outlined in equation (9). This iterative process leads to successive trees addressing smaller residuals.

\[
\mathcal{L}(\theta) = \sum_{i=1}^n \mathcal{L}(y_i, \hat{y}_i) + \sum_{j=1}^T \Omega(f_j) \tag{9}
\]

\[
\Omega(f) = \gamma T + \frac{1}{2} \lambda \sum_{j=1}^T w_j^2 \tag{10}
\]

In equation (9), \(\mathcal{L}\) represents the loss function, assessing the disparity between the predicted value \(\hat{y}_i\) and the actual label \(y_i\), where \(f_j\) signifies the j-th tree in the ensemble. What sets XGBoost (XGB) apart from traditional gradient tree boosting techniques is its incorporation of diverse regularization techniques, denoted by the term \(\Omega(f)\). Regularization aims to diminish model variance by introducing slight bias, reducing reliance on observations and enhancing the accuracy of long-term predictions. The number of leaf nodes is indicated by \(T\).

Within equation (10), \(\gamma\) facilitates pruning, diminishing complexity in ensemble trees, \(w_j\) denotes the leaf weight, and \(\lambda\) is another user-defined parameter governing the magnitude of the regularization-induced penalty. The ultimate output of the XGB model is determined by aggregating the outputs of all trees. XGBoost has gained popularity for its swift performance and proficiency in handling a substantial number of features, missing values, and noisy data. The authors have also introduced features like sparsity-aware split finding, parallel learning, etc., further optimizing its performance, especially on larger datasets.

The fundamental unit of an MLP is the artificial neuron, also known as a perceptron. Each perceptron within a layer receives inputs from the preceding layer, conducts a weighted sum of these inputs, and then employs an activation function to produce its output. The activation function introduces non-linearity, enabling the modeling of intricate relationships between inputs and outputs. The design parameters of an MLP encompass the number of neurons in each layer and the overall number of layers, which can be adjusted to regulate the network's capacity. The MLP's parameters, including the weights and biases of each neuron, are acquired from the training data through an optimization algorithm such as back propagation. This algorithm utilizes stochastic gradient descent to minimize a loss function, gauging the disparity between the network's predicted outputs and the actual outputs.

\[
p = \phi \left( \sum_j w_j x_j + b \right) \tag{11}
\]

Equation (11) presents the mathematical depiction of a single perceptron unit “p,” where the inputs to the unit, weights, and biases are symbolized by \(x_j\), \(w_j\), and \(b\), respectively. The activation function is denoted by \(\phi\). Extending this concept to include \(L\) hidden layers, the MLP network is expressed in equation (12), where \(x\) and \(y\) represent the input and output of the model. The output of any layer \(l\) is represented by \(h^{(l)}\), and \(W^{(l)}\) signifies the weight matrix of that specific layer. Various layers within the network can employ distinct activation functions, denoted by \(\phi^{(l)}\).

\[
\begin{aligned}
h^{(i)} &= \phi^{(i)} \left( W^{(i)} x + b^{(i)} \right) \\
h^{(l)} &= \phi^{(l)} \left( W^{(l)} x + b^{(l)} \right) \\
y &= \phi^{(f)} \left( W^{(f)} h^{(l)} + b^{(f)} \right) \tag{12}
\end{aligned}
\]

### E. Long Short-Term Memory (LSTM)

Long Short-Term Memory (LSTM) represents a distinctive form of recurrent neural network (RNN) architecture, specifically crafted to tackle the challenge of vanishing gradients, encountered in conventional RNNs. The issue of vanishing gradients can impede the learning of long-term dependencies within sequential data. LSTMs introduce a memory cell state, enabling them to retain information from distant past instances across numerous timesteps. Functioning with three gating mechanisms, LSTMs selectively manage the forgetting, remembering, or updating of information from preceding time steps. Equations (13)-(18) provide a comprehensive depiction of an LSTM unit for a singular timestep.

\[
f_t = \sigma(W_f[h_{t-1}, x_t] + b_f) \tag{13}
\]

\[
i_t = \sigma(W_i[h_{t-1}, x_t] + b_i) \tag{14}
\]

\[
\tilde{C} = \tanh(W_c[h_{t-1}, x_t] + b_c) \tag{15}
\]

\[
C_t = f_t * C_{t-1} + i_t * \tilde{C} \tag{16}
\]

\[
o_t = \sigma(W_o[h_{t-1}, x_t] + b_o) \tag{17}
\]

\[
h_t = o_t * \tanh(C_t) \tag{18}
\]

where \(x_t\) and \(h_{t-1}\) denote the input sequence component of the current timestep and the hidden state from the previous timestep, respectively. The forgetting, input, and output gates are denoted by \(f_t\), \(i_t\), and \(o_t\), respectively. These gates’ outputs are determined through the application of a sigmoid activation function, yielding values between 0 and 1. The forget gate (\(f_t\)) governs the extent to which the previous cell state should be disregarded. Subsequently, the current cell state (\(C_t\)) undergoes an update involving \(i_t\) and \(\tilde{C}\), where \(\tilde{C}_t\) represents the candidate cell state. The weight matrices, denoted as \(W_f\), \(W_i\), \(W_c\), and \(W_o\), optimize the behavior of these gates and are learned during the LSTM training process on input samples. Additionally, \(b_f\), \(b_i\), and \(b_o\) are referred to as biases.

\[
C_{1,j} = \mathrm{ReLU}(Z^* h_{1,j} + b_{1,j}) \tag{19}
\]

Here, (*) signifies the convolution operation. The result feature map of the initial convolutional layer is represented as \(C_{1j}\), where \(h_{1j}\) denotes the \(j\)-th convolution kernel, and \(b_{1j}\) is the bias term. The equation includes a rectified linear unit (ReLU) as the activation function, introducing non-linearity to the input. The ensuing feature map is subsequently input into the following convolutional layer, undergoing additional processing to extract more advanced features. Consequently, the \(l\)-th convolutional layer \(C_l\), generating the output feature space \(j\)-th, can be expressed as depicted in the equation.

\[
C_{l,j} = \mathrm{ReLU}(C^*_{l-1,j} h_{l,j} + b_{l,j}) \tag{20}
\]

In recent years, Perovskite Solar Cells (PSCs) have garnered significant attention due to their noteworthy attributes such as low cost, high absorption coefficient, tunable bandgap, long carrier lifetime and diffusion length, high defect tolerance, low exciton energy, and high carrier mobility. The configuration of PSCs comprises an absorber layer, often referred to as the perovskite layer, positioned between the hole transport layer (HTL) and the electron transport layer (ETL). Substantial advancements in PSC power conversion efficiency (PCE) have been achieved, increasing from 3.8% to 25.7% through extensive research efforts capitalizing on the superior properties of these cells. This rapid progress positions PSCs as a practical and appealing alternative to traditional solar technology (Figure 1 illustrates the structure of PSC). While PSCs have demonstrated high efficiency within a relatively short timeframe, they still confront several challenges before becoming commercially viable. The perovskite material possesses the general molecular structure of \(ABX_3\), where A represents an organic or inorganic monovalent cation, B is a divalent metal ion, and X is a halogen anion. The crystal structure of perovskite material is outlined in Figure 1, with commonly used elements such as Cesium (\(Cs^+\)), Rubidium (\(Rb^+\)), Methylammonium (\(MA^+/CH_3NH_3^+\)), and Formamidinium (\(FA^+/NH_2CHNH_2^+\)) at the A site; lead (\(Pb^+\)), Tin (\(Sn^+\)) typically used at the B site; and Iodide (\(I^-\)), Bromide (\(Br^-\)), Chloride (\(Cl^-\)) at the X site. Essentially, there exist infinite combinations and possibilities for perovskites in solar cell applications.

A notable characteristic of perovskite materials is their tunable bandgap, allowing them to absorb a broad range of photons. Altering the perovskite’s composition enables the adjustment of its bandgap, facilitating the tuning of the material’s absorption properties. Achieving optimal efficiency in PSCs requires meticulous attention to various aspects of fabrication, including the composition of perovskite materials, interface engineering, and device architecture.

Identifying a perovskite material with an ideal bandgap matching the solar spectrum is crucial for the efficiency of solar cells. Perovskites exhibit the capacity to fine-tune their bandgap within the range of \(1.5\ \text{eV}\) to \(3.2\ \text{eV}\), with the most efficient bandgap for perovskite solar cells being approximately \(1.6\ \text{eV}\). This specific bandgap optimally absorbs a diverse range of photons present in the solar spectrum (Cozzi et al., 2020). Consequently, tuning the composition of perovskites is essential to optimize their properties. However, relying solely on trial and error for such an intricate scenario is impractical and illogical.

Structural instability poses a significant challenge to the commercialization of Perovskite Solar Cells (PSCs) as it can lead to cell degradation over time. Factors such as temperature, humidity, and light exposure contribute to this instability. The deterioration of perovskite materials negatively impacts the efficiency and lifespan of solar cells. Additionally, the use of Pb, a toxic substance, in PSCs is an environmental concern as it can leach out over time and contaminate the surroundings. To address these issues, researchers are actively developing new perovskite materials that are more stable and less toxic. Strategies include creating lead-free perovskite materials, utilizing alternative materials to stabilize the perovskite structure, and employing encapsulation methods to shield solar cells from environmental factors.

In recent years, Machine Learning (ML) techniques have been employed to predict the bandgap, Power Conversion Efficiency (PCE), and stability of PSCs with high accuracy, significantly expediting the development and optimization of PSCs. Figure 1 illustrates the implementation of ML in the fabrication process of PSCs. Various studies have demonstrated the predictive capabilities of ML methods in effectively estimating the bandgap, PCE, and stability of PSCs. This section provides a succinct overview of the application of ML techniques in the fabrication of PSCs.
