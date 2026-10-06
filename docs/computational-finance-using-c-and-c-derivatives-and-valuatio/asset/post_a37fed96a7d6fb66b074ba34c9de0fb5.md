
# 248 CHAPTER 8 C# Portfolio Pricing Application

```csharp
public class TPair : IComparable
{
    public double t;
    public double val;

    public TPair(double t1, double val1) {
        t = t1;
        val = val1;
    }

    public int CompareTo(object obj) {
        TPair temp = (TPair)obj;
        if (this.t < temp.t)
            return -1;
        if (this.t > temp.t)
            return 1;
        else
            return 0;
    }
}
```

```csharp
// ICur - a curve for storing interest rates
public class ICur
{
    private double _t; // internal value used for matching
    private string _name = "";

    public ICur(string name) {
        _name = name;
    }

    public double this[double t, double t1] {
        get { // return the discount factor between t and t1
        double eps = 1.6e-6;
        t_pt = t;
        // find the bounding indices corresponding to a given t value
        int indx = this.FindIndex(TPairfind);
        if (indx == -1)
            throw new Exception("Invalid market data interest rate curve for currency " + _name + "");
        double v2 = this[indx].val;
        double v1 = this[indx-1].val;
        double t2 = this[indx].t;
        double t1 = this[indx-1].t;
        if (Math.Abs(t2 - t) < eps)
            val = v2;
        else
            // use linear interpolation to compute the value of DF
            val = v1 + (v2 - v1) * (t - t1) / (t2 - t1);
        }
        val = Math.Exp(-val * t);
        return val;
    }

    public double this(double t, double t1, double t2) {
        // return the forward rate between t1 and t2
        // t = t1;
        double DF1 = this[t, t1];
        double DF2 = this[t, t2];
        double fwd = (DF1 / DF2 - 1.6) / (t2 - t1);
        return fwd;
    }

    private bool TPairfind(TPair v) {
        if (v.t > _t_pt)
            return true;
        else {
            return false;
        }
    }
}
```

**Code excerpt 8.3** Showing the class Currency and all the classes ICur and TPair which enable the interest rate curve to be stored.

```csharp
public class Currency {
    public string name; // the name of the currency (e.g GBP, or USD)
    public double spot; // the spot of the currency with respect to base currency
    public Curve YieldCurve; // the currency yield curve
    public Curve VolCurve; // the volatility of the yield curve (not currently used by the C# application)

    public Currency(string name, double spot) // two parameter constructor {
        name = name;
        spot = spot;
        YieldCurve = new YieldCurve(name);
    }

    public Currency(string name) // single parameter constructor {
        YieldCurve = new YieldCurve(name);
        VolCurve = new VolCurve(name);
    }
}
```

# Code excerpt 8.3 (Continued).

It is straightforward to add currency data to CurrencyTable. The following C# code fragment illustrates the addition of USD information.

```csharp
string CyCode = "USD"; // set the currency code to USD
// creates a new (empty) entry in the CurrencyTable for USD
CurrencyTable.Add(CyCode, new Currency(CyCode));

double FXSpot = 0.8565; // set the USD to base currency FX spot
// assign to the public data member spot, in class Currency
CurrencyTable[CyCode].spot = FXSpot;
// assign to the public data member name, in class Currency
CurrencyTable[CyCode].name = CyCode;

double dt;
t = 0.06; // time for point 1
rt = 0.9184; // rate for point 1
// add the first point to the public data member YieldCurve, in class Currency
CurrencyTable[CyCode].YieldCurve.Add(new TPair(t, rt));

t = 0.50;
rt = 0.9513;
CurrencyTable[CyCode].YieldCurve.Add(new TPair(t, rt));
```

# Code excerpt 8.4. Showing the addition of USD market data to the CurrencyTable dictionary.

The information in the CurrencyTable is accessed by the deal classes and to compute discount factors, forward rates, and FX spots. In the market data file, see Exhibit 8.2, the YieldCurve consists of a set of time/value pairs and is defined using the following syntax:

