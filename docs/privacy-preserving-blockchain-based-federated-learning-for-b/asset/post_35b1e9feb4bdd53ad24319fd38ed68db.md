
federated learning, each user \( u \in U \) possesses their own private dataset samples.

```
\( F_l(w) = \frac{1}{|D_i|} \sum_{j \in D_i} f_j(w; x_i, y_i) \) (2)
```

A global loss function \( f_j(w; x_i, y_i) \) minimizes the weights for multiple hospitals in a dataset \( D \). In order to handle the statistical heterogeneity among participating clients, a proximal term is added as a local subproblem to the each client optimization so as to effectively limit the impact of divergent variable local updates as:

```
\( F_i(w; w^t) = \frac{1}{|D_i|} \sum_{j \in D_i} f_j(w; x_i, y_i) + \frac{\mu}{2} \|w - w^t\|^2, \) (3)
```

where \( w^t \) is the latest global parameter update and \( \mu \) is a scaled parameter for the proximal term.

The global model function \( F(w) \) is defined as the difference between the estimated and actual values for each hospital, represented as \( f_j(w; x_i, y_i) \).

```
\( F(w) = \frac{1}{|M_I|} \sum_{l \in I} u_l \cdot F_l(w) \)
\( = \frac{1}{|M_I|} \sum_{l \in I} \sum_{j \in D_i} u_l \cdot \frac{f_j(w; x_i, y_i)}{|D_i|} \) (4)
```

where \( i \) represents a sample \( (x_i, y_i) \) from the gallery \( I = 1, 2, \dots, n \), and \( n_i \) denotes the number of individual dataset models of hospitals. In our proposed training method, we improved the model's accuracy through an iterative process of minimizing the loss function associated with the global model.

### 2.2. Background of blockchain

Training an effective AI model for Industry 4.0 requires collecting data from multiple sources without compromising privacy. For authenticating users, a blockchain network is essential. Several challenges persist in federated learning on a central server, such as insufficient incentives and the risk of poisoning attacks. To address these, some authors, such as Lu et al. [39] and Qu et al. [40], have utilized blockchain to secure federated learning data. Choi and Pokhrel [41] designed a technique to safeguard the privacy of federated learning using blockchain. However, a major issue with previous studies is their failure to include encryption and masking techniques for securing model parameters. Therefore, we combine federated learning with a blockchain distributed ledger for secure data sharing and to update the global AI model with data from various hospitals. The primary advantage of blockchain technology is its ability to collect data models from different nodes and aggregate local and global models. Smart contracts are used to upload the weights and update the models. The architecture we propose seamlessly combines the strengths of blockchain technology with the capabilities of federated learning, resulting in a fully decentralized system with enhanced security measures. This decentralized approach not only improves the precision of the model but also cultivates a higher level of trust among the participating entities.

## 3. Secure data sharing for blockchain and federated learning

In this section, we introduce the high-level architecture of the system and its technical details.

### 3.1. System model

Our proposed scheme involves multiple users securely training a global model using federated learning combined with blockchain technology. This proposed architecture consists of several phases (see Fig. 1).

| Notation | Description |
|---|---|
| L | Loss |
| \( D_i \) | Dataset |
| \( w_i \) | Weight vector |
| \( w_i \) | Masked weight vector |
| \( \Delta L \) | Partial derivative function. |
| H | The hospital |
| M | The global model |
| s | Secret key |
| \( g_i \) | Gradient vector |

Local Model: Each hospital uses its own private dataset to train the local model. Hospitals train and evaluate their local models separately. The following steps should be followed to secure and learn the local model:

- 1. Send local model for training local dataset.
- 2. Train the local model and compute the local gradients.
- 3. Add the mask to parameters for secure model sharing.

Send the Weights to the Blockchain Network for the Aggregation Model: The global model parameters are updated based on the local model parameters of each hospital. Subsequently, the blockchain employs a federated learning averaging technique to aggregate these model parameters. The global model is trained using the local datasets. One advantage of blockchain is its ability to verify the quality of the model, which helps in rejecting false models.

```
\( AggregateW_l(\beta) \leftarrow \frac{1}{\sum_{i \in S_i} |D_i|} \sum_{i \in S_i} |D_i| W_l(\beta). \) (5)
```

where \( S_t \) denotes a set of participants at time \( t \) and \( \beta \) represents the random share of participants masked with the learned model parameter \( W \).

Broadcast the Weights: Finally, the trained global model updates the local hospital models by sharing the latest information for more accurate diagnoses, as shown in Algorithm 3.

- 1. Update the federated or global model based on local model weights.
- 2. Send the latest or updated weights to the local model.

