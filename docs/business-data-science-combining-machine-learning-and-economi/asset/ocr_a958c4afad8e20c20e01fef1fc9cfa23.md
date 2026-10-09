This is a fancy plot. It looks cool, with lots of different lines. It is the sort of plot that you might see on a computer screen in a TV ad for some online brokerage platform. *If only I had that information, I'd be rich!*

But what can you actually learn from **Figure I.1**? You can see that returns do tend to bounce around near zero.² You can also pick out periods of higher volatility (variance) where the S&P 500 changes more from month to month and the individual stock returns around it are more dispersed. That's about it. You don't learn *why* these periods are more volatile or when they will occur in the future. More important, you can't pull out useful information about any individual stock. There is a ton of *data* on the graph but little useful information.

INSTEAD OF PLOTTING RAW DATA, let's consider a simple *market model* that relates individual stock returns to the market average. The capital asset pricing model (CAPM) regresses the returns of an individual asset onto a measure of overall market returns:

```
r$_{jt}$ = $\alpha$$_j$ + $\beta$$_j$ *m*$_t$ + $\varepsilon$$_{jt}$ (I.1)
```

The *output* *r*$_{jt}$ is equity *j* return at time *t* (actually the excess return³). The *input* *m*$_t$ is a measure of the average return—the “market”—at time *t*. You can take *m*$_t$ as the return on the S&P 500, which weights companies according to their market capitalization (the total value of their stock). Finally, $\varepsilon$$_{jt}$ is an *error* that has mean zero and is uncorrelated with the market: **E**[*$\varepsilon$$_{jt}$] = 0 and **E**[*m*$_t$, *$\varepsilon$$_{jt}$] = 0.

Equation I.1 is the first regression model in this book. You'll see many more. This is the “simple linear regression” (or ordinary least squares [OLS]) that should be familiar to most readers. The Greek letters define a line relating each individual equity return to the market, as shown in **Figure I.2** for example. A small $\beta$$_j$, near zero, indicates an asset with low market sensitivity. In the extreme, fixed-income assets like T-bills have $\beta$$_j$ = 0. On the other hand, a $\beta$$_j$ > 1 indicates a stock that is more volatile than the market, typically growth and higher-risk stocks. The $\alpha$$_j$ is free money: assets with $\alpha$$_j$ > 0 are adding value regardless of wider market movements, and those with $\alpha$$_j$ < 0 destroy value.