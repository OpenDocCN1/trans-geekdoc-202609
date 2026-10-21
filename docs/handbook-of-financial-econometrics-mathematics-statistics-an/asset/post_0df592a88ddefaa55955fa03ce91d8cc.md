
## Table 83.1: Options Quotes for JNJ at March 29, 2011.

**Stock Price at March 29, 2011 = $59.38**
**Call Options Expiring Fri. April 15, 2011**

| Strike | Symbol | Last | Bid | Ask | Vol | Open Int |
|---|---|---|---|---|---|---|
| 35 | JNJ110483C00035000 | 24.7 | 23.95 | 24.45 | 0 | 122 |
| 40 | JNJ110483C00040000 | 17.85 | 18.95 | 19.35 | 33 | 360 |
| 45 | JNJ110483C00045000 | 13.85 | 14.15 | 14.25 | 45 | 54 |
| 50 | JNJ110483C00050000 | 8.75 | 9.2 | 9.35 | 2 | 213 |
| 52.5 | JNJ110483C00052500 | 6.62 | 6.7 | 6.85 | 1 | 518 |
| 55 | JNJ110483C00055000 | 4.25 | 4.2 | 4.3 | 5 | 1787 |
| 57.5 | JNJ110483C00057500 | 1.84 | 1.89 | 1.94 | 40 | 4491 |
| 60 | JNJ110483C00060000 | 0.3 | 0.3 | 0.31 | 399 | 23603 |
| 62.5 | JNJ110483C00062500 | 0.04 | 0.03 | 0.04 | 232 | 24478 |
| 65 | JNJ110483C00065000 | 0.02 | N/A | 0.02 | 407 | 12559 |
| 67.5 | JNJ110483C00067500 | 0.02 | N/A | 0.02 | 24 | 8731 |

**Put Options Expiring Fri. April 15, 2011**

| Strike | Symbol | Last | Bid | Ask | Vol | Open Int |
|---|---|---|---|---|---|---|
| 47.5 | JNJ110483P00047500 | 0.02 | 0.01 | 0.04 | 2 | 1983 |
| 50 | JNJ110483P00050000 | 0.04 | 0.02 | 0.04 | 2 | 3518 |
| 52.5 | JNJ110483P00052500 | 0.05 | 0.05 | 0.07 | 4 | 3355 |
| 55 | JNJ110483P00055000 | 0.09 | 0.09 | 0.1 | 2 | 7993 |
| 57.5 | JNJ110483P00057500 | 0.23 | 0.2 | 0.22 | 53 | 24464 |
| 60 | JNJ110483P00060000 | 1.21 | 1.09 | 1.13 | 15 | 83678 |
| 62.5 | JNJ110483P00062500 | 3.28 | 3.25 | 3.4 | 1 | 10861 |
| 65 | JNJ110483P00065000 | 5.85 | 5.75 | 5.85 | 3 | 1038 |
| 67.5 | JNJ110483P00067500 | 8.45 | 8.2 | 8.5 | 2 | 713 |

The party buying the option contract (call or put) is the option buyer (or holder), while the party selling the option is the option seller (or writer). If the writer of an option does not own the underlying asset, he or she is said to write a naked option.

Table 83.1 shows a listing of publicly traded options for Johnson & Johnson (JNJ) at March 29, 2011.

## 83.2.3 Relationships between the option price and the underlying asset price

A call (put) option is said to be in the money if the underlying asset is selling above (below) the exercise price of the option. An at-the-money call (put) is one whose exercise price is equal to the current price of the underlying asset. A call (put) option is out of the money if the underlying asset is selling below (above) the exercise price of the option.

Suppose the ABC stock is selling at $30 per share. An ABC June 25 call option is in the money ($30 − 25 > 0), while an ABC June 35 call option is out of the money ($30 − 35 < 0). Of course, the expiration dates could be any month without changing the option’s standing as in, at, or out of the money.

The relationship between the price of an option and the price of the underlying asset indicates both the amount of intrinsic value and time value inherent in the option’s price, as shown in equation (83.1):

```
Intrinsic value = Underlying asset price − Option exercise price.   (83.1)
```

For a call (put) option that is in the money (underlying asset price > exercise price), its intrinsic value is positive. And for at-the-money and out-of-the-money options, the intrinsic value is zero. An option’s time value is the amount by which the option’s premium (or market price) exceeds its intrinsic value. For a call or put option,

```
Time value = Option premium − Intrinsic value,   (83.2)
```

where intrinsic value is the maximum of zero or stock price minus exercise price. Thus an option premium or market price is composed of two components: intrinsic value, and time value. In-the-money options are usually most expensive because of their large intrinsic-value component. An option with an at-the-money exercise price will have only time value inherent in its market price. Deep out-of-the-money options have zero intrinsic value and little time value and consequently are the least expensive. Deep in-the-money cases also have little time value, and time value is the greatest for at-the-money options. In addition, time value (as its name implies) is positively related to the amount of time the option has to expiration. The theoretical valuation of options focuses on determining the relevant variables that affect the time-value portion of an option premium and the derivation of their relationship in option pricing.

