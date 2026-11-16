

The technique of wavelet transforms as adapted in the literature is a filtering continuous application of high-pass and low-pass filters to extract the wavelets of the signal which, when added together, constitute the original signal and downsampled by a factor of 2 as shown in Figure 5.

![](img/1752b062af2760b8561f6faaf183b3d0_293_0.png)

Figure 5. Wavelet transform.

g and h are consecutive high-pass and low-pass filters which produce the relevant detailed and approximated coefficients of the EEG signals [5].

## Neural Networks

Before starting to explain what deep learning is, it is first beneficial to explain the role of deep learning and its fundamental blocks.

Deep learning is a classification tool used in a variety of daily applications which is composed of speech recognition and computer vision to natural language processing in the context of the BCI; the input features which are different brain frequency bands are classified according to what activity the user is performing at the moment.

Neural Network. A neural network is a model similar to that of a neuron in our brain that has input nodes and output nodes; the mathematical model for a neural network is given by the following equation:

```
v = wx + b, (2)
```

where v is the weighted sum of the inputs and the bias term which will be fed at the output node, b is a bias term which is mostly set to 1, and w is the random weights assigned that are multiplied with the input in order to reach closer to the desired output.

The neural network is shown in Figure 6.

![](img/1752b062af2760b8561f6faaf183b3d0_294_0.png)

Figure 6. Neural network.

These calculations are often presented in the form of matrices; the input, the weight terms, the output, and the bias are as follows:

$v = (w_1 \times x_1) + (w_2 \times x_2) + (w_3 \times x_3) + b.$ (3)

Finally, the output node is passed to an activation function and provides the final output; the activation function calculates the characteristic of the node. The activation function acts to map the corresponding inputs to the right output $y$ present at the output node:

$y = \varphi(v).$ (4)

The neural network does not get its right output at the first attempt. It needs to be trained a lot, and so a training rule is assigned to neural networks to get the right output. Many training rules are adapted, but one of the most commonly used is the delta rule, and the rule is expressed using the following equation:

$w_{ij} \longleftarrow w_{ij} + \alpha e_i x_j.$ (5)

where $x_j$ represents the number of inputs, $e_i$ is the error generated at the output node, and $\alpha$ is the learning rule between $(0 < \alpha < 1)$.

The training rule is summarized as follows:

- (1) Assign adequate values to the weights.
- (2) Obtain the input from the training data and feed it into the neural network which will give an output $d$; subtract the output $d$ to obtain the correct output at the output node.

$e_i = d_i - y_i.$ (6)

- (3) Calculate the weight updates:

$\Delta w_{ij} = \alpha e_i x_j.$ (7)

- (4) Adjust the weights accordingly until the correct output or that has small tolerance is obtained:

$w_{ij} \longleftarrow w_{ij} + \Delta w_{ij}$ (8)

The above explanation was presented for a single-layer neural network; the architecture of neural networks is becoming better with the cost of greater memory, but with higher classification accuracy, we use deep neural networks which are the same as the single-layer neural network but with hidden layers added in between the input and output nodes, as shown in Figure 7.

![](img/1752b062af2760b8561f6faaf183b3d0_295_0.png)

Figure 7. Structure of the deep neural network.

The concepts are similar to those of a single neural network but with the adjustments of added hidden layers and a different training rule because the delta rule has a drawback of not propagating the output to the hidden layers, thereby the weights are not adjusted.

To explain how the deep neural network works, the above explained single neural network is set as basis.

In Figure 8, given a multiple-layered neural network, the weighted sum obtained at the first hidden layer is presented as

\[ \begin{bmatrix} y_1^{(1)} \\ y_2^{(1)} \end{bmatrix} = \begin{bmatrix} w_{11}^{(1)} & w_{12}^{(1)} \\ w_{21}^{(1)} & w_{22}^{(1)} \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} \quad \triangleq W_1 x . \]

![](img/1752b062af2760b8561f6faaf183b3d0_296_0.png)

Figure 8. Multilayered network.

The outputs are calculated via the sigmoid activation function:

\[ \begin{bmatrix} y_1^{(1)} \\ y_2^{(1)} \end{bmatrix} = \begin{bmatrix} \phi(v_1^{(1)}) \\ \phi(v_2^{(1)}) \end{bmatrix} . \]

The process is repeated, and the outputs obtained are treated as the inputs to the other nodes, and we get the outputs as

