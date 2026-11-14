
investor recovers the $10,000 back, netting a total loss of $4,000. The rule is that the investor always exercises the option if the option is in the money or S - X > 0. The following formulas are used for calculating the output when buying a call option:

```
Call option payoff = Maximum (0, cryptocurrency price – exercise price), max (0, S – X)
Call option profit = Payoff–premium
Holding period return % = Profit/premium
Break-even cryptocurrency price for call option = Exercise price + premium
Maximum loss on buying a call option = Premium
Maximum gain on buying a call option = Unlimited
```

## Buying Put Options

A put option is a contract that gives the holder the right, not the obligation, to sell cryptocurrency at exercise price (X), at and before the expiration date, no matter what happens to the price of the cryptocurrency. Of course, if the investor has the right to sell the set number of cryptocurrencies at a set price, he or she is then hoping that the price of the cryptocurrency goes down significantly and can profit from the difference, representing a bearish view on the cryptocurrency.

For example, the June put option on Bitcoin with an exercise price of $60,000 entitles its owner to buy Bitcoin at a price of $60,000 by the third Friday of June (contract expiration date). If the Bitcoin goes down to $40,000 before the third week of June, the option holder will buy it at $40,000 from the market and exercise the right to sell it at $60,000, profiting from the $20,000 difference. If the Bitcoin goes above $60,000, the option holder will let the contract expire without exercising. To purchase the option, the investor needs to pay premium upfront. In this example, the buyer of the June Bitcoin option will need pay $14,110 (please note that the investor can purchase a fraction of the Bitcoin). Figure 11.2 shows the payoff, profit, HPR and BE of Bitcoin stock during various scenarios and prices (using a range of $20,000–$100,000).

Figure 11.2 shows that if the range of the price of Bitcoin is above $60,000, the put option is not exercisable, since the exercise price (X) minus the Bitcoin spot price (S) is negative, representing the out-of-money option. At $60,000, where Bitcoin (S) is equal to the exercise price (X), the call option is at the money and not exercisable since there is zero payoff (X – S = 0). If Bitcoin is lower than $60,000, the put option is exercisable, or an in-the-money option. It’s important to note that being in the money does not necessarily mean that the option is profitable. It means that there is a payoff. We see in the example in Figure 11.2 that if Bitcoin is at $40,000 on the last day, then the investor needs to exercise the option with

## 2. UNCOVERED (NAKED) OPTION STRATEGIES - Buying a Put Option

| BTC | PUTS | | |
|---|---|---|---|
| Exercise Price (X) | APRIL | MAY | JUNE |
| 20,000 | 9 | 250 | 225 |
| 30,000 | 90 | 400 | 900 |
| 40,000 | 750 | 1277 | 2500 |
| 50,000 | 4200 | 5102 | 6100 |
| 60,000 | 13500 | 14000 | 14110 |
| 70,000 | 22900 | 23000 | 29754 |
| 100,000 | 53000 | 53500 | 58722 |

![](img/f08f3915c6e1afa13e4417a1426bd7c3_230_0.png)

ACTION
- Buy Put @ Exercise (X) = $ 60,000.00
- Pay Premium (p) = $ 14,110.00

Break Even = $ 45,890.00
Max Loss = $ (14,110.00)
Max Gain = X - Premium at S=0

- Out-of-the-money Option
- On-the-money Option
- In-the-money Option

| ACTION | Exercise Price (X) | Premium Per Bitcoin (p) |
|---|---|---|
| Buy April 60,000 Put | 60,000 | (14,110) |
| Buy April 60,000 Put | 60,000 | (14,110) |
| Buy April 60,000 Put | 60,000 | (14,110) |
| Buy April 60,000 Put | 60,000 | (14,110) |
| Buy April 60,000 Put | 60,000 | (14,110) |
| Buy April 60,000 Put | 60,000 | (14,110) |
| Buy April 60,000 Put | 60,000 | (14,110) |
| Buy April 60,000 Put | 60,000 | (14,110) |

| S |
|---|
| Bitcoin Price ($) |
| 20,000 |
| 30,000 |
| 40,000 |
| 50,000 |
| 60,000 |
| 70,000 |
| 80,000 |
| 90,000 |

| Exercise Y/N? | Payoff (0) | Profit (π) | HPR (%) | Break Even Price |
|---|---|---|---|---|
| Yes | 40,000 | 25,890 | 183.5% | 45,890 |
| Yes | 30,000 | 15,890 | 112.6% | 45,890 |
| Yes | 20,000 | 5,890 | 41.7% | 45,890 |
| Yes | 10,000 | (4,110) | -29.1% | 45,890 |
| No | - | (14,110) | -100.0% | 45,890 |
| No | - | (14,110) | -100.0% | 45,890 |
| No | - | (14,110) | -100.0% | 45,890 |
| No | - | (14,110) | -100.0% | 45,890 |

