
**Open Access** This chapter is licensed under the terms of the Creative Commons Attribution 4.0 International License (http://creativecommons.org/licenses/by/4.0/), which permits use, sharing, adaptation, distribution and reproduction in any medium or format, as long as you give appropriate credit to the original author(s) and the source, provide a link to the Creative Commons licence and indicate if changes were made

The images or other third party material in this chapter are included in the chapter's Creative Commons licence, unless indicated otherwise in a credit line to the material. If material is not included in the chapter's Creative Commons licence and your intended use is not permitted by statutory regulation or exceeds the permitted use, you will need to obtain permission directly from the copyright holder.

![](img/a2f5eed6507498d886a06be86239344b_103_0.png)

## Detection of Directed Connectivities in Dynamic Systems for Different Excitation Signals using Spectral Granger Causality

Christian Kühnert, Christian Frey and Ruben Seyboldt

Fraunhofer Institute of Optronics, System Technologies and Image Exploitation IOSB Fraunhoferstraße 1, 76131 Karlsruhe, Germany

{christian.kuehnert,christian.frey,ruben.seyboldt}@iosb.fraunhofer.de

**Abstract.** Industrial plants usually consist of different process units which are strongly cross-linked to each other. This leads to the point that a voluntary or involuntary change in one unit (e.g. changing some process control parameter or having a malfunctioning value) can lead to unexpected results in another process unit. Hence, knowing which are the causing and which are the effecting process variables is of great interest. Still, depending on the underlying process and the characteristics of the excitation signal, directed connectivities can or can not be detected. Therefore, in this paper several types of dynamic SISO systems and excitation signals are defined for which a directed connectivity from input to output signal should be detected and from output to input should not be detected. As a method for the detection of directed influences Spectral Granger Causality is used, which has been extended with a surrogate-based significance test. This test is used to define if a directed influence exists from one process variable to another.

**Keywords:** Spectral Granger Causality · Detection of Directed Connectivities · Time Series Analysis.

## 1 Introduction

Process control systems at production plants usually consist of a large number of process variables, while the interconnectivity of the variables is not always directly evident. Hence, due to the interconnectivity, if some change, voluntary or on purpose is performed on one unit, this can lead to unwanted effects at another unit. Therefore, it is of great interest to understand which variable has a significant influence on another variable.

For the automatic detection of directed connectivities in time series exists already a wide variety of methods, which are mainly developed for the use in neuroscience (e.g. [3] or [1] for reviews) or for the analysis of econometric data [9]. One of the first methods developed, was done by Granger [8], being called the Granger Causality. This method uses two vector autoregressive functions and, by comparing their residual sum of squares, the method tells if one variable causes the other or not. The original approach, taking place in the time domain, was extended by Geweke [7] into the spectral domain, having the advantage to select specific frequencies for analysis. In 2000 Schreiber, [14] developed a method called Transfer Entropy, which measures the amount of information transferred from one random process to another. In recent research, Transfer Entropy has been extended. It contains several extensions like Partial Transfer Entropy [11] or Symbolic Entropy [13]. Bauer [2] proposes a Nearest-Neighbor approach for cause-effect analysis. In [12] different methods for the detection of significant directed influences were developed and compared on several benchmarks, consisting of simulated dynamic systems data, biosignals and on disturbances from a glass forming process. Kaminski [10] proposes the estimation of directed transfer functions.

This aim of this paper to investigate under which circumstances it is possible to detect directed influences in measurements, depending on the excitation signal as well as the underlying dynamic systems. As specific detection method Spectral Granger Causality [7] is used, which is extended with a surrogate-based significance test. In difference to [12], which already defines benchmark processes for the detection of causal dependencies, the current paper focuses more on the excitation signal characteristics.

The paper is structured as follows: Section 2 introduces how directed connectivities can be detected in time series and how Spectral Granger Causality is applied. Additionally, the surrogate-based calculation of the significance threshold is explained. Section 3 describes the defined input signals and dynamic systems for benchmarking, while section 4 discusses the results. Finally, section 5 gives a summary and some ideas for future research.

## 2 Detecting directed connectivities in time series

### 2.1 Bivariate Spectral Granger Causality

The concept of Granger causality (GC) has been originally introduced in the field of economics by Clive Granger in 1969 [8] who used it to determine the relationships of different econometric models. The basic concept of bivariate GC can be explained by assuming the two time series \(u[k] \in \mathbb{R}\) and \(y[k] \in \mathbb{R}\) with \(k = 1, \dots, K\) samples. In that case, the causal connectivity \(u \to y\) is assumed to exist if past values from \(u[k]\) and \(y[k]\) result in a higher forecast accuracy for \(y[k]\) than using only past values from \(y[k]\). Mathematically, this is evaluated by comparing two linear vector autoregressive models, while the first one only contains past values of \(y[k]\), called the restricted model, and the other one containing past values of \(u[k]\) and \(y[k]\), called the unrestricted model. Furthermore, Granger Causality can be easily extended into the multivariate case, while good explanations can be found e.g. in [16] or [4]. Since the developed benchmarks in section 3 compare always one input against one output, for simplicity, multivariate GC will not be explained in this paper.

**GC in the time domain:** Checking if \(u\) causes \(y\) or \(y\) causes \(u\), is in the time domain is done by comparing two linear vector autoregressive (VAR) models.

The two VAR models are defined as

$$
u[k] = \sum_{j=1}^n a_{uu}[j] \cdot u[k-j] + \sum_{j=1}^n a_{uy}[j] \cdot y[k-j] + e_u[k], \quad (1)
$$
$$
y[k] = \sum_{j=1}^n a_{yy}[j] \cdot y[k-j] + \sum_{j=1}^n a_{yu}[j] \cdot u[k-j] + e_y[k] \quad (2)
$$

containing the residual covariance matrix being defined as

$$
\Sigma = \begin{pmatrix} \Sigma_{uu} & \Sigma_{uy} \\ \Sigma_{yu} & \Sigma_{yy} \end{pmatrix} \quad (3)
$$

In (1), (2) n is the model order, \(a_{uu}, a_{uy}, a_{yu}, a_{yy} \in \mathbb{R}^n\) contain the model coefficients and \(e_u[k], e_y[k] \in \mathbb{R}\) define the residuals. Finally GC checks the coefficients in \(a_{yu}\) (respectively \(a_{uy}\)). If these are significantly different from zero, it is assumed that \(u\) causes \(y\) (respectively \(y\) causes \(u\)). Usually, this is done by comparing the squared-sum of residuals of \(e_u\) (respectively \(e_y\)) with and without taking into account the influencing variable \(y\) (respectively \(u\)).

**GC in the frequency domain** The advantage when working in the frequency domain compared to the time domain is that causal connectivities can be tied to specific frequency bands and one gets better insights in the data. The methodology has been explained in detail in [7] and the main steps are given here for completeness. The Fourier Transformation of the equations 1 and 2 can be written in the following set of equations:

$$
\begin{pmatrix} A_{uu}(f) & A_{uy}(f) \\ A_{yu}(f) & A_{yy}(f) \end{pmatrix} \begin{pmatrix} u(f) \\ y(f) \end{pmatrix} = \begin{pmatrix} e_u(f) \\ e_y(f) \end{pmatrix} \quad (4)
$$

with \(u(f)\) and \(y(f)\) are the Fourier transformed time series from \(u[k]\) and \(y[k]\) and \(e_u(f), e_y(f)\) are the Fourier transformations of \(e_u[k]\) and \(e_y[k]\). The components of \(A\) are then transformed as

$$
A_{uu}(f) = 1 - \sum_{i=1}^n a_{uu}(i) e^{(-i2\pi fn)} \quad (5)
$$
$$
A_{uy}(f) = - \sum_{i=1}^n a_{uy}(i) e^{(-i2\pi fn)} \quad (6)
$$

which holds analogous for \(A_{yu}(f)\) and \(A_{yy}(f)\). Finally, equation 4 can be rewritten as

$$
\begin{pmatrix} u(f) \\ y(f) \end{pmatrix} = \begin{pmatrix} H_{uu}(f) & H_{uy}(f) \\ H_{yu}(f) & H_{yy}(f) \end{pmatrix} \begin{pmatrix} e_u(f) \\ e_y(f) \end{pmatrix} \quad (7)
$$

