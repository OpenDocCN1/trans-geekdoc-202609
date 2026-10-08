
# C# portfolio pricing application

protected double ForeignFreeRate_ = 0.0;
protected double DomesticRiskFreeRate_ = 0.0;
protected double Sigma_f_ = 0.0;
protected double EuropeanExerciseStyle_ = EuropeanAmerican.European;
protected int CalculationMethod_ = CalculationMethod.Analytic;
protected int TimeSteps_ = 300;
protected int NumberScenarios_ = 3000;
protected double Strike_, Barrierlevel_b_;
protected bool UseBrownianbridge_ = true;
protected string Pre_string_ = "";

```csharp
public override string Name()
{
    return "Down FX Option";
}
```

```csharp
public override double Price()
{
    double val = 0.0;
    int flag, put, _is_american;
    double discount_fac = 0.0;
    double X_f_b = 0.0, X_d_b = 0.0;

// Get discount factor

```csharp
try {
    ICurve Curve = MarketDataDictionaries.CurrencyTable[DomesticCurrency].YieldCurve;
    // obtain the discount factor
    discount_fac = DF(0, Time_To_Expiry);
    DomesticRiskFreeRate_ = -Math.Log(discount_fac) / Time_To_Expiry;
    X_f_b = MarketDataDictionaries.CurrencyTable[DomesticCurrency].spot;
    Strike_ = X_d_b * Strike_f_j;
    // Strike is in the base currency units
    BarrierLevel_b_ = X_d_b * Barrier_f_j;
    BarrierLevel_d_b_ = Math.Max(BarrierLevel_b_, PricingUtils.EPS);
}
catch {
    throw new Exception(Pre_string_ + "---- No Market data supplied for " + DomesticCurrency_);
}
```

// Get foreign currency information

```csharp
try {
    ICurve Curve = MarketDataDictionaries.CurrencyTable[ForeignCurrency].YieldCurve;
    // obtain the discount factor
    discount_fac = DF(0, Time_To_Expiry);
    ForeignRiskFreeRate_ = -Math.Log(discount_fac) / Time_To_Expiry;
    X_f_b = MarketDataDictionaries.CurrencyTable[ForeignCurrency].spot;
    S0_ = X_f_b; // Exchange rate base currency
}
catch {
    throw new Exception(Pre_string_ + "---- No Market data supplied for " + ForeignCurrency_);
}
```

```csharp
if (iflag == 0) {
    put = OptionType_ == Call.Put ? 1 : 0;
    _is_american = ExerciseStyle_ == European.American ? 1 : 0;
}

if (CalculationMethod_ == CalculationMethod.Analytic) {
    if (put == 1) throw new Exception(Pre_string_ + "---- Can't put using this calculation method");
    if (_is_american == 1) throw new Exception(Pre_string_ + "---- Can't an American option using this calculation method");
}

// C routine.
// Note: A null pointer is supplied so that the Greeks are not computed
// Dividend yield is set to risk free rate
// Risk free interest rate is set to the domestic rate
```

# Code example 16 (Continued).

```csharp
// val is the value of the FX option in currency units
PricingUtils.bs_opt_barrier_downout_call(ref val, BarrierLevel_b,
S0_, Strike_b_, Sigma_f_d,
TimeToExpiry_, DomesticDiskFreeRate,
ForeignRiskRate_, ref iflag);

