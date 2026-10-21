```
C = P(0,T) · E^Q
× [ max ( S(0)/P(0,T) · exp{ -σ²T + σ · Z̃(T) } - K, 0 ) | F0 ]
= P(0,T) · E^Q
× [ max ( S(0) · exp{ (R - σ²/2) T + σ · Z̃(T) } - K, 0 ) | F0 ]
```

Now Z̃(t) = Z̃(t) - Z̃(0) is the increment of a Wiener process, that is, it follows the normal distribution with zero mean and variance equal to T, i.e.,

```
C = P(0,T) · ∫_{-∞}^∞ { max ( S(0) · exp{ (R - σ²/2) T + σ · y √T } - K, 0 ) · exp(-y²/2) / √(2π) } dy
```

The option is exercised only when the final stock price is greater than the strike, that is,

```
S(0) · exp{ (R - σ²/2) T + σ · y √T } ≥ K
⇒ exp{ (R - σ²/2) T + σ · y √T } ≥ K/S(0)
⇒ -(R - σ²/2) T - σ · y √T ≤ ln(S(0)/K)
⇒ y ≥ - [ln(S(0)/K) + (R - σ²/2) T] / (σ √T) = -d₂
```

We can then write equation (27.79) as

```
C = P(0,T) · ∫_{-d₂}^∞ { [S(0) · exp{ (R - σ²/2) T + σ · y √T } - K] · exp(-y²/2) / √(2π) } dy
```