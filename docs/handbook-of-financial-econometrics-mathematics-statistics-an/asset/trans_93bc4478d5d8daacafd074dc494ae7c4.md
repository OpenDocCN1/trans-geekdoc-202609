
对于第i个公司或投资组合。有时用(1 + R)表示总收益率。

然后，对于任意持续时间为n年（n < T）的第t个短期，n年模型与前一节使用的模型相同。R_T与r_t以及R_MT与r_MT之间的关系分别定义如下：

(1 + R_T) = ∏_{t=1}^{T/n} (1 + r_t),  (114.14a)
且
(1 + R_MT) = ∏_{t=1}^{T/n} (1 + r_Mt).  (114.14b)

方程(114.14a)和(114.14b)表明，长期总收益率可以表示为每个互不相交的子时期连续总收益率的乘积。这一性质称为可乘性。例如，如果r_t和r_Mt代表月收益率且T/n = 3，则R_T和R_MT将代表季度收益率。

Levhari和Levy（1977）以及Chen（1980）分析了在可乘性假设下时间聚合对beta估计的影响。已证明，如果假设市场收益率同分布但不独立分布，与可乘模型相关的N期系统风险通常可以写成

β_N = [Cov(r_t, r_Mt) + μ_i μ_M]^N - (μ_i μ_M)^N + b_N / (σ_M^2 + μ_M^2)^N - μ_M^{2N} + c_N
= Σ_{t=0}^{N-1} a_t β_u^{N-1} (1 + α)^t + b_N / Σ_{t=0}^{N-1} a_t + c_N,  (114.15)

其中r_t = 证券收益率，r_Mt = 市场收益率，μ_i = E(r_t)，μ_M = E(r_Mt)，σ_M^2 = Var(r_Mt)；a_t = (N choose t)(σ_M^2)^{N-t}(μ_M^2)^t，α = (β_u - 1) μ_M - r / μ_M，其中r为Levhari-Levy定义的无风险利率；b_N和c_N分别代表市场收益率自相关对Cov(r1, r2, ..., rN, rM1, rM2, ..., rMN)和Var(rM1, rM2, ..., rMN)的影响。如果假设市场收益率独立分布（b_N = c_N = 0），方程(114.15)就简化为Levhari-Levy方程。为了考察与可乘收益率相关的单期系统风险中自相关的影响，将在第114.2.2.1–114.2.2.3节中对方程(114.15)进行探讨。

### 114.2.2.1 中性股票

对于中性股票（$\beta_u = 1$），其$N$期系统风险可以表示为

$$\beta_N^* = \frac{\sum_{t=0}^{N-1} a_t + b_N}{\sum_{t=0}^{N-1} a_t + c_N}. \tag{114.16}$$

因此，仅当$b_N = c_N = 0$时，$\beta_N^* = 1 = \beta_u$。换言之，除非与单期市场收益率自相关的项$b_N$和$c_N$为零，否则$\beta_N^*$不可能等于1，这要求假设市场收益率独立分布。因此，如果市场收益率存在自相关，中性股票的$\beta_N^*$不等于1。

### 114.2.2.2 进取型股票

波动性大于市场的股票称为进取型股票；即$\beta_u > 1$。在这种情况下，$\alpha > 0$且$\beta_u^{N-i} \ge \beta_u$，$i = 0,1,\dots, N - 1$。那么，根据方程(114.15)，很容易证明

$$\beta_N^* > \beta_u \left[ \frac{\sum_{t=0}^{N-1} a_t + b_N/\beta_u}{\sum_{t=0}^{N-1} a_t + c_N} \right]. \tag{114.17}$$

如Levhari和Levy所指出的，如果假设收益率独立同分布，则$\beta_N^* > \beta_u$。然而，方程(114.17)暗示$\beta_N^*$的下界可能大于或小于$\beta_u$，具体取决于$b_N$和$c_N$的大小。如果$b_N/\beta_u$大于$c_N$，则$\beta_N^*$的下界大于$\beta_u$。在这种情况下，Levhari–Levy的结论$\beta_N^* > \beta_u$仍然成立。但是，如果$b_N/\beta_u$小于$c_N$，则$\beta_N^*$的下界小于$\beta_u$。这意味着对于某些$N$，$\beta_N^*$可能小于$\beta_u$。这一发现解释了为什么在Levhari–Levy的实证结果中，某些股票在某个$N$下的$\beta_N^*$并不大于$\beta_u$。因此，市场收益率中自相关的存在可以增大或减小与进取型股票相关的$N$期系统风险的大小。

### 114.2.2.3 防御型股票

在这种情况下，β_u < 1，α < 0，β_u^{N-i} ≤ β_u，i = 0,1,…, N − 1。那么，可以证明

β_N^* ≤ β_u [ (∑_{t=0}^{N-1} a_t + b_N/β_u) / (∑_{t=0}^{N-1} a_t + c_N) ] . (114.18)

如果b_N/β_u小于c_N，则会得到与Levhari和Levy相同的结果β_N^* < β_u，因为β_N^*的上界小于β_u。此外，如果对于某些N，b_N或c_N为负，使得方程(114.18)的分子或分母变为负，则β_N^*将小于−β_u。具体而言，市场收益率中自相关的影响可能会减小与防御型股票相关的β_N^*的数值。并且，对于某些N，N期系统风险可能变为负值。这一结果有助于解释为什么在Levhari–Levy的实证结果中，一些与防御型股票相关的估计N期系统风险为负。因此，市场收益率中自相关的存在可以用来解释Levhari和Levy发现的实证结果。

