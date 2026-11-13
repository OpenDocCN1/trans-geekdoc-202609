
where class defined the number of categories of the data, $z_i$ represents an instance, and $T_{l_i}$ is the predicted probability. However, $l$ indicates an observation of classes. $z_i$ could be 0 or 1 depending on the classes of data. If the same class, then 0 otherwise 1.

Each hospital requests the global model from the blockchain network and then uses its associated local data and local model instance. The deep learning model uses the stochastic gradient descent where the gradient of the model is $g_i$ and the weight is $w_i$ under the specified data. The federated learning model aggregates the weights of each local hospital model and updates the local model without leaking the privacy of data.

The proposed model is categorized into three parts (i) model training, (ii) model data sharing and, (iii) model masking and uploading.

- 1. **Model training**: Every hospital uses the same model to train a global model employing the CNN neural network. However, to save time and memory resources, we do not train the neural network model from scratch. To reduce communication overhead, gradients are not uploaded directly to the blockchain. Instead, hospitals share their gradients, which are then aggregated to further train the latest model weights $w_i$. Moreover, the training process is divided into two parts. In the first part, each hospital shares its model information. The blockchain then verifies the hospital's model based on data quality. In the second stage, the federated learning averaging algorithm aggregates the weights, and the updated weights are subsequently sent to the local models.

