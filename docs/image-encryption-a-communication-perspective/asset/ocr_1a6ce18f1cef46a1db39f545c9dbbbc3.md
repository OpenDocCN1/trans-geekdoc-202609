# 8.2 Analysis of Intercarrier Interference

The main problem of OFDM is its susceptibility to small differences in frequency at the transmitter and receiver, normally referred to as frequency offset. This frequency offset can be caused by Doppler shift due to relative motion between the transmitter and receiver or by differences between the frequencies of the local oscillators at the transmitter and receiver. The frequency offset is modeled as a multiplicative factor introduced in the channel, as shown in Figure 8.1 [153–155].

The received signal is given by

$$y(n)=i(n)\exp\left(\frac{j2\pi n\epsilon}{N}\right)+w(n) \tag{8.1}$$

where ε is the normalized frequency offset and is given by $\Delta fNT_s$. $\Delta f$ is the frequency difference between the transmitted and received carrier frequencies, and $T_s$ is the subcarrier symbol period. $w(n)$ is the additive white Gaussian noise (AWGN) introduced in the channel.

The effect of this frequency offset on the received symbol stream can be understood by considering the received symbol $Y(k)$ on the kth subcarrier [151–153].

$$Y(k)=X(k)S(0)+\sum_{\substack{l=0\\l\ne k}}^{N-1}X(l)S(l-k)+W(k) \tag{8.2}$$

where $k=0,1,\ldots,N-1$; $N$ is the total number of subcarriers; $X(k)$ is the transmitted symbol for the kth subcarrier; $W(k)$ is the fast Fourier transform (FFT) of $w(n)$; and $S(l-k)$ are the complex coefficients for the ICI components in the received signal. The ICI components are

![](bbox=[0.3, 0.793, 0.789, 0.904])

Figure 8.1  Frequency offset model.