# 8.2.4.1 Filtering: algorithm

The predict step has a similar structure to the update step in moment form. We start with the prior \(p(\mathbf{z}_{t-1}|\mathbf{y}_{1:t-1}, \mathbf{u}_{1:t-1}) = \mathcal{N}_c(\mathbf{z}_{t-1}|\boldsymbol{\eta}_{t-1|t-1}, \boldsymbol{\Lambda}_{t-1|t-1})\) and then compute

```
p(\mathbf{z}_t|\mathbf{y}_{1:t-1}, \mathbf{u}_{1:t}) = \mathcal{N}_c(\mathbf{z}_t|\boldsymbol{\eta}_{t|t-1}, \boldsymbol{\Lambda}_{t|t-1}) \quad (8.89)
\mathbf{M}_t = \boldsymbol{\Lambda}_{t-1|t-1} + \mathbf{F}_t^\mathsf{T} \mathbf{Q}_t^{-1} \mathbf{F}_t \quad (8.90)
\mathbf{J}_t = \mathbf{Q}_t^{-1} \mathbf{F}_t \mathbf{M}_t^{-1} \quad (8.91)
\boldsymbol{\Lambda}_{t|t-1} = \mathbf{Q}_t^{-1} - \mathbf{Q}_t^{-1} \mathbf{F}_t (\boldsymbol{\Lambda}_{t-1|t-1} + \mathbf{F}_t^\mathsf{T} \mathbf{Q}_t^{-1} \mathbf{F}_t)^{-1} \mathbf{F}_t^\mathsf{T} \mathbf{Q}_t^{-1} \quad (8.92)
= \mathbf{Q}_t^{-1} - \mathbf{J}_t \mathbf{F}_t^\mathsf{T} \mathbf{Q}_t^{-1} \quad (8.93)
= \mathbf{Q}_t^{-1} - \mathbf{J}_t \mathbf{M}_t \mathbf{J}_t^\mathsf{T} \quad (8.94)
\boldsymbol{\eta}_{t|t-1} = \mathbf{J}_t \boldsymbol{\eta}_{t-1|t-1} + \boldsymbol{\Lambda}_{t|t-1} (\mathbf{B}_t \mathbf{u}_t + \mathbf{b}_t), \quad (8.95)
```

where \(\mathbf{J}_t\) is analogous to the Kalman gain matrix in moment form Equation (8.28). From the matrix inversion lemma, Equation (2.93), we see that Equation (8.92) is the inverse of the predicted covariance \(\boldsymbol{\Sigma}_{t|t-1}\) given in Equation (8.24).

The update step in information form is as follows:

```
p(\mathbf{z}_t|\mathbf{y}_{1:t}, \mathbf{u}_{1:t}) = \mathcal{N}_c(\mathbf{z}_t|\boldsymbol{\eta}_{t|t}, \boldsymbol{\Lambda}_{t|t}) \quad (8.96)
\boldsymbol{\Lambda}_{t|t} = \boldsymbol{\Lambda}_{t|t-1} + \mathbf{H}_t^\mathsf{T} \mathbf{R}_t^{-1} \mathbf{H}_t \quad (8.97)
\boldsymbol{\eta}_{t|t} = \boldsymbol{\eta}_{t|t-1} + \mathbf{H}_t^\mathsf{T} \mathbf{R}_t^{-1} (\mathbf{y}_t - \mathbf{D}_t \mathbf{u}_t - \mathbf{d}_t). \quad (8.98)
```

# 8.2.4.2 Filtering: derivation

For the predict step, we first derive the joint distribution over hidden states at \(t, t-1\):

```
p(\mathbf{z}_{t-1}, \mathbf{z}_t|\mathbf{y}_{1:t-1}, \mathbf{u}_{1:t}) = p(\mathbf{z}_t|\mathbf{z}_{t-1}, \mathbf{u}_t) p(\mathbf{z}_{t-1}|\mathbf{y}_{1:t-1}, \mathbf{u}_{1:t-1}) \quad (8.99)
= \mathcal{N}_c(\mathbf{z}_t, | \mathbf{Q}_t^{-1} (\mathbf{F}_t \mathbf{z}_{t-1} + \mathbf{B}_t \mathbf{u}_t + \mathbf{b}_t), \mathbf{Q}_t^{-1} ) \quad (8.100)
\times \mathcal{N}_c(\mathbf{z}_{t-1}, | \boldsymbol{\eta}_{t-1|t-1}, \boldsymbol{\Lambda}_{t-1|t-1}) \quad (8.101)
= \mathcal{N}_c(\mathbf{z}_{t-1}, \mathbf{z}_t | \boldsymbol{\eta}_{t-1,t|t}, \boldsymbol{\Lambda}_{t-1,t|t}) \quad (8.102)
```

where

```
\(\boldsymbol{\eta}_{t-1,t|t-1} = \left( \begin{array}{ c }
\boldsymbol{\eta}_{t-1|t-1} - \mathbf{F}_t^\mathsf{T} \mathbf{Q}_t^{-1} (\mathbf{B}_t \mathbf{u}_t + \mathbf{b}_t) \\
\mathbf{Q}_t^{-1} (\mathbf{B}_t \mathbf{u}_t + \mathbf{b}_t) 
\end{array} \right) \quad (8.103)\)

\(\boldsymbol{\Lambda}_{t-1,t|t-1} = \left( \begin{array}{ c c }
\boldsymbol{\Lambda}_{t-1|t-1} + \mathbf{F}_t^\mathsf{T} \mathbf{Q}_t^{-1} \mathbf{F}_t & - \mathbf{F}_t^\mathsf{T} \mathbf{Q}_t^{-1} \\
- \mathbf{Q}_t^{-1} \mathbf{F}_t & \mathbf{Q}_t^{-1} 
\end{array} \right) \quad (8.104)\)
```

The information form predicted parameters \(\boldsymbol{\eta}_{t|t-1}, \boldsymbol{\Lambda}_{t|t-1}\) can then be derived using the marginalisation formulae in Section 2.3.1.4.

For the update step, we start with the joint distribution over the hidden state and the observation