# 8.3.1 The Delta Decomposition

This decomposition is useless, but conceptually important. Take the basis of impulses Ψ_δ = I / √n_t as the temporal basis. This basis is orthonormal and we distinguish this decomposition from the others using the subscript δ.

This decomposition generalizes the convolution representation of a signal introduced in Chapter 4. The general temporal structure is ψ_r[k] = δ_r[k] = δ[k − r]. The decomposition of the snapshot d_k[i] becomes

$$\mathbf{d}_k[\mathbf{i}] = \sum_{r=0}^{R-1} \sigma_{\delta r}\,\phi_{\delta r}[\mathbf{i}]\,\psi_{\delta r}[k] = \sum_{r=0}^{R-1} \sigma_{\delta r}\,\phi_{\delta r}[\mathbf{i}]\,\frac{\delta[k - r]}{\sqrt{n_t}} = \frac{\sigma_{\delta k}\,\phi_{\delta k}[\mathbf{i}]}{\sqrt{n_t}}\,.$$
(8.20)

Therefore, the spatial basis corresponds to the normalized snapshots:

$$\phi_{\delta k}[\mathbf{i}] = \frac{\mathbf{d}_k[\mathbf{i}]}{\|\mathbf{d}_k[\mathbf{i}]\|} \quad\text{and}\quad \sigma_{\delta k} = \|\mathbf{d}_k[\mathbf{i}]\|\sqrt{n_t} = \|\mathbf{d}_k(\mathbf{x}_i)\|\sqrt{n_t\,n_s}\,.$$
(8.21)

This decomposition yields the highest possible temporal localization: large amplitudes σ_{δr} correspond to a snapshot with large energy content. A strong amplitude decay indicates that some snapshots have much lower energy content than others. In a data set in which a strong impulsive event occurs, the POD temporal structure may approach a delta-like form: when this happens, the associated spatial structure tends to the corresponding normalized snapshot. A similar limit is obtained in a DWT (see Chapter 5) if the finest scale is pushed to its limit. In a Haar wavelet transform, for example, the finest scale corresponds to elements of the form w_r = (δ_r + δ_{r+1})/√2. The spatial structures associated to these are normalized averages of the snapshots d_k and d_{k+1}. Similarly, the spatial structure associated with the basis of the form ψ_r = 1/√n_t is the normalized time average of the data.

# 8.3.2 The Discrete Fourier Transform

We here refer to the DFT of the data set in time, that is, this is equivalent to performing the DFT of D row-wise as in (8.5), followed by a normalization to compute the amplitudes. In the DFT we set Ψ = Ψ_F and we use the subscript F to distinguish it from the others. This matrix is defined in (8.8). This basis is orthonormal and symmetric. Using (8.13) and the general Algorithm 2 gives

$$\mathbf{D}\bar{\mathbf{\Psi}}_\mathcal{F} = \mathbf{\Phi}_\mathcal{F}\mathbf{\Sigma}_\mathcal{F} = \widehat{\mathbf{D}} \iff \sigma_{\mathcal{F}r} = \|\phi_r\sigma_r\| = \|\mathbf{D}\bar{\psi}_r\|, \quad \text{that is, } \mathbf{\Phi}_\mathcal{F} = \widehat{\mathbf{D}}\mathbf{\Sigma}_\mathcal{F}^{-1}\,.$$
(8.22)

The first step on the left is the row-wise Fourier transform of D, denoted as \widehat{D}. The second step is the normalization, which can be computed along the rows of \widehat{D}, and in the last step we see that the spatial structures correspond to the normalized distribution of a given entry of the Fourier spectra. We thus see that each entry of the spatial basis tells how much the data at a specific location correlates with the harmonic associated with the discrete frequency r. The computation of the digital frequencies from the sampling frequency of the data is described in Chapter 4. In the same section, it was recalled that the DFT implicitly assumes that the data is periodic of period T = n_t Δt.