```
Algorithm 1: Local Training of the Hospital Datasets
Input:
\( D_i \): Local hospital dataset,
\( E \): Number of local hospital iterations;
\( w \): Local model parameters,
\( \eta \): Learning rate
Output:
\( \theta_l \): Trained model parameters
Initialize model parameters \( w \);
while Hospital Participating in Federated Learning do
  if globalBroadcastReceived then
    Initialize local model parameters \( w_i \) with global model parameters \( w_l^t \) ;
    \( w_i \leftarrow w_l^t \) ;
  end
  for local epoch \( e \leftarrow 1 \) to \( E \) do
    for \( b = (x, y) \in \) random batch from \( D_i \) do
\( w_i \leftarrow w_i - \eta(\nabla(\mathcal{L}(w_l; b))) \) ;
    end
  end
end
return \( w_i \);
```

![](img/d4c581239fa91a9df419238aaf133f2b_3_0.png)

**Fig. 1.** An illustration of our proposed permissioned blockchain-based federated learning framework is provided. The federated algorithm, FedProx, aggregates the fixed weights from each hospital's model within the blockchain framework. Each model is trained on the hospital's private data and dynamically adjusted throughout the training process while interacting with the blockchain's shared trust mechanism.

### 3.2. Federated learning for model broadcasting

First, we present the algorithm for training both local and global models. Algorithm 1 displays the pseudocode for training the \(i_{th}\) local model using its dataset, which operates independently on the local client's machine. The definitions of basic notations are presented in Table 1.

The federated learning algorithm is used to train our model for the distributed hospital dataset. The _H_ hospitals is collaborating to train a global model by using each hospital's private data without data leakage. Each hospital \(H_i\), \(i \in \{1, ..., n\}\), where _n_ represents the number of hospitals, has a local dataset _D<sub>i</sub>_ with _X<sub>i</sub>_ scheduled training sample per-trained model. The loss weight of the local model of each hospital, constrained on the model weights _w<sub>i</sub>_ calculated as

```
L(w, D) = \frac{\sum_{i=1}^n L_i (w_i, D_i)}{n}, \tag{6}
```

Multiple hospitals send blockchain ledger requests for the global trained model, and the blockchain nodes automatically adjust the number of hospitals that receive feedback at different times. The function that controls the _n_ requests is represented as follows:

```
n = \gamma C, \tag{7}
```

where _C_ shows the coefficient, and \(\gamma\) is the coefficient threshold. To this end, _n_ represents multiple hospitals that control the blockchain network (see Fig. 1).

Using the following formulae, this paper optimize the objective function by decreasing the value of the loss function for faster model convergence:

```
w^* = \min L(w) \tag{8}
```

To share the weight vectors among _H_ hospitals, we employ the secret _s_ sharing technique. In the first phase, it generates a _m_-1 polynomial degree, where \(\beta(0)\) is secret key to be shared. This ensures that each hospital does not generate its own random number \(B_1, B_2, ..., B_{m-1}\). The hospitals only need to send \(s_1 = \beta(1), s_2 = \beta(2), s_3 = \beta(n)\) to \(H_1, H_2, ..., H_n\). The _m_ and \(\beta(1), \beta(2)...\beta(n)\) can be solved together, _m_-1 is not a correct solution of _s_. Homomorphic encryption is introduced by Shamir to share the secret key [42]. Where \(\beta(d)\) is calculated as

```
\beta(d) = s + \beta_1 d + \beta_2 d^2 + \cdots + \beta_{m-1} d^{m-1} \mod p \tag{9}
```

To prevent access to each hospital's private dataset, we implement a dynamic secret key sharing scheme. The time component of the secret key is divided into multiple parts, with each fragmented part being updated at the outset. The instance at time _t_ of each hospital's snapshot of the distributed global model is recorded in the blockchain ledger \(s'_i\).

Federated learning aggregates the local model parameters trained by each hospital. In addition to aggregating the local model weights _w_, we employ both the stochastic gradient descent and batch gradient descent algorithms to optimize the loss function, ensuring the convergence of the global model. To prevent data leakage and enhance data security, a secret key sharing technique is implemented to mask the model parameters.

## 4. Blockchain based collaborative learning with effective latency

### 4.1. Collaborative learning

A deep learning model is used for the tumor segmentation task. Specifically, we utilized a convolutional neural network model to build the global model for collaborative learning on datasets from different clients. Since the medical data contains multiple class instances, we use the categorical cross-entropy loss function, which is calculated as follows:

```
L = - \sum_{r=1}^{class} z_r \log (T_r) , \tag{10}
```