In general, the call price should be equal to or exceed the intrinsic value:

```
C ≥ Max(S − E, 0),
```

where C is the value of the call option, S is the current stock price, and E is the exercise price.

Figure 83.1 illustrates the relationship between an option’s time value and its exercise price. When the exercise price is zero, the time value of an option is zero. Although this relationship is described quite well in general by Figure 83.1, the exact relationship is somewhat ambiguous. Moreover, the identification of options with a mispriced time-value portion in their total premium motivates interest in a theoretical pricing model.

![Figure 83.1](img/31ee7e6fa5107b22bbf7960ec96106a1_2971_0.png)

**Figure 83.1:** The relationship between an option's exercise price and its time value.

One more aspect of time value that is very important to discuss is the change in the amount of time value an option has as its duration shortens. As previously mentioned, options with a longer time to maturity and those near to the money have the largest time-value components. Assuming that a particular option remains near to the money as its time to maturity diminishes, the rate of decrease in its time value, or what is termed the effect of time decay, is of interest. How time decay affects an option's premium is an important question for the valuation of options and the application of option strategies. To best see an answer to this question, refer to Figure 83.2.

In general, the value of call options with the same exercise price increases as time to expiration increases: $C(S_1, E_1, T_1) \le C(S_1, E_1, T_2)$, where $T_1 \le T_2$ and $T_1$ and $T_2$ are the times to expiration.

Note that for the simple case in Figure 83.2, the effect of time decay is smooth up until the last month before expiration when the time value of an option begins to decay very rapidly. Example 83.1 shows the effect of time decay.

### Example 83.1

It is January 1, the price of the underlying ABC stock is $20 per share, and the time premiums are shown in the following Table 83.2. What is the value for the various call options?

![Figure 83.2](img/31ee7e6fa5107b22bbf7960ec96106a1_2972_0.png)

**Figure 83.2:** The relationship between time value and time to maturity for a near-to-the-money option (assuming a constant price for the underlying asset).

**Table 83.2: Time Premiums.**

| Exercise Price X | January | April | July |
|---|---|---|---|
| 15 | $0.50 | $1.25 | $3.50 |
| 20 | 1.00 | 2.00 | 5.00 |
| 25 | 0.50 | 1.25 | 3.50 |

### Solution

Call premium = Intrinsic value + Time premium

$C_{15,Jan} = \text{Max}(20 - 15, 0) + 0.50$

= $5.50 per share or $550 for 1 contract

Other values are shown in Table 83.3.

**Table 83.3: Value of Call premiums.**

| Exercise Price X | January | April | July |
|---|---|---|---|
| 15 | $5.50 | Max (20 − 15, 0) + 1.25 = $6.25 | Max (20 − 15, 0) + 3.50 = $8.50 |
| 20 | Max (20 − 20, 0) + 1.00 = $1.00 | Max (20 − 20, 0) + 2.00 = $2.00 | Max (20 − 20, 0) + 5.00 = $5.00 |
| 25 | Max (20 − 25, 0) + 0.50 = $0.50 | Max (20 − 25, 0) + 1.25 = $1.25 | Max (20 − 25, 0) + 3.50 = $3.50 |

## 83.2.4 Additional definitions and distinguishing features

Options may be specified in terms of their classes and series. A *class of options* refers to all call and put options on the same underlying asset. For example, all AT&T call and put options at various exercise prices and expiration months form one class. A *series* is a subset of a class and consists of all contracts of the same class (such as AT&T) having the same expiration date and exercise price.

When an investor either buys or sells an option (i.e., is long or short) as the initial transaction, the option exchange adds this opening transaction to what is termed the open interest for an option series. Essentially, open interest represents the number of contracts outstanding at a particular point in time. If the investor reverses the initial position with a closing transaction (i.e., sells the option if he or she originally bought it or vice versa), then the open interest for the particular option series is reduced by one.

While open interest is more of a static variable, indicating the number of outstanding contracts at one point in time, volume represents a dynamic characteristic. More specifically, volume indicates the number of times a particular option is bought and sold during a particular trading day. Volume and open interest are measures of an option’s liquidity, the ease with which the option can be bought and sold in large quantities. The larger the volume and/or open interest, the more liquid the option.

Again, an option holder who invokes the right to buy or sell is exercising the option. Whenever a holder exercises an option, a writer is assigned the obligation to fulfill the terms of the option contract by the exchange on which the option is traded. If a call holder exercises the right to buy, a call writer is assigned the obligation to sell. Similarly, when a put holder exercises the right to sell, a put writer is assigned the obligation to buy.

The seller or writer of a call option must deliver 100 shares of the underlying stock at the specified exercise price when the option is exercised. The writer of a put option must purchase 100 shares of the underlying stock when the put option is exercised. The writer of either option receives the premium or price of the option for this legal obligation. The maximum loss an option buyer can experience is limited to the price of the option. However, the maximum loss from writing a naked call is unlimited; the maximum loss possible from writing a naked put is the exercise price less the original price of that put. To guarantee that the option writer can meet these obligations, the exchange clearinghouse requires margin deposits.
