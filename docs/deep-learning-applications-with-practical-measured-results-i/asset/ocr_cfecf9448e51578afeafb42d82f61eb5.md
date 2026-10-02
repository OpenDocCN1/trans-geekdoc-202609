According to the extremum principle of multivariate function, when Q gets the minimum value, the partial derivatives of Q to β̂₀, β̂₁ and β̂₂ are all equal to zero. Then there is Equation (6).

```
$$\begin{cases}\frac{\partial Q}{\partial \hat{\beta}_0}=2\sum(H_{Oi}-\hat{\beta}_0-\hat{\beta}_1 H_{ii}-\hat{\beta}_2 T_i)(-1)=0\\\frac{\partial Q}{\partial \hat{\beta}_1}=2\sum(H_{Oi}-\hat{\beta}_0-\hat{\beta}_1 H_{ii}-\hat{\beta}_2 T_i)(-H_{ii})=0\\\frac{\partial Q}{\partial \hat{\beta}_2}=2\sum(H_{Oi}-\hat{\beta}_0-\hat{\beta}_1 H_{ii}-\hat{\beta}_2 T_i)(-T_i)=0\end{cases}\tag{6}$$
```

Then Equation (7) is derived.

```
$$\begin{cases}n\hat{\beta}_0+\hat{\beta}_1\sum H_{ii}+\hat{\beta}_2\sum T_i=\sum H_{Oi}\\\hat{\beta}_0\sum H_{ii}+\hat{\beta}_1\sum H_{ii}^2+\hat{\beta}_2\sum T_i H_{ii}=\sum H_{ii}H_{Oi}\\\hat{\beta}_0\sum T_i+\hat{\beta}_1\sum T_i H_{ii}+\hat{\beta}_2\sum T_i^2=\sum T_i H_{Oi}\end{cases}\tag{7}$$
```

Its matrix form is

```
$$\begin{bmatrix}n & \sum H_{ii} & \sum T_i\\\sum H_{ii} & \sum H_{ii}^2 & \sum T_i H_{ii}\\\sum T_i & \sum T_i H_{ii} & \sum T_i^2\end{bmatrix}\begin{bmatrix}\hat{\beta}_0\\\hat{\beta}_1\\\hat{\beta}_2\end{bmatrix}=\begin{bmatrix}\sum H_{Oi}\\\sum H_{ii}H_{Oi}\\\sum T_i H_{Oi}\end{bmatrix}\tag{8}$$
```

In Equation (8), two of the matrices can be written as

```
$$\begin{bmatrix}n & \sum H_{ii} & \sum T_i\\\sum H_{ii} & \sum H_{ii}^2 & \sum T_i H_{ii}\\\sum T_i & \sum T_i H_{ii} & \sum T_i^2\end{bmatrix}=\begin{bmatrix}1 & 1 & \cdots & 1\\H_{I1} & H_{I2} & \cdots & H_{In}\\T_1 & T_2 & \cdots & T_n\end{bmatrix}\begin{bmatrix}1 & H_{I1} & T_1\\1 & H_{I2} & T_2\\\vdots & \vdots & \vdots\\1 & H_{In} & T_n\end{bmatrix}\tag{9}$$
```

```
$$\begin{bmatrix}\sum H_{Oi}\\\sum H_{ii}H_{Oi}\\\sum T_i H_{Oi}\end{bmatrix}=\begin{bmatrix}1 & 1 & \cdots & 1\\H_{I1} & H_{I2} & \cdots & H_{In}\\T_1 & T_2 & \cdots & T_n\end{bmatrix}\begin{bmatrix}H_{O1}\\H_{O2}\\\vdots\\H_{On}\end{bmatrix}\tag{10}$$
```

Assume

```
$$\begin{bmatrix}1 & H_{I1} & T_1\\1 & H_{I2} & T_2\\\vdots & \vdots & \vdots\\1 & H_{In} & T_n\end{bmatrix}=X\tag{11}$$
```

Then, Equations (9) and (10) can be rewritten as

```
$$\begin{bmatrix}n & \sum H_{ii} & \sum T_i\\\sum H_{ii} & \sum H_{ii}^2 & \sum T_i H_{ii}\\\sum T_i & \sum T_i H_{ii} & \sum T_i^2\end{bmatrix}=X'X\tag{12}$$
```

```
$$\begin{bmatrix}\sum H_{Oi}\\\sum H_{ii}H_{Oi}\\\sum T_i H_{Oi}\end{bmatrix}=X'H_O\tag{13}$$
```