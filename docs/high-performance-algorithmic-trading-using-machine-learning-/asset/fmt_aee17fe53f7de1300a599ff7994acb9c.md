
# Chapter 4

## Trading Logic Implementation

```python
self.sell(data=self.datas[0])
```

### Trading logic for Asset2

```python
if self.custom_signal2[0] == 1:
    self.buy(data=self.datas[1])
elif self.custom_signal2[0] == -1:
    self.sell(data=self.datas[1])
```

If we are implementing a flipping trading system, where the purchase of an asset automatically triggers the selling of another, you can modify the trading logic in the next method as follows. Now, the `next` function implements a flipping trading system, where buying one asset automatically triggers selling the other. Here, the strategy uses `order_target_size` to manage the position sizes of both assets explicitly.

```python
def next(self):
    # buy signal
    if self.custom_signal1[0] == 1:
        self.order_target_size(data=self.datas[0], target=1)  # Buy Asset1 : PG
        self.order_target_size(data=self.datas[1], target=-1)  # Sell Asset2 : KO
    # sell signal
    if self.custom_signal1[0] == -1:
        self.order_target_size(data=self.datas[0], target=-1)  # Sell Asset1
        self.order_target_size(data=self.datas[1], target=1)  # Buy Asset2
```

In this modified code, buying or selling one asset automatically triggers the opposite action for the other asset. This is done by using `order_target_size` to set the target size to 1 share for a buy and -1 share for a sell. If `custom_signal1` signals a buy for Asset1, the strategy will not only buy Asset1 but also sell Asset2; conversely, for a sell signal. This logic is ideal when the two assets are inversely correlated or when the strategy aims to maintain a balanced exposure (e.g., a pair trading strategy).

Next, update the order notifications to account for multiple assets. This involves modifying the `notify_order` method to identify which asset each order is associated with, ensuring that notifications are correctly handled for all assets in your strategy:

```python
def notify_order(self, order):
    data_name = order.data._name
    # ... (existing logic, now aware of which asset the order is for)
```

### Initialize Cerebro engine and Run the backtest

```python
cerebro = init_cerebro_before_run(data1, data2)
results = cerebro.run()
print('Ending Portfolio Value: %.2f' % cerebro.broker.getvalue())
```

```
2023-10-23, PG : SELL EXECUTED, Price: 147.12, Size: -1
2023-10-23, KO : BUY EXECUTED, Price: 54.65, Size: -1
2023-10-24, PG : BUY EXECUTED, Price: 148.86, Size: 1
2023-10-24, KO : SELL EXECUTED, Price: 55.37, Size: 1
2023-11-02, PG : SELL EXECUTED, Price: 148.79, Size: -1
2023-11-02, KO : BUY EXECUTED, Price: 56.78, Size: -1
Ending Portfolio Value: 99995.12
```

The following is the price history of the Procter&Gamble (PG) share contained in the `data1` structure to trace and reconstitute the sequences:

| Date | Open | Close | custom |
| --- | --- | --- | --- |
| 2023-10-20 | 149.050003 | 148.050003 | -1 |
| 2023-10-23 | 147.860001 | 148.149994 | 1 |
| 2023-10-24 | 148.119995 | 149.899994 | 1 |
| … | … | … | … |
| 2023-11-01 | 150.679993 | 149.610001 | -1 |
| 2023-11-02 | 149.539993 | 150.865005 | -1 |

**Table 4.2: Price History of the 'PG' share**

We can see the sequence of trades in line with the desired logic: intervention on one asset (PG), which triggers an opposite trade on the other asset (KO) in a hedging logic.

## Conclusion

In this chapter, we explored the basics of backtesting and trading libraries. We introduced key libraries and criteria for selecting the right tool and then provided a practical, step-by-step guide to implementing a strategy using BackTrader. Along the way, we explored key concepts such as managing algorithmic orders, incorporating risk management techniques (e.g., setting stop-loss limits or position sizing rules). With this solid understanding of backtesting using a state-of-the-art, event-driven library, you are now equipped to design and test sophisticated trading strategies.

In the next chapter, we will look at supervised learning and its applications in trading. You will learn how these algorithms analyze historical data to identify patterns and predict market movements. By focusing on key algorithms and evaluation metrics, this chapter lays the ground for the practical strategies and implementations that follow.

## Multiple Choice Questions

1. Which of the following is a key feature of the BackTrader library?
   a. Exclusively supports live trading
   b. Versatility and ease of use for backtesting and live trading
   c. Limited to basic order types
   d. Requires a subscription fee

2. What is the primary function of the `Cerebro` object in BackTrader?
   a. To manage risk parameters
   b. To define trading strategies
   c. To handle the backtesting workflow
   d. To visualize performance metrics

3. Which method in a BackTrader strategy is called for every data point (bar) in the dataset?
   a. `__init__`
   b. `log`
   c. `notify_order`
   d. `next`

4. What does the `order_target_size` method in BackTrader allow traders to do?
   a. Set a percentage of the current portfolio value allocated to the asset.
   b. Set the monetary value of the asset in the portfolio.
   c. Set the number of shares or contracts of a particular asset
   d. Set a stop loss price

5. In BackTrader, what is the purpose of the `notify_order` method?
   a. To define trading logic
   b. To log trade executions
   c. To intercept messages regarding the status of orders
   d. To set the initial cash

6. What does slippage refer to in trading?
   a. The commission charged by the broker
   b. The difference between the expected price of a trade and the actual executed price
   c. The profit made on a trade
   d. The initial capital required for a trade

7. Which of the following is NOT a criterion for choosing a trading library?
   a. Ease of implementation
   b. Adaptability
   c. Broker integration
   d. The color of the library's logo

8. What is a key advantage of using a machine learning-based strategy in BackTrader?
   a. It is simpler than using traditional methods
   b. It relies on technical indicators
   c. It uses predictive outputs to drive trade decisions
   d. It does not need historical data

9. What is the function of a stop-loss order?
   a. To automatically sell a position to secure earnings
   b. To limit potential losses by selling an asset when the price drops below a predefined level
   c. To buy an asset at a lower price
   d. To monitor market trends

10. In a multi-asset strategy, how can you manage trades for different assets in BackTrader?
    a. By combining all data into one feed
    b. By using the same trading logic for all assets
    c. By initializing variables and trading logic specific to each asset
    d. By only trading one asset at a time

### Answers

| Question | Answer |
| --- | --- |
| 1 | b |
| 2 | c |
| 3 | d |
| 4 | c |
| 5 | c |
| 6 | b |
| 7 | d |
| 8 | c |
| 9 | b |
| 10 | c |

## References

1. The official website for BackTrader, a versatile Python library for algorithmic trading  
   <https://backtrader.com>

2. The documentation for Zipline, a backtesting engine that was originally part of Quantopian  
   <https://zipline-trader.readthedocs.io/en/latest/index.html>

3. The Github page for PyAlgoTrade, which offers robust support for multi-asset trading  
   <https://gbeced.github.io/pyalgotrade>

4. The website for Alpaca, a platform for direct market access and real-time trading  
   <https://alpaca.markets>

5. The website for QuantRocket, which is tailored for InteractiveBrokers users  
   <https://www.quantrocket.com>

6. The InteractiveBrokers API page  
   <https://www.interactivebrokers.com/en/trading/ib-api.php>

---

**Join our book's Discord space**

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![Discord](images/Discord.png)

# Chapter 5

## Supervised Learning for Trading Systems

### Introduction
