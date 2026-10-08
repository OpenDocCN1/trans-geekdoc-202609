

# 280

# 使用 C 和 C# 进行计算金融金融

- 3.8269-蒙特卡洛，下穿股票期权
- 3.8860-蒙特卡洛（美式），下穿股票期权
- 3.8906-蒙特卡洛（1000次场景：不使用布朗桥），下穿股票期权
- 3.8908-蒙特卡洛（2000次场景：不使用布朗桥），下穿股票期权
- 4.1168-蒙特卡洛（4000次场景：不使用布朗桥），下穿股票期权
- 4.1176-蒙特卡洛（8000次场景：不使用布朗桥），下穿股票期权
- 4.1798-蒙特卡洛（16000次场景：不使用布朗桥），下穿股票期权
- 4.1961-蒙特卡洛（32000次场景：不使用布朗桥），下穿股票期权
- 3.1833-蒙特卡洛（44000次场景：不使用布朗桥），下穿股票期权
- 3.8754-蒙特卡洛（50000次场景：使用布朗桥），下穿股票期权
- 3.8773-蒙特卡洛（100000次场景：使用布朗桥），下穿股票期权
- 3.7386-蒙特卡洛（200000次场景：使用布朗桥），下穿股票期权
- 3.8089-蒙特卡洛（160000次场景：使用布朗桥），下穿股票期权
- 3.8506-蒙特卡洛（320000次场景：使用布朗桥），下穿股票期权
- 3.8644-蒙特卡洛（400000次场景：使用布朗桥），下穿股票期权

总价值 = 70.83 GBP
============================================

# 8.5 外汇交易类别

在这里，我们提供用于为外汇衍生品定价的代码。外汇期权程序与我们已经考虑过的股票期权程序非常相似，根本区别在于，对于外汇程序，同时存在本币和外币。外汇程序调用 Black-Scholes 模型，并将股息收益率设置为外币无风险利率，波动率则是外币/本币汇率的波动率。在市场数据中，少数现汇率是相对于基准货币的。

### 8.5.1 外汇远期

代码示例 8.14 用于计算外汇远期价值的 C# 代码。

```csharp
using System;
namespace Computational_Lib
{
    public class FXForwardDeal : BaseDeal
    {
        public double ForeignAmount { get { return fForeignAmount; }
        set { fForeignAmount = value; }

        // 注意：执行价是获得一个单位外币所需的本币单位数。
        public double strike { get { return fStrike; } set { fStrike = value; }}
        public string ForeignCurrency { get { return fForeignCurrency; }
        set { fForeignCurrency = value; }
        public string DomesticCurrency { get { return fDomesticCurrency; }
        set { fDomesticCurrency = value; }
        public bool BuySell { get { return fBuySell; } set { fBuySell = value; }
        public double Settlement { get { return fSettlement; } set { fSettlement = value; }
    }
}
```

代码示例 8.14 用于计算外汇远期价值的 C# 代码。*

# C# 定价组合应用程序

```csharp
protected double fStrike = 0;
protected string fForeignCurrency = "";
protected string fDomesticCurrency = "";
protected double fForeignAmount = 0;
protected double fBuySell = BuySell.Buy;
protected double fSettlement = 0;
protected string pre_string = "";
```

```csharp
public override string Name()
{
    return "FX Forward";
}

public override double Price()
{
    double val=0.0;
    Validate();
    double sign = fBuySell == Buy.Buy ? 1.0 : -1.0;

    try {
        ICurveDF_F = Currency[fForeignCurrency].YieldCurve;
        // 获取折扣因子
        ICurveDF_D = Currency[fDomesticCurrency].YieldCurve;
        // 获取折扣因子
        double X_fb = Currency[fForeignCurrency].spot;
        double X_db = Currency[fDomesticCurrency].spot;
        double DF_f = Currency[fForeignCurrency][settlement];
        double DF_d = Currency[fDomesticCurrency][settlement];

        val = ForeignAmount * DF_f * X_fb * sign - DF_d * X_db;
    } catch (Exception ex) {
        throw new Exception(pre_string + " " + ex.Message);
    }

    return val;
}

protected override void Validate()
{
    pre_string = Name() + " (";
```
```代码示例 8.14 用于计算外汇远期价值的 C# 代码。

### 8.5.2 外汇期权

用于计算外汇远期价值的 C# C# 代码在代码示例 8.15 中给出，与股票期权非常相似。例如，外汇期权使用：

```csharp
public override string Name()
{
    return "FX Option";
}

public override double Price()
{
    double val=0.0;
    double Delta = 0.0;
    double Gamma = 0.0;
    double Theta = 0.0;
    double Vega = 0.0;
    double Rho = 0.0;

    Validate();

    try {
        // 实现外汇期权定价
    } catch (Exception ex) {
        throw new Exception(pre_string + " " + ex.Message);
    }

    return val;
}

protected override void Validate()
{
    pre_string = Name() + " (");
```
### 8.5.3 外汇障碍期权

障碍障碍期权的 C# 代码在代码示例 8.16 中给出。

```csharp
using System;
namespace Computational_Lib
{
    public class DownOutFXOption:BaseDeal
    {
        public int NumberOfUnits { get { return NumberOfUnits_ } 
        set { NumberOfUnits_ = value; };
        // 注意：执行价是获得一个单位外币所需的本币单位数。
        public double Strike { get { return Strike_f_d } } set { Strike_f_d = value; };
        // 障碍水平与执行价单位相同
        public double BarrierLevel { get { return Barrier_f_d } } 
        set { Barrier_f_d = value; };
        // 波动率是外币/本币汇率的波动率。
        public double volatility { get { return Sigma_f_d } } set { Sigma_f_d = value; };
        public string ForeignCurrency { get { return ForeignCurrency_ } 
        set { ForeignCurrency_ = value; }
        public string DomesticCurrency { get { return DomesticCurrency_ } 
        set { DomesticCurrency_ = value; }
        public string BuySell { get { return BuySell_ } set { BuySell_ = value; }
        public string CalculationMethod { get { return CalculationMethod_ } 
        set { CalculationMethod_ = value; };
        public string EuropeanExerciseStyle { get { return ExerciseStyle_ } set { ExerciseStyle_ = value; };
        public int NumberScenarios { get { return NumberScenarios_ } 
        set { NumberScenarios_ = value; };
        public bool UseBrownBridge { get { return UseBrownBridge_ } 
        set { UseBrownBridge_ = value; };

        protected double Strike_f_d = 0.0;
        protected double Barrier_f_d = 0.0;
        protected string ForeignCurrency_ = "";
        protected string DomesticCurrency_ = "";
        protected string BuySell_ = "";
        protected int NumberOfUnits_ = 0;
        protected double Time_To_Expiry_ = 0.0;
        protected PutCallOptionType OptionType_ = PutCall;
    }
}
```

代码示例 8.16 用于计算外汇障碍期权价值的 C# 代码。

