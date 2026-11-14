binomial outcome of 50%, in this case the payoff is $6,400 and the 50% payoff is $0; using the probability theory explained below, the fair bet or premium should be at $3,200, representing 50% × $6,400 + 50% × $0.

If we calculate the present value of the $3,200 back to today’s value, since it is what are we paying today for the future outcome, the value is calculated to be $3,047.62 based on the present-value calculation of

```
$PV = \frac{FV}{(1+i)^t} \text{ or } \frac{\$3,200}{(1+0.05)^1} = \$3,047.62$
```

Figure 11.14 calculates the put option premium using the same probabilities. Looking at the put option scenario using the same variables as the call option described above, the payoffs and premiums are calculated differently. If the price of Bitcoin goes up to $56,400, the out-of-the-money put option payoff will be at $0 (P = max (0, X – S) = max (0, $50,000 – $56,400). If the p goes down to $42,300, the put option will be in the money, and the payoff will be $7,700 based on P = max (0, X – S) = max (0, $50,000 – $42,300). Given the binomial outcome of 50%, in this case the payoff is $7,700 and the 50% payoff is $0; using the probability theory explained below, the fair bet or premium should be at $3,850, representing 50% × $7,700 + 50% × $0. If we calculate the present value the $3,850 back to today’s value, since it is what are we paying today for the future outcome, the value is calculated to be $3,666.67 based on the present-value calculation of

```
$PV = \frac{FV}{(1+i)^t} \text{ or } \frac{\$3,850}{(1+0.05)^1} = \$3,666.67$
```

# # Binomial Option Pricing Model:
Two-Period Probability Method

The BOPM using two periods measures four possible outcomes of the cryptocurrency—up and then up, down and then up, down and then down—from any point in time until expiration. The four outcomes illustrated in Figure 11.15 show three possible payoffs, since the cryptocurrency that is going up and then down (Sud) is the same as its going down and then up (Sdu). As before with the single-period BOPM, the up (u) and down (d) values are derived from historical experiences and are used to derive such probabilities. This probability of the cryptocurrency’s going up or down ultimately measures the fair bet or the premium an investor is willing to pay to meets his or her expectation. Figure 11.15 uses an example of how to calculate the premium for both call and put options using two-period BOPM. The example calculates both the European and American structures.