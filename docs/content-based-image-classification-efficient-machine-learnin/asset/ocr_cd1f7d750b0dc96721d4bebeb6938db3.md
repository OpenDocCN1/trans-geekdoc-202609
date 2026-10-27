# TABLE 5.6

Classification Performance with Partial DST Coefficients with Four Different Public Datasets using Four Different Classifiers

| Datasets | Metrics | KNN | RIDOR | ANN | SVM |
|---|---|---:|---:|---:|---:|
| Wang | Precision | 0.67 | 0.41 | 0.557 | 0.49 |
|  | Recall | 0.68 | 0.414 | 0.562 | 0.497 |
|  | MR | 0.071 | 0.097 | 0.08 | 0.092 |
|  | F1-Score | 0.683 | 0.412 | 0.558 | 0.466 |
| OT-Scene | Precision | 0.376 | 0.31 | 0.437 | 0.354 |
|  | Recall | 0.379 | 0.313 | 0.438 | 0.36 |
|  | MR | 0.14 | 0.16 | 0.097 | 0.15 |
|  | F1-Score | 0.372 | 0.31 | 0.436 | 0.329 |
| Corel | Precision | 0.501 | 0.446 | 0.544 | 0.449 |
|  | Recall | 0.51 | 0.45 | 0.556 | 0.471 |
|  | MR | 0.097 | 0.098 | 0.09 | 0.1 |
|  | F1-Score | 0.488 | 0.447 | 0.542 | 0.43 |
| Caltech | Precision | 0.45 | 0.406 | 0.424 | 0.327 |
|  | Recall | 0.499 | 0.431 | 0.512 | 0.492 |
|  | MR | 0.1 | 0.12 | 0.097 | 0.14 |
|  | F1-Score | 0.424 | 0.417 | 0.456 | 0.372 |

[Observations: Wang and Caltech datasets have the highest classification results with KNN classifier; OT-Scene and Corel datasets have the highest classification results with ANN classifier.]

The maximum value of F1-Score of 0.683 and minimum value of MR of 0.071 are observed with 0.012% of the full DST coefficients of the test images. The average Precision, Recall, MR and F1-Score values of classification for feature extraction with 0.012% of the fully transformed coefficient of DST for four different public datasets using four different classifiers—namely, KNN, RIDOR, ANN and SVM are given in Table 5.6.

# 5.6.5 Discrete Hartley Transform

Discrete Hartley transform (DHT) is formed as a Fourier-related transform of discrete periodic data, which transforms the real inputs to real outputs while avoiding the elementary association of complex numbers [4]. It has acted as a linear operator and has been the discrete analogue of the continuous Hartley Transform. DHT has been a linear, invertible function $H: \mathbb{R}^n \to \mathbb{R}^n$ (where $\mathbb{R}$ denotes the set of real numbers). Transformation of $n$ real numbers starting from $x_0, ..., x_{n-1}$ into $n$ real numbers $h_0, ..., h_{n-1}$ can be performed by equation 5.4

$$H_k = \sum_{n=0}^{N-1} x_n \left[\cos\left(\frac{2\pi}{N}nk\right) + \sin\left(\frac{2\pi}{N}nk\right)\right]_{k=0,\ldots,N-1} \tag{5.4}$$

Interpretation of the transform has been done as the multiplication of the vector $(x_0, ..., x_{N-1})$ by an $N \times N$ matrix; therefore, the discrete Hartley