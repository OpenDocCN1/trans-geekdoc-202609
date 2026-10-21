# 86.2 Delta (Δ)

The delta of an option, Δ, is defined as the rate of change of the option price with respect to the rate of change of underlying asset price:

$$\Delta = \frac{\partial \Pi}{\partial S},$$

where Π is the option price and S is underlying asset price. We next show the derivation of delta for various kinds of stock option.

# 86.2.1 Derivation of delta for different kinds of stock options

From Black-Scholes option pricing model, we know the price of call option on a non-dividend stock can be written as

$$C_t = S_t N(d_1) - X e^{-r\tau} N(d_2), \qquad (86.1)$$

and the price of put option on a non-dividend stock can be written as

$$P_t = X e^{-r\tau} N(-d_2) - S_t N(-d_1), \qquad (86.2)$$

where

$$d_1 = \frac{\ln\left(\frac{S_t}{X}\right) + \left(r + \frac{\sigma_s^2}{2}\right)\tau}{\sigma_s\sqrt{\tau}},$$
$$d_2 = \frac{\ln\left(\frac{S_t}{X}\right) + \left(r - \frac{\sigma_s^2}{2}\right)\tau}{\sigma_s\sqrt{\tau}} = d_1 - \sigma_s\sqrt{\tau},$$
$$\tau = T - t,$$

N(·) is the cumulative density function of normal distribution:

$$N(d_1) = \int_{-\infty}^{d_1} f(u) du = \int_{-\infty}^{d_1} \frac{1}{\sqrt{2\pi}} e^{-\frac{u^2}{2}} du.$$

First, we calculate
$$N'(d_1) = \frac{\partial N(d_1)}{\partial d_1} = \frac{1}{\sqrt{2\pi}} e^{-\frac{d_1^2}{2}}, \qquad (86.3)$$