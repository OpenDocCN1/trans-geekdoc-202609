one year, and a volatility of 20 percent (i.e., 0.2). The first value 3.8347 was computed by a bs_opt_barrier_downout_call, which uses the closed form analytic expression in Code excerpt 4.7.

The second price 3.8269, is in close agreement with the first, was obtained from dko_call and uses finite difference grid. The third valuation was also computed using dko_call and illustrates the early exercise premium for an American call option (with a nonzero dividend). The other values were estimated using Monte Carlo simulation as the number of scenarios varied from 1000 to 64000; the default of 300 steps was used through.

It can be seen when the Brownian bridge used is much closer agreement is obtained with both the analytic and numeric estimates.

+   DownOuts in units of GBP
DownOuts::26/07/2007 13:11:28
3.8347-Analytic Down Out Equity Option
3.8269-Down Out Equity Option
3.8836-Numeric (American style).Down Out Equity Option
4.1798-4000 Scenarios: not using Brownianbridge;Down Out Equity Option
4.3988-4000 Scenarios: not using Brownianbridge;Down Out Equity Option
4.3166-8000 Scenarios: not using Brownianbridge;Down Out Equity Option
4.1796-8000 Scenarios: not using Brownianbridge;Down Out Equity Option
4.1832-16000 Scenarios: using Brownianbridge;Down Out Equity Option
3.8175-16000 Scenarios: not using Brownianbridge;Down Out Equity Option
3.6499-32000 Scenarios: not using Brownianbridge;Down Out Equity Option
3.6723-32000 Scenarios: using Brownianbridge;Down Out Equity Option
3.7156-32000 Scenarios: not using Brownianbridge;Down Out Equity Option
3.8893-64000 Scenarios: using Brownianbridge;Down Out Equity Option
3.8566-64000 Scenarios: not using Brownianbridge;Down Out Equity Option
3.8482-64000 Scenarios: using Brownianbridge;Down Out Equity Option

TOTAL VALUE = 70.83 GBP

# 8.4 FX CLASSES

Here, we provide code for valuing derivatives. The FX option routines are very similar to the equity option routines we have already considered. The fundamental difference is that for FX there is both a domestic and a foreign currency. The FX routine calls the Black-Scholes routine with the dividend yield set to the foreign currency risk-free interest rate, and the supplied volatility is that of the foreign/domestic exchange rate. In the market data file, the currency FX spot rates are with respect to the base currency.

# 8.4.1 Forward

Excerpt 8.12 provides C# code to compute the value of FX Forwards.

```
using System;
namespace Computational_lib
{
    public class FXForward: BaseDeal
    {
        public double FXForwardAmount(double iForwardAmount = value)
        {
            return iForwardAmount;
        }

    // Note: Strike is the number of units of domestic currency required to
```

Code excerpt 8.12 C# code to compute the value of FX forwards.