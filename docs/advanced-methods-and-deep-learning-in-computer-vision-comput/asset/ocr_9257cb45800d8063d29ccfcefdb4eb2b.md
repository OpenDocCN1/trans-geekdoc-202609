+   - Scale estimation:
+     4. Extract sample $z_{t,\text{scale}}$ from $I_t$ at $p_t$ and $s_{t-1}$
+     5. Compute correlation scores $y_{t,\text{scale}}$ using (9.33) with $f_{t-1,\text{scale}}$ according to (9.43)
+     6. Set $s_t$ to the target scale that maximizes $y_{t,\text{scale}}$
+   - Model update:
+     7. Extract samples $x_{t,\text{trans}}$ and $x_{t,\text{scale}}$ from $I_t$ at $p_t$ and $s_t$
+     8. Update the translation model $A_{t,\text{trans}}$, $B_{t,\text{trans}}$ using (9.41) and (9.42)
+     9. Update the scale model $A_{t,\text{scale}}$, $B_{t,\text{scale}}$ using (9.41) and (9.42).

Note: The scaling of the window content makes the problem with the periodic extension apparent, as the Hann window is not scaled in this process.

# 9.3.5 Spatial and temporal weighting

Despite the use of a Hann-window, the implicit periodic extension of the patch caused by the Fourier transform reduces the discriminative power of the filter. Features that are characteristic for the object of interest reappear in the vicinity of the patch and generate side-lobes in the score function. A naive attempt to counter those side-lobes using an increased search windows fails, because a large part of the considered patch now consists of background pixels. The filter tends to associate those background pixels with the peak in the target function, i.e., it learns high coefficients at these locations, and the tracker will stick to the background instead of following with the object (Danelljan et al., 2015).

To counter this effect, adding a spatial regularization to (9.32), which penalizes filter coefficients outside the bounding-box, has been proposed (Danelljan et al., 2015):

$$\varepsilon_t(f) = \sum_{k=1}^{t} \alpha_k \| S_f(x_k) - y_k \|^2 + \sum_{l=1}^{d} \| w \cdot f^l \|^2. \tag{9.45}$$

However, the required point-wise multiplication of $w$ and $f$ in the spatial domain becomes a convolution in the Fourier domain and the major advantage of DCFs, the efficient computation in the Fourier domain, is lost. One option is to alternate between spatial and Fourier domain (Galoogahi et al., 2015), the other is to choose a weight function $w$ that has only a few nonzero Fourier coefficients. In the latter case, the convolution in the Fourier domain is no problem as the computational effort is only marginally increased; see Danelljan et al. (2015).

The number of computations is greatly reduced by replacing the complex Hadamard (point-wise) products in (9.38) with real matrix products. We start from the system of equations

$$\left(\mathbf{X}^* \text{diag}(\alpha) \mathbf{X} + \lambda \mathbf{I}\right) \bar{\mathbf{F}} = \mathbf{X}^* \text{diag}(\alpha) \mathbf{Y} \tag{9.46}$$