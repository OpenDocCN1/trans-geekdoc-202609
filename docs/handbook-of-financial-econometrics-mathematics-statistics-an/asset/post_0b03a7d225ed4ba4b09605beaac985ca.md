
C = P(0,T) · E^Q
× [ max ( S(0)/P(0,T) · exp{ -σ²T + σ · Z̃(T) } - K, 0 ) | F0 ]
= P(0,T) · E^Q
× [ max ( S(0) · exp{ (R - σ²/2) T + σ · Z̃(T) } - K, 0 ) | F0 ]

Now Z̃(t) = Z(t) - Z(0) is the increment of a Wiener process, that is, it follows the normal distribution with zero mean and variance equal to T, i.e.,

C = P(0,T) · ∫_{-∞}^∞ { max ( S(0) · exp{ (R - σ²/2) T + σ · y √T } - K, 0 ) · exp(-y²/2) / √(2π) } dy

The option is exercised only when the final stock price is greater than the strike, that is,

S(0) · exp{ (R - σ²/2) T + σ · y √T } ≥ K
⇒ exp{ (R - σ²/2) T + σ · y √T } ≥ K/S(0)
⇒ -(R - σ²/2) T - σ · y √T ≤ ln(S(0)/K)
⇒ y ≥ - [ln(S(0)/K) + (R - σ²/2) T] / (σ √T) = -d₂

We can then write equation (27.79) as

C = P(0,T) · ∫_{-d₂}^∞ { [S(0) · exp{ (R - σ²/2) T + σ · y √T } - K] · exp(-y²/2) / √(2π) } dy

## Itô's Calculus and the Derivation of the Black-Scholes Option-Pricing Model

= P(0, T) · 1/√(2π) · ∫_{-d₂}^∞ { S(0) · exp{ -y²/2 + σ · y · √T + (R - σ²/2) T } } dy - P(0, T) · 1/√(2π) · ∫_{-∞}^{d₂} K · exp(-y²/2) dy = I₁ - I₂. (27.81.)

The first integral is calculated by “completing the square”. Indeed, -y²/2 + σ · y · √T + (R - σ²/2) T = -1/2 · [y² - 2 · σ · y · √T - 2 · R · T + σ² · T] = -1/2 · [(y - σ√T)² - 2 · R · T]. (27.82.)

We employ the change of variable x = y − σ√T ⇒ y = x + σ√T and I₁ becomes I₁ = P(0, T) · S(0) · exp(R · T) · 1/√(2π) · ∫_{-(d₂+σ√T)}^{∞} exp(-½ · x²) dx = S(0) · N(d₁). (27.83.)

The second integral is simply equal to I₂ = P(0, T) · K · N(d₂), thus reaching the Black–Scholes result. (27.84.)

### Sample Problem 27.7.2: Pricing an Option to Exchange One Asset for Another.

Let us consider two tradable assets with respective prices X(t) and Y(t) that provide no income. In this section we are pricing the option that permits us, if we hold the asset X(t), to exchange it for Y(t), i.e., the payoff of the option is max(Y(t) − X(t), 0). Let’s also assume that the maturity of the option is T.

The natural choice for the numeraire asset is X(t) — the asset we hold. Since both assets are tradable without any dividends, equation (27.72) tells us that there exists a unique density function/measure Q that satisfies

E^Q [Y(T)/X(T) | F_0] = Y(0)/X(0). (27.85.)

This is the density function that ensures that the current price of this ratio is fair.

For reasons of simplicity we let the dynamics of the two assets be described by the following Itô processes
dX(t) = μ_X · X(t) · dt + σ_X · X(t) · dZ_1(t),
dY(t) = μ_Y · Y(t) · dt + σ_Y · ρ · Y(t) · dZ_1(t) + σ_Y · ρ̄ · Y(t) · dZ_2(t). (27.86.)

In equation (27.86) the driving Wiener process Z_1(t) and Z_2(t) are independent. However, we observe that although X(t) is driven only by Z_1(t), Y(t) is driven by both. The result is that the returns of Y(t) become correlated with the returns of X(t). Indeed, it is very easy to check from the definition of correlation that

