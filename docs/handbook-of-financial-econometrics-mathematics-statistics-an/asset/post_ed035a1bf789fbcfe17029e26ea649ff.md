
The amount equal to the exercise price, $100. The total value of this position will equal the value of the listed put, $20.

### 89.3.4 Portfolio insurance with dynamic hedging

Portfolio insurance is a method of hedging a portfolio of stocks against the market risk by short selling stock index futures. This hedging technique is frequently used by institutional investors when the market direction is uncertain or volatile. Short selling index futures can offset any downturns, but it also hinders any gains. Portfolio insurance is an investment strategy where various financial instruments such as equities, debts, and derivatives are combined in such a way that degradation of portfolio value is protected. It is a dynamic hedging strategy which uses stock index futures. It implies buying and selling securities periodically in order to maintain the limit of the portfolio value. The working of portfolio insurance is akin to buying an index put option, and can also be done by using the listed index options. The technique, invented by Hayne Leland and Mark Rubinstein in 1976, is often associated with the October 19, 1987, stock market crash.

As a practical matter, rather than buying, selling, or short selling stocks, a portfolio manager may trade (buy or sell) stock-index futures to adjust the exposure of a portfolio. If the stock market is declining, futures contracts are sold to effectively reduce the position in the portfolio. The selling of stock-index futures has the same effect on the portfolio as the sale of stocks and the investment in a risk-free asset. As the market turns around and begins to go up in value, the portfolio manager purchases futures contracts to cover the short position by liquidating the investment in the risk-free asset. This procedure is called dynamic hedging. Whether it works depends upon a high degree of correlation between the value of index-futures contracts and the value of the underlying index. For most time periods, there is a very high degree of comovement between the index and the futures contract. However, this may not always be the case.

Suppose that a portfolio manager wishes to insure a portfolio of well-diversified stocks with a value of $1 million, and the portfolio beta is 1.1 when measured relative to the S&P 500. (This means that if the S&P 500 goes up or down by 1%, the change in the value of the portfolio will be 1.1%.) If the portfolio manager is worried about a market decline, he or she can insure his or her portfolio by selling S&P 500 index futures contracts. By selling futures contracts, the fall in the value of the portfolio would be offset by gains in the futures market. If the strategy for portfolio insurance incorporates the beta, the following relationship is necessary to determine the number of contracts required to insure the portfolio:

\[
\text{Number of contracts} = \frac{\text{Value of portfolio}}{\text{Value of futures contracts}} \times \beta . \tag{89.7}
\]

Equation (89.7) is a hedge ratio without considering the risk-return tradeoff and degree of risk aversion. Hedge ratios consider these factors, which can be found in Chen et al. (2019).

Assume the S&P 500 index is selling at $110, and the portfolio is worth $1 million on day 1. If the market falls by 10%, the value of the portfolio falls 11% to $890,000, the value of the S&P 500 futures contract falls to $99, and the scenario is as follows.

1. The portfolio has lost $110,000.
2. Each S&P 500 futures contract sold can be repurchased for $99 × 500, or $49,500, for a gain of $5,500 ($55,000 − $49,500).

In order to have a perfect hedge, the portfolio manager would need $110,000 / $5,500 = 20 contracts. Using equation (89.7), we see that adjusting the number of contracts for the volatility or beta of the portfolio yields

\[
\text{Number of contracts} = \frac{\$1{,}000{,}000}{\$110 \times 500} \times 1.1 = 20 \text{ contracts}.
\]

This result of a perfect hedge is dependent upon two critical assumptions.

1. The relationship of the volatility of the portfolio to the volatility of the index remains the same or the beta does not change.
2. The movement of the price of the futures contract is in lock step with the movement of the index; they are perfectly correlated.

In spite of the problems for portfolio insurance associated with the validity of these critical assumptions, the use of futures contracts for portfolio hedging is widespread. The main reason why futures have been accepted as a trading vehicle for portfolio insurance is the low trading costs. This and the following reasons have led to rapid growth in the use of futures contracts for insuring portfolios during the early part of the 1980s.

1. Low trading costs allow for rapid and frequent adjustments in implementing the portfolio strategy.
2. Futures markets are liquid enough for insurance programs for large institutional portfolios.
3. The use of futures allows for independence between management of the risky assets in the portfolio and the portfolio insurance.

