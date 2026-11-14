![](bbox=[0.138, 0.108, 0.835, 0.648])

Figure 8.20: Optimization setup for Holt's trend-corrected exponential smoothing

# So Are You Done? Looking at Autocorrelations

All right. Is this the best you can do? Have you accounted for everything?

Well, one way to check if you have a good model for the forecast is to check the one-step ahead errors. If those errors are random, you've done your job. But if there's a pattern hidden in the error—some kind of repeated behavior at a regular interval—there may be something seasonal in the demand data that is unaccounted for.

And by a “pattern in the error,” I mean that if you took the error and lined it up with itself shifted by a month or two months or twelve months, would it move in sync? This concept of the error being correlated with the time-shifted version of itself is called autocorrelation.