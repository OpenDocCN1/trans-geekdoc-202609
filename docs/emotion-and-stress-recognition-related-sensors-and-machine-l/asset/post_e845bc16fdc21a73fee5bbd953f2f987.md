
motion history at that specific point. A MHI $H_{\tau}$ is computed using an update function $\Psi(x, y, t)$, and is defined as follows,

```
$H_{\tau}(x, y, t) = \begin{cases} \text{if } \Psi(x, y, t) = 1 & \max(0, H_{\tau}(x, y, t-1) - \delta) \\ \text{otherwise} & \end{cases}$
```

where $(x, y)$ represents the pixel's location, $t$ the temporal extent of the observed motion (a length of a sequence of images); $\Psi(x, y, t)$ is 1 of motion at the location $(x, y)$ and at the time $t$; and $\delta$ represents a decay parameter. The update function is defined as follows,

```
$\Psi(x, y, t) = \begin{cases} 1 & \text{if } D(x, y, t) \geq \zeta \\ \text{otherwise} & \end{cases}$
```

where $\zeta$ is a threshold; $D(x, y, t)$ represents the absolute value of pixel intensity values of consecutive frames and is defined as follows,

```
$D(x, y, t) = |I(x, y, t) - I(x, y, t \pm \Delta t)|$
```

where $I(x, y, t)$ represents the pixel intensity at the location $(x, y)$ and at the time $t$; $\Delta t$ represents the temporal distance between the frames.

Therefore, the computation of a MHI consists of first performing image difference $[49]$ on a specific, preceding frame of movement (depending on the value assigned to the threshold $\zeta$ based on Equation (2)). Equation (1) is used to assign pixel values to the MHI. If a motion has been detected at the location $(x, y)$ of the $t$th frame, a pixel value of $t$ is assigned to that location. Otherwise, the previous value of location is reduced by $\delta$, thereby indicating the temporal occurrence of the motion at that specific location, and the actual time $t$. This process is conducted iteratively until the entire sequence of images has been processed. History of motion is encoded into the resulting MHI. Therefore, a sequence of images is encoded into a single MHI. However, in the current work, a sequence of MHIs is generated from each single sequence by saving each MHI generated at each single step of the iterative process described earlier. The resulting sequence of images is used as input for the deep neural networks. A depiction of such a sequence can be seen in Figure 1b, with the corresponding sequence of greyscale images depicted in Figure 1a.

![](img/601340ca744b738277eef45ff127492a_24_0.png)

![](img/601340ca744b738277eef45ff127492a_24_1.png)

![](img/601340ca744b738277eef45ff127492a_24_2.png)

**Figure 1.** Data preprocessing. Following the detection, alignment, normalisation and extraction of the facial area in each frame of a video sequence, the images are converted into greyscale. MHI and OFI sequences are subsequently generated.

## 3.2. Optical Flow (OFI)

Optical flow refers to the apparent motion of visual features (e.g., corners, edges, textures and pixels) in sequence of images. It is characterised by a set of vectors (optical flow vectors) defined at each location (x,y) of an entire image (dense optical flow [50,51]), or at specific locations of a predefined set of visual features (sparse optical flow [2,52]). The orientation of an optical flow vector depicts the direction of the apparent motion, whereas the magnitude of an optical flow vector depicts the velocity of the apparent motion of the corresponding visual feature in frames. The OFI provides a compact description of the motion, direction and velocity of specific motion occurring in consecutive frames. The estimation of the optical flow is based on the brightness constancy assumption, which stipulates that pixel intensities are constant between consecutive frames. If $I(x,y,t)$ is the pixel intensity at the location (x,y) and at the time $t$, the brightness constancy assumption can be formulated as,

```
$I(x,y,t) = I(x+\delta x, y+\delta y, t+\delta t)$
```

where $(\delta x, \delta y, \delta t)$ represents a small motion. By applying a first-order Taylor expansion, $I(x+\delta x, y+\delta y, t+\delta t)$ can be written as,

```
$I(x+\delta x, y+\delta y, t+\delta t) \approx I(x,y,t) + \frac{\partial I}{\partial x}\delta x + \frac{\partial I}{\partial y}\delta y + \frac{\partial I}{\partial t}\delta t$.
```

Thus,

```
$$\frac{\partial I}{\partial x}\delta x + \frac{\partial I}{\partial y}\delta y + \frac{\partial I}{\partial t}\delta t \approx 0$$
```

and by dividing by $\delta t$, the optical flow constraint equation can be written as,

```
$$\frac{\partial I}{\partial x}\frac{\delta x}{\delta t} + \frac{\partial I}{\partial y}\frac{\delta y}{\delta t} + \frac{\partial I}{\partial t} \approx 0$$
```