E [dX(t)/X(t) · dY(t)/Y(t)] / sqrt{E[(dX(t)/X(t) - μ_X dt)^2] · E[(dY(t)/Y(t) - μ_Y dt)^2]} = σ_X · σ_Y · ρ / (σ_X · σ_Y) = ρ. (27.87.)

It is also very easy to check that the sum of the two Wiener processes is a Wiener process itself
dZ(t) = ρ · dZ_1(t) + ρ̄ · dZ_2(t) (27.88.)
with ρ̄ = sqrt(1 - ρ²), since the successive increments of the new process
- are independent with the previous one,
- they follow the normal distribution,
- with mean 0, and standard deviation sqrt(t).

According to the previous, we now know that the solutions to these SDE’s are

X(t) = X(0) · exp { (μ_X - σ_X²/2) · t + σ_X · Z_1(t) },
Y(t) = Y(0) · exp { (μ_Y - σ_Y²/2) · t + σ_Y · ρ · Z_1(t) + σ_Y · ρ̄ · Z_2(t) }.

$$Y(t)=Y(0)\cdot\exp\left\{\left(\mu_Y-\frac{\sigma_Y^2}{2}\right)\cdot t+\sigma_Y\cdot\rho\cdot Z_1(t)+\sigma_Y\cdot\bar{\rho}\cdot Z_2(t)\right\}.$$ \tag{27.89.}

By dividing the equations in (27.89) we get the ratio

$$\frac{Y(t)}{X(t)}=\frac{Y(0)}{X(0)}\cdot\exp\left\{\left(\mu_Y-\mu_X-\left(\frac{\sigma_Y^2}{2}-\frac{\sigma_X^2}{2}\right)\right)\cdot t+(\sigma_Y\cdot\rho-\sigma_X)\cdot Z_1(t)+\sigma_Y\cdot\bar{\rho}\cdot Z_2(t)\right\}.$$ \tag{27.90.}

If we consider (27.90) as a bivariate function $u=f(Z_1,Z_2)$ and we apply the Itô’s lemma (27.18) with the multiplication rules of (27.19) we have

$$d\left(\frac{Y(t)}{X(t)}\right)=\frac{\partial f}{\partial t}\cdot dt+\frac{\partial f}{\partial Z_1}\cdot dZ_1+\frac{\partial f}{\partial Z_2}\cdot dZ_2+\frac{1}{2}\frac{\partial^2f}{\partial Z_1^2}\cdot dt+\frac{1}{2}\frac{\partial^2f}{\partial Z_2^2}\cdot dt.$$ \tag{27.91.}

The partial derivatives are presented below from (27.92a) to (27.92e)

$$\frac{\partial f}{\partial t}=\left(\mu_Y-\mu_X-\left(\frac{\sigma_Y^2}{2}-\frac{\sigma_X^2}{2}\right)\right)\cdot\frac{Y(t)}{X(t)},$$ \tag{27.92a.}

$$\frac{\partial f}{\partial Z_1}=(\sigma_Y\cdot\rho-\sigma_X)\cdot\frac{Y(t)}{X(t)},$$ \tag{27.92b.}

$$\frac{\partial f}{\partial Z_2}=\sigma_Y\cdot\bar{\rho}\cdot\frac{Y(t)}{X(t)},$$ \tag{27.92c.}

$$\frac{\partial^2f}{\partial Z_1^2}=(\sigma_Y\cdot\rho-\sigma_X)^2\cdot\frac{Y(t)}{X(t)},$$ \tag{27.92d.}

$$\frac{\partial^2f}{\partial Z_2^2}=\sigma_Y^2\cdot\bar{\rho}^{\,2}\cdot\frac{Y(t)}{X(t)}.$$ \tag{27.92e.}

We substitute in (27.91) to get the Stochastic Differential Equation of the ratio of the assets, that is,

$$\frac{d\left(\frac{Y(t)}{X(t)}\right)}{\frac{Y(t)}{X(t)}}=\left[\mu_Y-\mu_X-\left(\frac{\sigma_Y^2}{2}-\frac{\sigma_X^2}{2}\right)+\frac{1}{2}(\sigma_Y\cdot\rho-\sigma_X)^2+\frac{1}{2}\sigma_Y^2\cdot\bar{\rho}^{\,2}\right]\cdot dt+(\sigma_Y\cdot\rho-\sigma_X)\cdot dZ_1+\sigma_Y\cdot\bar{\rho}\cdot dZ_2.$$ \tag{27.93.}

