
Solving these equations results in Δ_u = 0.9545 and M_u = 92.22. Thus the value of the replicating portfolio is 110 × Δ_u − M_u = $12.78. If instead, 6 months from now the stock declines 10% in value, to $90 (the down state), the stock price at the expiration of the option will either be $99 or $81, which is always less than the exercise price. Thus the option is worthless a year from now if the down state is realized 6 months from now, and consequently the value of the option in the down state is zero. Given the two possible values of the option 6 months from now, it is now possible to derive the number of shares of the stock that one needs to buy and the amount necessary to borrow to replicate the option payoffs in the up and down state 6 months from now. Since the option is worth $12.78 and $0 in the up and down states, respectively, it follows that

$110 × Δ − 1.0247 × M = $12.78 Eq 10.6

and

$90 × Δ − 1.0247 × M = $0 Eq 10.7

Solving Equations 10.6 and 10.7 results in Δ = 0.6389 and M = $56.11. Thus the value of the option price today is 100 × Δ − M = $7.77. The values of the stock option are shown graphically in Figures 10.2 and 10.3.

A feature of this replicating portfolio is that it is always self-financing. Once it is set up, no further external cash inflows or outflows are required in the future. For example, if the replicating portfolio is set up by borrowing $56.11 and buying 0.6389 shares of the stock and in 6 months the up state is realized, the initial portfolio is liquidated. The sale of the 0.6389 shares of stock at $110 per share nets $70.28. Repaying the loan with interest, which amounts to $57.50, leaves $12.78. The new replicating portfolio requires borrowing $92.22. Combining this amount with the proceeds of $12.78 gives $105, which is exactly enough to buy the required 0.9545 shares of stock at $110 per share. Replicating portfolios always have this property: liquidating the current portfolio nets exactly enough money to form the next portfolio. Thus the portfolio can be set up today, rebalanced at the end of each period with no infusions of external cash, and at expiration should match the payoff of the option, no matter which states of the world occur.

In the replicating portfolio presented above, the option expires either one or two periods from now, but the same principle applies for any number of periods. Given, in this example, that there are only two possible states over each period, a self-financing replicating portfolio can be formed at each date and state by trading in the stock and a risk-free asset. As the number of periods increases, the individual periods get shorter so that more and more possible states of the world exist at expiration. In the limit, continuums of possible states and periods exist so that the portfolio will have to be continuously rebalanced. The Black–Scholes–Merton model, discussed below, is the limiting case of these models with a limited number of periods.

## Determining the value of call options

A call option is the right to purchase the underlying asset for a specified exercise price until the expiration date. As discussed earlier, American options can be exercised at any time. European options can be exercised only at the expiration date. In the discussion below, which draws on Livingston (1996), the following notation is used:

- C = market value of the call option
- P = market value of the underlying asset
- E = exercise price (strike price)

If the price of the underlying asset (P) is less than the exercise price (P<E), the call is described as being out-of-the-money. If P equals E, the call option is described as being at-the-money. If the price of the underlying asset exceeds the exercise price (P>E), the call option is described as being in-the-money.

### What is the value of the call option at expiration?

At expiration, the value of the call option must be zero if the market value of the underlying asset is less than or equal to the exercise price. No rational investor would exercise a call option if the underlying asset sells for the exercise price or less since buying the underlying security in the open market would be cheaper than exercising the call option. For example, in Table 10.3, if a bond sells for $90 in the open market, a call option with an exercise price of $100 is valueless at expiration. Instead of exercising the call and paying the $100 exercise price, it is preferable to buy the bond directly for $90.

In Table 10.3, if the price of the underlying asset exceeds the exercise price, the call option is worth the price of the underlying asset minus the exercise price, that is, P − E. The amount P − E is called the intrinsic value of a call option. If the call option sells for less than P − E, an arbitrageur would buy the call, exercise it and make an arbitrage profit. At expiration, buying the call option for $C and exercising it is equivalent to buying the underlying security directly for $P. Thus, P = C + E, or C = P − E.

