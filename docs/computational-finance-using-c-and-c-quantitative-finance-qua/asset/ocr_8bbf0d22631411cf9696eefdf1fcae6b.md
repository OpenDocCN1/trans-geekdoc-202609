# C# portfolio pricing application

```
}
public override double Payoff() ( // implement Call on average of n_assets
double the_average = 0.0;
double pay_val = 0.0;
double zero = 0.0;
the_average = ST[0];
for (int jj = 0; jj < n_; jj++) {
    the_average += ST[jj];
}
the_average = the_average/n_;
pay_val = Math.Max(the_average - Strike_, zero);
return pay_val;
}

```

The contents of the file Payoff_AvgPut can be deduced from Payoff_AvgCall in the obvious manner. The output from the application is given below:

```
TestGenericEQ in units of GBP
TestGenericEQ :31/07/2007 19:05:10
23.0101a6,Generic: Put on the maximum of 4 assets
23.0101a18,Four Equity Option
681.403+5,Generic option: Call on the average of 4 assets
338.3212+6,Generic option: Put on the average of 10 assets
302.6056+9,Generic option: Put on the average of 10 assets
TOTAL_VAL: 1993.18 GBP
```

It can be seen that result 1A, obtained using the deal class GenericEquity-BasketOption, is exactly the same as result 1B, which was computed with the deal FourEquityOptionDeal. This is because in both Monte Carlo simulation is used, and the same random seed is used for all Monte Carlo simulations.

# 8.4.4 Equity barrier option

Code example 8.13 gives the C# code for computing the value of an equity barrier option.

```
using System;
namespace Computational_Lib
public class DownOutEquityOptionDeal : BaseDeal {
    public string EquityName_ { get { return EquityName_; } set (EquityName_ = value); }
    public double BarrierLevel_ { get { return BarrierLevel_; } set (BarrierLevel_ = value); }
    public double TimeTo_Expiry_ { get { return TimeTo_Expiry_; } set (TimeTo_Expiry_ = value); }
    public OptionType OptionType_ { get { return OptionType_; } set (OptionType_ = value); }
    public double Strike_ { get { return Strike_; } set (Strike_ = value); }
    public string CalcMethod_ { get { return CalcMethod_; } set (CalcMethod_ = value); }
}
```

Code example 8.13 is C# code to compute the value of an equity barrier option.