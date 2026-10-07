
`protected Custom OptionType_ = PutCall;`

`protected European ExerciseStyle_ = American.European;`

`protected double TimeToExpiry_ = 0.0;`

`protected double DomesticIsFreeRate_ = 0.0;`

`protected double Sigma_f_d_ = 0.0;`

`protected string Pre_String_ = "";`

`public override string Name()`

`{`

`    return "FX Option";`

`}`

`public override double Price()`

`{`

`    Validate();`

`    double val = 0.0;`

`    double[] geeks = new double[6];`

`    int i, j;`

`    double discount_fac = 0.0;`

`    double X_f_b = 0.0, X_d_b = 0.0;`

`    double Sigma=0.0,Strike_b;`

`// 获取本币信息`

`try`

`{`

`    ICurve Curve = MarketDataDictionaries.CurrencyTable[DomesticCurrency_].YieldCurve;`

`    ICurve Curve = MarketDataDictionaries.CurrencyTable[ForeignCurrency_].YieldCurve;`

`    // 获取折因子`

`    discount_fac = Curve.Get(0)`

`// 获取外币信息`

`try`

`{`

`    ICurve Curve = MarketDataDictionaries.CurrencyTable[ForeignCurrency_].YieldCurve;`

`    // 获取折因子`

`    discount_fac = Curve.Get(0, Time_To_Expiry_);`

`    ForeignIsFreeRate_ = -Math.Log(discount_fac) / Time_To_Expiry_;`

`    X_f_b = MarketDataDictionaries.CurrencyTable[ForeignCurrency_].spot;`

`    Spot_ = X_f_b; // 外汇基货币`

`}`

`catch`

`{`

`}`

# 代码示例 8.13 计算外汇期权价值的 C# 代码。

*注意*

```csharp
throw Exception(Pre_string_ + " ----- 调用定价库时发生错误");
```

```csharp
if (lag <= 0)
    put = OptionType.Call ? 1 : 0;

if (ExerciseStyle == American.European) // 使用 BlackScholes
{
    // 提供一个 Null 以便不计算希腊值
```

```csharp
protected override void Validate()
{
Pre_string_ = Name + " (" + Reference + ")";
    if (Time_Expiry < 0)
    {
        throw new Exception(Pre_string_ + " ----- 到期时间不能小于零");
    }
    if (NumberOfUnits_ < 0)
    {
        throw new Exception(Pre_string_ + " ----- 单位数量不能小于零");
    }
    if (Strike_f_d_ < 0.0)
    {
        throw new Exception(Pre_string_ + " ----- 执行价不能小于零");
    }
}
```

### 8.4.3 外汇期权细节

```csharp
using Systems;
namespace Computational_lib
{
    public class DefaultFXOption:BaseDeal
    {
        public int NumberOfUnits_ { get return NumberOfUnits_ } set { NumberOfUnits_ = value; };
        // 注意：执行价是获取一个单位外币所需的本币单位数
        public double Strike { get return Strike_f_d } set { Strike_f_d_ = value; }
    }
}
```

代码示例 8.14 计算外汇障碍期权价值的 C# 代码。

# 第270 章 | 第8章 C# 投资组合定价应用

```csharp
// Barrier 以执行价单位为单位
public double Barrier { get { Barrier_f_d; } set { Barrier_f_d = value; }

// Volatility 以汇率表示
public double Volatility { get { Volatility; } set { Sigma_f_d = value; }
public string Currency { get { Currency_; } set { Currency_ = value; }
public string DomesticCurrency { get { DomesticCurrency; } set { DomesticCurrency_ = value; }
public bool Buysel { get { Buysel; } set { Buysel_ = value; }

public double CalculationMethod { get { CalculationMethod; } set { CalculationMethod_ = value; }
public string AmericanExerciseStyle { get { ExerciseStyle; } set { ExerciseStyle_ = value; }
public int NumberScenario { get { NumberScenario; } set { NumberScenario_ = value; }
public bool UseAmericanBridge { get { UseAmericanBridge; } set { UseAmericanBridge_ = value; }

protected double Strike_f_d = 0.0;
protected string Currency_ = "";
protected bool Buysel_ = false;
protected int NumberUnits_ = 0;
public double Time_To_Expiry { get { Time_To_Expiry; } set { Time_To_Expiry_ = value; }
public CallOptionType OptionType { get { OptionType; } set { OptionType_ = value; }
protected CallOptionType OptionType = CallOption;
protected double EuropeanStrike_ = 0.0;
protected double Sigma_f_d = 0.0;
protected string AmericanExerciseStyle = AmericanExerciseStyle;
protected double CalculationMethod = CalculationMethod;
protected int Time = 0;
protected int NumberScenario = 1000;
protected double Barrier_b = Barrier_b;
protected bool UseAmericanBridge_ = true;
protected string String_ = "";

public string override ToString()
{
    return "外汇期";
}

public override double Price()
{
    Validate();

    double val = 0;
    int iflag = 0;
    double discount_fact = 0.0;
    double X_f = 0.0, X_b = 0.0;

    // 获取货币信息
    ICur df = DomesticCurrency.Table[DomesticCurrency_].YieldCurve;
    // 获取折现因子
    discount_fact = df(0, Time_To_Expiry);
    ForwardStrikeRate_ = -Math.Log(discount_fact) / Time_To_Expiry;
    X_f = DomesticCurrency.Table[DomesticCurrency_].spot;
    X_b = Strike; // Strike 是货币单位的执行价
    Barrier_b = Barrier_f * Barrier_b;
    Barrier_ = Math.Max(Barrier_b, EPS);

    catch
    {
        throw new Exception(Pre_String + "-- 为 " + DomesticCurrency_ + "提供了市场数据)");
    }

    // 获取货币信息
    ICur df = DomesticCurrency.Table[DomesticCurrency_].YieldCurve;
    // 获取折现因子
    discount_fact = df(0, Time_To_Expiry);
    ForwardStrikeRate_ = -Math.Log(discount_fact) / Time_To_Expiry;
    X_f = DomesticCurrency.Table[DomesticCurrency_].spot;
    X_b = Strike; // 外汇基货币

    catch
    {
        throw new Exception(Pre_String + "-- 为 " + ForeignCurrency_ + "提供了市场数据)");
    }

    if iflag = 0;
    put = OptionType == Put ? 1 : 0;
    is_American = ExerciseStyle == American ? 1 : 0;
```

