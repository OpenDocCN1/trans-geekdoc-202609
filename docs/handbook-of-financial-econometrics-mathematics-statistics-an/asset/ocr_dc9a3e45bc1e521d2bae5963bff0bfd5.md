-\frac{1}{2}\left[\sum_{i=1}^{n} W_i (\bar{R}_i - R_f)\right]\left[\sum_{i=1}^{n} W_i^2 \sigma_i^2 + \sum_{i=1}^{n}\sum_{j=1}^{n} W_i W_j \sigma_{ij}\right]^{-3/2} \times \left[2W_i \sigma_i^2 + 2\sum_{j=1}^{n} W_j \sigma_{ij}\right] = 0 \quad (i = 1,2,\dots,n). \tag{82A.1}

Multiplying equation (82A.2) by $\left[\sum_{i=1}^{n} W_i^2 \sigma_i^2 + \sum_{i=1}^{n}\sum_{j=1}^{n} W_i W_j \sigma_{ij}\right]^{1/2}$, $i \neq j$, and rearranging yields

$\bar{R}_i - R_f = \left(\frac{\sum_{i=1}^{n} W_i (\bar{R}_i - R_f)}{\sum_{i=1}^{n} W_i^2 \sigma_i^2 + \sum_{i=1}^{n}\sum_{j=1}^{n} W_i W_j \sigma_{ij}}\right)\left(W_i \sigma_i^2 + \sum_{j=1}^{n} W_j \sigma_{ij}\right).$ \tag{82A.2}

Defining $k = \frac{\sum_{i=1}^{n} W_i (\bar{R}_i - R_f)}{\sum_{i=1}^{n} W_i^2 \sigma_i^2 + \sum_{i=1}^{n}\sum_{j=1}^{n} W_i W_j \sigma_{ij}}$, $i \neq j$

yields $-k\left(W_i \sigma_i^2 + \sum_{i=1}^{n} W_i \sigma_{ij}\right) + (\bar{R}_i - R_f) = 0, \quad j \neq i.$

Therefore, $\frac{dL}{dW_i} = -\left(kW_1 \sigma_{1i} + kW_2 \sigma_{2i} + \cdots + kW_i \sigma_i^2 + \cdots + kW_n \sigma_{ni}\right) + (\bar{R}_i - R_f) = 0.$

Define $H_i = kW_i$, where $W_i$ are the fractions to invest in each security and $H_i$ are proportional to this fraction. Substituting $H_i$ for $kW_i$, $\bar{R}_i - R_f = H_i \sigma_{1i} + H_2 \sigma_{2i} + \cdots + H_i \sigma_i^2 + \cdots + H_n \sigma_{ni}.$ There is one equation like this for each value of $i$: $\bar{R}_1 - R_f = H_1 \sigma_1^2 + H_2 \sigma_{12} + \cdots + H_n \sigma_{1n},$ $\bar{R}_2 - R_f = H_1 \sigma_{21} + H_2 \sigma_2^2 + \cdots + H_n \sigma_{2n},$ $\vdots$ $\bar{R}_n - R_f = H_1 \sigma_{n1} + H_2 \sigma_{n2} + \cdots + H_n \sigma_n^2.$ This is equation (82.6a).