YieldCurve = {(t1, r1), ..., (tn, rn)}, where ti is the time in years, and ri is the zero coupon rate with tenor ti.

The value, at t = 0, of a zero coupon bond with cash-flow maturity, ti, is exp(-ri * ti) and is known as the discount factor DF(0,ti). Code excerpt 8.4 shows the addition of two items data to the USD yield curve, while Code excerpt 8.5 illustrates the retrieval from DF(0,ti) of ri. The code fragment

```csharp
double discount_fac = DF(0, Time_To_Expiry);
RiskFreeRate = -Math.Log(discount_fac) / Time_To_Expiry;
```

computes the zero coupon rate RiskFreeRate. It should be mentioned that it would have been easier to write code to directly obtain the interpolated risk-free rate from the USD yield curve (without first computing the associated discount factor). However, the required code can easily supplied by the reader.

```csharp
try {
    string Currency = "USD";
    // DF will be used to access discount factors
    double DF = MarketDataDictionaries.CurrencyTable[Currency].YieldCurve;
    // FWD will be used to access forward rates
    double FWD = MarketDataDictionaries.CurrencyTable[BaseCurrency].YieldCurve;
**Code 8.5** Showing the retrieval of USD market data from the CurrencyTable dictionary.

Discount factors and forward rates are accessed from an ICur object. The discount factor is obtained as follows:

```csharp
double discount_fac = DF[0, Time_To_Expiry];
```

where DF[0, Time_To_Expiry] calls the ICur accessor (declared as public double this[double t0, double t1]) with t0 = 0 and t = Time_To_Expiry. It is seen from Code excerpt 8.3 that linear interpolation is performed by the accessor. The forward rate is accessed in a similar manner:

```csharp
double forward_rate = FWD(0, t1, t2);
```

where FWD[0, t1, t2] is returned with the statement

```csharp
FWD(0,t1,t2) = (DF(0,t2) / DF(0,t1) - 1.0) / (t2 - t1);
```

with t=0.5, and t2 = 1.5. Code excerpt 8.7 The MarketDataDictionaries classes, illustrating how market data is added to the internal dictionaries.

```csharp
if (v.IndexOf("--Base") != -1) BaseCurrency_ = CyCode;
k += 2;
if (CurrencyTable.ContainsKey(Cycode)) {
    CurrencyTable.Add(Cycode;
```

# Code except 8.7 (Continued).

# Code example 8.7 (Continued).

Code example 8.7 shows how market data is added to the internal dictionaries of the MarketDataDictionaries class. For instance it is first necessary to construct the dictionary and then determine whether or not the entry already exists in the dictionary. This is shown in the code fragment below

```csharp
// CorrelationKey = AssetName1 + " - " + AssetName2;
// Check whether this key already exists in the dictionary CurrencyTable.
// if it doesn't then add a new entry, if it does raise an exception
if(!CorrelationTable.Contains(CorrelationKey)) {
    // Create a new empty dictionary for the unique key
    CurrencyTable.Add(CorrelationKey, new Correlation());

    // Fill out the entry by assigning the correlation and the asset names
    CorrelationTable[CorrelationKey].Correl = corr;
    CorrelationTable[CorrelationKey].Name = AssetName1;
    CorrelationTable[CorrelationKey].Name = AssetName2;

    // Create another entry by assigning the asset names in reverse order
    // by correlation(a,b) + correlation(b,a)
    CorrelationKey = AssetName2 + " - " + AssetName1;

    // Fill out the entry by assigning the correlation and the asset names
    CorrelationTable.Add(CorrelationKey, new Correlation());
    CorrelationTable[CorrelationKey].Correl = corr;
    CorrelationTable[CorrelationKey].Name = AssetName2;
    CorrelationTable[CorrelationKey].Name = AssetName1;
} else {
    throw new Exception("market data already supplied for " + CorrelationKey);
}
}
FILE.Close();
```

# 8.3 EQUITY DEAL CLASSES

In this section, we provide the C# code for both single and multi-asset equity options. The trade attributes correspond to the properties of the deal class, and attribute default values can be readily found by reading the C# code.
