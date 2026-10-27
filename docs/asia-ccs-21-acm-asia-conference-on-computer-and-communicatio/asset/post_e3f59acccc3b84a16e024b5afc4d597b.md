
![](img/0d980298d6e695afbf52eecaa73818c4_4_0.png)

**Figure 1: Overview of Eth2Vec**

The PV-DM model is initially designed for text data that is sequentially laid out while it can also be used for analysis of assembly code by extending vector representation of language [11].

In this paper, we present a contract-wide representation learning model by extending the PV-DM model in accordance the syntax of EVM bytecode as described in Section 4.4.

### 4.3.2 EVM Extractor.

EVM Extractor is a module that syntactically analyzes EVM bytecodes for PV-DM model. In particular, EVM Extractor parses Solidity files as in the following hierarchical structure:

```
data: dictionary
  name: file name
  md5: md5 hash
  functions: list
    name: function name
    sea: start point
    see: end point
    id: function id
    call: list of callee functions
    blocks: list
      name: block name
      bytes: bytecodes
      sea: start point
      eea: end point
      id: block id
      call: list of callee blocks
      src: assembly instructions
```

The top-level, data, represents a contract file to be analyzed. The second level indicates file-dependent information. The third level indicates function-dependent information. The fourth level indicates a block consisting of multiple instructions. In each level, sea means the start address of the current function and that of the current block. Likewise, see and eea mean the start address of the next function and that of the next block, respectively. In contrast, call represents a callee function (or a callee block) from the current function (or block). Finally, at the bottom level, instructions of EVM bytecodes are stored in src together with their addresses. Meanwhile, a library function is treated as an individual function.

## 4.4 Design of Objective Function

Eth2Vec is a model that learns and infers codes of Ethereum smart contracts through unsupervised learning. Intuitively, it can be regarded as an extension of Word2Vec with a wider vector representation of codes given its ability to target Ethereum smart contracts.

The objective function of Eth2Vec is designed by extending that of the original PV-DM model described in Equation (1) along with the syntax shown in Section 4.3.2. The following argument is inspired by Asm2Vec [11], which is an extension of the PV-DM model for an assembly language. Given a file of an Ethereum smart contract to be analyzed, Eth2Vec vectorizes the codes for instruction-level and then computes the code similarity to the learned codes by the training. The process above is executed for block-level related to the instructions, function-level, and contract-level recursively, and therefore Eth2Vec can detect codes with distribution similar to that of the training data. Formally, an objective function is defined as follows:

$$\sum_{C_i}^{Dict} \sum_{f_s}^{U(C_i)} \sum_{seq_i}^{S(f_s)} \sum_{in_j}^{I(seq_i)} \sum_{t_c}^{T(in_j)} \log P(t_c | C_i, in_{j-1}, in_{j+1}), \tag{2}$$

where we denote by Dict a contract file, by C_i a contract, by f_s a function, by seq_i a block consisting of multiple instructions, by in_j each instruction, and by t_c a token with respect to the current instruction. Likewise, we denote by U(C_i) multiple functions, by S(f_s) multiple blocks, by I(seq_i) a list of instructions, and by T(in_j) a list of tokens.

Here, the first summation term, i.e., ∑_{C_i}^{Dict}, is included in the second level shown in the previous section, i.e., file name. Equation (2) is given contracts and their instructions, and then it maximizes the log probability for the current token t_c. Intuitively, the lexical meaning for each contract is computed through the current instruction and its neighbor instructions. Moreover, codes consisting of multiple contracts can also be analyzed by extracting features for each contract.

We describe the objective function to represent the aforementioned intuition in detail below. Given a contract file Dict, a function f_s for each contract C_i is vectorized and then we denote by \vec{\theta}_{f_s} the vector representation of f_s. Furthermore, we denote by \mathcal{CT}(in) the average of the vector representation of neighbor instructions of in. We then define a concatenation of the vector representation of the instruction itself and that of its operands as follows:

$$\mathcal{CT}(in)=\vec{v}_{\mathcal{P}(in)}\Vert\frac{1}{|\mathcal{A}(in)|}\sum_{t\in\mathcal{A}(in)}\vec{v}_t. \tag{3}$$

where \mathcal{P}(in) is one operation with respect to in, \mathcal{A}(in) is a list of operands with respect to in, and \Vert is a concatenation of strings. In doing so, for any contract C_i, by averaging f_s and the j-th instruction in in_j (with j\in\{1,\ldots,n\}), a function \delta(in_j,f_s) to evaluate the joint memory of neighbor instructions in f_s is defined as follows:

$$\delta(in_j,f_s)=\frac{1}{3}\left(\vec{\theta}_{f_s}+\mathcal{CT}(in_{j-1})+\mathcal{CT}(in_{j+1})\right). \tag{4}$$

Therefore, the log probability in Equation (2) can be replaced with P(t_c\mid C_i,in_{j-1},in_{j+1})=P(t_c\mid\delta(in_j,f_s)). According to the literature [11], by letting X=(\vec{v}_{t_c})^T\times\delta(in_j,f_s) and utilizing a sigmoid function \sigma(X)=\frac{1}{1+e^{-X}}, the above computation can be approximated by the k-negative sampling [22, 30] as follows:

