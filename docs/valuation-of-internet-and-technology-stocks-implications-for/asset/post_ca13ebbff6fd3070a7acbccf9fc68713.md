
and sellers have an agreement with the clearing corporation. Ultimately, if a trader takes delivery rather than offsets the contract, i.e., reverses it, the exchange will select someone who is what is technically known as ‘short’ the contract to make delivery. The party making delivery does not have to be the party who sold the contract originally. After the trade settles, the original parties to the trade lose any direct tie to each other based on the trade. No credit intermediary is necessary, but margin must be deposited to ensure each party meets its obligations.

The exchange clearing corporation has to stand behind the credit-worthiness of its members, so it asks everyone for a deposit. Customers make a deposit with their broker, known as margin, and the broker passes the deposit to the clearing corporation. Futures margin is a good faith deposit, demonstrating ability and willingness to meet contractual obligations. Table 10.1 illustrates the advantages and disadvantages of futures and forward contracts.

**Table 10.1 The advantages and disadvantages of futures and forwards**

|  | Futures markets | Forward markets |
|---|---|---|
| Default risk | + Low | – Greater than for futures |
| Transaction costs/commissions | + Low | – Higher than for futures |
| Standardization | + Contracts are liquid; allows for secondary market<br>– Imperfect hedge | – No secondary market<br>+ Tailor-made hedge |
| Interest rate risk | – Daily cash flows from marking to market must be deposited at unknown interest rates | Not applicable |
| Contract sizes and underlying currencies | – Limited number of contracts and underlying securities makes hedging with futures less effective | + Tailor-made |
| Maturities | – Short maturity only | + Slightly longer to much longer maturities than for futures |

## How are options priced?

The method used to price options depends on the type of option being priced. As can be seen from Table 10.2, the two pricing models are the binomial model used for American options, which was designed by Cox, Ross and Rubinstein, and the Black–Scholes option pricing model, used for pricing European options. As we show below, the binomial model can also be used to price European options.

**Table 10.2 European versus American options**

| Type of option | Exercise date | Pricing model |
|---|---|---|
| American option | Any time up to maturity | Cox, Ross and Rubinstein |
| European option | At maturity date | Black–Scholes |

The key to valuing options is to design a risk-free portfolio in which the value does not change when there is a change in the underlying asset. This risk-free element is achieved by designing a portfolio which replicates, i.e., one in which the payoffs of the portfolio exactly match the payoffs of the option. A good example of this is achieved by applying the binomial model.

### The binomial model

### One-period binomial model – the role of the replicating portfolio

To illustrate the binomial model it is necessary to look at what the effect of the prices of the underlying stock rising or falling in price should have on the option price. Our first example is a European call option on a stock, and assuming that the stock is currently valued at $100. In this example an option to purchase this stock expires in one year and the strike or exercise price is $100. The annual risk-free interest rate is 5%, so that borrowing $1 today will mean having to pay back $1.05 one year from now. For simplicity, the assumption here is that there are only two possible outcomes when the option expires – the stock price can be either $120 (an up state) or $80 (a down state). Note that the value of the call option will be $20 if the up state occurs and $0 if the down state occurs, as shown in Figure 10.1.

![](img/67ce553842aa835a611c7cbbbb028358_176_0.png)

**Figure 10.1 Stock and option values in the one-period model**

In other words, if the price falls to $80 the option becomes valueless.

Since there are only two possible states in the future it is possible to replicate the value of the option in each of these states by forming a portfolio of the stock and risk-free asset. If Δ, an unknown number of shares of the stock are purchased and M, an unknown number of dollars, are borrowed at the risk-free rate, the stock portion of the portfolio is worth 120 × Δ in the up state and 80 × Δ in the down state while 1.05 × M will have to be paid back in either of the two states. Thus, to match, or replicate, the value of the portfolio to the value of the option in the two possible states, it must be the case that

$120 × Δ − 1.05 × M = $20 (up state, Eq 10.2)

and

$80 × Δ − 1.05 × M = $0 (down state, Eq 10.3)

By rearranging the formulae from Equations 10.2 and 10.3, we get a value for Δ: $40Δ = 20, so Δ = 0.5. Inserting Δ = 0.5 in Equation 10.2 gives us $120 × 0.5 − 1.05M = $20, so $40 = 1.05M and M = $38.10.

The resulting system of two equations with two unknowns Δ and M, solved above, gives us Δ = 0.5, and M is approximately $38.10. This means that one would need to buy 0.5 shares of the stock and borrow $38.10 at the risk-free rate in order for the value of the portfolio to be $20 and $0 in the up state and down state, respectively. Equivalently, selling 0.5 shares of the stock and lending $38.10 at the risk-free rate would mean payoffs from that portfolio of –$20 and $0 in the up and down states, respectively, which would completely offset the payoffs from the option in those states. This is a very powerful finding as it enables us to replicate the risk-free portfolio and price the options accordingly. It is also worth noting that the current value of the option must equal the current value of the portfolio, which is 100 × Δ – M = 100 × 0.5 – M = $11.90. In other words, a call option on the stock is equivalent to a long position in the stock financed by borrowing at the risk-free rate.

The variable Δ is called the delta of the option. In the previous example, if C_u and C_d denote the values of the call option in the up and down states, with S_u and S_d denoting the price of the stock in the up and down states, respectively, then it can be verified that Δ = (C_u – C_d)/(S_u – S_d). The delta of an option reveals how the value of the option is going to change with a change in the stock price. For example, knowing Δ, C_d, and the difference between the stock prices in the up and down states makes it possible to know how much the option is going to be worth in the up state, that is to say that C_u is also known.

### The two-period binomial model

A model in which a year from now there are only two possible states of the world is certainly not realistic, but construction of a multi-period model can alleviate this problem. The one-period model assumes a replicating portfolio for a call option on a stock currently valued at $100 with a strike price of $100 and which expires in a year. However, let us now assume the year is divided into two 6-month periods and the value of the stock can either increase or decrease by 10% in each period. Assume the semi-annual risk-free interest rate is 2.47%, which is equivalent to an annual compounded rate of 5%. The states of the world for the stock values are given in Figures 10.2 and 10.3. Given this structure, how does one build a portfolio of the stock and the risk-free asset to replicate the option? The calculation is similar to the one above except that it is done recursively, starting one period before the option expires and working backward to find the current position.

![](img/67ce553842aa835a611c7cbbbb028358_178_0.png)

**Figure 10.2 Stock values in the two-period model**

![](img/67ce553842aa835a611c7cbbbb028358_178_1.png)

**Figure 10.3 Option values in the two-period model**

In the case in which the value of the stock over the first 6 months increases by 10% to $110 (that is, the up state 6 months from now), the value of the option in the up state is found by forming a replicating portfolio containing Δ_u shares of the stock financed by borrowing M_u dollars at the risk-free rate. Over the next 6 months, the value of the stock can either increase another 10% to $121 or decline 10% to $99, so that the option at expiration will be worth either $21 or $0. Since the replicating portfolio has to match the values of the option, regardless of whether the stock price is $121 or $99, the Equations 10.4 and 10.5 must be satisfied:

$121 × Δ_u − 1.0247 × M_u = $21 (Eq 10.4)

and

$99 × Δ_u − 1.0247 × M_u = $0 (Eq 10.5)
