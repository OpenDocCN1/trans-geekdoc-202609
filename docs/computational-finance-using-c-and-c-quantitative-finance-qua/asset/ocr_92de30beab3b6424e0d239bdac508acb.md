# C# portfolio pricing application

# 277

```
BarrierLevel_ = Math.Max(BarrierLevel_, PricingUtils.EPS);
```

```
if (CalcMethod == CalculationMethod.Analytic)
    if (put == 1) throw new Exception(Pre_String_ + "--- Can't put a price using this calculation method");
    if (is_american == 1) throw new Exception(Pre_String_ + "--- Can't price an American option using this calculation method");
```

```
PricingUtils.bs_opt_barrier_downout_call(ref val, BarrierLevel_, S1_, Strike, Sigma1_, Time_To_Expiry_, RiskFreeRate_, DividendYield_, ref iflag);
```

```
if (iflag != 0)
    throw new Exception(Pre_String_ + "--- An error occurred in a call to the pricing library");
else if (CalcMethod == CalculationMethod.Numeric)
    if (put == 1) throw new Exception(Pre_String_ + "--- Can't put a price using this calculation method");
```

```
int n_size = 2;
// set up the parameters that have "reasonable accuracy"
double[] sigma_array = new double[n_size];
double[] sigma_times = new double[n_size];
```

```
sigma_array[0] = Sigma1;
sigma_array[1] = Sigma1;
```

```
sigma_times[0] = 0.0;
sigma_times[1] = Time_To_Expiry_
```

```
int nt = 100;
t ns_below_0 = nt / 2;
t ns_above_0 = nt / 2;
double theta_m = 0.5;
double UpperBarrierLevel = S1_ * 5.0;
```

```
PricingUtils.dco_call(BarrierLevel_, UpperBarrierLevel,
theta_m, S1_, ref sigma_array[0], ref sigma_times[0],
n_size, RiskFreeRate_, Time_To_Expiry_,
Strike_, is_american, ref val,
nt, ns_below_0, ns_above_0,
t, iflag);
```

```
if (iflag != 0)
    throw new Exception(Pre_String_ + "--- An error occurred in a call to the pricing library");
```

```
else
    bool is_put = (put == 1);
    if (is_american == 1) throw new Exception(Pre_String_ + "--- Can't price an American option using this calculation method");
```

```
if (S1_ < BarrierLevel_) // the option is already knocked out
    val = 0.0;
else
    val = MonteCarloSim(is_put);
```

```
val = fx_spot * NumberOfUnits;
    return val;
```

# Code excerpt 8.13 (Continued).