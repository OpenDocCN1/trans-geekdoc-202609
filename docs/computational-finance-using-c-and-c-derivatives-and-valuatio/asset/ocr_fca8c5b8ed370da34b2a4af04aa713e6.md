# 264 CHAPTER | 8 C# Portfolio Pricing Application

```
if (put == 1) throw Exception(Pre_String, + "--- Can't pick a price uisng calculation method");

int n_sigma = 2;

// set the parameters to have "reasonable accuracy"
double[] sigma_array = new double[n_sigma];
double[] times = new double[n_sigma];

sigma_array[0] = Sigma;
sigma_array[1] = Sigma;

sigma_times[0] = 0.0;
times[1] = Time_To_Expiry;

int nt = 196;
int ns_below = nt / 2;
int ns_above_50 = nt / 2;
double the_alpha = 0.5;
double UpperBarrier = S1 * S0;

int flag = 0;
pricing.dll.call(BarrierLevel, UpperBarrier,
them, S1, ref sigma_array, ref sigma_times,
n_sigma, ref is_american, + ref Time_To_Expiry.
Strike, ref is_american, ref val.
IntPtr.Zero, DividendYield, ref ns_below, ref ns_above_50, ref val);

if (flag != 0)
throw new Exception(Pre_String, + "--- An error occurred in a call to the pricing library");
else
bool is_put = (put == 1);
if (is_american == 1) throw new Exception(Pre_String, + "--- Can't pick an American option uisng
this calculation method");

if (S1 < BarrierLevel) // the option is already knocked out
val = 0;
else
val = MonteCarloSim(is_put);
```

protected void Validate()

```
{
  Pre_String = Name() + " (" + Reference + ")";
  if (NumberUnits < 0)
    throw new Exception(Pre_String, + "--- Number of units cannot be less than zero");
  if (Time_To_Expiry < 0.0)
    throw new Exception(Pre_String, + "--- Time to expiry cannot be less than zero years");
  if (RiskFreeRate < 0.0)
    throw new Exception(Pre_String, + "--- Risk free rate cannot be less than zero");
  if (Strike < 0.0)
    throw new Exception(Pre_String, + "--- Strike cannot be less than zero");
  if (BarrierLevel < 0.0)
    throw new Exception(Pre_String, + "--- BarrierLevel cannot be less than zero");
  if (Signal < 0.0)
    throw new Exception(Pre_String, + "--- Volatility cannot be less than zero");
}
```

private double MonteCarloSim(bool is_put)

```
// Use the Brownian Bridge to compute the value of a down and out call option
int seed = 111;
```

# Code excerpt 8.11 (Continued).