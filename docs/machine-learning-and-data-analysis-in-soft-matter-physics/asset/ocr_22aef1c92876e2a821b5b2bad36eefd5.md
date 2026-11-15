# 6.2.4 Exponential Moving Average

An exponential moving average (EMA), also known as an exponentially weighted moving average (EWMA), is a first-order infinite impulse response filter that applies weighting factors which decrease exponentially. The weighting for each older datum decreases exponentially, never reaching zero. This formulation is according to Hunter.

# 6.2.5 Other Weightings

Other weighting systems are used occasionally – for example, in share trading a volume weighting will weight each time period in proportion to its trading volume.

A further weighting, used by actuaries, is Spencer’s 15-Point Moving Average (a central moving average). Its symmetric weight coefficients are [–3, –6, –5, 3, 21, 46, 67, 74, 67, 46, 21, 3, –5, –6, –3], which factors as [1, 1, 1][1, 1, 1][1, 1, 1][1, 1, 1, 1, 1][1, 1, 1, 1][–3, 3, 4, 3, –3]/320 and leaves samples of any cubic polynomial unchanged.

Outside the world of finance, weighted running means have many forms and applications. Each weighting function or “kernel” has its own characteristics. In engineering and science the frequency and phase response of the filter is often of primary importance in understanding the desired and undesired distortions that a particular filter will apply to the data.

A mean does not just “smooth” the data. A mean is a form of low-pass filter. The effects of the particular filter used should be understood in order to make an appropriate choice.

# 6.2.6 Moving Median

From a statistical point of view, the moving average, when used to estimate the underlying trend in a time series, is susceptible to rare events such as rapid shocks or other anomalies. A more robust estimate of the trend is the simple moving median over n time points:

```
P_SM = Median(P_M, P_M-1, ..., P_M-n+1)
```

where the median is found by, for example, sorting the values inside the brackets and finding the value in the middle. For larger values of n, the median can be efficiently computed by updating an indexable skiplist.