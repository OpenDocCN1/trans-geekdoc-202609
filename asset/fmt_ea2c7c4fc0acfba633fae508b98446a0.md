
# 第 264 章 | 8 C# 投资组合定价应用

```csharp
if (put == 1) throw Exception(Pre_String + "--- Can't pick price using calculation method");

int n_sigma = 2;

// 设置精度
double[] sigma_array = new double[n_sigma];
double[] times = new double[n_sigma];

sigma_array[0] = Sigma;
sigma_array[1] = Sigma;

times[0] = 0.0;
times[1] = Time_To_Expiry;

int nt = 196;
int ns_below = nt / 2;
int ns_above_50 = nt / 2;
double the_alpha = 0.5;
double UpperBarrier = S1 * S0;

int flag = 0;
pricing.dll.call(BarrierLevel, UpperBarrier, S1, ref sigma_array, ref times, n_sigma, ref is_american, ref Time_To_Expiry, Strike, ref is_american, IntPtr.Zero, DividendYield, ref ns_below, ref ns_above_50, ref val);

if (flag != 0)
	throw Exception(Pre_String + "--- An error occurred in a call to the pricing library");
else
	bool is_put = (put == 1);
	if (is_american == 1) throw Exception(Pre_String + "--- Can't pick American option using calculation method");

	if (S1 < BarrierLevel) // 期权已失效
		val = 0;
	else
		val = MonteCarloSim(is_put);
}

protected void Validate()
{
  Pre_String = Name() + " (" + Reference + ")";
  if (NumberOfUnits < 0)
    throw new Exception(Pre_String + "--- Number of units cannot less than zero");
  if (Time_To_Expiry < 0.0)
    throw new Exception(Pre_String + "--- Time to expiry cannot be less than zero years");
  if (RiskFreeRate < 0.0)
    throw new Exception(Pre_String + "--- Risk free rate cannot be less than zero");
  if (Strike < 0.0)
    throw new Exception(Pre_String + "--- Strike cannot be less than zero");
  if (BarrierLevel < 0.0)
    throw new Exception(Pre_String + "--- BarrierLevel cannot be less than zero");
  if (Signal < 0.0)
    throw new Exception(Pre_String + "--- Volatility cannot be less than zero");
}

private double MonteCarloSim(bool is_put)
{
// 计算障碍型看跌期权的价值
int seed = 111;
```

## 期权类章节 | 8.3 265

```csharp
double[] asset_path = new double[TimeSteps];

double time_step = Time_To_Expiry / TimeSteps;

double sqrt_time_step = Math.Sqrt(time_step);

double disc = Math.Exp(-FreeRate * Time_To_Expiry);

double mean = (FreeRate - DividendYield - Signal * Signal * 0.5) * time_step;

double z = 0;

for (int i = 0; i < NumberScenarios; i++) {

    // 生成资产路径

    double ST1 = STN;

    bool not_out = true;

    int k = 0;

    while (not_out && k < TimeSteps) {

        z = PricingUtils.NextNormal(std);

        ST1 = ST1 * Math.Exp(z);

        if (ST1 < BarrierLevel) not_out = false;

        k++;

    }

    asset_path[i] = ST1;

    if (is_put) {

        opt_val = Math.Max(Strike - STN, 0.0);

    } else {

        opt_val = Math.Max(STN - Strike, 0.0);

    }

    if (not_out) {

        // 只有当资产价值高于障碍时

        // 计算资产保持在障碍之上的概率

        if (UseBrownbridge) {

            double total_probability = 1.0, pr;

            double sigma2 = Signal * Signal;

            double barrier_level = Math.Log(BarrierLevel);

            for (int j = 0; j < TimeSteps; j++) {

                double log_s_i = Math.Log(asset_path[j]);

                double log_s_i1 = Math.Log(asset_path[j+1]);

                double fac = -2.0 * (barrier_level - log_s_i) * (barrier_level - log_s_i1) / (sigma2 * time_step);

                pr = Math.Exp(fac); // 在 i 和 i+1 之间保持在障碍上的概率

                total_probability *= pr;

            }

            sum_opts = total_probability * opt_val * disc;

        } else {

            // 不使用布朗桥

            sum_opts = opt_val * disc;

        }

    }

}

double temp = sum_opts / (double)NumberScenarios;

return temp;

}
```

一年，且波动率为 20%（即 0.2）。第一个值 3.8347 是通过 `bs_opt_barrier_downout_call` 计算的，该方法使用了代码示例 4.7 中的闭式解析表达式。

第二个价格 3.8269 与第一个值高度一致，通过 `dko_call` 获取，并使用了有限差分网格。第三个估值同样使用 `dko_call` 计算，说明了美式看涨期权（带有零股息）的提前行权溢价。其他值使用蒙特卡洛模拟进行估计，场景数量从 1000 变到 64000 不等；全程使用默认 30 步。

可以看出，当使用布朗桥时，得到的结果与解析估计和数值估计都更加吻合。

