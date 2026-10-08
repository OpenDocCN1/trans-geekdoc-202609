# Computational Finance Using C and C#

```
public double Strike (get { return Strike_; } set { Strike_ = value; } )
public double BuySell (get { return BuySell_; } set { BuySell_ = value; } )
public double Volatility (get { return Sigma_; } set { Sigma_ = value; } )
```

```
protected PutOptMaximum = PutCall;
protected MinimumMaximum MinMax = MinimumMaximum.Maximum;
protected EuropeanAmericanExercisestyle = EuropeanAmerican.European;
protected double Strike = 0;
protected string EquityName = "*";
protected string EquityName2 = "*";
protected string Currency = "*";
protected int NumberOfUnits = 1;
protected double Time_To_Expiry = 0.0;
protected double freeStarting = "*";
protected double S1 = 0.0;
protected double S2 = 0.0;
protected double Sigma1 = 0.0;
protected double Sigma2 = 0.0;
protected double BuySell1 = BuySell.Buy;
```

```
public override string overrideName ()
{
    return "Rainbow option(two equities)";
}
```

```
public override double Price ()
{"
```

```
Validate();
double val = 0.0;
double rho = 0.0; // default correlation set to zero
double RiskFreeRate = 0.0;
double fx_spot = 0.0;
```

```
try
{
S1 = MarketDataDictionaries.EquityTable[EquityName_].Spot;
}
catch
{
throw new Exception(Pre_string, + "---- No Market Data supplied for " + EquityName_ + ");
}
```

```
try
{
S2 = MarketDataDictionaries.EquityTable[EquityName2_].Spot;
S1 = MarketDataDictionaries.EquityTable[EquityName_].Spot;
}
catch
{
throw new Exception(Pre_string, + "---- No Market Data supplied for " + EquityName2_ + ");
n
```

```
if (string.Compare(MarketDataDictionaries.EquityTable[EquityName_].Currency,
MarketDataDictionaries.EquityTable[EquityName2_].Currency) != 0)
{
throw new Exception(Pre_string, + "---- Currencies for both equities are not the same*");
}
```

```
Currency = MarketDataDictionaries.EquityTable[EquityName_].Currency;
try
{
ICCurve = MarketDataDictionaries.CurrencyTable[Currency_].YieldCurve;
// obtain the discount factor
double discount_fac = DF[0, Time_To_Expiry];
RiskFreeRate = -Math.Log(discount_fac) / Time_To_Expiry;
fx_spot = MarketDataDictionaries.CurrencyTable[Currency_].spot;
}
```

# Code example 81.11 (Continued).