## 114.3 估计R²的时间聚合

Jacob（1971）发现，由月度数据估计的R²小于由季度数据和年度数据估计的R²；Altom、Jacquillat和Levasseur（1974）发现，由季度数据估计的R²小于由半年和年度数据估计的R²；McDonald（1974）发现，由月度共同基金数据获得的R²小于由季度和年度共同基金数据获得的R²。Schwartz和Witcomb（1977a,b）试图用时间-方差关系解释上述发现。现在，我们采用一种新方法来解释时间聚合对估计R²的影响。

在给定(114.5)–(114.8)的情况下，为了推导用日收益率表示的R²与用周收益率表示的R²之间的关系，我们首先计算以下方差：

Var(AY) = β_daily² I' Var(X) I + I' I σ², (114.19)

其中

I' = (1,1,1,1,1)

Y. Xiao, Y. Tang & C. F. Lee

以及

Var(X) = 
\begin{bmatrix}
 Var(X_t) & Cov(X_{t,t-1}) & Cov(X_{t,t-2}) \\
 Cov(X_{t,t-1}) & Var(X_{t-1}) & Cov(X_{t-1,t-2}) \\
 Cov(X_{t,t-2}) & Cov(X_{t-1,t-2}) & Var(X_{t-2}) \\
 Cov(X_{t,t-3}) & Cov(X_{t-1,t-3}) & Cov(X_{t-2,t-3}) \\
 Cov(X_{t,t-4}) & Cov(X_{t-1,t-4}) & Cov(X_{t-2,t-4}) \\
 Cov(X_{t,t-3}) & Cov(X_{t,t-3}) & Cov(X_{t-1,t-3}) & Cov(X_{t-2,t-3}) & Var(X_{t-3}) & Cov(X_{t-3,t-4}) \\
 Cov(X_{t,t-4}) & Cov(X_{t-1,t-4}) & Cov(X_{t-2,t-4}) & Cov(X_{t-3,t-4}) & Var(X_{t-4}) 
\end{bmatrix}

= Var(X_t) = 
\begin{bmatrix}
 1 & \rho_x^1 & \rho_x^2 & \rho_x^3 & \rho_x^4 \\
 \rho_x^1 & 1 & \rho_x^2 & \rho_x^3 & \rho_x^4 \\
 \rho_x^2 & \rho_x^2 & 1 & \rho_x^3 & \rho_x^4 \\
 \rho_x^3 & \rho_x^3 & \rho_x^3 & 1 & \rho_x^4 \\
 \rho_x^4 & \rho_x^4 & \rho_x^4 & \rho_x^4 & 1 
\end{bmatrix}, (114.20)

其中\rho_x^i (i = 1,2,3,4)是日市场指数的自相关系数。

此外，根据方程(114.4)，Y_t的方差定义如下：

Var(Y_t) = \beta_{daily}^2 Var(X_t) + \sigma^2. (114.21)

方程(114.19)和(114.21)表明，日数据的方差与周数据的方差之间存在关系。

基于R^2的定义，可以定义“日”和“周”的总体拟合优度度量R^2_daily和R^2_weekly为：

R^2_daily = \frac{\beta_{daily}^2 Var(X_t)}{\beta_{daily}^2 Var(X_t) + \sigma^2}, (114.22)

$$R_{\text{weekly}}^2 = \frac{\beta_{\text{daily}}^2 (1\ 1\ 1\ 1\ 1)\,\text{Var}(\mathbf{X})\begin{pmatrix}1\\1\\1\\1\\1\end{pmatrix}}{\beta_{\text{daily}}^2 (1\ 1\ 1\ 1\ 1)\,\text{Var}(\mathbf{X})\begin{pmatrix}1\\1\\1\\1\\1\end{pmatrix}+5\sigma^2}.\tag{114.23}$$

将(114.20)代入(114.23)可得：

$$R_{\text{weekly}}^2 = \frac{1}{1 + \frac{5\sigma^2}{\text{Var}(X_t)\left(5+8\rho_X^1+6\rho_X^2+4\rho_X^3+2\rho_X^4\right)\beta_{\text{daily}}^2}}.\tag{114.24}$$

并且注意，由方程(114.22)，我们可得：

$$\frac{\sigma^2}{\beta_{\text{daily}}^2\,\text{Var}(X_t)} = \frac{1 - R_{\text{daily}}^2}{R_{\text{daily}}^2}.\tag{114.25}$$

最后，将(114.25)代入(114.24)，我们得到：

$$R_{\text{weekly}}^2 = \frac{R_{\text{daily}}^2}{R_{\text{daily}}^2 + k_{d-w}\left(1 - R_{\text{daily}}^2\right)},\tag{114.26}$$

其中$k_{d-w}$是利用日数据和周数据估计$R^2$的日到周乘数：

$$k_{d-w} = \frac{1}{1 + \frac{8}{5}\rho_X^1 + \frac{6}{5}\rho_X^2 + \frac{4}{5}\rho_X^3 + \frac{2}{5}\rho_X^4}.\tag{114.27}$$

因此，如果$k_{d-w} < 1$，则$R_{\text{weekly}}^2 > R_{\text{daily}}^2$，这意味着估计的拟合优度随时间间隔的增加而增大。另一方面，如果$k_{d-w} > 1$，则$R_{\text{weekly}}^2 < R_{\text{daily}}^2$，这意味着使用周数据估计的$R^2$将小于使用日数据估计的$R^2$。在第112.3节中，我们将提供当投资期限增加时$R^2$估计值变化的实证结果。

