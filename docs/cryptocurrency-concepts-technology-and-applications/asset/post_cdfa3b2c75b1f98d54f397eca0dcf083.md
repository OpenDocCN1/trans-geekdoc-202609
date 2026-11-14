

simple example, let's assume that the payoff is $20 if the coin turns up to be heads (H) and $0 if the coin turns out to be tails (T). On a toss of a die, the winner will be paid $60 if it turns out to be a 6. The likelihood (probability) that on one single throw the die will turn out to be 6 is one in six (1/6), and the probability of not getting a 6 is five out of six (5/6). To evaluate what a fair bet would be based on these games of chance, the formula starts with the following decision tree, shown in Figures 11.12a and 11.12b.

![](img/f08f3915c6e1afa13e4417a1426bd7c3_248_0.png)

![](img/f08f3915c6e1afa13e4417a1426bd7c3_248_1.png)

The figures show that the winnings or payoffs as $20 and $60 for the coin toss and dice throw, respectively. Using the probability formulas derived from the decision tree, the bets are calculated as follows:

$$ \text{Coin toss bet} = \frac{1}{2} (\$20) + \frac{1}{2} (\$0) = \$10 $$

$$ \text{Die toss bet} = \frac{1}{6} (\$60) + \frac{5}{6} (\$0) = \$10 $$

The wins or losses of these games of chance represent the option payoff, and the outcome from the toss of a coin and throw of a die represent the cryptocurrency spot price. This probability formula concept can be used to determine the fair bet that the player needs to pay up front to enter this game; this fair bet represents the premium that the investor needs to pay upfront to have the right to exercise such an option when there is a positive payoff outcome. The challenge is to derive such probabilities when the investor is betting on the direction of the cryptocurrency in the future. Such direction is measured by historical cryptocurrency spot price movements, expressed in statistics as the variance ($\sigma^2$) of the cryptocurrency spot price or standard deviation ($\sigma$). A few such valuation models that use cryptocurrencies spot price variances and standard deviations are the binomial option pricing model and Black-Scholes.*

## Binomial Option Pricing Model: Single-Period Probability Method

The binomial option pricing model (BOPM) continuously measures the two possible outcomes of the cryptocurrency, up or down, from any point in time until expiration. As the spot price of cryptocurrency goes up, the probability it will continue to go up can change versus the probability of going down from that new level. The up (u) and down (d) values are derived from historical experiences and are used in the BOPM to derive such probabilities. The probability of the cryptocurrency spot price’s (S) going up or down is ultimately measured to be the fair bet or the premium an investor is willing to pay to meet his or her expectation. Figure 11.13 uses an example on how to calculate the premium using BOPM.

Figure 11.13 shows there is a 50% probability that the price of Bitcoin will go up from its current level of $47,000 to $56,400 and a 50% probability that it will go down to $42,300 within the measurable period, in this case one year. The probability calculation is as follows:

```
p = \frac{[(1 + i) - d]}{u - d} = \frac{[(1 + 0.05) - 0.90]}{1.20 - 0.90} = \frac{1.05 - 0.90}{1.20 - 0.90} = \frac{0.15}{0.30} = 0.5 \text{ and } i - p = 0.5
```