Figure 11.2 Uncovered Option Strategies—Buying Put Options

the payoff per Bitcoin being $20,000 (X – S = payoff or $60,000 – $40,000 = $20,000). The profit is calculated to be $5,890 per Bitcoin (Payoff – Premium or $20,000 – 14,110 = $5,890).

If Bitcoin price goes down to $50,000, the buyer of the option needs to exercise, since the $50,000 Bitcoin price is lower than the $60,000 exercise price. Please note that the investor will still exercise this option, even though the transaction is not profitable, receiving only a $10,000 payoff against a $14,110 premium, showing a loss of $4,110. By exercising the option, the investor at least recovers some of the premium paid, calculating the net loss to be $4,110 per share instead of the entire premium of $14,110 if the buyer of the put option had not exercised. The rule is that the investor always exercises the option if the option is in the money or the exercise price is higher than the Bitcoin spot price or X – S > 0.

The following formulas are used for calculating the output when buying a put option:

```
Put option payoff = Maximum (0, exercise price – cryptocurrency spot price), max (0, X – S)
Put option profit = Payoff–premium
Holding period return % = Profit/premium
Break-even cryptocurrency spot price for put option = Exercise price – premium
Maximum loss on buying a put option = Premium
Maximum gain on buying a put option = Exercise price – premium or the price of cryptocurrency = 0
```

## Selling Call and Put Options

Selling call and put options are contracts in which the seller has the obligation to sell or buy cryptocurrencies when the buyer exercises his or her option at the exercise price. The seller of an option receives the premium and is hoping that the price of cryptocurrency remains out of the money until expiration, so he or she can keep the premium. Selling uncovered or naked call options is the most dangerous play, since the loss could be unlimited if, for example, Bitcoin significantly rises above the exercise price. Selling uncovered or naked puts is also very dangerous—for example, if Bitcoin goes down to zero. It's usually advised to sell call or put options in conjunction with either holding Bitcoin (covered later in this chapter) or in combination with a buy of a call option (also covered later in this chapter).

The following formulas are used for calculating the output when selling call and put options:

```
Call option payoff = cryptocurrency price – exercise price
Break-even price of cryptocurrency price for call option = Exercise price + premium
Maximum loss on selling a call option = Unlimited
Maximum gain on selling a call option = Premium
Put option payoff = Exercise price – Cryptocurrency price
Break-even price of cryptocurrency price for put option = Exercise price – premium
Maximum loss on selling a put option = Exercise price – premium at price of cryptocurrency = 0
Maximum gain on selling a put option = Premium
```

## Buying and Selling Straddles

A straddle contract involves a buy of both calls and puts at the same exercise price. This contract gives the holder the right, not the obligation, to buy or sell cryptocurrencies at a set exercise price (X) at and before the expiration date, no matter what happens to the price of the cryptocurrency. The strategy for buying both call and put options represents the view of buying against the price of the cryptocurrency’s volatility. This is a strategy in which the investor expects that, for example, Bitcoin will move significantly (scenario based) up or down based on a coming announcement.

As an example, let’s say that the government will decide if they will use or not use Bitcoin as a major currency. If it’s approved, the Bitcoin price is expected to increase significantly, and the straddle holder will be exercising the option (supported by the call option side of the straddle) to buy it at the exercise price (X). If the government announces that it does not approve using Bitcoin as one of the acceptable currencies, then it is expected to significantly decline. The seller of a straddle is hoping that the news will not have as much as of an effect on the price of cryptocurrency and that it will stay within the break-even points.

Of course, the best-case scenario for the seller of straddles and the worst-case scenario for the buyer of straddles is when the cryptocurrency expires at the exercise price (S = X). For example, let’s assume that the May call and put options for Bitcoin with an exercise price of $50,000 entitles its owner to buy or sell it at price of $50,000 at any time up until the third week of May (contract expiration date). If Bitcoin goes above $50,000 by the expiration day, the straddle option holder will exercise the right to buy it at $50,000, respectively, and get paid the difference. If Bitcoin goes below $50,000 by the expiration day, the straddle option holder will exercise the right to sell it at $50,000, respectively, and get paid the difference. To purchase the straddle option, the investor needs to pay both call and put premiums upfront. Figure 11.3 shows the payoff, profit, HPR, and two break