## 89.4 Comparison of Alternative Portfolio-Insurance Strategies

This section compares alternative portfolio-insurance strategies — that is, synthetic options, listed put options, and dynamic hedging.

### 89.4.1 *Synthetic options*

As previously discussed, *synthetic options* are not options but a strategy for allocating assets that replicates the return on a call option. There are four advantages to using a dynamic-hedging strategy instead of a synthetic-option approach. First, the futures contracts have lower transaction costs than stocks. Kidder, Peabody reports that index funds pay one-way transaction costs of $125 for $100,000 of stock, or 0.125% (they assume a commission of $0.05 per share at an average price of $40), and institutional clients pay approximately $0.06 per share (Hill, 1987). In contrast, one-way futures transaction costs for institutional investors are $15 per $100,000, or 0.015%. Thus, the transaction costs for futures are one-eighth to one-tenth of the cost of trading stocks, thereby reducing the cost of dynamic hedging compared with synthetic options. Second, liquidity is much greater in the futures market than in options or stock markets. For example, during the large downside movement in the stock market on September 11–12, 1986, the consulting arm of Leland O’Brien Rubinstein Associates sold more than $500 million of stock-index futures (Anders, 1986). Such large transactions could not be made in options markets.

The third advantage is that futures contracts are highly levered and less cash is necessary to carry out a dynamic-hedging strategy. As little as $2,000 can control each futures contract. The fourth advantage is that because stocks are not sold, the management of the stock portfolio is independent of the portfolio insurance. In contrast, managers must be active when implementing a synthetic option because the underlying stock is bought or sold to replicate the returns on an option.

The main disadvantage of dynamic hedging with respect to synthetic options is the tracking error that might occur because the futures are not perfectly correlated with the stock. This is not a problem with synthetic options because the stock itself is purchased or sold.

Another disadvantage of implementing either a dynamic-hedging or synthetic-option strategy is that they require continuous monitoring to insure that the delta of the replicated put equals the delta of a theoretical option. The replicated put must be rebalanced at certain intervals to maintain a proper mix of stock and futures. Here, a tradeoff results: the more frequent the rebalancing, the better the replication of the theoretical put; however, more frequent rebalancing also results in higher transaction costs. Thus, determining when to rebalance the portfolio is a major decision when implementing a synthetic-option or dynamic-hedging strategy in the presence of transaction costs.

There might be a price advantage or disadvantage to a dynamic-hedging strategy due to futures mispricing. When shorting futures for hedging purposes, the manager hopes that the futures sell at a premium and the basis (the cash price minus the futures price) widens. By selling futures when they are expensive and buying them back at a lower price, a profit results on the hedge. On the other hand, losses on the hedge will probably result if “cheap” futures are sold for hedging purposes. The following example illustrates these concepts. Suppose that a manager holds a portfolio worth $250 and shorts futures on the same portfolio that are worth $260. The basis is $250 − $260 = −$10. Because the basis is equal to zero at expiration, the negative basis will have to increase.

In this example, the investor makes a profit of $10 on the hedge, regardless of how the portfolio performs. The profit is a result of selling “expensive” futures and waiting for the basis to increase (see Table 89.3). In contrast, suppose that an investor with a portfolio worth $250 shorts futures worth $245. In this example, the investor will lose money if he waits until expiration, because the basis will decrease (see Table 89.4).

Here, the basis decreases and losses result for the hedger. Cheap futures will increase the costs of implementing a dynamic-hedging strategy and expensive futures will reduce the costs. The dynamic hedger hopes to sell futures selling at a premium and buy the futures at a discount.

The synthetic-call approach is usually used when implementing a portfolio-insurance strategy without futures. Thus, more of the risky asset is purchased when performance is favorable and the stock is sold when the

**Table 89.3: Profit or loss of expensive futures.**

| Value of stock at expiration of futures | Value of futures at expiration | Profit or loss on stock | Profit or loss on futures | Profit or loss |
|---|---|---|---|---|
| 270 | 270 | +20 | -10 | +10 |
| 230 | 230 | -20 | +30 | +10 |
