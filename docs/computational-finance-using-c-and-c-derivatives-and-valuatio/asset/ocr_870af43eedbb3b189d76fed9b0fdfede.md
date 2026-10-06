# Equity Deal Classes Section | 8.3 259

```
throw new Exception(Pre_string
```

```
)
Currency_ = MarketDataDictionaries.CurrencyTable[EquityNames[1]].Currency;
try {
ICurve DF = MarketDataDictionaries.CurrencyTable[Currency].YieldCurve; // obtain the discount factor
double discount_scf = DF(W
```

```
String[] Vols = Volatilities.Split(seps, StringSplitOptions.None);
int n = Vols.Length;
m = Vols.Length;
if (n != m) {
throw new Exception(Pre_string, + "---- Number of variables is not the same
as the number of keys ");
}
```

```
Sigma_ = new double[n];
for (int k = 0; k < n; k++) {
try {
Sigma_[k] = double.Parse(Vols[k]);
catch {
throw new Exception(Pre_string, + "---- Invalid volatility supplied for " + EquityNames[k]);
}
}
```

```
Correlations_ = new double[n, n];
for (int i = 0; i < n; i++) {
for (int j = 0; j < n; j++) {
if (i != j) {
string corr_key = EquityNames[i] + "_" + EquityNames[j];
if (MarketDataDictionaries.CorrelationTable.ContainsKey(corr_key))\nCorrelations_[i, j] = MarketDataDictionaries.CorrelationTable[corr_key].Correl;
else
Correlations_[i, j] = 0.0; // default correlation is zero
}
else {
Correlations_[i, j] = 1.0;
}
}
}
```

```
int iflag=0;
val = MonteCarloSim(iflag);
if (iflag != 0) {
throw new Exception(Pre_string, + "---- An error occurred in the calling to the pricing library");
val = fx_spot * NumberOfUnits;
return val;
}
```

```
protected void Validate() {
Pre_string = Name + + " (---- Reference_ ");
if (Time_To_Expiry < 0.0) {
throw new Exception(Pre_string, + "---- Time to expiry cannot be less than zero years");
}
if (NumberOfUnits < 0) {
throw new Exception(Pre_string, + "---- Number of units cannot be less than zero");
}
}
```

# Code excerpt 8.10 (Continued).