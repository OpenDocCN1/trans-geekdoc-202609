# # Splines, Heat, and IPOs

firms to reconsider issuing shares. These signals (i.e., higher IRs) create the conditions for cascades, bubbles, and industry clustering to occur.

In the second panel listed above, we have provided an illustration from Smith et al. (2018), which compared the performance of the Helwege et al. (2004) model of hot and cold performance against the Smith et al. (2018) model. Using data from the August 1996 to January 2008 period, we see that the Helwege et al. (2004) model better fits the data, but the explanatory power of the first through the third lags of volume seem to affect the volume of IPOs issued in a given period. This seems to suggest that the volume of IPOs issued in a given period may have long-term memories (i.e., that trends persist). Continuing our analysis of IPO issuance during the January 2005 to December 2015 period, we see that there is some evidence that the model used in Smith et al. (2018) better fits the volume of IPOs issued during this period and there is some consistency in both the sign and the statistical significance associated with the idea that there may be a long memory in the volume of IPOs issued during this time frame when compared against the results generated with the Helwege et al. (2004) model.

```
NIPO_t = β_0 + β_1IR_t + β_2IR_{t-1} + β_3IR_{t-2} + β_4IR_{t-3} + β_5NIPO_{t-1} + β_6NIPO_{t-2} + β_7NIPO_{t-3} + β_8D_Heat + β_9D_Cold + β_{10}D_{2008} + β_{11}Z_{Obs} + Z_{Change} + ε,
```

where the ZJOBS and ZChange are structural knot positions and all of the other variables have been previously defined in equations 67.1 through 67.6. Interpret the ZJOBS variable as follows, the JOB's act was initiated on April 2012; therefore, a knot position was placed at March 2012 to initiate this variable on April 2012. The spline takes a value of 1 on April 2012, 2 on May 2012, and so on and so forth until December 2015, which is the end of the sample and it had a value of 45 at that time. Similarly, a knot position was added for the structural break that occurred in August 2014, which took on a value of 1 on September 2014, 2 on October 2014, and so on and so forth until the end of the sample, which was December 2015 and it had a value of 16. Marsh and Cormier (2002) provide an excellent summary of how the spline regression technique could be integrated into an analytical framework and use the following representation:

```
Y = a_0 + b_0X_t + b_1Z_{1t} + ε,
```

where Y is simply the dependent variable of interest, a0+b0X_t is the intercept and a standard dependent variable, but according to Smith et al. (2018), we