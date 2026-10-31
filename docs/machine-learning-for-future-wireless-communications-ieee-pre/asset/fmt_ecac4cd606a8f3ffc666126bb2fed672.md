
`RNNs` can also be trained using the method for `DNN`‐ and `CNN`‐based equalizers, described in [Sections 12.4.2](#c12.xhtml#c12-sec-0020) and [12.4.3](#c12.xhtml#c12-sec-0023), respectively. Furthermore, the `L2(·)` loss function and the stochastic gradient descent algorithm with forward/backward propagation can be adopted to obtain the appropriate network parameters.

In summary, with the aid of these neural networks, equalizers are able to extract the key features of wireless channels and reduce ISI adaptively and intelligently. Based on `MLP`, we can design `DNN`‐based equalizers having the capability to mitigate ISI, thanks to embedded multiple‐layered neural networks. Moreover, as shown in [Figure 12.11](#c12.xhtml#c12-fig-0011), the channel‐favorite properties of `RNN` and `CNN` facilitate equalizer design; owing to this, `RNNs` and `CNNs` have been widely used to combat ISI and achieve reliable communications. In the next section, we will present a range of simulation results to demonstrate the achievable performance of `NN`‐based equalizers in `OFDM` systems.

![Figure 12.10 Structure of an RNN: folded and unfolded computational graph.](images/c12f010.jpg)
[Figure 12.10](#c12.xhtml#R_c12-fig-0010) Structure of an RNN: folded and unfolded computational graph.

![Figure 12.11 System model for a RNN‐based equalizer.](images/c12f011.jpg)
[Figure 12.11](#c12.xhtml#R_c12-fig-0011) System model for a RNN‐based equalizer.

## 12.5 Performance of OFDM Systems With Neural Network‐Based Equalization

In this section, we investigate the performance of `OFDM` systems, which adopt DL techniques, including `CNN` and `DNN`, for channel equalization. Before providing the simulation performance, let us first describe the system model and network structure used for this performance investigation.

### 12.5.1 System Model and Network Structure

[Figure 12.12](#c12.xhtml#c12-fig-0012) illustrates the structure of an `OFDM` system with a `NN`‐based equalizer. The baseband `OFDM` system is identical to traditional ones (E. Dahiman and Skold, [2014](#c12.xhtml#c12-bib-0016)). At the transmitter side, the transmitted `QAM` modulated symbols associated with the pilots for channel estimation are first converted to a parallel data representation. After that, the inverse fast Fourier transform (`IFFT`) module converts the data from the frequency domain to the time domain. Then, a cyclic prefix (`CP`) is inserted in order to avoid inter‐block interference. Finally, after a parallel‐to serial conversion, the signals are transmitted over the channel, which is usually dispersive.

Let the discrete sample‐spaced multiple‐path channel be expressed as `{h(n)}`_{n=0}^{N-1}, where the complex random variable `h(n)` is the channel gain at instant `n`. Then the discrete received signal can be expressed as

(12.38) `y(n) = h(n) ⋆ x(n) + w(n) , n = 0,1,...`

![Figure 12.12 System model for OFDM with a DNN‐ or CNN‐based equalizer.](images/c12f012.jpg)
[Figure 12.12](#c12.xhtml#R_c12-fig-0012) System model for OFDM with a DNN‐ or CNN‐based equalizer.

where `⋆` denotes the circular convolution, `x(n)` is the transmitted time‐domain signal, and `w(n)` is the `AWGN`.

As shown in [Figure 12.12](#c12.xhtml#c12-fig-0012), at the receiver side, after the serial‐to‐parallel conversion and removing the cyclic prefix, the fast Fourier transform (`FFT`) converts the received signal from the time domain to the frequency domain. Hence, in the `OFDM` system considered, the `DNN`‐ or `CNN`‐based equalizer operates in the frequency domain. Finally, received information is recovered by demodulation based on the output of the equalizer, as seen in [Figure 12.12](#c12.xhtml#c12-fig-0012).

### 12.5.2 DNN and CNN Network Structure

For `OFDM` systems, [Figure 12.13](#c12.xhtml#c12-fig-0013) depicts the specific structure of the `DNN`, which consists of six layers, four of them being hidden layers marked as `ELU`. In our study, the numbers of neurons in each layer are set to 256, 600, 400, 300, 200, and 128, respectively. The number of the input to the network is the number of real parts and that of imaginary parts of an `OFDM` frame containing both a pilot block and a data block. In contrast, the number of outputs equals the number of real parts plus the number of the imaginary parts of the data symbols derived from the data block.

In our performance study, the exponential linear unit (`ELU`) function (Goodfellow et al., [2016](#c12.xhtml#c12-bib-0024)) is used as the activation function in all the layers other than the last layer. The `ELU` function is

(12.39) `f(α, x) = f_ELU(α, x) = { α(e^x - 1), x < 0 ; x, x ≥ 0 }`