Resolving the optical flow constraint equation (Equation (7)) consists of the estimation of both $u = \frac{\delta x}{\delta t}$ and $v = \frac{\delta y}{\delta t}$. Several methods have been proposed to perform this task. The authors in [53,54] propose an approach of such techniques. In the current work, dense optical flow is applied, using the method of Farnebäck [50], to compute OFIs from consecutive greyscale images. A depiction of such a sequence of images can be seen in Figure 1 (both direction and motion encoded).

## Architecture

As opposed to, the motion of a video sequence is integrated into both MHIs and OFIs, providing more valuable information for facial expressions analysis. Therefore, the proposed architecture consists of a multi-view neural network [55] with OFIs and MHIs as input. An overall illustration of the two-stream neural network can be seen in Figure 2. In a nutshell, an attention mechanism specific to each input channel (OFIs and MHIs) first generates a weighted representation ($h_j^{ofi}$ and $h_j^{mhi}$). The generated representation is subsequently fed into a channel specific model (which in this case is a MLP). Learning probabilities of each channel ($score^{ofi}$ and $score^{mhi}$) are further fed into an aggregation layer with a linear output, where weighted aggregation of provided scores is performed as follows,

```
$score_j = a_{ofi} \cdot score_j^{ofi} + a_{mhi} \cdot score_j^{mhi}$
```

with the constraint
```
$a_{ofi} + a_{mhi} = 1.$ (9)
```

The entire architecture is trained in end-to-end model using the following loss function,

```
$\mathcal{L} = \lambda_{oft} L_{oft} + \lambda_{mhi} L_{mhi} + \lambda_{agg} L_{agg}$ (10)
```

where loss functions of each input channel and the aggregation layer are respectively depicted by $L_{oft}$ and $L_{agg}$. The parameters $\lambda_{oft}$, $\lambda_{mhi}$ and $\lambda_{agg}$ correspond to regularization parameters of each loss function. Once the network has trained, unseen samples are classified based on the output of the aggregation layer.

![](img/601340ca744b738277eef45ff127492a_26_0.png)

**Figure 2.** Two-Stream Attention Network with Weighted Aggregation.

The attention network (see Figure 3) consists of a CNN coupled to a LSTM module [47]. The CNN consists of a time distributed feature embedding network which takes a single input image $image_{i,j}$ as input and produces a fixed-dimension feature representation $X_{k,j}$ specific to that image. Therefore, the output of the $j$-th input sequence of features $\{x_{k,j}\}_{j=1}^T$ consists of a set of features $\{X_{k,j}\}_{j=1}^T$. The temporal component of the sequence of features is further integrated using a LSTM layer. A BiLSTM [58] RNN is an ensemble of regular LSTM [40], to enable the use of context in both forward and backward directions. It consists of LSTM layers, processing the input sequence $\{X_{k,1}, X_{k,2}, ..., X_{k,T}\}$ sequentially forward (from $X_{k,1}$ to $X_{k,T}$) and the second sequence sequentially backward (from $X_{k,T}$ to $X_{k,1}$). A LSTM RNN is capable of learning long-term dependencies in data, while avoiding the vanishing gradient problem of RNNs [57]. This is achieved through the use of cells (see Figure 4), which regulate the amount of information flowing through a LSTM network throughout the use of three principal gates: forget gate ($f_t$), input gate ($i_t$) and output gate ($o_t$). The cell output $h_t$ (at each time step $t$) is computed, given a specific input $x_t$, the previous hidden state $h_{t-1}$, and as follows,

```
$f_t = \sigma(W_f x_t + U_f h_{t-1} + b_f)$ (11)
```

```
$i_t = \sigma(W_i x_t + U_i h_{t-1} + b_i)$ (12)
```

```
$\tilde{C}_t = \tanh(W_c x_t + U_c h_{t-1} + b_c)$ (13)
```

```
$C_t = f_t \odot C_{t-1} + i_t \odot \tilde{C}_t$ (14)
```

```
$o_t = \sigma(W_o x_t + U_o h_{t-1} + b_o)$ (15)
```

```
$h_t = o_t \odot \tanh(C_t)$ (16)
```

where $\sigma$ represents the sigmoid activation function $\sigma(x) = (1 + \exp(-x))^{-1}$ and tanh represents the hyperbolic tangent activation function. The element-wise multiplication operator is represented by the symbol $\odot$. The weight matrices for the input $x_t$ are represented by $W_i, W_f, W_o$ and $W_c$ for the input gate, forget gate, output gate and cell state, respectively. Analogously, the weight matrices for the previous
