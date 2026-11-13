have more liquid shares and thus require smaller fees) or bid-ask spreads (smaller spreads mean smaller fees).

As a first order approximation, it is often useful to compute the average turnover:

```
Turnover = \frac{1}{T - 1} \sum_{t=2}^T \sum_{n=1}^N |w_{t,n} - w_{t-,n}|,
```

where $w_{t,n}$ are the desired $t$-time weights in the portfolio and $w_{t-,n}$ are the weights just before the rebalancing. The positions of the first period (launching weights) are exluded from the computation by convention. Transaction costs can then be proxied as a multiple of turnover (times some average or median cost in the cross-section of firms). This is a first order estimate of realized costs that does not take into consideration the evolution of the scale of the portfolio. Nonetheless, a rough figure is much better than none at all.

Once transaction costs (TCs) have been annualized, they can be deducted from average returns to yield a more realistic picture of profitability. In the same vein, the transaction cost-adjusted Sharpe ratio of a portfolio $P$ is given by

```
SR_{TC} = \frac{\mu_P - TC}{\sigma_P}. \quad (12.4)
```

Transaction costs are often overlooked in academic articles but can have a sizable impact in real life trading (see, e.g., Novy-Marx and Velikov (2015)). DeMiguel et al. (2020) show how to use factor investing (and exposures) to combine and offset positions and reduce overall fees.

# 12.4 Common errors and issues

# 12.4.1 Forward looking data

One of the most common mistakes in portfolio backtesting is the use of forward looking data. It is for instance easy to fall in the trap of the danger zone depicted in Figure 12.2. In this case, the labels used at time $t$ are computed with knowledge of what happens at times $t + 1, t + 2$, etc. It is worth triple checking every step in the code to make sure that strategies are not built on prescient data.

# 12.4.2 Backtest overfitting

The second major problem is backtest overfitting. The analogy with training set overfitting is easy to grasp. It is a well-known issue and was formalized for instance in White (2000) and Romano and Wolf (2005). In portfolio choice, we refer to Bajgrowicz and Scaillet (2012) and Bailey and de Prado (2014) and the references therein.

At any given moment, a backtest depends on _only_ one particular dataset. Often, the result of the first backtest will not be satisfactory - for many possible reasons. Hence, it is tempting to have another try, when altering some parameters that were probably not optimal. This