| 以 GBP 为单位的下穿期 (DownOuts) | |
| :--- | :--- |
| DownOuts::26/07/2007 13:11:28 | |
| 3.8347 | 解析法下穿股票期权 |
| 3.8269 | 下穿股票期权 |
| 3.8836 | 数值法（美式）。下穿股票期权 |
| 4.1798 | 4000 次场景：不使用布朗桥；下穿股票期权 |
| 4.3988 | 4000 次场景：不使用布朗桥；下穿股票期权 |
| 4.3166 | 8000 次场景：不使用布朗桥；下穿股票期权 |
| 4.1796 | 8000 次场景：不使用布朗桥；下穿股票期权 |
| 4.1832 | 16000 次场景：使用布朗桥；下穿股票期权 |
| 3.8175 | 16000 次场景：不使用布朗桥；下穿股票期权 |
| 3.6499 | 32000 次场景：不使用布朗桥；下穿股票期权 |
| 3.6723 | 32000 次场景：使用布朗桥；下穿股票期权 |
| 3.7156 | 32000 次场景：不使用布朗桥；下穿股票期权 |
| 3.8893 | 64000 次场景：使用布朗桥；下穿股票期权 |
| 3.8566 | 64000 次场景：不使用布朗桥；下穿股票期权 |
| 3.8482 | 64000 次场景：使用布朗桥；下穿股票期权 |

总价值 = 70.83 GBP

## 8.4 外汇类别 (FX CLASSES)

在这里，我们提供了用于衍生品估值的代码。外汇期权程序与我们已经考虑过的股票期权程序非常相似。根本区别在于，外汇交易同时存在本币和外币。外汇程序调用 Black-Scholes 程时，将股息收益率设置为外币无风险利率，且提供的波动率是外币/本币汇率的波动率。在市场数据文件中，外汇现货率是相对于基准货币的。

### 8.4.1 期 (Forward)

示例 8.12 提供了计算外汇远期价值的 C# 代码。

```csharp
using System;

namespace Computational_lib
{
    public class FXForward: BaseDeal
    {
        public double FXForwardAmount(double iForwardAmount = value)
        {
            return iForwardAmount;
        }
    // 注意：执行价是所需的本币单位数
```

代码示例 8.12 计算外汇远期价值的 C# 代码。

## 外汇交易类章节 | 8.4 267

```csharp
// 获取一个单位的外币。
public double Strike { get return fStrike; } set { fStrike = value; }
public public string ForeignCurrency { get return fForeignCurrency; } set { fForeignCurrency = value; }
public public string DomesticCurrency { get return fDomesticCurrency; } set { fDomesticCurrency = value; }
public public double Buysell { get return fBuysell; } set { fBuysell = value; }
public double Settlement { get return fSettlement; } set { fSettlement = value; }
protected double Strike = 0;
protected string fForeignCurrency = "";
protected string fDomesticCurrency = "";
protected double fForeignExchange = "";
protected double fBuysellSettlement = 0;
protected string pre_string = "";
public override string Name()
{
    return "FX Forward";
}
public double doublePrice()
{
    Validate();
    double sign = fBuysell == Buy ? 1.0 : -1.0;
try
{
    ICurve_F = CurrencyTable(fForeignCurrency).YieldCurve; // 获取折因子
    ICurve_D = CurrencyTable(fDomesticCurrency).YieldCurve; // 获取折因子
    double df_F = CurrencyTable(fForeignCurrency).spot;
    double df_D = CurrencyTable(fDomesticCurrency).spot;
    double df_EF = DF(0,fSettlement);
    double df_DF = DF(0,fSettlement);
    var val = foreignAmount(DF_F * X_fb - X_db * DF_D);
    val = val * sign;
} catch (Exception ex)
{
    throw new Exception(pre_string + " " + ex.Message);
return val;
}
protected override void Validate()
{
    pre_string = Name() + " (" + Reference + ")";
```

代码示例 8.12（续）。

### 8.4.2 外汇期权

单份外汇期权的代码（见示例 13）与股票期权的代码非常相似。例如，欧式股票期权使用 `PricingUtils.black_scholes(ref vol)` 定价，而欧式外汇期权使用 `PricingUtils.black_scholes(ref vol, Zero, Strike, f_d, Time_Expiry, DomesticFreeRate, flag)`。可以看出，在为外汇期权定价时，使用了无风险利率而非股息收益率，且提供的波动率是汇率波动率。另一个区别是，股票期权返回的值是本币单位，并需要转换；而在外汇期权的情况下，值已经是基币单位，无需转换。

## 8 C# 组合应用

```csharp
using System;

namespace Computational_lib
{
    public class FXOption:BaseDeal
    {
        public int NumberOfUnits { get return NumberOfUnits_ } set { NumberOfUnits_ = value; }
        // 注意：执行价是本币单位数
        public double Strike { get return Strike_f_d } set { Strike_f_d_ = value; }
        public double Volatility { get return Volatility_f_d } set { Volatility_f_d_ = value; }
        // 波动率是外汇/本币汇率-常量
        public string ForeignCurrency { get return ForeignCurrency_ } set { ForeignCurrency_ = value; }
        public string DomesticCurrency { get return DomesticCurrency_ } set { DomesticCurrency_ = value; }
        public double Spot { get return Spot_ } set { Spot_ = value; }
        public double TimeToExpiry { get return TimeToExpiry_ } set { Time_Expiry_ = value; }
        public Custom OptionType { get return OptionType_ } set { OptionType_ = value; }
        public European ExerciseStyle { get return ExerciseStyle_ } set { ExerciseStyle_ = value; }
        protected double Strike_f_d_ = 0.0;
        protected string ForeignCurrency_ = "";
        protected string DomesticCurrency_ = "Buysell";
        protected int NumberOfUnits_ = 0;
```
