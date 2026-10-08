# 282

# Computational Finance Using C and C#

using System;

```
public override string FXName()
{
    return FXName_;
}
```

```
public override double Price()
{
    double val = 0.0;
    double[] greek = new double[6];

    int flag, put;
    double discount_fac = 0.0;
    double X_f_b = 0.0, X_d_b = 0.0;
    double Delta = 0.0, Strike_b;
```

```
// Get domestic currency information
try {
    ICurve df = MarketDictionaries.CurrencyTable[DomesticCurrency].YieldCurve;
    // obtain the domestic discount factor
    discount_fac = df.Get(0, TimeToExpiry);
    DomesticRiskFreeRate_ = -Math.Log(discount_fac) / TimeToExpiry;
    X_d_b = MarketDictionaries.CurrencyTable[DomesticCurrency].Spot;
    Strike_b = X_d_b * Strike_f_d;
    // Strike_b is the Strike in base currency units
```

```
catch {
    throw new Exception(PreString_ + " +---- No Market Data supplied for *" + DomesticCurrency_);
}
```

Code example 15 C# to calculate the value of FX options.