This last equation denotes a simple call option on the asset $\frac{Y(t)}{X(t)}$ with strike equal to one.

Furthermore, the dynamics of this asset satisfies the assumptions of the Black–Scholes model, which means that we can apply the formula if we make the following substitutions:

$\frac{Y(t)}{X(t)} \to S(t)$ $1 \to K$ $1 \to P(t,T)$
$\bar{\sigma} \to \sigma$ $0 \to R.$
(27.98.)

That way we reach the result

$\frac{V(0)}{X(0)} = \frac{Y(0)}{X(0)} N(d_1) - N(d_2)$
(27.99.)

with

$d_1 = \frac{\ln\left(\frac{Y(0)}{X(0)}\right) + \frac{\bar{\sigma}^2}{2}T}{\bar{\sigma} \cdot \sqrt{T}}$ $d_2 = \frac{\ln\left(\frac{Y(0)}{X(0)}\right) - \frac{\bar{\sigma}^2}{2}T}{\bar{\sigma} \cdot \sqrt{T}}.$
(27.100.)

## 27.8 Remarks on Option Pricing

For a review on the early literature on option-pricing, see the two papers by Smith (1976, 1979). It is appropriate here to make a few remarks on the Black–Scholes option-pricing model to clarify its significance and its limitation.

First, the Black–Scholes model for a European call as original derived, and as reported here, is based on several simplifying assumptions.

- 1. The stock price follows an Itô equation.
- 2. The market operates continuously.
- 3. There are no transaction costs in buying or selling the option or the underlying stock.
- 4. There are no taxes.
- 5. The riskless rate is known and constant.
- 6. There are no restrictions on short sales.

Several researchers have extended the original Black–Scholes model by modifying these assumptions. Merton (1973) generalizes the model to include dividend payments, exercise-price changes, and the case of a stochastic interest rate. Roll (1977) has solved the problem of valuing a call option that can be exercised prior to its expiration date when the underlying stock is assumed to make known dividend payments before the option matures.

Ingersoll (1976) studies the effect of differential taxes on capital gains and income while Scholes (1976) determines the effects of the tax treatment of options on the pricing model. Furthermore, Merton (1976) and Cox and Ross (1976) show that if the stock-price movements are discontinuous, under certain assumptions the valuation model still holds.

Derman et al. (1996) replaced the assumption of constant volatility with the concept of the local volatility — volatility that is stochastic in the sense that depends on the asset price — but also not fully stochastic since this dependence is deterministic. This assumption helped explain the existence of volatility smiles but with results that lacked economic intuition. Following a different direction Hull and White (1987) examined the effects of stochastic volatility and the capacity of the extended model to fit parsimoniously market prices. Also, Leland (1985) studied the consequences of introducing transaction costs in the replication of options. These and other modifications of the original Black–Scholes analysis indicate the model is quite robust about the relaxation of its fundamental assumptions.

Second, it is worth repeating that the use of Itô’s calculus and the important insight concerning the appropriate concept of an equilibrium by creating a risk-free hedge portfolio have let Black and Scholes obtain a closed-form solution for option-pricing. In this closed-form solution several variables do not appear, such as (1) the expected rate of return of the stock, (2) the expected rate of return of the option, (3) a measure of investor’s risk preference, (4) investor expectations, and (5) equilibrium conditions for the entire capital market.

Third, the Black–Scholes pricing model has found numerous applications. Among these are: (1) pricing the debt and equity of a firm; (2) the effects of corporate policy and, specially, the effects of mergers, acquisitions, and scale expansions on the relative values of the debt and equity of the firm; (3) the pricing of convertible bonds; (4) the pricing of underwriting contracts; (5) the pricing of leases; and (6) the pricing of insurance. Smith (1976, 1979) summarizes most applications and indicates the original reference. See also Brealey and Myers (1996).

Fourth, Black (1976) shows that the original call-option formula for stocks can be easily modified to be used in pricing call options on futures. The formula is

C(T, F, σ², X, r) = e^{-rT}[F N(d₁) − X N(d₂)],      (27.101.)

d₁ = [ln(F/X) + ½ σ² T] / [σ √T],      (27.102.)
