

### 方程 (3.45)

![equation](images/c3-disp-0047.png)

且 `a[0] = 1`。根据 [(3.39)](#c03.xhtml#c3-disp-0041)，`y(n)` 计算为其 `p` 个过去值的加权和。随后构造 `y(n)` 并估计参数 `f[k]` 和 `r[k]`。因此，阻尼因子可得为

### 方程 (3.46)

![equation](images/c3-disp-0048.png)

谐振频率可得为

### 方程 (3.47)

![equation](images/c3-disp-0049.png)

其中 `Re(.)` 和 `Im(.)` 分别表示复数量的实部和虚部。`w[k]` 参数是利用以下事实计算得出的：

![images](images/c3-i0021.png)

或者

### 方程 (3.48)

![equation](images/c3-disp-0050.png)

用向量形式可表示为 `Rw = y`，其中

![images](images/c3-i0022.png)

`k = 0, 1, ⋯, p − 1`，`l = 1, ⋯, p` 表示上式矩阵的元素。因此，`w = R^(−1) y`，假设 `R` 是满秩矩阵，即不存在重极点。通常，这只需实施 Cholesky 分解算法 [[34]](#c03.xhtml#c3-bib-0034) 即可完成。最后，利用 `w[k]`，指数项的幅度和初始相位计算如下：

### 方程 (3.49)

![equation](images/c3-disp-0051.png)

以及