# 代码 8.14 (续)。

# 外汇类类部分 | 8.4 271

```csharp
if (CalcMethod == Analytic)
{
    if (Put == 1) throw new Exception(Pre_String + "--- 无法使用此方法为看跌期权定价");
    if (Is_American == 1) throw new Exception(Pre_String + "--- 无法使用此方法为美式期权定价");

// C++ 程序；
// 如果未提供速率，则不计算希腊字母
// 股息率设置为无风险利率
// 无风险利率设置为本币利率
// 以货币单位估算外汇期权的价值
PricingUtils.bs_opt_domestic_call(ref Barrier_Level_, Time_To_Expiry, DomesticFreeRate, ForeignFreeRate);

    if (flag != 0)
    {
        throw new Exception(Pre_String + "--- 调用定价库时发生错误");
    } else if (CalcMethod == Numeric)
    {
        if (Put == 1) throw new Exception(Pre_String + "--- 无法使用此方法为看跌期权定价");
        int n_sigma = 2;
        // 设置参数以获得“合理的准确性”
        double[] sigma_array = new double[n_sigma];
        double[] sigma = new double[n_sigma];

        sigma_array[0] = Sigma_f_;
        sigma_array[1] = Sigma_f_;

        sigma[0] = 0.0;
        sigma[1] = Time_To_Expiry;

        int nt = 100;
        int ns_below = 50 / nt;
        int ns_above = 50 / nt;
        double strike = 0.0;
        double UpperBarrierLevel = 50.0 * 5.0;
        // val 是以货币单位衡的外汇期权价值
        PricingUtils.dm_call(Barrier_Level, UpperBarrierLevel, strike, sigma_array, ref sigma, n_sigma, n_sigma, DomesticFreeRate, Time_To_Expiry, Strike, is_American, ref val, ForeignFreeRate, ns_below, ns_above, ref iflag);
    }

    if (flag != 0)
    {
        throw new Exception(Pre_String + "--- 调用定价库时发生错误");
    } else
    {
        bool is_put = (Put == 1);
        if (is_American == 1) throw new Exception(Pre_String + "--- 无法使用此方法为美式期权定价");

        if (S_0 >= Barrier_Level) // 期权已经失效
            val = 0.0;
        else
            val = MonteCarlo(is_put);
    }

    val = NumberOfUnits;
    return val;

    protected override void Validate()
    {
        Pre_String = Name() + " (" +
        if (Time_To_Expiry < 0)
        {
            throw new Exception(Pre_String + "--- 到期时间小于0");
        }
        if (NumberOf < 0)
        {
            throw new Exception(Pre_String + "--- 数量小于0");
        }
        if (Strike_f < 0)
        {
            throw new Exception(Pre_String + "--- 执行价小于0");
        }
    }

# **代码 8.14 (续)。**

272 章 | C# 投资组合定价应用

```csharp

}

if (Barrier_Level < 0)

{

    throw new Exception(Pre_String + "--- 障碍水平小于0");

}

if (Sigma_f_d < 0)

{

    throw new Exception(Pre_String + "--- 波动率小于0");

}

private double MonteCarlo(bool is_out)

{

    // 使用布朗桥计算向下和看涨期权的价值

    int seed = 1;

    double[] path = new double[TimeSteps];

    double time_step = Time_To_Expiry / TimeSteps;

    double opt_val = 0.0;

    bool not_out = true;

    double STN = 0.0;

    double mean = (DomestFreeRate - ForeignRiskRate - 0.5 * Sigma_f_d * Sigma_f_d) * time_step;

    double z;
```
