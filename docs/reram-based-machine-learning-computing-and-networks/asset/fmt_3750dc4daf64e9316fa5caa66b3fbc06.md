
10: Note: {For auto-encoder layers, `![image](images/ch04_si273.gif)` is the activation matrix `![image](images/ch04_si274.gif)` (`![image](images/ch04_si275.gif)`). For the decision layer, `![image](images/ch04_si276.gif)` is the label matrix `![image](images/ch04_si277.gif)`.

11: `end if`

12: `end for`

TNN is to develop high-dimensional weights and use tensor-train decomposition method to compress it. For example, a `![image](images/ch04_si278.gif)` fully connected layer can be expressed as a 4D `![image](images/ch04_si279.gif)` tensor. Therefore, instead of generating a random input weight `![image](images/ch04_si280.gif)`, we will generate a low rank tensor `![image](images/ch04_si281.gif)` by specifying the rank of each core `![image](images/ch04_si282.gif)`. Then the input weight can be generated as ([4.23](#Chapter4.html#c04_eqn23)) with each core `![image](images/ch04_si283.gif)` randomly generated.

As discussed in the general neural network, the training of TNN requires to solve an LS problem in the tensor-train data format. For the output weight `![image](images/ch04_si284.gif)` in ([4.29](#Chapter4.html#c04_eqn29)), we propose a tensor-train-based LS training method using MALS algorithm (also known as density matrix renormalization group in quantum dynamics) [203,204]. The MALS for minimization of `![image](images/ch04_si285.gif)` is working as follows.

For the output weight `![image](images/ch04_si286.gif)`, we have two potential solutions to achieve tensor-train data format. One straight way is to solve the general matrix LS problem and then reshape it to a high-dimensional tensor following iterative truncated support vector decomposition (SVD) algorithm [197]. This is similar to high-order SVD and performance degradation is significant with relatively small compression rate. Instead, we propose a tensor-train-based LS training method using MALS algorithm (also known as density matrix renormalization group in quantum dynamics) [203,204].

1.  **Initialization**: Randomly initialized cores `![image](images/ch04_si287.gif)` and set `![image](images/ch04_si288.gif)`. The process is the same as Steps 3, 4 in [Algorithm 4.3](#Chapter4.html#c04_stat3).

2.  **Sweep of cores**: Core `![image](images/ch04_si289.gif)` is optimized with other cores fixed. Left-to-right sweep from `![image](images/ch04_si290.gif)` to `![image](images/ch04_si291.gif)`.

3.  **Supercore generated**: Create supercore `![image](images/ch04_si292.gif)` and find it by minimizing the LS problem `![image](images/ch04_si293.gif)`, reshape `![image](images/ch04_si294.gif)` and `![image](images/ch04_si295.gif)` to fit matrix—matrix multiplication^([3](#Chapter4.html#ch04-03)).

4.  **Split supercore**: SVD `![image](images/ch04_si299.gif)`, let `![image](images/ch04_si300.gif)` and `![image](images/ch04_si301.gif)`. `![image](images/ch04_si302.gif)` is determined and `![image](images/ch04_si303.gif)` is updated. Truncated SVD can also be performed by removing smaller singular values to reduce ranks.

5.  **Sweep termination**: Terminate if maximum sweep times reached or error is smaller than required.

The low-rank initialization is very important to have smaller rank `![image](images/ch04_si304.gif)` for each core. Each supercore generation is the process of solving LS problems. The complexity of LS for `![image](images/ch04_si305.gif)` are `![image](images/ch04_si306.gif)` [204] and the SVD compression requires `![image](images/ch04_si307.gif)`, where `![image](images/ch04_si308.gif)`, `![image](images/ch04_si309.gif)` and `![image](images/ch04_si310.gif)` are the rank of activation matrix `![image](images/ch04_si311.gif)`, the maximum rank of core `![image](images/ch04_si312.gif)` and maximum mode size of `![image](images/ch04_si313.gif)`, respectively. By using truncated SVD, we can adaptively reduce the rank of each core to reduce the computation complexity and save memory storage.

Such tensorization can benefit from implementing large neural networks. First, by performing tensorization, the size of neural network can be compressed. Moreover, the computation load can also be reduced by adopting small tensor ranks. Second, a tensorization of weight matrix can decompose the big matrix into many small tensor-core matrices, which can effectively reduce the configuration time of ReRAM. Lastly, the multiplication of a small matrix can be performed in a highly parallel fashion on ReRAM to speed up the large neural network processing time.

[¹](#Chapter4.html#ch04_01) Interested readers can refer to [197,198] for more details on the tensor-train data format.

[²](#Chapter4.html#ch04_02) We ignore bias for a better illustration.

[³](#Chapter4.html#ch04_03) Details on `![image](images/ch04_si296.gif)` and `![image](images/ch04_si297.gif)` can be found in [203,204]. Since each core is 3D tensors, permuting to 2D matrix is required. Without abuse of notations, we use `![image](images/ch04_si298.gif)` to represent it.

## Chapter 5  

**XIMA: the in-ReRAM machine learning architecture**

### 5.1 ReRAM network-based ML operations

Among different hardware architectures, resistive random-access memory (ReRAM)-based architectures are seen to be one of the efficient architectures in terms of the area, power consumption and the computational latency. In this chapter, we will introduce two types of ReRAM neural networks with focus on intensive matrix multiplication operations. ReRAM-crossbar network can be used as matrix–vector multiplication accelerator and then to illustrate the detailed mapping. The coupled ReRAM oscillator network can be applied for low-power and high-throughput L2-norm calculation.

#### 5.1.1 ReRAM-crossbar network

This section describes the matrix–vector multiplication on the binary ReRAM crossbar. It is the most popular operation in various data-analytic applications such as compressive sensing and machine learning (ML). For example, the feature extraction can be achieved by multiplying Bernoulli matrix in [205].

Matrix multiplication can be denoted as `![image](images/ch05_stripin_si1.gif)`, where `![image](images/ch05_stripin_si2.gif)` and `![image](images/ch05_stripin_si3.gif)` are the multiplicand matrices, and `![image](images/ch05_stripin_si4.gif)` is the result matrix.

##### 5.1.1.1 Mapping of ReRAM crossbar for matrix–vector multiplication

In this section, hardware mapping of matrix multiplication on the ReRAM architecture is introduced. The logic required is a matrix–vector multiplier by the ReRAM crossbar. In general, one can utilize current merge on bitlines (BLs) to realize matrix–vector multiplication and then use an ReRAM-based flash analog–digital converter (ADC) for format conversion. Here, a three-step ReRAM-crossbar-based binary matrix–vector multiplier is presented, in which both the input and output of the ReRAM crossbar are binary data without the need of ADC. The three ReRAM-crossbar steps parallel digitizing, XOR and encoding are presented in details as follows. As the output of an ReRAM-crossbar array can be connected to the input of another ReRAM-crossbar array, one can utilize multiple ReRAM arrays in the logic block for the mappings. Here, the symbol `![image](images/ch05_stripin_si5.gif)` is used to denote the result of binary matrix–vector multiplication. As such, `![image](images/ch05_stripin_si6.gif)` follows

`![image](images/ch05_stripin_si165.gif)`

where `![image](images/ch05_stripin_si7.gif)` is the maximum result. To illustrate the three-step procedure more clearly, let us consider the following matrix–vector multiplication as an illustrative example:

`![image](images/ch05_stripin_si166.gif)`

The output after the three-step procedure will be shown, here `![image](images/ch05_stripin_si8.gif)` and `![image](images/ch05_stripin_si9.gif)`.

###### Parallel digitizing
