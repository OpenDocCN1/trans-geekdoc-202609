# TABLE 2.1
Standards D50 and D65 of the Type of Lighting CIE

| Norm | Temp (K) | X | Y | Z | x | Y |
|---|---|---|---|---|---|---|
| D50 | 5,000 | 0.96429 | 1.00000 | 0.82510 | 0.3457 | 0.3585 |
| D65 | 6,500 | 0.95045 | 1.00000 | 1.08905 | 0.3127 | 0.3290 |
| N | - | 1.00000 | 1.00000 | 1.00000 | 1/3 | 1/3 |

N represents the absolute neutral point in the CIEXYZ color model.

The calculation carried out by this transformation converts the white point considered as a reference to the values to which it corresponds in another color space, where another reference white point is defined. In practice, this linear transformation is defined by the matrix $M_{CAT}$, which defines the following transformation:

```
\(\begin{bmatrix} X_2 \\ Y_2 \\ Z_2 \end{bmatrix} = M_{CAT}^{-1} \begin{bmatrix} \frac{r_2}{r_1} & 0 & 0 \\ 0 & \frac{g_2}{g_1} & 0 \\ 0 & 0 & \frac{b_2}{b_1} \end{bmatrix} M_{CAT} \begin{bmatrix} X_1 \\ Y_1 \\ Z_1 \end{bmatrix} \tag{2.47}\)
```

where \((r_1, g_1, b_1)\) and \((r_2, g_2, b_2)\) represent the values converted from the white reference points \(W_1\) and \(W_2\) by the linear transformation \(M_{CAT}\). This process can be defined as follows:

```
\(\begin{bmatrix} r_1 \\ g_1 \\ b_1 \end{bmatrix} = M_{CAT} \begin{bmatrix} X_{W1} \\ Y_{W1} \\ Z_{W1} \end{bmatrix} \quad \text{and} \quad \begin{bmatrix} r_2 \\ g_2 \\ b_2 \end{bmatrix} = M_{CAT} \begin{bmatrix} X_{W2} \\ Y_{W2} \\ Z_{W2} \end{bmatrix} \tag{2.48}\)
```

The most commonly used transformation matrix in practice is the so-called “Bradford” model, which is defined by:

```
\(M_{CAT} = \begin{bmatrix} 0.8951 & 0.2664 & -0.1614 \\ -0.7502 & 1.7135 & 0.0367 \\ 0.0389 & -0.0685 & 1.0296 \end{bmatrix} \tag{2.49}\)
```

# ## 2.6.5 The Gamut

The entire set of colors that can be used for recording, playback, and display by a color model is called the Gamut. This set is related to a three-dimensional space region CIEXYZ, where the dimension is reduced by considering only