![](bbox=[0.226, 0.108, 0.763, 0.468])

# Figure 4.2. Binned-scatter plot and the distribution histogram of systolic and diastolic BP target values.

![](bbox=[0.151, 0.543, 0.848, 0.663])

# Figure 4.3. Various preprocessing steps to prepare PPG segment series.

corresponding invasive BP waveforms. They would be our target vectors. R-wave occurrences are utilized as the time references during the segmentation procedure. Therefore, each recording turns to an input vector (X) and a target vector (T) as follows:

```
$X = \{x_1, x_2, ..., x_n\}$ (4.9)
```

```
$T = \{t_1, t_2, ..., t_2\}$ (4.10)
```

Each element corresponds to a heart cycle. Figure 4.3 depicts various preprocessing steps. Here, we also provide more details.