- 2. **Model sharing**: To improve the quality of the model for every single hospital, multiple hospitals share their models in the blockchain network to enhance the model quality. However, hospitals share the model with differential privacy to achieve a secure way of sharing the models among hospitals. Assuming that two similar datasets D and $\hat{D}$ are used, which differs by one single data instance, the mapping function $f : f(D) = (z_1, z_2, ..., z_d)^T$, where $D \rightarrow R^d$ is used to show the relationship between vector-space and dataset. Adding noise to secure the dataset, we use Laplace function $Laplace(\frac{\Delta f}{\epsilon})$, where the output function $f$ defined as $A(D)$ below: $A(D) = f(D) + \left( Laplace_1(\frac{\Delta f}{\epsilon}) \cdot Laplace_2(\frac{\Delta f}{\epsilon}) \right)$ (11) where $\Delta f$ is defined as follows $\Delta f = \max_{D,D'} \| f(D) - f(D') \|_c,$ (12) where $\Delta f$ confirm both parties and $c$ is taken as 1 $P_r[A(D) = O] \le e^\epsilon * P_r [ A ( D' ) = O ]$ (13)

Algorithm 1 shows the privacy preserved model, where the hospital add the mask in the dataset; then blockchain nodes update the hospital model based on its weights. The blockchain network adds the mask noise to the model where $t$ represents time slot, and the mask defined as $\{\vec{g^i_1}, \vec{g^i_2}, ..., \vec{g^i_n}\}$. For each hospital, the convergence function for the updated weights is to map $\{\vec{g^i_1}, \vec{g^i_2}, ..., \vec{g^i_n}\}$ to $\{w^i_1, w^i_2, ..., w^i_j, ..., w^i_n\}$. However, each dataset and other weights received from other hospitals are represented below:

$$\vec{g^i_r} \leftarrow \frac{1}{n} \sum_{j=1}^n \left( \vec{g^i_j}(d_i) + Laplace\left( \frac{\Delta f}{\epsilon} \right) \right)$$ (14)

Based on the local model accuracy, the blockchain network can deny the uploading weights from local models with low accuracy. In this way, the global model aggregates weights of models with the best accuracies for a better model. The global model will not accept low accuracy models or malicious models, which affect the performance of the global model.

```
**Algorithm 2: Asynchronous Privacy Preserved Federated Learning**
Input: local dataset $d_i$, hospitals $H$ ;
Output: Global Model $M$
for each hospital $h_i \in [H]$ do
  for $t \in [timeslot]$ do
    if t=1 then
      Train a new model based on local models dataset $d_i \subset D$;
      Calculate the noise using the $\vec{g^i_r} \leftarrow \frac{1}{n} \sum_{j=1}^n \left( \vec{g^i_j} (d_i) + Laplace \left( \frac{\Delta f}{\epsilon} \right) \right)$ ;
      Broadcast the masked model to the network;
    else
      Collect all uploaded model from other hospitals ;
      Aggregate the local models and train the final model using Eqn. 5 and Eqn. 17 ;
      $m_i(t) = m_i(t-1) + \frac{1}{N} \sum_1^N \gamma \cdot S ( v_i ) \cdot w_i(t)$;
      Add the mask using the Gaussian mechanism $\vec{w^i_t} = w^i_t + s^i$ ;
      Broadcast the global model $M$
    end
  end
end
return M
```

- 3. **Model parameters masking and uploading**: Each hospital shares its model weights $\vec{w_i}$ with the secret mask. The privacy preservation scheme is shown in Algorithm 2. Hospitals $H_i$ updates the shards $s$ with respect to time $t$. Firstly, we select the random number $m-1$ with $\beta_{i1}, \beta_{i2}, ..., \beta_{i(m-1)} \in_R Z_p$. The polynomial function is represented as follows: $\beta_i(d) = \beta_{i1}d + \beta_{i2}d^2 + ... + \beta_{i(m-1)}d^{m-1},$ (15) where $H_i$ calculate the $q_{ij} = \beta_j$ and then send to other model $q_{ij}$. $q_{ij}$ is updated according to $s_i^{(t)} = s_i^{(t-1)} + (q_{i1} + q_{i2} + ... + q_{in}) j \in [1, ..., n] \& j \neq i$ (16)

- 4. **Store and aggregate the shared model in blockchain network**: After receiving the local model $m$, the gradients are aggregated together. Then, the final results of the updated model will be stored in the blockchain network. For efficient use of resources and reducing communication overhead of the blockchain network, we use IPFS to store the local model and hashes stored in the blockchain network. Furthermore, the unmapping of the mask of the final model is calculated as: $M = \sum_{q \in Q} \vec{w_i} + \sum_{q \in Q} \lambda_q s_q^{(t)} - s = \sum_{q \in Q} \vec{w_{iq}} + \sum_{q \in Q} \lambda_q \left( s_q^{(t-1)} + \sum_{h \in Q \setminus \{q\}} \beta_v(q) \right) - s = \sum_{q \in Q} \vec{w_i} + \sum_{q \in Q} \lambda_q s_q^{(t-1)} + \sum_{h \in Q \setminus \{q\}} \lambda_u \beta_v(q) - s = \sum_{q \in Q} \vec{w_{iq}} + s + \sum_{q \in Q} \beta_h(0) - s = \sum_{q \in Q} \vec{w_{iq}}.$ (17) The model averaging and aggregation process is described in algorithm 2.

```
Algorithm 3: Model Aggregation Process
var Accu=0;
for each hospital h ∈ H do
  Calculate model information of hospital ;
  Aggregate model w = ∑h∈H w h ;
  Train Model(w,Train-dataset);
  Compute Accu_h ;
  Accu = Accu + Accu_h ;
end
return M_h, Accu_h
```

## 4.2. Committee blockchain consensus mechanism for trust

Each hospital broadcasts the local model to the blockchain ledger and requested the global model. All local models are aggregated in the blockchain network. The following are the steps to calculate the trust on model:

- 1. It verifies the training of the local hospital model based on the other collected model.
- 2. Calculate the accuracy between the local model and other model set.
- 3. The accuracy of model is calculated as
  \(\rho_b^t = \left( 1 + \frac{\sum_{R \in R} (A_b - A_j)}{|B| - 1} \right)\)
- 4. The current or local hospital model can calculate the trust. It updates the model based on the historical trust value: It computed as \(S_{R_b}^t = \frac{1}{1 + e^{-\alpha(S_{R_b}^{t-1} - \rho_b^t)}}\)
- 5. After calculating trust, a reward will be given based on the accuracy of the model.

The calculation process of reward is as follows:

- 1. The blockchain verifies the trust value according to training models with higher accuracy. If the value verifies a certain threshold, the model is published; otherwise rejected.
- 2. The reward is 0 to 1, rewarding higher deviation rate models with increased trust while punishing lower deviation rate models with less trust.
- 3. The calculation process is calculated as :
  \(S'_{R_k^i} = \begin{cases} S'_{R_k^i} - \frac{\eta_i e^{A_i}}{\sum_{i=1}^n \eta_i e^{A_i}}, & 0 < \beta < 1 \\ S'_{R_k^i} + \frac{\eta_i e^{A_i}}{\sum_{i=1}^n \eta_i e^{A_i}}, & 1 \le \beta \end{cases}\)
- 4. Finally, we calculate the trust value evaluation as follows: max \(\left( S_{R_b} = [\max_{b \in B} S_{R_b}^k (\alpha, \rho_b^t)] \right)\)

The trustworthiness model ensures that messages are delivered on time and without error, facilitating effective communication between parties. Reliability is determined by comparing the number of transmitted packets with the number of packets confirmed as received. Additionally, we take into account the node selection process to enhance the model's reliability. The steps are as follows:

- 1. The initial position of a node is (x0, y0) with k = 1
- 2. Choose a speed sk from [smin, smax] for the destination position (xk, yk) within the network area; the node then moves at a constant speed sk between (x0, y0) and (xk, yk).
- 3. The node halt for a time (tRP) if the pause function is enabled, with the pausing time taken from a distribution with the density function (f p(t)).
- 4. Increase k+1 and go to step 2

## 5. Security analysis and performance analysis

### 5.1. Security analysis

By leveraging a permissioned blockchain architecture, a decentralized and secure framework is established for collaboration among various healthcare institutions. The integration of the blockchain consensus mechanism with federated learning techniques effectively mitigates concerns pertaining to trust, potential security vulnerabilities, and the confidentiality of sensitive patient information.

- 1. Ensuring Differential Privacy: To safeguard user privacy, our proposed protocol guarantees that the generated values are indistinguishable from randomly generated ones. A random vector is chosen to create the ciphertext wii, where K acts as a security parameter that ensures indistinguishability from random values. The polynomial \(\widetilde{w}_i\) is then used to compute Hi based on these random values.
- 2. Data Access: The proposed technique utilizes federated learning in conjunction with blockchain technology, with the primary goal of safeguarding data privacy. This model ensures data privacy by combining encryption techniques with blockchain, thereby guaranteeing the protection of the data.
- 3. Secure Aggregation of Model Weights: The blockchain and local model client collaborate to ensure the security of the weight aggregation process through the following steps:
  - (a) Initialization: To begin, the security algorithm is established to generate the necessary public parameters for the model.
  - (b) Encryption: Clients define the parameter pair (i, m), where i represents the entity's index and m denotes the plaintext message. The encrypted value Enc(i, m) is then returned to the model.
  - (c) Iterative Compromise: The model incorporates an i entity, and the aggregated model releases the secret keys SKc. This phase is iterated several times.
  - (d) Single Challenge: This step is permitted only once throughout the entire process. For each i ∈ K, two plaintext messages, m1 and m2, are generated and sent. If the bit equals 0, ci = Enc(mi) is computed. Otherwise, the encryption is performed in the same manner, and ci is sent.
  - (e) Final Prediction: The output of the process is either 1 or 0.
- 4. Eliminating the Need for Centralized Trust: By leveraging the decentralized nature of blockchain technology, hospitals can engage in collaborative efforts without relying on intermediaries or third-party trust.
- 5. Secure Data Management: Only a trusted data provider uploads data to the network to ensure the model's reliability. Moreover, the cryptography algorithm guarantees the security of the data.
- 6. Ensuring the Integrity of the Shared Model: The consensus mechanism employed by the system serves to validate the quality and reliability of the data used in the learning process, thereby safeguarding the integrity of the resulting model.

### 5.2. Dataset and experimental setting

Data Preparation: The BraTS 2020 dataset [43] includes multi-parametric MRI scans of subjects with brain tumors. Each subject underwent four different imaging modalities: (1) T1-weighted, (2) T1-weighted with contrast enhancement, (3) T2-weighted, and (4) T2 fluid-attenuated inversion recovery (T2-FLAIR). The scans for each subject are annotated at the voxel level with the following tumor labels:
