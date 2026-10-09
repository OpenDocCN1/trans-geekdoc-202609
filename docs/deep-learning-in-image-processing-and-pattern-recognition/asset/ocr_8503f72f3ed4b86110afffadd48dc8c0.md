In MobileNetV3 construction, deep Separable Convolution (Depth-wise Convolution) is used [17]. It is constituted of a tier of Depth-wise convolution and a tier of Point-wise convolution. Each tier of convolution is followed by batch normalization and ReLU activation function. The difference between deeply separable convolution and standard convolution is that the parameters and the computation are significantly reduced when the accuracy remains unchanged. For the contrast between depth-separable convolution and traditional convolution, see Figure A2 in Appendix A.

# 3. Methods

# 3.1. *Lightweight Network Structure with a Mixed Attention Mechanism*

SE module is introduced in MobileNetV3, and it is a kind of attention mechanism [18]. SE block is a sub-construction that can be embedded in other classification or detection models rather than a complete network construction.

# 3.1.1. Channel Domain Attention Mechanism

This attention mechanism is divided into three sections: Squeeze, Excitation, and Attention [19]. SE module construction see Figure A3 in Appendix A.

The squeeze function in the squeeze construction as in Equation (1) [19]:

$z_{C}=F_{sq}(u_{c})=\frac{1}{H \times W} \sum_{i=1}^{H} \sum_{j=1}^{W} u_{c}(i, j)$            (1)

where $u_{c}(i, j)$ represents the feature value of the $i$-th row and $j$-th column of the $c$-th channel in the feature map $u$; $H$ and $W$ denotes the length and width of the feature map severally; $z_{C}$ indicates the output of the $c$-th channel. The squeeze function shown in Equation (1) completes a global average operation, namely global average pooling.

The excitation function in the excitation construction as in Equation (2) [19]:

$s_{c}=F_{ex}(z_{c}, W)=\sigma(g(z_{c}, W))=\sigma(W_{2} \frac{1}{1+e^{-W_{1} z_{c}}})$            (2)

where $z_{C}$ is the squeezing function shown in Equation (1). $\sigma$ is the ReLU function; the dimensions of $W_{1}$ and $W_{2}$ are $C / r \cdot C$ and $C \cdot C / r$, where $r$ is a scaling parameter. The purpose of introducing parameter $r$ is to decrease the number of accesses, thus decreasing the total computation; $r$ is set to 16 in this paper. By training and learning the weight values of $W_{1}$ and $W_{2}$, a one-dimensional weight $s_{C}$ is acquired to activate each tier channels which is shown in Equation (2). The final output $\widetilde{X_{c}}$ of the block is obtained by the scale function as in Equation (3) [19]:

$X_{c}=F_{scale}(u_{c}, s_{c})=s_{c} \cdot u_{c}$            (3)

where $s_{c}$ is the output of the $c$-th feature map of the excitation function, and $u_{c}$ is the output feature value of the $c$-th channel of the feature map. As shown in Equation (3), by multiplying the eigenvalues of disparate channels with disparate weights, the key access weight is large and the non-key channel weight is small, which can enhance the attention to the key channel domain.

# 3.1.2. Spatial Domain Attention Mechanism

Another kind of attention mechanism is the attention mechanism of the space domain, and its construction (see Figure A4 in Appendix A). According to the feature graph obtained from the former processing, the maximum value is globally pooled on the channel, and the average value is globally pooled on the dimension. Then, the feature information of different locations in the feature graph is compared and extracted, and the weight of each location is acquired. The output $O(i, j)$ at the aftermath of the maximum global pooling as in Equation (4) [18]:

$O(i, j)=\max (I_{m}(i, j)), m \in(1, C)$            (4)