

## 254 第 8 章 C# 投资组合定价应用程序

交易属性所使用的枚举定义在下方。

```csharp
public enum BuySell { Buy, Sell };
public enum CallPut { Call, Put };
public enum EuropeanAmerican { European, American };
public enum MinimumMaximum { Minimum, Maximum };
public enum VaOptionType { Va, NoVa };
public enum CalculationMethod { Analytic, Numeric, MonteCarlo };
```

可以看出，这些枚举具有明显的名称。
之前已经提到，应用程序用于为期权定价的波动率是作为交易属性提供的，而不是存储在市场数据中。这样做的原因是为了简单明了。在第 4 章中，我们提到需要一个波动率曲面来获取用于期权定价的隐含波动率。存储隐含波动率将需要在市场数据文件中存储一组波动率曲面，并使用多维插值法来获取适用于特定期权的波动率。我们决定选择波动率作为交易属性并更新其其值。

## 8.3.1 简单股票期权

代码段 8.8 显示了计算单个股票期权值的类。

```csharp
namespace ComputationalLib
{
    public class EquityOptionDeal : BaseDeal
    {
        public string EquityName { get { EquityName; } set { EquityName = value; }
        public int NumberUnits { get { NumberUnits; } set { NumberUnits = value; }
        public double TimeToExpiry { get { TimeToExpiry; } set { TimeToExpiry = value; }
        public CallPut OptionType { get { OptionType; } set { OptionType = value; }
        public EuropeanAmerican ExerciseStyle { get { ExerciseStyle; } set { ExerciseStyle = value; }
        public double Strike { get { Strike; } set { Strike = value; }
        public BuySell BuySell { get { BuySell; } set { BuySell = value; }
        public double Volatility { get { Volatility; } set { Volatility = value; }

        protected CallPut OptionType = CallPut.Call;
        protected EuropeanAmerican ExerciseStyle = EuropeanAmerican.European;
        protected double Strike;
        protected string EquityName = "";
        protected double TimeToExpiry = 0.0;
        protected double DividendYield = 0.0;
        protected double PreStrike = 0.0;
        protected BuySell BuySell = BuySell.Buy;
        protected int NumberUnits = 1;
        protected double Sigma = 0.0;
    }

    public override string Name()
    {
        return "Equity Option";
    }

    public override double Price()
    {
        double val = 0.0;
        double[] spots = new double[6];
        double fx_spot = 0.0;
        try
        {
            s = MarketDataDictionaries.EquityTable[EquityName].Spot; // 获取当前股票价格
```

代码段 8.8 `EquityOptionDeal` 的 C# 类计算单个股票期权的值。

```csharp
Currency_ = MarketDictionaries.EquityTable[EquityName].Currency;
// 获取股票波动率（假设为常数）
DividendField = MarketDictionaries.EquityTable[EquityName].DivField; // 获取股票股息率
```

```csharp
catch {
    throw new Exception(Pre_String + " No Market data supplied for " + EquityName);
    // 获取无风险利率
double discount_fact = 0.6;
double RiskFree_rate = 0.6;
```

```csharp
Curve DF = MarketDictionaries.CurrencyTable[Currency_].YieldCurve; // 获取折因子
discount_fact = DF(Time_To_Expiry);
RiskFree_Rate = Math.Log(discount_fact) / Time_To_Expiry;
fx_spot = MarketDictionaries.CurrencyTable[Currency_].spot;
```

```csharp
catch {
    throw new Exception(Pre_String + " No Market data supplied for " + Currency_);
```

```csharp
int flag;
flag = 0;
put = OptionType == Put ? 1 : 0;
```

```csharp
if (ExerciseStyle == EuropeanAmerican.American) // 使用 Black-Scholes
    // Call++ 程序；
    // 注意：提供一个点以便不计算希腊字母（Greeks）
Pricing.black_scholes(ref val, IntPtr.Zero, Strike, Sigma, Time_To_Expiry,
RiskFreeRate, DividendField, put, ref flag);
```