\[ \begin{bmatrix} v_1^{(1)} \\ v_2^{(1)} \end{bmatrix} = \begin{bmatrix} w_{11}^{(1)} & w_{12}^{(1)} \\ w_{21}^{(1)} & w_{22}^{(1)} \end{bmatrix} \begin{bmatrix} y_1^{(1)} \\ y_2^{(1)} \end{bmatrix} \triangleq W_1 y^{(1)} . \]

And lastly, the weighted sum is being inserted into the activation function, and we return our final output: Deep learning training rule is given in the following.

\[ \begin{bmatrix} y_1 \\ y_2 \end{bmatrix} = \begin{bmatrix} \phi(v_1) \\ \phi(v_2) \end{bmatrix} . \]

Backpropagation algorithm is commonly used as the training instruction for the deep neural networks; the procedure is summarized as follows:

- (1) Assign adequate values to the weights.
- (2) Take the input from the training data and feed it into the neural network which will give an output d. Subtract the output d to obtain the correct output at the output node and the delta (\(\delta\)) of the output nodes:

  \(e = d - y\),
  \(\delta = \varphi' (v)e.\)

- (3) Propagate the delta back towards the hidden nodes, and determine respective delta \(\delta\) of nodes:

  \(e^k = W^T \delta\),
  \(\delta^{(k)} = \varphi' (v^{(k)})e^{(k)}.\)

- (4) Repeat until it reaches the input nodes.
- (5) Modify the weights according to the rule:

  \(\Delta w_{ij} = \alpha \delta_i x_j\),
  \(w_{ij} \longleftarrow w_{ij} + \Delta w_{ij}.\)

- (6) These steps are repeated until the neural network is utterly trained as shown in Figure 6.

Now, the alpha-beta ranges are extracted, and consecutive energies are calculated. The features are fed into the deep learning neural network, and using the backpropagation learning rule, the model is trained, yielding an accuracy of 97.83%, as shown in Figure 9 [5].

![](img/1752b062af2760b8561f6faaf183b3d0_297_0.png)

Figure 9. General diagram of neural networks in the BCI.

## CRITICAL REVIEW OF THE RELATED LITERATURE

A brain-computer interface involves various stages, and development in each stage leads to an improved and efficient system. Here, the literature review of major steps including data acquisition, feature extraction, classification algorithm, and applications is presented.

(1) Improvement of EEG signal acquisition: An electrical aspect for state of the art of front end. Computational intelligence and neuroscience: a research paper published by Ali Bulent Usakli, the NCO Academy, Turkey, presented some applicable concerns for acquiring quality EEG signals which are proven helpful for users and design engineers. One of the most important considerations is selecting suitable electrodes and headset. In the EEG-based BCI, electrodes, signal processing components including mental and environmental conditions, filtration of noise, amplification, signal translation, and data storage affect the recording process. The data acquisition is an important step in any machine learning procedure. Brain signals need to be cleaned and preprocessed so that a good result can be obtained [1].

(2) P300 wave detection using Emotiv Epoc+ headset: effects of matrix size, flash duration, and colors: Saleh Ibrahim Alzahrani conducted research on P300 wave detection using the Emotive Epoc+ headset to study the effects of the size of the matrix, flash duration, and colors. In this study, P300 signals were obtained from five subjects with Emotive EPOC+ using all 14 channels. For this research, EEG signals obtained were communicated to software OpenViBE through a USB dongle. A sample was taken every 8 seconds at a rate of 128 samples per second. The configured sampling rate provides ample samples for the four frequency bands, containing significant ERP data. During process of signal recording, the subjects were shown a matrix of 6×6 or 3×3 on the computer screen. They were instructed to stay calm, avoid any needless movement, and set all on letter which they desire to spell. It is reported in the study that one of the advantages of using the Emotiv EPOC+ headset is that it takes merely two to three minutes for preparation as compared to other headsets that take more than ten minutes. The quality of sensors is verified through Emotiv Xavier SDK which provides feedback report of each sensor. To decrease the contact impedance, saline liquid was applied to the sensor surface. Primary objective was to assess the potential of Emotiv EPOC+ to perceive P300 signals. Finding the electrodes proficient at providing target signals helps minimize the number of channels which makes signal processing a lot easier. The results of this experiment provide evidence of the capability of Emotiv EPOC+ to detect the P300 signals from two channels, O1 and O2