If the price of Bitcoin goes up to $56,400, the call option payoff will be $6,400 (C = max (0, S – X) = max (0, $56,400 – $50,000). If the price of Bitcoin goes down to $42,300, the call option will be out of the money, and the payoff will be $0 based on C = max (0, S – X) = max (0, $42,300 – $50,000). Given the

## ONE-PERIOD BINOMIAL OPTION PRICING MODEL - Calculating the Call Option Premium

### INPUT

| Item | Value |
|------|-----|
| Current Bitcoin (S) | $47,000 |
| Up (u) | 1.20x |
| Down (d) | 0.90x |
| Exercise Price (X) | $50,000 |
| Risk Free Rate (I) | 5.00% |
| Time in Years (t) | 1 |
| Periods | 1 |

### OUTPUT

| | PERIOD 0 | PERIOD 1 |
|---|---|---|
| Su= 56,400 -> Cu= | 6,400.00 | |
| S = 47,000.0 | | |
| Sd = 42,300 -> Cd= | - | |
| C = 3,047.62 | | |
| p = 0.50 | | |
| 1-p = 0.50 | | |
| C= 3,047.62 European Option Premium | | |

### FORMULAS

- Su = S . u
- Sd = S . d
- Cu = Max (0, Su - X)
- Cd = Max (0, Sd - X)
- p = [(1+i) - d ] / (u - d)
- C= [ (p . Cu) + [(1-p) Cd] ] / [(1+i)^t]

Figure 11.13 One-Period Binomial Option Pricing Model—Calculating Call Option Premium

binomial outcome of 50%, in this case the payoff is $6,400 and the 50% payoff is $0; using the probability theory explained below, the fair bet or premium should be at $3,200, representing 50% × $6,400 + 50% × $0.

If we calculate the present value of the $3,200 back to today’s value, since it is what are we paying today for the future outcome, the value is calculated to be $3,047.62 based on the present-value calculation of

```
$PV = \frac{FV}{(1+i)^t} \text{ or } \frac{\$3,200}{(1+0.05)^1} = \$3,047.62$
```

Figure 11.14 calculates the put option premium using the same probabilities. Looking at the put option scenario using the same variables as the call option described above, the payoffs and premiums are calculated differently. If the price of Bitcoin goes up to $56,400, the out-of-the-money put option payoff will be at $0 (P = max (0, X – S) = max (0, $50,000 – $56,400). If the price goes down to $42,300, the put option will be in the money, and the payoff will be $7,700 based on P = max (0, X – S) = max (0, $50,000 – $42,300). Given the binomial outcome of 50%, in this case the payoff is $7,700 and the 50% payoff is $0; using the probability theory explained below, the fair bet or premium should be at $3,850, representing 50% × $7,700 + 50% × $0. If we calculate the present value the $3,850 back to today’s value, since it is what are we paying today for the future outcome, the value is calculated to be $3,666.67 based on the present-value calculation of

```
$PV = \frac{FV}{(1+i)^t} \text{ or } \frac{\$3,850}{(1+0.05)^1} = \$3,666.67$
```

## Binomial Option Pricing Model: Two-Period Probability Method

The BOPM using two periods measures four possible outcomes of the cryptocurrency—up and then up, down and then up, down and then down—from any point in time until expiration. The four outcomes illustrated in Figure 11.15 show three possible payoffs, since the cryptocurrency that is going up and then down (Sud) is the same as its going down and then up (Sdu). As before with the single-period BOPM, the up (u) and down (d) values are derived from historical experiences and are used to derive such probabilities. This probability of the cryptocurrency’s going up or down ultimately measures the fair bet or the premium an investor is willing to pay to meets his or her expectation. Figure 11.15 uses an example of how to calculate the premium for both call and put options using two-period BOPM. The example calculates both the European and American structures.

## ONE-PERIOD BINOMIAL OPTION PRICING MODEL - Calculating the Put Option Premium

### INPUT

| Item | Value |
|------|-----|
| Current Stock (S) | $47,000 |
| Up (u) | 1.20x |
| Down (d) | 0.90x |
| Exercise Price (X) | $50,000 |
| Risk Free Rate (i) | 5.00% |
| Time in Years (t) | 1 |
| Periods | 1 |

### OUTPUT

| | PERIOD 0 | PERIOD 1 |
|---|---|---|
| S = 47,000 | | |
| Su = 56,400 -> Cu = | - | |
| Sd = 42,300 -> Cd = | 7,700.00 | |
| C = 3,666.67 | | |
| p = 0.50 | | |
| 1-p = 0.50 | | |
| P = 3,666.67 European Option Premium | | |

### FORMULAS

- Su = S . u
- Sd = S . d
- Pu = Max (0, X-Su)
- Pd = Max (0, X-Sd)
- p = [(1+i) - d] / (u - d)
- P = [ (p . Pu) + [(1-p) Pd] ] / [(1+i)^Freq]

Figure 11.14 One-Period Binomial Option Pricing Model—Calculating Put Option Premium

## TWO-PERIOD BINOMIAL OPTION PRICING MODEL - Call and Put Options

### INPUT

### CALL OPTION

| Item | Value |
|------|-----|
| S | $47,000 |
| u | 1.20x |
| d | 0.90x |
| X | $50,000 |
| i | 5.00% |
| Frequency | 1 |
| Periods | 2 |

Frequency: (Annual = 1, Semiannual = 2, Quarterly = 4)

![](img/f08f3915c6e1afa13e4417a1426bd7c3_253_0.png)

### FORMULAS

- Su= S . u
- Sd= S . d
- Su²= S . u²
- Cu²= Max (0, Su²- X)
- Cd²= Max (0, Sd²- X)
- Cud= Max (0, Sud- X)
- p = [{(1+ i) / d]} - { (u - d) ] / [{(1+i)^Freq]
- Cu= [ {p . Cu²} + {(1-p) Cud)] / [{(1+i)^Freq]
- Cd= [ {p . Cud} + {(1-p) Cd²]] / [{(1+i)^Freq]
- C= [ {p . C1} + {(1-p) C2]] / [{(1+i)^Freq]

### INPUT

### PUT OPTION

| Item | Value |
|------|-----|
| S | $47,000 |
| u | 1.20x |
| d | 0.90x |
| X | $50,000 |
| i | 5.00% |
| Frequency | 1 |
| Periods | 2 |

Frequency: (Annual = 1, Semiannual = 2, Quarterly = 4)

![](img/f08f3915c6e1afa13e4417a1426bd7c3_253_1.png)

### FORMULAS

- Su= S . u
- Sd= S . d
- Su²= S . u²
- Pu²= Max (0, X- Su²)
- Pd²= Max (0, X - Sd²)
- Pud= Max (0, X - Sud)
- p = [{(1+ i) / d]} - { (u - d) ] / [{(1+i)^Freq]
- Pu= [ {p . Pu²} + {(1-p) Pud)] / [{(1+i)^Freq]
- Pd= [ {p . Pud} + {(1-p) Pd²]] / [{(1+i)^Freq]
- P= [ {p . P1} + {(1-p) P2]] / [{(1+i)^Freq]