```csharp
else {
    // 使用 Crank Nicolson
double steps = 0.5;
int is_american = 1;
    // 固定网格密度（这些值值应当是“合理”的结果）
tnx = 50; // 资产轴划分
tny = 50; // 时间轴划分
double max = 10.0 * sk;
```

```csharp
Pricing.opt_get_the_tas(steps, Sigma, RiskFreeRate, Time_To_Expiry, Strike,
is_american, ref val, IntPtr.Zero, DividendField, ns);
```

```csharp
if (flag != 0)
    throw new Exception(Pre_String + " --- 在调用定价库时发生错误);
val = "fx " + NumberOfUnits_; // 返回基础货币的值
```

```csharp
if (NumberOfUnits_ < 0) {
        throw new Exception(Pre_String_ + " --- 单位数不能小于零);
    }
    if (Sigma_ < 0) {
        throw new Exception(Pre_String_ + "--- 波动率不能小于零);
    }
```

代码段 8.8（续）。

256 第 8 章 C# 投资组合定价应用程序

两种股票

计算两种股票期权的代码在下方代码段 8.9。

```csharp
using System;
namespace ComputationalLib
{
    public class EquityDetail : BaseDeal
    {
        public string Equity1 { get { Equity1_ } set { Equity1_ = value; }
        public string Equity2 { get { Equity2_ } set { Equity2_ = value; }
        public double TimeToExpiry { get { TimeToExpiry_ } set { TimeToExpiry_ = value; }
        public int NumberOfHedges { get { NumberOfHedges_ } set { NumberOfHedges_ = value; }
        public CallPut OptionType { get { OptionType_ } set { OptionType_ = value; }
        public double MinimumMaximum { get { MinimumMaximum_ } set { MinimumMaximum_ = value; }
        public EuropeanAmerican ExerciseStyle { get { ExerciseStyle_ } set { ExerciseStyle_ = value; }
        public double Strike { get { Strike_ } set { Strike_ = value; }
        public BuySell BuySell { get { BuySell_ } set { BuySell_ = value; }
        public double Volatility { get { Volatility_ } set { Volatility_ = value; }
        public double Signal { get { Signal_ } set { Signal_ = value; }

        protected string Equity1_;
        protected string Equity2_;
        protected double TimeToExpiry_ = 0.0;
        protected int NumberOfHedges_;
        protected string Pre_string_ = "";
        protected double d1_ = 0.0;
        protected double d2_ = 0.0;
        protected double Signal1_ = 0.0;
        protected double Signal2_ = 0.0;
        protected BuySell BuySell_ = BuySell.Buy;

        public override string Name()
        {
            return "Rainbow(two equities)";
        }

        public override double Price()
        {
            Validate();

            double val = 0.0;
            double rho = 0.0; // 相关性默认为零
            double fx_spot = 0.0;

            try
            {
                S1_ = MarketDataDictionaries.EquityTable[Equity1_].Spot;
            }
            catch
            {
                throw new Exception(Pre_string_ + "--- 未提供 " + Equity1_ + " 的市场数据");
            }

            try
            {
                S2_ = MarketDataDictionaries.EquityTable[Equity2_].Spot;
                S1_ = MarketDataDictionaries.EquityTable[Equity1_].Spot;
            }
            catch
            {
                throw new Exception(Pre_string_ + "--- 未提供 " + Equity2_ + " 的市场数据");
            }

            if(string.Compare(MarketDataDictionaries.EquityTable[Equity1_].Currency,
                MarketDataDictionaries.EquityTable[Equity2_].Currency) != 0)
            {
                throw new Exception(Pre_string_ + "--- 者的货币不相同");
            }

            Currency_ = MarketDictionaries.EquityTable[Equity1_].Currency;
            return val;
        }
    }
}
```

计算两种股票期权值的 C# 代码。

## 8.3.3 通用篮型期权

在这里，我们考虑抽象交易 `GenericEquityBasketOptionDeal`，它允许其衍生类对任意数量的股票进行期权交易。

