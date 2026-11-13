# ## 4.6.2 Decomposition 5

In Figure 4.24, the results of the interpolation with the quaternion-based decomposition approach can be seen.

![](bbox=[0.27, 0.24, 0.68, 0.52])

Figure 4.24: Visualization of interpolated (orange) and measured (blue) tensors when using the decomposition-based interpolation method described in this thesis. Extracted from Blarr et al. [17].

The before-mentioned progress of orientations can be visually traced as a clear curve. As for the interpolation method as such, the visual results are for the most part very appealing. Interpolation between the individual measured FOT is good and the transition between two adjacent tensors also appears reasonable. The anisotropy is not basically lost between two differently oriented tensors by "rounding the tensor". The rotation of two adjacent tensors occurs with small angles and therefore smoothly. The only exception to this can be seen at the upper right edge: The interpolated tensor T_10,13 in the middle of UM and UR behaves somewhat strangely as far as the behavior of the row is concerned.

5 This section is extracted from the author's publication [17] with only slight linguistic changes.