At expiration, the value of a call option is:

C = 0      if P ≤ E   at- or out-of-the-money      Eq 10.8

C = P − E   if P > E                               10.9

### Table 10.3 Value of call option at expiration (E = $100)

| P < E | P = E | P > E |
|---|---|---|
| e.g., P = 90 | P = 100 | P = 110 |
| C = 0 | C = 0 | C = P − E |
|  |  | e.g. C = 10 |
| out-of-the-money | at-the-money | in-the-money |

Source: Livingston, 1996

### What is the profit profile for a call option?

The possible value of a call option can be seen from a profit profile. As a reference point, consider someone who buys a bond (for which options trade) currently selling at its exercise price of $100 and holds this bond for 3 months until the option expires. The possible profits and losses, overlooking coupon interest, are shown as a solid line in Figure 10.4.

Consider the purchase of a call option for $4 with an exercise price of $100. The investor holds this call option for 3 months until expiration. The profit profile is shown as the dotted line in Figure 10.4. The first step in drawing the profit profile is to compute the profit and loss on the position for several levels of the price of the underlying asset at expiration. These prices should include the option’s exercise price and several points on either side of the exercise price. The procedure is illustrated in Table 10.4.

![](img/67ce553842aa835a611c7cbbbb028358_182_0.png)

Figure 10.4 Profit profiles for a call option. Source: Livingston, 1996

The call buyer suffers a loss of $4, the entire purchase, if the bond price is below the exercise price of $100. This $4 is the maximum loss for the buyer of a call option. If the bond price at expiration is above the exercise price, the profit equals P − E = $4. A net loss is incurred if the bond price is below $104 and a net profit if the bond price is above $104. The profit profile indicates that call buyers are anticipating a rising price for the underlying asset.

If the bond price is at or below the exercise price, the profit profile shows the call buyer’s maximum loss to be the purchase price, C, since this call purchase price is a small percentage of the bond price, the loss from buying a call is small in absolute dollars compared to the loss from purchasing the bond outright. On the other hand, the call buyer gains substantially if the bond does well.

### Table 10.4 Profits or losses for a call buyer (E = $100)

|  | Price of underlying security at expiration |  |  |  |
|---|---|---|---|---|
|  | 98 | 100 | 102 | 104 |
| Buy call (C) | -4 | -4 | -4 | -4 |
| Exercise call at expiration |  |  | -100 | -100 |
| Sell underlying bond acquired from exercising option |  |  | +102 | +104 |
| Net profit = +C −E +P | -4 | -4 | -2 | 0 |

Source: Livingston, 1996

For everyone who buys a call option, someone sells or writes the call. The call writer agrees to sell the underlying asset at the exercise price if the option is exercised by the call buyer. Call options are a zero-sum game, meaning that the call buyer’s gains are the call writer’s losses and vice versa. In effect, the buyer and the writer are betting against each other.

### What are the determinants of the value of a call option?

The value of a call option is determined by the following six factors.

- (1) **The price of the underlying asset:** The value of a call option is positively related to the price of the underlying security. The higher the value of the underlying asset, the greater the value of the call option. This is not surprising, as a call buyer has bought the right to buy at a fixed price. The more the underlying asset rises the more the call option is worth, and vice versa.
- (2) **The exercise price:** The value of a call option is inversely related to the exercise price. The lower the exercise price, the higher the value of the call option. Other things being equal, a lower exercise price means that the call option is more in-the-money. Again this is not surprising as this is what the call option owner has to pay when he exercises the option.
- (3) **The time until expiration:** The value of a call option is a positive function of time until expiration. The longer the time until expiration, the greater the value of the call option. The reason for this is that the call owner has more time to allow his option to get in-the-money.

The first three determinants of call option value are illustrated by Table 10.5. Look across any row of the table; the value of the call option decreases as the exercise price increases. Look down any column; as time to maturity increases and the value of the call option also increases.

- (4) **The price volatility of the underlying asset:** The greater the volatility of the underlying asset, the higher the value of