$$\sum_{C_i\in Dict}\sum_{f_s}\sum_{seq_i}\sum_{in_j}\sum_{t_c}J(\theta) = \sum_{C_i\in Dict}\sum_{f_s}\sum_{seq_i}\sum_{in_j}\sum_{t_c}\log P(t_c\mid\delta(in_j,f_s)). \tag{5}$$

$$J(\theta)\approx\log(\sigma(X))+\sum_{i=1}^{k}\mathbb{E}_{t_d\sim P_n(t_c)}\left([\![t_d\ne t_c]\!]\log\sigma(X)\right). \tag{6}$$

where [\![t_d\ne t_c]\!] is an identity function which returns 1 if the expression inside the function is true or 0 otherwise. On the other hand, \mathbb{E}_{t_d\sim P_n(t_c)} is a sampling function that samples a token t_d in accordance with the noise distribution P_n(t_c) from t_c. We finally utilize Equation (6) as the objective function of Eth2Vec. Intuitively, the function maximizes the probability of a token t_c of the current instruction and decreases that of a token t_d of the other instructions. Then, we can compute the gradient with respect to \theta_{f_s} through the following derivative:

$$\frac{\partial J(\theta)}{\partial\theta_{f_s}}=\frac{\partial J(\theta)}{\partial X}\frac{\partial X}{\partial\theta_{f_s}}=\frac{\vec{v}_{t_c}}{3}(1-\sigma(X)) + \frac{\vec{v}_{t_c}}{3}\sum_{i=1}^{k}\mathbb{E}_{t_d\sim P_n(t_c)}\left([\![t_d\ne t_c]\!](1-\sigma(X))\right).$$

Moreover, we can also utilize a more intuitive gradient by approximating the aforementioned gradient computation as follows:

$$\frac{\partial J(\theta)}{\partial\theta_{f_s}}\approx\frac{\vec{v}_{t_c}}{3}\sum_i^k\mathbb{E}_{t\sim P_n(t_c)}\left([\![t=t_c]\!]-\sigma(X)\right). \tag{7}$$

Intuitively, Equation (7) approximates the original derivative described above in a manner that it moves a gradient to the positive if a token is identical to the current instruction or to the negative otherwise. Likewise, the gradient with respect to the vector representation \vec{v}_{t_c} of a token on the current instruction can be approximated. Moreover, for the vector representation \vec{v}_{\mathcal{P}(in)} of a token of some operation \mathcal{P}(in) and that \vec{v}_{\mathcal{A}(in)} of operands on the current instruction, their gradients can be approximated in a similar manner. These gradients are computed as follows although we omit their derivation:

$$\frac{\partial J(\theta)}{\partial\vec{v}_{t_c}}\approx([\![t=t_c]\!]-\sigma(X))\cdot\delta(in_j,f_s). \tag{8}$$

$$\frac{\partial J(\theta)}{\partial\vec{v}_{\mathcal{P}(in_j)}}\approx([\![t=t_c]\!]-\sigma(X))\cdot\frac{1}{|\mathcal{A}(in)|}\sum_{t\in\mathcal{A}(in)}\vec{v}_t. \tag{9}$$

$$\frac{\partial J(\theta)}{\partial\vec{v}_{\mathcal{A}(in_{j+1})}}\approx([\![t=t_c]\!]-\sigma(X))\cdot\left(\vec{v}_{\mathcal{P}(in_{j+1})}\right). \tag{10}$$

Similar equations hold for the previous instruction in_{j-1} by replacing in_{j+1} with in_{j-1} although we omit the details due to space limitation.

## 4.5 Training and Inference

We now present the training algorithm and the inference algorithm with the gradients described in the previous subsection. First, the training algorithm is shown in Algorithm 1. The goal of the training is to optimize vectors for each instruction belonging to the given contract file as input. Instructions with similar meaning are mapped to a similar position in the vector space through the training. These resulting vectors by the algorithm can be used as features for vector representation of contract-level analysis. The algorithm is an unsupervised training algorithm, and thus the procedure does not require a ground-truth mapping between equivalent contracts.

The aforementioned features can be utilized directly in the inference algorithm shown in Algorithm 2. In particular, for an unseen contract C_t\notin Dict, the algorithm first initializes \vec{\theta}_{f_t}, which is associated with any function f_t belonging to C_t. Then, the algorithm follows the same procedure as the training algorithm. However, all \vec{v}_t's in the trained model are kept, and \vec{\theta}_{f_t}'s are updated following their errors. At the end of the inference, \vec{\theta}_{f_t} is output whereas the vectors for all C_i\in Dict remain the same except for \vec{\theta}_{f_t}. Finally, to search contracts for a match with the given contract C_t, the resultant vectors are compared with those of the training contracts using a typical statistical method, e.g., the cosine similarity.
