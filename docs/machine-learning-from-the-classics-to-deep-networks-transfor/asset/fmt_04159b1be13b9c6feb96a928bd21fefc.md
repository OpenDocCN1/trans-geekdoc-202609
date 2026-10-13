
## Echo Cancellation and Sparsity

In [Chapter 4](#Chp004_119-175_B978044329238500010X.xhtml), we discussed the task of echo cancellation. In a number of cases, the echo path, represented by a vector comprising the values of the impulse response samples/coefficients, is a sparse one. This is the case, for example, in internet telephony and in acoustic and network environments (e.g., [3,10,73]). [Fig. 9.5](#Chp009_417-462_B9780443292385000159.xhtml#f0035) shows the impulse response of such an echo path. The impulse response of the echo path is of short duration; however, the delay with which it appears is not known. So, in order to model it, one has to use a long impulse response, yet only a relatively small number of the coefficients will be significant and the rest will be close to zero. Of course, one could ask, why not use an LMS or an RLS, and eventually the significant coefficients will be identified? The answer is that this turns out not to be the most efficient way to tackle such problems, because the convergence of the algorithm can be very slow. In contrast, if one embeds, somehow, into the problem the a priori information concerning the existence of (almost) zero coefficients, then the convergence speed can be significantly increased and also better error floors can be attained.

![Figure 9.5 The impulse response function of an echo path in a telephone network. Observe that although it is of relatively short duration, it is not a priori known where exactly in time it will occur.](images/B9780443292385000159/gr006.jpg)

[Figure 9.5](#Chp009_417-462_B9780443292385000159.xhtml#cf0285) The impulse response function of an echo path in a telephone network. Observe that although it is of relatively short duration, it is not a priori known where exactly in time it will occur.

## Sparsity in Wireless Communication

A similar situation occurs in wireless communication systems, which involve multipath channels. A typical application is in high-definition television (HDTV) systems, where the involved communication channels consist of a *few* nonnegligible coefficients, some of which may have quite large time delays with respect to the main signal (see, e.g., [4,32,52,77]). If the information signal is transmitted at high symbol rates through such a dispersive channel, then the introduced intersymbol interference (ISI) has a span of several tens up to hundreds of symbol intervals. This in turn implies that quite long channel estimators are required at the receiver's end in order to reduce effectively the ISI component of the received signal, although only a small part of it has values substantially different from zero. The situation is even more demanding when the channel-frequency response exhibits deep nulls. More recently, sparsity has been exploited in channel estimation for multicarrier systems, both for single-antenna as well as for multiple-input-multiple-output (MIMO) systems [46,47]. A thorough, in-depth treatment related to sparsity in multipath communication systems is provided in [5].

## Sparsity in Signal Compression

Another example, which might be more widely known, is that of signal compression. It turns out that if the signal modalities with which we communicate (e.g., speech) and also sense the world (e.g., images, audio) are transformed into a suitably chosen domain, then they are sparsely represented; only a relatively small number of the signal components in this domain are large, and the rest are close to zero. As an example, [Fig. 9.6](#Chp009_417-462_B9780443292385000159.xhtml#f0040)A shows an image and [Fig. 9.6](#Chp009_417-462_B9780443292385000159.xhtml#f0040)B shows the plot of the magnitude of the obtained discrete cosine transform (DCT) components, which are computed by writing the corresponding image array as a vector in lexicographic order. Note that more than 95% of the total energy is contributed by only 5% of the largest components. This is at the heart of any compression technique. Only the large coefficients are chosen to be coded and the rest are considered to be zero. Hence, significant gains are obtained in memory/bandwidth requirements while storing/transmitting such signals, without much perceptual loss. Depending on the modality, different transforms are used. For example, in JPEG-2000, an image array, represented in terms of a vector that contains the intensity of the gray levels of the image pixels, is transformed via the discrete wavelet transform (DWT), resulting in a transformed vector that comprises only a few large components.

![Figure 9.6 (A) A 512 × 512 pixel image and (B) the magnitude of its DCT components in descending order and logarithmic scale. Note that more than 95% of the total energy is contributed by only 5% of the largest components.](images/B9780443292385000159/gr007.jpg)

Figure 9.6 (A) A 512 × 512 pixel image and (B) the magnitude of its DCT components in descending order and logarithmic scale. Note that more than 95% of the total energy is contributed by only 5% of the largest components.

## Mathematical Formulation

Let

$$\widetilde{\mathbf{s}} = \Phi^{H}\mathbf{s},\ \mathbf{s},\widetilde{\mathbf{s}} \in \mathbb{C}^{l},$$

where $\mathbf{s}$ is the vector of the "raw" signal samples, $\widetilde{\mathbf{s}}$ is the (complex-valued) vector of the transformed ones, and $\Phi$ is the $l \times l$ transformation matrix. Often, this is an orthonormal/unitary matrix, $\Phi^{H}\Phi = I$. Basically, a transform is nothing more than a projection of a vector on a new set of coordinate axes, which comprise the columns of the transformation matrix $\Phi$. Celebrated examples of such transforms are the wavelet, the discrete Fourier (DFT), and the discrete cosine (DCT) transforms (e.g., [87]). In such cases, where the transformation matrix is orthonormal, one can write

$$\mathbf{s} = \Psi\widetilde{\mathbf{s}},$$
