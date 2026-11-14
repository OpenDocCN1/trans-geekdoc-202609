where the lowpass filter \(v(\|\bar{\omega}\|)\) is the Fourier-domain representation of the filter \(V\) and is freely chosen by the user. For example, this filter can be chosen as

\(V(\omega) = \left[ \frac{1 + \cos(\omega)}{2} \right]^{10} \text{ with } -\frac{\pi}{2} < \omega \le \frac{\pi}{2}.\)

(8.68)

# 8.10.4 Real-time selection of iteration number

Determination of an optimal stopping point for an iterative image reconstruction algorithm has been an open problem for a long time. The stopping point is strongly dependent on the task that the radiologists are performing. For the lesion detection tasks, the stopping point is lesion size-dependent. There is no single iteration number that gives an optimal image for all lesion sizes. One image can be better for the detection of one lesion but is worse for the detection of another lesion.

Radiologists nowadays are provided with slices of a patient image volume to make a clinical diagnosis. The radiologists are only able to change the display gray-scale window on the computer screen by using the sliders on the screen. We can provide the radiologists another option: real-time adjustment of the iteration number, which is able to improve the lesion detectability for targeted lesion size. We observe that for any given lesion size, its contrast curve peaks at a certain iteration number. One distinguished advantage of the proposed method is that no special additional computational hardware is required. Thus it is applicable for tele- or mobile-radiology of the modern world.

As an alternative way to real-time adjustment of the emulated iteration number, the radiologists are able to click on a suspicious lesion and a background region. A gradient ascent algorithm is then searching for the optimal emulated iteration number to give the maximum contrast for this lesion or the maximum contrast-to-noise for this lesion.

# 8.11 Summary

+   - A linear iterative algorithm can be implemented as an FBP algorithm or a back-projection-then-filtering algorithm. The trick is the equivalence of the matrix multiplication with \(A^T A\) and filtering with the transfer function \(1/|\omega|\).

+   - When you actually implement the iterative Landweber algorithm and the windowed FBP algorithm, you will notice that the step size \(\alpha\) in the iterative Landweber algorithm and the \(\alpha\) in the FBP algorithm are different. This is because \(A^T A\) and \(1/|\omega|\) are not exactly the same. The \(\alpha\) for \(A^T A\) is determined by the maximum singular value of the matrix \(A\), while the \(\alpha\) for \(1/|\omega|\) is determined by the sampling interval of the frequency \(\omega\).