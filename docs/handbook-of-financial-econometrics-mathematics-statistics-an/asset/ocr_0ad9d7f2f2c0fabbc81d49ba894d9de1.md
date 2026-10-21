= X e^{-rτ} \frac{\partial(1 - N(d_2))}{\partial d_2} \frac{\partial d_2}{\partial S_t} - e^{-qτ}(1 - N(d_1))
- S_t e^{-qτ} \frac{\partial(1 - N(d_1))}{\partial d_1} \frac{\partial d_1}{\partial S_t}
= -X e^{-rτ} \frac{1}{\sqrt{2π}} e^{-\frac{d_2^2}{2}} \cdot \frac{S_t}{X} \cdot e^{(r-q)τ} \cdot \frac{1}{S_t σ_s \sqrt{τ}} - e^{-qτ}(1 - N(d_1))
+ S_t e^{-qτ} \frac{1}{\sqrt{2π}} e^{-\frac{d_2^2}{2}} \cdot \frac{1}{S_t σ_s \sqrt{τ}}
= -S_t e^{-qτ} \frac{1}{S_t σ_s \sqrt{2π τ}} e^{-\frac{d_1^2}{2}} + e^{-qτ}(N(d_1) - 1)
+ S_t e^{-qτ} \frac{1}{S_t σ_s \sqrt{2π τ}} e^{-\frac{d_1^2}{2}}
= e^{-qτ}(N(d_1) - 1).

# 86.2.2 Application of delta (Δ)

Figure 86.1 shows the relationship between the price of a call option and the price of its underlying asset. The delta of this call option is the slope of the line at the point of A corresponding to current price of the underlying asset.

By calculating delta ratio, a financial institution that sells option to a client can make a delta-neutral position to hedge the risk of changes of the underlying asset price. Suppose that the current stock price is $100, the call option price on stock is $10, and the current delta of the call option is 0.4.

![](bbox=[0.22, 0.75, 0.8, 0.88])

Figure 86.1: The relationship between the price of a call option and the price of its underlying asset.