any difficult quantities in its construction. They proposed the form for the naive probability similar to the Merton DD model. None of the numerical choices of naïve model is result of any type of estimation or optimization as required by original Merton DD model, which is defined in equation (126.11).

For constructing a naive probability, they first approximate the market value of each firm’s debt with the face value of its debt,

$$\text{naive } D = F \tag{126.13}$$

Since they assume that firms that are close to default have very risky debt, and the risk of their debt is correlated with their equity risk, they approximate the volatility of each firm’s debt as

$$\text{naive } \sigma_D = 0.05 + 0.25 \cdot \sigma_E \tag{126.14}$$

They include the five percentage points in this term to represent term structure volatility, and they include the 25% times equity volatility to allow for volatility associated with default risk.

This gives them an approximation to the total volatility of the firm of

$$\text{naive } \sigma_V = \frac{E}{E + \text{naive } D}\sigma_E + \frac{\text{naive } D}{E + \text{naive } D}\text{naive } \sigma_D$$

$$= \frac{E}{E + F}\sigma_E + \frac{E}{E + F}(0.05 + 0.25 * \sigma_E) \tag{126.15}$$

Next, they set the expected return on the firm’s assets equal to the firm’s stock return over the previous year,

$$\text{naive } \mu = r_{i t-1} \tag{126.16}$$

This allows them to capture some of the same information that is captured by the Merton DD iterative procedure described above. The iterative procedure is able to condition on an entire year of equity return data. By allowing their naïve estimate of μ to depend on past rate of returns, they incorporate the same information used by Merton DD model.

The naive distance to default is then

$$\text{naive } DD = \frac{\ln\left(\frac{E+F}{F}\right) + \left(r_{i t-1} - 0.5\,\text{naive } \sigma_V^2\right)T}{\text{naive } \sigma_V \sqrt{T}} \tag{126.17}$$

This naive alternative model is easy to compute; however, it retains the structure of the Merton DD distance to default and expected default frequency. It also captures approximately the same quantity of information as the Merton DD probability. Thus, examining the forecasting ability of this quantity helps them separate the value of solving the Merton model from