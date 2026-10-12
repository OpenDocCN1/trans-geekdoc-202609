
where `Cij(ω) = Xi(ω) Xj*(ω)` is the Fourier transform of cross‐correlation coefficients between channel *i* and channel *j* of the EEGs. [Figure 8.1](#c08.xhtml#c8-fig-0001) shows an example of the cross‐spectral coherence around one second prior to finger movement. A measure of this coherency, such as an average over a frequency band, is capable of detecting zero time‐lag synchronization and fixed time non‐zero time‐lag synchronization, possibly occurring when a significant delay between the two neuronal population sites exists [[15]](#c08.xhtml#c8-bib-0015). Nonetheless, it does not provide any information on directionality of the coupling between the two recording sites.

One important requirement of brain connectivity representation is the direction of information flow. In this respect, multivariate spectral techniques such as `DTF` or partial directed coherence (`PDC`) were proposed [[16](#c08.xhtml#c8-bib-0016), [17](#c08.xhtml#c8-bib-0017)] for determining the directional influences between any given pair of channels in a multivariate dataset. Both `DTF` and `PDC` [[17](#c08.xhtml#c8-bib-0017), [18](#c08.xhtml#c8-bib-0018)] rely on the key concept of Granger causality between time series [[19]](#c08.xhtml#c8-bib-0019), according to which an observed timeseries `x(t)` causes another series `y(t)` if the knowledge of `x(t)`’s past significantly improves the prediction of `y(t)`; this relation between time series is not reciprocal, i.e. `x(t)` may cause `y(t)` without `y(t)` necessarily causing `x(t)`. This lack of reciprocity allows the evaluation of the direction of information flow between structures.

Granger causality (also called as Wiener–Granger causality) [[19]](#c08.xhtml#c8-bib-0019) attempts to extract and quantify directionality from EEGs. It is based on bivariate auto‐regressive `AR` estimates of the data. In a multichannel environment this causality is calculated from pair‐wise combinations of electrodes. This method has been used to evaluate directionality of the source movement from the local field potential in a cat's visual system [[20]](#c08.xhtml#c8-bib-0020).

![Figure 8.1 Cross‐spectral coherence for a set of three electrode EEGs, one second prior to right‐finger movement. Each block refers to one electrode. By careful inspection of this figure, one can observe the same waveform transferred from Cz to C3.](images/c08f001.gif)

[**Figure 8.1**](#c08.xhtml#R_c8-fig-0001) Cross‐spectral coherence for a set of three electrode EEGs, one second prior to right‐finger movement. Each block refers to one electrode. By careful inspection of this figure, one can observe the same waveform transferred from `C[z]` to `C[3]`.

Based on Granger causality if past samples of a time series `y(t)` can be used in prediction of another series `x(t)` then, `y(t)` is said to cause `x(t)`. In order to determine an estimate of this causality consider:

(8.2)
```
e(t) = x(t) − Σ(i=1 to p) â(i) x(t − i)
```

and

(8.3)
```
e1(t) = x(t) − Σ(i=1 to p) a11(i) x(t − i) − Σ(i=1 to p) a12(i) y(t − i)
```

which also implies:

(8.4)
```
e2(t) = y(t) − Σ(i=1 to p) a22(i) y(t − i) − Σ(i=1 to p) a21(i) x(t − i)
```

Granger causality index is defined as:

(8.5)
```
GCI(x(t)→y(t)) = ln(σ²_e2 / σ²_e1)
```

where `σ²_e1` and `σ²_e2` are respectively the variances of first and second signals. Such a definition can easily be extended to multichannel case when the included channels change the residual variance ratios. This is a time domain measure. The Granger causality measure is, however, sensitive to arbitrary mixtures of independent noise.

## 8.3 Phase‐Slope Index

To overcome the effect of noise and establish a more robust measure of connectivity phase‐slope index (`PSI`) was introduced [[21]](#c08.xhtml#c8-bib-0021). The main idea behind `PSI` is that the cause precedes the effect in time and hence the slope of phase of the cross‐spectrum between two time series reflects the directionality [[22]](#c08.xhtml#c8-bib-0022). The cross‐spectrum of two signals `z[i](t)` and `z[j](t)` is defined as:

(8.6)
```
Sij(f) = E[ Zi(f) Zj*(f) ]
```
