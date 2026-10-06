# 268 CHAPTER |8 C# Portfolio Pricing Application

and is then converted to base units, in the case of FX options, the value val1 is already in base currency units and requires no conversion.

using System;

```
namespace Computational_lib
{
    public class FXOption:BaseDeal
    {
        public int NumberOffUnits { get return NumberOffUnits_; } set { NumberOffUnits_ = value; }
        // Note: Strike is the number of units of domestic currency required to
        public double Strike { get return Strike_f_d; } set { Strike_f_d_ = value; }
        public double Volatility { get return Volatility_f_d; } set { Volatility_f_d_ = value; }
        // Volatility is that the FX/Domestic exchange rate is de-constant
        public string ForeignCurrency { get return ForeignCurrency_; } set { ForeignCurrency_ = value; }
        public string DomesticCurrency { get return DomesticCurrency_; } set { DomesticCurrency_ = value; }
        public double Spot { get return Spot_; } set { Spot_ = value; }
        public double TimeToExpiry { get return Time_Expiry_; } set { Time_Expiry_ = value; }
        public Custom OptionType { get return OptionType_; } set { OptionType_ = value; }
        public European ExerciseStyle { get return ExerciseStyle_; } set { ExerciseStyle_ = value; }
        protected double Strike_f_d_ = 0.0;
        protected string ForeignCurrency_ = "";
        protected string DomesticCurrency_ = "Buysell";
        protected int NumberOffUnits_ = 0;
        protected Custom OptionType_ = PutCall;
        protected European ExerciseStyle ExerciseStyle_ = American.European;
        protected double TimeToExpiry_ = 0.0;
        protected double DomesticIsFreeRate_ = 0.0;
        protected double Sigma_f_d_ = 0.0;
        protected string Pre_String_ = "";
```

```
public override string Name()
{
    return "FX Option";
}
```

```
public override double Price()
{
    Validate();
    double val = 0.0;
    double[] geeks = new double[6];
    int i, j;
    double discount_fac = 0.0;
    double X_f_b = 0.0, X_d_b = 0.0;
    double Sigma=0.0,Strike_b;
```

```
// Get domestic currency information
try
{
    ICurve Curve = MarketDataDictionaries.CurrencyTable[DomesticCurrency_].YieldCurve;
    ICurve Curve = MarketDataDictionaries.CurrencyTable[ForeignCurrency_].YieldCurve;
    // obtain the domestic discount factor
    discount_fac = Curve.Get(0
```

```
// Get foreign currency information
try
{
    ICurve Curve = MarketDataDictionaries.CurrencyTable[ForeignCurrency_].YieldCurve;
    // obtain the domestic discount factor
    discount_fac = Curve.Get(0, Time_To_Expiry_);
    ForeignIsFreeRate_ = -Math.Log(discount_fac) / Time_To_Expiry_;
    X_f_b = MarketDataDictionaries.CurrencyTable[ForeignCurrency_].spot;
    Spot_ = X_f_b; // Foreign exchange art base currency
}
catch
{
}
```

# Code example 8.13 C# code to compute the value of FX options.

* Note*