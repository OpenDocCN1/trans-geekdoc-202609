
# 276 Computational Finance Using C and C#

```csharp
public EuropeanAmericanExerciseStyle { get { return ExerciseStyle_; }
set { ExerciseStyle_ = value; } }
public int TimeSteps { get { return TimeSteps_; } set { TimeSteps_ = value; } }
public int NumberScenarios { get { return NumberScenarios_; } }
public bool UseBrownianBridge { get { return UseBrownianBridge_; } set { UseBrownianBridge_ = value; } }
public bool BuySell { get { return BuySell_; } set { BuySell_ = value; } }
public double volatility { get { return Signal_; } set { Signal_ = value; } }
public int NumberOfUnits { get { return NumberOfUnits_; } set { NumberOfUnits_ = value; } }
protected double CallPut_ = PutCall;
protected double Strike_ = 0.0;
protected double BarrierLevel_ = 0.0;
protected double TimeToExpiry_ = 0.0;
protected double RiskFreeRate_ = 0.0;
protected double Dividend_ = 0.0;
protected string Pre__ = "*";
protected CalculationMethod CalculationMethod_ = CalculationMethod.Analysis;
protected int NumberScenarios_ = 3000;
protected bool UseBrownianbridge_ = true;
protected double S1_ = 0.0;
protected int NumberOfUnits_ = 1;
protected bool BuySell_ = BuySell.Buy;
protected EuropeanAmericanExercisestyle_ = EuropeanAmerican.European;
protected string Currency_ = "*";
```

```csharp
public override string Name()
{
    return "Down Out Equity Option";
}
public override double overridePrice()
{
    Validate();
    double val = 0.0;
    double fx_spot = 0.0;
    try {
        S1_ = MarketDataDictionaries.EquityTable[EquationName_].Spot;
        Currency_ = MarketDataDictionaries.EquityTable[EquationName_].Currency;
        // get volatility (assumed constant)
        DividendField_ = MarketDataDictionaries.EquityTable[EquationName_].DivYield;
        // get equity yield
    } catch {
        throw new Exception(Pre_string_ + " +-- No Market data supplied for " + EquationName_);
    }
double discount_fac = 0.0;
try {
    ICurve DF = MarketDataDictionaries.CurrencyTable[Currency_].YieldCurve;
    // obtain the discount
    discount_fac = DF[0, TimeToExpiry_];
    RiskFreeRate_ = Math.Log(discount_fac) / TimeToExpiry_;
    fx_spot = MarketDataDictionaries.CurrencyTable[Currency_].spot;
} catch {
    throw new Exception(Pre_string_ + " +-- No Market data supplied for " + Currency_);
}
int iflag = 0;
iflag = 
put = OptionType_ = PutCall.Put ? 1 : 0;
is_american = ExerciseStyle_ = EuropeanAmerican.American ? 1 : 0;
```

# Code excerpt 8.13 (Continued).

# C# portfolio pricing application

```csharp
BarrierLevel_ = Math.Max(BarrierLevel_, PricingUtils.EPS);
```

```csharp
if (CalcMethod == CalculationMethod.Analytic)
    if (put == 1) throw new Exception(Pre_String_ + "--- Can't put a price using this calculation method");
    if (is_american == 1) throw new Exception(Pre_String_ + "--- Can't price an American option using this calculation method");
```

```csharp
PricingUtils.bs_opt_barrier_downout_call(ref val, BarrierLevel_, S1_, Strike, Sigma1_, Time_To_Expiry_, RiskFreeRate_, DividendYield_, ref iflag);
```

```csharp
if (iflag != 0)
    throw new Exception(Pre_String_ + "--- An error occurred in a call to the pricing library");
else if (CalcMethod == CalculationMethod.Numeric)
    if (put == 1) throw new Exception(Pre_String_ + "--- Can't put a price using this calculation method");
```

```csharp
int n_size = 2;
// set up the parameters that have "reasonable accuracy"
double[] sigma_array = new double[n_size];
double[] sigma_times = new double[n_size];
```

```csharp
sigma_array[0] = Sigma1;
sigma_array[1] = Sigma1;
```

```csharp
sigma_times[0] = 0.0;
sigma_times[1] = Time_To_Expiry_
```

```csharp
int nt = 100;
t ns_below_0 = nt / 2;
t ns_above_0 = nt / 2;
double theta_m = 0.5;
double UpperBarrierLevel = S1_ * 5.0;
```

```csharp
PricingUtils.dco_call(BarrierLevel_, UpperBarrierLevel,
theta_m, S1_, ref sigma_array[0], ref sigma_times[0],
n_size, RiskFreeRate_, Time_To_Expiry_,
Strike_, is_american, ref val,
nt, ns_below_0, ns_above_0,
t, iflag);
```

```csharp
if (iflag != 0)
    throw new Exception(Pre_String_ + "--- An error occurred in a call to the pricing library");
```

```csharp
else
    bool is_put = (put == 1);
    if (is_american == 1) throw new Exception(Pre_String_ + "--- Can't price an American option using this calculation method");
```

```csharp
if (S1_ < BarrierLevel_) // the option is already knocked out
    val = 0.0;
else
    val = MonteCarloSim(is_put);
```

```csharp
val = fx_spot * NumberOfUnits;
    return val;
```

# Code excerpt 8.13 (Continued).

```csharp
protected override void Validate()
{}
```

```csharp
if (NumberofUnits_ < 0)
    throw new Exception(Pre_string_ + "---- Number of units cannot be less than zero;");
{}
```

```csharp
if (Time_Expiry_ < 0.0)
    throw new Exception(Pre_string_ + "---- Time to expiry cannot be less than zero years;");
{}
```

```csharp
if (RiskFreeRate_ < 0.0)
    throw new Exception(Pre_string_ + "---- Risk free rate cannot be less than zero;");
{}
```

```csharp
if (Strike_ < 0.0)
    throw new Exception(Pre_string_ + "---- Strike cannot be less than zero;");
{}
```

```csharp
if (BarrierLevel_ < 0.0)
    throw new Exception(Pre_string_ + "---- Barrier level cannot be less than zero;");
{}
```

```csharp
if (Signal_ < 0.0)
    throw new Exception(Pre_string_ + "---- Volatility cannot be less than zero;");
{}
```

```csharp
private double MonteCarloSim(bool is_put)
// The asset path
int seed = 11;
double[] asset_path = new double[TimeSteps];
double time_step = Time_Expiry_ / TimeSteps;
double sigma_z = Math.Sqrt(time_step);
double opt_val = 0.0;
bool not_out = true;
int k = 0;
double sum_opt_vals = 0.0;
for (int i = 0; i < NumberScenarios_; i++)
{
    while (not_out)
    {
        z = PricingUtils.Rnd(seed);
        asset_path[k] = S1_ * Math.Exp(z * sigma_z);
        if (asset_path[k] < BarrierLevel_)
        {
            not_out = false;
            break;
        }
        k++;
        if (k == TimeSteps)
        {
            k = 0;
            not_out = true;
        }
    }
    if (is_put)
    {
        opt_val += Math.Max(Strike - asset_path[k], 0);
    }
    else
    {
        opt_val += Math.Max(asset_path[k] - Strike, 0);
    }
}
return (opt_val / NumberScenarios_);
```
