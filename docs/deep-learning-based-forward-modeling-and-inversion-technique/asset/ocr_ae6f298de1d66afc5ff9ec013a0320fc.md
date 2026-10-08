# Reconstruction of Thermophysical Parameters Based on Deep Learning 137

![](bbox=[0.318, 0.175, 0.681, 0.269])

![](bbox=[0.293, 0.347, 0.706, 0.558])

**FIGURE 4.19**
The inversion of temperature-related thermal conductivity. The solid line is the ground truth while the dot line is the prediction curve.

vigorously confirms the favorable prediction ability of the NMM for varying thermal conductivities.

# 4.5.2.3 Statistics Analyze

The aforementioned figures merely exhibit the results qualitatively. To further analyze the inversion capability from a statistical point of view, the average relative error is introduced as

> $Err = \frac{1}{M} \sum_{i=1}^{M} \frac{|k_r(i) - k_p(i)|}{k_r(i)}$

where $M$ represents $N_f$, $N_T$ or $N_r$ for the space/temperature/time related cases. Here, $k_p$ and $k_r$ are the predicted thermal conductivity and the ground