if (iflag != 0) {
    throw new Exception(Pre_string_ + "--- An error occurred in a call to the
    pricing library");
} else if (CallMethod == CalculationMethod.Numeric) {
    if (put == 1) throw new Exception(Pre_string_ + "--- Can't price a put using
    this calculation method");
}
```

```csharp
n_sigma = 2;
// set up the parameters so that they have "reasonable accuracy"
double[] sigma_array = new double[n_sigma];
double[] sigma_times = new double[n_sigma];

sigma_array[0] = Sigma_f_d;
sigma_array[1] = Sigma_f_d;
sigma_times[0] = 0.0;
sigma_times[1] = Time_To_Expiry;

nt = 100;
nt_below_S0 = nt / 2;
nt_above_S0 = nt / 2;
double UpperBarrierLevel = S0_ * 5.0;
```

```csharp
if (iflag == 0) {
    // val is the value of the FX option in currency units
    dko.call(BarrierLevel_b, UpperBarrierLevel,
    theta_m, S0_, ref sigma_array[0], ref sigma_times[0],
    n_sigma, DomesticRiskFreeRate_, Time_To_Expiry,
    Strike_b_, is_American, ref val;
    IntPtr.Zero, ForeignRiskFreeRate_, ns_below_S0, ns_above_S0,
    nt, ref iflag);
}

if (iflag != 0) {
    throw new Exception(Pre_string_ + "--- An error occurred in a call to the
    pricing library");
}
else {
    bool is_put = (put == 1);
    if (is_American == 1) throw new Exception(Pre_string_ + "--- Can't price an American option using this method");
    if (S0_ < BarrierLevel_b) // the option has been knocked out
        val = 0.0;
    } else {
        val = MonteCarlo(is_put);
    }
}

val *= NumberOfUnits;
return val;

protected override void Validate() {
    Pre_string_ = Name() + " (Reference)";
    if (Time_To_Expiry_ < 0) {
        throw new Exception(Pre_string_ + "--- Time to expiry cannot be less than years");
    }
}
```

# Code excerpt 8.16 (Continued).

# C# portfolio pricing application

```csharp
if (NumberOfUnits < 0) {
    throw Exception(Pre_string_ + "---- Number of units cannot be less than zero");
}
if (Strike_ < 0) {
    throw Exception(Pre_string_ + "---- The strike cannot be less than zero");
}
if (BarrierLevel_b < 0) {
    throw Exception(Pre_string_ + "---- BarrierLevel cannot be less than zero");
}
if (Sigma_f_d < 0) {
    throw Exception(Pre_string_ + "---- Volatility cannot be less than zero");
}

private double MonteCarlo(bool is_put)
{
    // Use the Brownian Bridge to compute the value of down out option
    int seed = 1;
    double[] asset_path = new double[TimeSteps];
    double time_step = Time_To_Expiry / TimeSteps;
    double sqrt_time_step = Math.Sqrt(time_step);
    double disc = Math.Exp(-DomesticRiskFreeRate_ * Time_To_Expiry);
    PricingUtils.set_seed(seed);
    double opt_val = 0.0;
    bool not_out = true;
    int k = 0;
    double STN = 0.0;
    double mean = (DomesticRiskFreeRate_ - Sigma_f_d_ * Sigma_f_d * 0.5) * time_step;
    double std = Math.Sqrt(Sigma_f_d_ * Sigma_f_d_ * time_step);
    double opt_vals = 0.0;

    for (int i = 0; i < NumberScenarios; i++)
    {
        // generate the asset path
        double ST1 = S0;
        not_out = true;

        while (not_out && k < TimeSteps) {
            double z = PricingUtils.RndNorm(mean, std);
            STN = Math.Exp(z);
            if (STN < BarrierLevel_b) not_out = false;
            ST1 = STN;
            asset_path[k] = STN;
            k++;
        }

        if (is_put) {
            opt_val = Math.Max(STN - Strike_b_, 0.0);
        }
        else {
            opt_val = Math.Max(Strike_b_, -STN, 0.0);
        }

        if (not_out)
            // only if value is above the barrier_level
            // compute the probability that the asset remained above the barrier
            if (useBrownianBridge) {
                double total_probability = 1.0, pr;
                double sigma_sim2 = Sigma_f_d_ * Sigma_f_d_;
                double log_barrier_level = Math.Log(BarrierLevel_b);
                double fac;
                for (int jj = 0; jj < TimeSteps - 1; jj++) {
                    double log_S_i = Math.Log(asset_path[jj]);
                    double log_S_li = Math.Log(asset_path[jj + 1]);
                    fac = 2.0 * (log_barrier_level - log_S_li) / (sigma_sim2 * time_step);
                    total_probability *= pr;
                    pr = (1.0 - Math.Exp(-fac));
                    // probability of staying above the barrier between i and i+1
                    sum_opt_vals += total_probability_above * opt_val * disc;
                }
            } else {
                // don't use the Brownian Bridge
                sum_opt_vals += opt_val * disc;
            }
        }
    }
    double temp = sum_opt_vals / (double)NumberScenarios;
    return temp;
}
```

# Code excerpt 8.16 (Continued).

# Appendix A:

## The Greeks for European options

### A.1 Introduction

In this section we will present some useful results which will be used later on to derive expressions for the Greeks.
A fundamental result of calculus is:

```
$$\frac{\partial}{\partial x}\int f(x) dx = f(x) \quad (A.1.1)$$
```

Also the indefinite integral, $\int f(x) dx$, can be expressed as a definite integral with variable upper bound as:

```
$$\int f(x) dx = \int_{a}^{x} f(x) dx + c$$
```

so

```
$$\frac{\partial}{\partial x}\int_{y=a}^{y=x} f(y) dy = f(x) \quad (A.1.2)$$
```

We can use this result to obtain the derivative of the cumulative distribution function:

```
$N_1(x) = \frac{1}{\sqrt{2\pi}}\int_{-\infty}^{y=x} exp(-\frac{y^2}{2}) dy$$
```

which gives:

```
$$\frac{\partial}{\partial x}N_1(x) = n(x) \quad (A.1.3)$$
```

We now derive various results for the parameters $d_1$ and $d_2$ which appear in the Black–Scholes equation:

```
$d_1 = \frac{\log(S/E) + (r-q+\sigma^2/2)(T-t)}{\sqrt{T-t}} \quad (A.1.4)$
```
