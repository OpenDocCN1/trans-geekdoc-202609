**NCS Dataset**
No. of patients: 350
(Normal: 200; Abnormal:150)
NCS parameters: 5
(DML, PML, Lat, CMAP, NCV)
Nerve: median nerve

**Input Feature Matrix**
$egin{bmatrix} a_{11}, a_{12}, a_{13}, \dots, a_{1n} \\ a_{21}, a_{22}, a_{23}, \dots, a_{2n} \\ \vdots \quad \vdots \quad \vdots \quad \vdots \\ a_{m1}, a_{m2}, a_{m3}, \dots, a_{mn} \end{bmatrix}$

**Pre-processing**
Optimize weights and bias
$W = \begin{bmatrix} w_1 \\ w_2 \\ \vdots \\ w_n \end{bmatrix}$
$B = \begin{bmatrix} b_1 \\ b_2 \\ \vdots \\ b_n \end{bmatrix}$
Normalize NCS features in [0 1]

**Neurophysiologist decision:**
Normal and Neuropathy

**Target matrix generation for NN**
[0 1] = Normal (Nor)
[1 0] = Abnormal (Ab)

**Classification, sensitivity and specificity**
(Nor and Ab)

FIGURE 15.8 Different steps involved in finding the optimized NN model.

![](bbox=[0.12, 0.09, 0.85, 0.81])