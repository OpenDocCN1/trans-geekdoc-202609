# Machine Learning for Biomedical Applications

![](bbox=[0.358, 0.096, 0.642, 0.303])

**Figure 8.1** ECG waveform. Red arrows show the QRS interval duration. The real ECG signal is shown on the pink background.

In this section we will give a brief overview of several types of features that can be extracted from the biomedical signals and images. **Morphological features** describe geometric aspects of the objects, such as length, area, or volume. **Texture descriptors** look at statistical properties of the signal or image values. **Transform-based features** provide features in other domains, such as frequency domain.

# 8.1.1 Morphological features

We have seen several types of morphological features, for example, the volumes of brain structures (Fig. 3.1) or QRS interval duration in an ECG (Fig. 8.1). Morphological features can contain some basic measurements, such as **length, peak height, area, maximum diameter, surface area A, or volume V**. Compactness measures how spherical the volume is:

```
C = 36\pi\frac{V^2}{A^3}$
```

An equivalent measurement in 2D would contain the ratio of the area and circumference. Another group of measurements can be extracted using PCA (Sect. 5.4). The eigenvalues correspond to the **length L of the major** and **minor axis** in 2D, and an additional **least axis** in 3D, e.g.,

```
$L_{major} = 4\sqrt{L_{minor}}$
```

The ratio of minor and major axes lengths **elongation**, and the ratio of least and major axis lengths **flatness.**¹ We have seen various 2D morphological

> ¹ For a detailed description of morphological imaging features, see Image biomarker standardization reference manual at https://arxiv.org/abs/1612.07003.